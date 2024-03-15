
## [L-01] Valid collateralValueLimitFactorX32 value will cause a revert

In the `_updateAndCheckCollateral` function, there are 2 checks to make sure that the `collateralValueLimitFactorX32` does not exceed `type(uint32).max`. This is because this maximal value represents a collateral value limit of 100%. 

However in the actual checks, `<` is used instead of `<=`. Meaning a valid value of 100% (type(uint32).max) would cause a revert. 

Even though setting a value of 100% is very unlikely, it remains a valid input and thus should not cause a revert. 


```diff 
                if (
-                    collateralValueLimitFactorX32 < type(uint32).max
+                    collateralValueLimitFactorX32 <= type(uint32).max    
                        && _convertToAssets(tokenConfigs[token0].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up) > lentAssets * collateralValueLimitFactorX32 / Q32
                ) {
                    revert CollateralValueLimit();
                }
                collateralValueLimitFactorX32 = tokenConfigs[token1].collateralValueLimitFactorX32;
                if (
-                    collateralValueLimitFactorX32 < type(uint32).max
+                    collateralValueLimitFactorX32 <= type(uint32).max  
                        && _convertToAssets(tokenConfigs[token1].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
                            > lentAssets * collateralValueLimitFactorX32 / Q32
                ) {
                    revert CollateralValueLimit();
                }
```

## [L-02] No slippage protection in Vault:liquidate

In the `Vault` `liquidate` function, the internal function `_sendPositionValue` is called which calls `nonfungiblePositionManager.decreaseLiquidity` with 100% slippage tolerance.
Meaning MEV bots will take advantage and the liquidity returned will be either extremely small or non-existing. 

This should a High finding, but it is mitigated by another finding. The `_sendPositionValue` does not return the decreased liquidity + fees, but only the fees. 
Which means in 90%+ of the cases, the `amount0` and `amount1` returned will be smaller than `params.amount0Min` and `params.amount1Min` and thus cause a `SlippageError` revert.

``` solidity
    function liquidate(){
        // send promised collateral tokens to liquidator
        (amount0, amount1) =
            _sendPositionValue(params.tokenId, state.liquidationValue, state.fullValue, state.feeValue, msg.sender);

        if (amount0 < params.amount0Min || amount1 < params.amount1Min) {
            revert SlippageError();
        }
    }
    function _sendPositionValue(
        uint256 tokenId,
        uint256 liquidationValue,
        uint256 fullValue,
        uint256 feeValue,
        address recipient
    ) internal returns (uint256 amount0, uint256 amount1) {
        uint128 liquidity;
        uint128 fees0;
        uint128 fees1;

        // if full position is liquidated - no analysis needed
        if (liquidationValue == fullValue) {
            (,,,,,,, liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);
            fees0 = type(uint128).max;
            fees1 = type(uint128).max;
        } else {
            (,,, liquidity,,, fees0, fees1) = oracle.getPositionBreakdown(tokenId);

            // only take needed fees
            if (liquidationValue < feeValue) { 
                liquidity = 0;
                fees0 = uint128(liquidationValue * fees0 / feeValue);
                fees1 = uint128(liquidationValue * fees1 / feeValue);
            } else {
                // take all fees and needed liquidity
                fees0 = type(uint128).max; 
                fees1 = type(uint128).max; 
                liquidity = uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue));
            }
        }

        if (liquidity > 0) {
            nonfungiblePositionManager.decreaseLiquidity(
                INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp)
            );
        }

        (amount0, amount1) = nonfungiblePositionManager.collect(
            INonfungiblePositionManager.CollectParams(tokenId, recipient, fees0, fees1)
        );
    }
```

## [L-03] Inconsistent Lending rounding in view functions

The `vaultInfo` function calculates the total lent by Rounding Up `_convertToAssets`. 


```solidity 
    function vaultInfo()
        external
        view
        override
        returns (
            uint256 debt,
            uint256 lent,
            uint256 balance,
            uint256 available,
            uint256 reserves,
            uint256 debtExchangeRateX96,
            uint256 lendExchangeRateX96
        )
    {
        (debtExchangeRateX96, lendExchangeRateX96) = _calculateGlobalInterest();
        (balance, available, reserves) = _getAvailableBalance(debtExchangeRateX96, lendExchangeRateX96);

        debt = _convertToAssets(debtSharesTotal, debtExchangeRateX96, Math.Rounding.Up);
        lent = _convertToAssets(totalSupply(), lendExchangeRateX96, Math.Rounding.Up);
    }
```

Yet the `lendInfo` function calculates the lend by Rounding Down `_convertTaAssets`.


```solidity 

    function lendInfo(address account) external view override returns (uint256 amount) {
        (, uint256 newLendExchangeRateX96) = _calculateGlobalInterest();
        amount = _convertToAssets(balanceOf(account), newLendExchangeRateX96, Math.Rounding.Down);
    }
```
As a result, the sum of all loans requested through `lendInfo` will be smaller than `vaultInfo`. The difference is minute, but I recommend changing the rounding of `vaultInfo` in order to be consistent.




## [L-04] Liquidaty does not need to be calculated when fees == liquidationValue

