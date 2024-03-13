## [G-01] `Unauthorized` check in `V3Vault::borrow` should be moved right below the `bool isTransformMode` declaration line to save gas in case of failure.

The function below performs 2 internal functions calls (`_updateGlobalInterest` and `_resetDailyDebtIncreaseLimit`) and a SLOAD before executing the `if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender)` check:
```
function borrow(uint256 tokenId, uint256 assets) external override {
        bool isTransformMode =
            transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];

        (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();

        _resetDailyDebtIncreaseLimit(newLendExchangeRateX96, false);

        Loan storage loan = loans[tokenId];

        // if not in transfer mode - must be called from owner or the vault itself
@>        if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {
@>            revert Unauthorized();
        }
```

That check could be moved right after [Line 552](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L552) to save gas in case of failure.

Please paste the following test into `V3Vault.t.sol`:
```
    function testBorrowUnauthorized() external {
        // 0 borrow loan
        uint256 amount = 1e6;
        _setupBasicLoan(false);

        (,, uint256 collateralValue,,) = vault.loanInfo(TEST_NFT);

        vm.assume(amount <= collateralValue * 100);

        uint256 debtLimit = vault.globalDebtLimit();
        uint256 increaseLimit = vault.dailyDebtIncreaseLimitMin();

        if (amount > debtLimit) {
            vm.expectRevert(IErrors.GlobalDebtLimit.selector);
        } else if (amount > increaseLimit) {
            vm.expectRevert(IErrors.DailyDebtIncreaseLimit.selector);
        } else if (amount > collateralValue) {
            vm.expectRevert(IErrors.CollateralFail.selector);
        }

        vm.prank(TEST_NFT_ACCOUNT);
        vm.expectRevert(IErrors.Unauthorized.selector);
        vault.borrow(0, amount); //NFT id hardcoded to 0 to make the function fail
    }
```
When snapshoting the before and after we get the following:
```
testBorrowUnauthorized() (gas: -2707 (-0.488%))
```
#### Recommendation

```diff
    function borrow(uint256 tokenId, uint256 assets) external override {
        bool isTransformMode =
            transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];

++        if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {
++            revert Unauthorized();

        (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();

        _resetDailyDebtIncreaseLimit(newLendExchangeRateX96, false);

        Loan storage loan = loans[tokenId];

        // if not in transfer mode - must be called from owner or the vault itself
--        if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {
--            revert Unauthorized();
        }
```

## [G-02] `V3Vault::liquidate` can be optimized by moving the `if (debtShares != params.debtShares)`

The function liquidate first performs the `transformedTokenId > 0` check, then loads `state` into memory then calls `_updateGlobalInterest()`. Only after these operations it reads the `debtShares` and then checks them against the input `params.debtShares`:

```
    function liquidate(LiquidateParams calldata params) external override returns (uint256 amount0, uint256 amount1) {
        // liquidation is not allowed during transformer mode
        if (transformedTokenId > 0) {
            revert TransformNotAllowed();
        }

        LiquidateState memory state;

        (state.newDebtExchangeRateX96, state.newLendExchangeRateX96) = _updateGlobalInterest();

@>        uint256 debtShares = loans[params.tokenId].debtShares;
@>        if (debtShares != params.debtShares) {
@>            revert DebtChanged();
        }
```
The check should be moved right after [Line 687-689](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L687-L689) check in order to optimize the gas consumption in case of failure.

Please paste the following test into `V3Vault.t.sol`:
```
    function testLiquidationDebtChanged() public {
        _setupBasicLoan(true);
        LiquidationType lType = LiquidationType.TimeBased;
        (, uint256 fullValue, uint256 collateralValue,,) = vault.loanInfo(TEST_NFT);
        assertEq(collateralValue, 8847206);
        assertEq(fullValue, 9830229);

        // debt is equal collateral value
        (uint256 debt,,, uint256 liquidationCost, uint256 liquidationValue) = vault.loanInfo(TEST_NFT);
        assertEq(debt, collateralValue);
        assertEq(liquidationCost, 0);
        assertEq(liquidationValue, 0);

        if (lType == LiquidationType.TimeBased) {
            // wait 7 day - interest growing
            vm.warp(block.timestamp + 7 days);
        } else if (lType == LiquidationType.ValueBased) {
            // collateral DAI value change -100%
            vm.mockCall(
                CHAINLINK_DAI_USD,
                abi.encodeWithSelector(AggregatorV3Interface.latestRoundData.selector),
                abi.encode(uint80(0), int256(0), block.timestamp, block.timestamp, uint80(0))
            );
        } else {
            vault.setTokenConfig(address(DAI), uint32(Q32 * 2 / 10), type(uint32).max); // 20% collateral factor
        }

        if (lType == LiquidationType.ValueBased) {
            // should revert because oracle and pool price are different
            vm.expectRevert(IErrors.PriceDifferenceExceeded.selector);
            (debt, fullValue, collateralValue, liquidationCost, liquidationValue) = vault.loanInfo(TEST_NFT);

            // ignore difference - now it will work
            oracle.setMaxPoolPriceDifference(10001);
        }

        // debt is greater than collateral value
        (debt, fullValue, collateralValue, liquidationCost, liquidationValue) = vault.loanInfo(TEST_NFT);

        vm.prank(WHALE_ACCOUNT);
        USDC.approve(address(vault), liquidationCost - 1);

        (uint256 debtShares) = vault.loans(TEST_NFT);

        vm.prank(WHALE_ACCOUNT);
        USDC.approve(address(vault), liquidationCost);

        uint256 daiBalance = DAI.balanceOf(WHALE_ACCOUNT);
        uint256 usdcBalance = USDC.balanceOf(WHALE_ACCOUNT);

        vm.prank(WHALE_ACCOUNT);
        vm.expectRevert(IErrors.DebtChanged.selector);
        vault.liquidate(IVault.LiquidateParams(TEST_NFT, 0, 0, 0, WHALE_ACCOUNT, "")); //`debtShares` variable has been hardcoded to 0 to make the check fail.
    }
```

When snapshoting the before and after we get the following:
```
testLiquidationDebtChanged() (gas: -18216 (-2.053%))
```

#### Recommendation

```diff
    function liquidate(LiquidateParams calldata params) external override returns (uint256 amount0, uint256 amount1) {
        // liquidation is not allowed during transformer mode
        if (transformedTokenId > 0) {
            revert TransformNotAllowed();
        }

++       uint256 debtShares = loans[params.tokenId].debtShares;
++        if (debtShares != params.debtShares) {
++            revert DebtChanged();
++        }

        LiquidateState memory state;

        (state.newDebtExchangeRateX96, state.newLendExchangeRateX96) = _updateGlobalInterest();

--        uint256 debtShares = loans[params.tokenId].debtShares;
--        if (debtShares != params.debtShares) {
--            revert DebtChanged();
--        }
```

## [G-03]