- In the `_sendPositionValue` function, a check is performed to see whether the fees cover the liquidation value. If not, liquidity is calculated and decreased. However, in the check  `<` is used instead of `<=`, meaning liquidity will be calculated when fees == liquidationValue.   

This is unnecessary so I recommend it being changed. 

```diff 
            // only take needed fees
-            if (liquidationValue < feeValue) {
+            if (liquidationValue <= feeValue) {  
                liquidity = 0;
                fees0 = uint128(liquidationValue * fees0 / feeValue);
                fees1 = uint128(liquidationValue * fees1 / feeValue);

```

## [L-05] Limit set to low in _requireMaxDifference

The `_requireMaxDifference` function checks for price manipulation by comparing a calculated difference with a maxDifference and reverting when it exceeds. 

Yet in the if statement we see that `>=` is used instead of `>`, meaning a price difference equal to the maxDifference will cause a revert. Since the maxDifference should be an valid value, I recommend the following change: 

```diff 
    function _requireMaxDifference(uint256 priceX96, uint256 verifyPriceX96, uint256 maxDifferenceX10000)
        internal
        pure
    {
        uint256 differenceX10000 = priceX96 > verifyPriceX96 ? (priceX96 - verifyPriceX96) * 10000 / priceX96 : (verifyPriceX96 - priceX96) * 10000 / verifyPriceX96; 
        // if too big difference - revert
-        if (differenceX10000 >= maxDifferenceX10000) {
+        if (differenceX10000 > maxDifferenceX10000) {
            revert PriceDifferenceExceeded();
        }
    }


```
## [L-06] onERC721Received not compliant with EIP721
 onERC721Received is missing the "operator" named input param. This has no actual effect but is not in line with the EIP721 standard.

 ```solidity
     function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4) 
 ```
## [L-07] _sendPositionValue does not return correct amounts

The `_sendPositionValue` function is supposed to return the total amount of collateral tokens transferred to the liquidator, but it only returns the fees. 

``` solidity
    function liquidate(){
        // send promised collateral tokens to liquidator
        (amount0, amount1) =
            _sendPositionValue(params.tokenId, state.liquidationValue, state.fullValue, state.feeValue, msg.sender);

        if (amount0 < params.amount0Min || amount1 < params.amount1Min) {
            revert SlippageError();
        }
    }
    function _sendPositionValue(
        uint256 tokenId,
        uint256 liquidationValue,
        uint256 fullValue,
        uint256 feeValue,
        address recipient
    ) internal returns (uint256 amount0, uint256 amount1) {
        uint128 liquidity;
        uint128 fees0;
        uint128 fees1;

        // if full position is liquidated - no analysis needed
        if (liquidationValue == fullValue) {
            (,,,,,,, liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);
            fees0 = type(uint128).max;
            fees1 = type(uint128).max;
        } else {
            (,,, liquidity,,, fees0, fees1) = oracle.getPositionBreakdown(tokenId);

            // only take needed fees
            if (liquidationValue < feeValue) { 
                liquidity = 0;
                fees0 = uint128(liquidationValue * fees0 / feeValue);
                fees1 = uint128(liquidationValue * fees1 / feeValue);
            } else {
                // take all fees and needed liquidity
                fees0 = type(uint128).max; 
                fees1 = type(uint128).max; 
                liquidity = uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue));
            }
        }

        if (liquidity > 0) {
            nonfungiblePositionManager.decreaseLiquidity(
                INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp)
            );
        }

        (amount0, amount1) = nonfungiblePositionManager.collect(
            INonfungiblePositionManager.CollectParams(tokenId, recipient, fees0, fees1)
        );
    }
```




## [NC-01] sqrtPriceX96 is set but never used

There are several instances where sqrtPriceX96 is set in a struct or returned from a function but not used. 
This should be cleaned up since unforeseen side-effect could lead to serious security vulnerabilities. 

-  `V3Oracle:_initalizeState`, the sqrtPriceX96 is set in the PositionState struct but is never accessed.
-  `AutoCompound:execute` the slot0 sqrtPriceX96 is set in the ExecuteParams struct, but is never used.
-  `Automator:_validateSwap` slot0 sqrtPriceX96 is returned from the function, but the sqrtPriceX96 output is never used whenever _validateSwap is called.

## [NC-02] Incorrect naming and Natspec of loanInfo

The `_requireMaxDifference` states Natspec & naming this returns information about one loan. 

But function code clearly takes all loans against one collateral position, and returns variables based on the sum of loans on a a position. Thereby giving a user erroneous understanding of their actual situation.

I recommend changing the natspec and naming to correctly reflect the code. 

## [NC-03] lacking permit2 functions

- `withdraw` and `redeem` are the only functions to not have a permit2 version. Even though the use-case is rare, for completeness those version should be added.


## [NC-04] Incorrect code comments

In two place in `V3Vault`, code comments are made suggesting the "vault itself" can perform an action. These are outdated comments dating from a change in logic dating several weeks ago and should be removed for clarity. 


```solidity
        // only the owner of the loan, the vault itself or any approved caller can call this 
        if (loanOwner != msg.sender && !transformApprovals[loanOwner][tokenId][msg.sender]) {
            revert Unauthorized();
        }

        // if not in transfer mode - must be called from owner or the vault itself
        if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {
            revert Unauthorized();
        }
```


