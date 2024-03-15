
# Gas Optimizations

| Number | Issue | Instances |
|--------|-------|-----------|
|[G-01]| Precompute Off-Chain When Possible  | 6 |
|[G-02]| Check Arguments Early | 3 |
|[G-03]| Don’t make variables public unless necessary | 19 |
|[G-04]| Greater or Equal Comparison Costs Less Gas than Greater Comparison | 24 |
|[G-05]| Initialize Variables With Default Value | 14 |
|[G-06]| Avoid zero transfers | 3 |
|[G-07]| Use named returns for local variables of pure functions where it is possible | 5 |
|[G-08]| Refactor functions to combine events to reduce gas cost | 1 |
|[G-09]| Use assembly in place of abi.decode to extract calldata values more efficiently | 13  |
|[G-10]| Using calldata instead of memory for read-only arguments in external functions saves gas | 10  |
|[G-11]| Using assembly to revert with an error message | 2 |
|[G-12]| Shorten arrays with inline assembly | 3 |
|[G-13]| Use hardcoded address instead of address(this) | 35  |
|[G-14]| Do not calculate Constant  | 16 |






## [G-1]   Precompute Off-Chain When Possible

Computing values in advance outside the blockchain is cheaper than doing it inside smart contracts:

<details>

```solidity
// On-chain computation
function verify(uint numA, uint numB) {
  require(numA * numB < 1000);
}

// Precomputed off-chain
function verify(uint result) {
  require(result < 1000); 
}
```
</details>

Do computations like hashes, signatures outside.
Pass in precomputed values to save on-chain gas.s

```solidity
file:  blob/main/src/V3Oracle.sol

338   if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0) {

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L338


```solidity
file: blob/main/src/V3Vault.sol

1227    if (
                    collateralValueLimitFactorX32 < type(uint32).max
                        && _convertToAssets(tokenConfigs[token0].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
                            > lentAssets * collateralValueLimitFactorX32 / Q32
                ) 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1227-L1231


```solidity
file: blob/main/src/transformers/AutoRange.sol

243    if (state.amount0 - state.amountAdded0 > 0) {

246    if (state.amount1 - state.amountAdded1 > 0) {

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L243

```solidity
file: blob/main/src/transformers/AutoRange.sol

166   if (
            state.currentTick < state.tickLower - config.lowerTickLimit
                || state.currentTick >= state.tickUpper + config.upperTickLimit
        )

174  if (
                baseTick + config.lowerTickDelta == state.tickLower
                    && baseTick + config.upperTickDelta == state.tickUpper
            )

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L166-L169

## [G-2] Check Arguments Early

Checks that if() or revert() statements that check input arguments are at the top of the function. Checks that involve constants should come before checks that involve state variables, function calls, and calculations. By doing these checks first, the function is able to revert before wasting a gas load in a function that may ultimately revert in the unhappy case.


### check the maxDifferenceX10000 function parameter first 

```solidity
file: blob/main/src/V3Oracle.sol

147  if (differenceX10000 >= maxDifferenceX10000) {
            revert PriceDifferenceExceeded();
        }

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L147-L149

### check the token function parameter first 

```solidity
file: blob/main/src/V3Oracle.sol

112  if (token0 == token) {

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L112


```solidity
file: blob/main/src/V3Vault.sol

774   if (amount > available) {
            revert InsufficientLiquidity();
        }
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L774-L776

## [G-3] Don’t make variables public unless necessary

Issue Description - Making variables public comes with some overhead costs that can be avoided in many cases. A public variable implicitly creates a public getter function of the same name, increasing the contract size.

Proposed Optimization - Only mark variables as public if their values truly need to be readable by external contracts/users. Otherwise, use private or internal visibility.

Estimated Gas Savings - The savings from avoiding unnecessary public variables are small per transaction, around 5-10 gas. However, this adds up over many transactions targeting a contract with public state variables that don’t need to be public.
```solidity
file: blob/main/src/V3Oracle.sol

58  address public immutable factory;

59  INonfungiblePositionManager public immutable nonfungiblePositionManager;

62  address public immutable referenceToken;

63  uint8 public immutable referenceTokenDecimals;

68  address public immutable chainlinkReferenceToken;

71  address public emergencyAdmin;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L58

```solidity
file: blob/main/src/V3Vault.sol

47  INonfungiblePositionManager public immutable nonfungiblePositionManager;

50  IUniswapV3Factory public immutable factory;

53  IInterestRateModel public immutable interestRateModel;

56  IV3Oracle public immutable oracle;

59  IPermit2 public immutable permit2;

62  address public immutable override asset;

65  uint8 private immutable assetDecimals;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L47

```solidity
file: blob/main/src/transformers/V3Utils.sol

19   IPermit2 public immutable permit2;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L19

```solidity
file: blob/main/src/utils/Swapper.sol

21  IWETH9 public immutable weth;

23  address public immutable factory;

26  INonfungiblePositionManager public immutable nonfungiblePositionManager;

29  address public immutable zeroxRouter;

32  address public immutable universalRouter;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L21

## [G-4] Greater or Equal Comparison Costs Less Gas than Greater Comparison

In Solidity, the >= operator costs less gas than the > operator. This is because the Solidity compiler uses the LT opcode for >= comparisons, which requires less gas than the combination of GT and ISZERO opcodes used for > comparisons. Therefore, replacing > with >= when possible can reduce the gas cost of your contract.

```solidity
file: blob/main/src/InterestRateModel.sol

88  if (
            baseRatePerYearX96 > MAX_BASE_RATE_X96 || multiplierPerYearX96 > MAX_MULTIPLIER_X96
                || jumpMultiplierPerYearX96 > MAX_MULTIPLIER_X96
        )

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L88-L91

```solidity
file: blob/main/src/V3Vault.sol

571  if (debtSharesTotal > _convertToShares(globalDebtLimit, newDebtExchangeRateX96, Math.Rounding.Down)) {

574  if (assets > dailyDebtIncreaseLimitLeft) {

774  if (amount > available) {

860  if (collateralFactorX32 > MAX_COLLATERAL_FACTOR_X32) {

906  if (totalSupply() > globalLendLimit) {

910  if (assets > dailyLendIncreaseLimitLeft) {

1131 if (reserveCost > reserves) {

1155 if (block.timestamp > lastExchangeRateUpdate) {

1216  if (oldShares > newShares) {

1249  if (force || time > dailyLendIncreaseLimitLastReset) {

1261  if (force || time > dailyDebtIncreaseLimitLastReset) {

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L571

```solidity
file: blob/main/src/automators/Automator.sol

91  if (_maxTWAPTickDifference > MAX_TWAP_TICK_DIFFERENCE) {

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L91

```solidity
file: blob/main/src/transformers/AutoCompound.sol

258  if (amount > currentBalance) {

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L258

```solidity
file: blob/main/src/transformers/AutoRange.sol

280  if (config.lowerTickDelta > config.upperTickDelta) {

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L280

```solidity
file: blob/main/src/transformers/LeverageTransformer.sol

87  if (amount0 > added0) {

90  if (amount1 > added1) {

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L87

```solidity
file: blob/main/src/transformers/V3Utils.sol

671  if (amountAdded0 > amount0) {

676  if (amountAdded1 > amount1) {

681  if (amountAddedOther > amountOther) {

690  if (amount0 > amountAdded0) {

693  if (amount1 > amountAdded1) {

696  if (
            amountOther > amountAddedOther && address(otherToken) != address(0) && token0 != otherToken

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L671


## [G-5] Initialize Variables With Default Value

It costs more gas to initialize variables to their default values than to let the default be applied.


```solidity
file: blob/main/src/V3Vault.sol

118   uint32 public reserveFactorX32 = 0;

124   uint256 public debtSharesTotal = 0;

127   uint256 public lastExchangeRateUpdate = 0;

131   uint256 public globalDebtLimit = 0;

132   uint256 public globalLendLimit = 0;

135   uint256 public minLoanSize = 0;

138   uint256 public dailyLendIncreaseLimitMin = 0;

139   uint256 public dailyLendIncreaseLimitLeft = 0;

140   uint256 public dailyLendIncreaseLimitLastReset = 0;

143   uint256 public dailyDebtIncreaseLimitMin = 0;

144   uint256 public dailyDebtIncreaseLimitLeft = 0;

145   uint256 public dailyDebtIncreaseLimitLastReset = 0;

161   uint256 private transformedTokenId = 0;

542   transformedTokenId = 0;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L118


## [G-6] Avoid zero transfers

In Solidity, performing unnecessary operations can consume more gas than needed, leading to cost inefficiencies. For instance, if a transfer function doesn’t have a zero amount check and someone calls it with a zero amount, unnecessary gas will be consumed in executing the function, even though the state of the contract remains the same. By implementing a zero amount check, such unnecessary function calls can be avoided, thereby saving gas and making the contract more efficient. Amounts should be checked for 0 before calling a transfer Checking non-zero transfer values can avoid an expensive external call and save gas. I suggest adding a non-zero-value.

```solidity
file: blob/main/src/automators/Automator.sol

226  SafeERC20.safeTransfer(token, to, amount);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L226

```solidity
file: blob/main/src/transformers/AutoCompound.sol

272  SafeERC20.safeTransfer(IERC20(token), to, amount);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L272

```solidity
file: blob/main/src/transformers/V3Utils.sol

872  SafeERC20.safeTransfer(token, to, amount);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L872

## [G-7] Use named returns for local variables of pure functions where it is possible

```solidity
file: blob/main/src/V3Vault.sol

264  function loanCount(address owner) external view override returns (uint256) {
        return ownedTokens[owner].length;
    }
  
271   function loanAtIndex(address owner, uint256 index) external view override returns (uint256) {
        return ownedTokens[owner][index];
    }

277  function decimals() public view override(IERC20Metadata, ERC20) returns (uint8) {
        return assetDecimals;
    }
  
284  function totalAssets() public view override returns (uint256) {
        return IERC20(asset).balanceOf(address(this));
    }

392  function maxRedeem(address owner) external view override returns (uint256) {
        return balanceOf(owner);
    }

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L264-L266 


## [G-8] Refactor functions to combine events to reduce gas cost

In scenarios where a function emits multiple event but these events are only emitted by that function we can combine these events to a single event in doing this we would save at least 1 Glog0 375 gas units

Combine the events in V3Utils.execute() to reduce gas cost

The V3Utils.execute() function emits three events CompoundFees,ChangeRange and WithdrawAndCollectAndSwap but these events are only emitted in this function. We can make the V3Utils.execute() function more gas efficient if we combine these CompoundFees,ChangeRange and TreasuryUpdated events to a single event.

```solidity 
file: blob/main/src/transformers/V3Utils.sol

115  function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {
        (,, address token0, address token1,,,, uint128 liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);

        uint256 amount0;
        uint256 amount1;
        if (instructions.liquidity != 0) {
            (amount0, amount1) = _decreaseLiquidity(
                tokenId,
                instructions.liquidity,
                instructions.deadline,
                instructions.amountRemoveMin0,
                instructions.amountRemoveMin1
            );
        }
        (amount0, amount1) = _collectFees(
            tokenId,
            IERC20(token0),
            IERC20(token1),
            instructions.feeAmount0 == type(uint128).max
                ? type(uint128).max
                : (amount0 + instructions.feeAmount0).toUint128(),
            instructions.feeAmount1 == type(uint128).max
                ? type(uint128).max
                : (amount1 + instructions.feeAmount1).toUint128()
        );

        // check if enough tokens are available for swaps
        if (amount0 < instructions.amountIn0 || amount1 < instructions.amountIn1) {
            revert AmountError();
        }

        if (instructions.whatToDo == WhatToDo.COMPOUND_FEES) {
            if (instructions.targetToken == token0) {
                (liquidity, amount0, amount1) = _swapAndIncrease(
                    SwapAndIncreaseLiquidityParams(
                        tokenId,
                        amount0,
                        amount1,
                        instructions.recipient,
                        instructions.deadline,
                        IERC20(token1),
                        instructions.amountIn1,
                        instructions.amountOut1Min,
                        instructions.swapData1,
                        0,
                        0,
                        "",
                        instructions.amountAddMin0,
                        instructions.amountAddMin1,
                        ""
                    ),
                    IERC20(token0),
                    IERC20(token1),
                    instructions.unwrap
                );
            } else if (instructions.targetToken == token1) {
                (liquidity, amount0, amount1) = _swapAndIncrease(
                    SwapAndIncreaseLiquidityParams(
                        tokenId,
                        amount0,
                        amount1,
                        instructions.recipient,
                        instructions.deadline,
                        IERC20(token0),
                        0,
                        0,
                        "",
                        instructions.amountIn0,
                        instructions.amountOut0Min,
                        instructions.swapData0,
                        instructions.amountAddMin0,
                        instructions.amountAddMin1,
                        ""
                    ),
                    IERC20(token0),
                    IERC20(token1),
                    instructions.unwrap
                );
            } else {
                // no swap is done here
                (liquidity, amount0, amount1) = _swapAndIncrease(
                    SwapAndIncreaseLiquidityParams(
                        tokenId,
                        amount0,
                        amount1,
                        instructions.recipient,
                        instructions.deadline,
                        IERC20(address(0)),
                        0,
                        0,
                        "",
                        0,
                        0,
                        "",
                        instructions.amountAddMin0,
                        instructions.amountAddMin1,
                        ""
                    ),
                    IERC20(token0),
                    IERC20(token1),
                    instructions.unwrap
                );
            }
            emit CompoundFees(tokenId, liquidity, amount0, amount1);
        } else if (instructions.whatToDo == WhatToDo.CHANGE_RANGE) {
            if (instructions.targetToken == token0) {
                (newTokenId,,,) = _swapAndMint(
                    SwapAndMintParams(
                        IERC20(token0),
                        IERC20(token1),
                        instructions.fee,
                        instructions.tickLower,
                        instructions.tickUpper,
                        amount0,
                        amount1,
                        instructions.recipient,
                        instructions.recipientNFT,
                        instructions.deadline,
                        IERC20(token1),
                        instructions.amountIn1,
                        instructions.amountOut1Min,
                        instructions.swapData1,
                        0,
                        0,
                        "",
                        instructions.amountAddMin0,
                        instructions.amountAddMin1,
                        instructions.swapAndMintReturnData,
                        ""
                    ),
                    instructions.unwrap
                );
            } else if (instructions.targetToken == token1) {
                (newTokenId,,,) = _swapAndMint(
                    SwapAndMintParams(
                        IERC20(token0),
                        IERC20(token1),
                        instructions.fee,
                        instructions.tickLower,
                        instructions.tickUpper,
                        amount0,
                        amount1,
                        instructions.recipient,
                        instructions.recipientNFT,
                        instructions.deadline,
                        IERC20(token0),
                        0,
                        0,
                        "",
                        instructions.amountIn0,
                        instructions.amountOut0Min,
                        instructions.swapData0,
                        instructions.amountAddMin0,
                        instructions.amountAddMin1,
                        instructions.swapAndMintReturnData,
                        ""
                    ),
                    instructions.unwrap
                );
            } else {
                // no swap is done here
                (newTokenId,,,) = _swapAndMint(
                    SwapAndMintParams(
                        IERC20(token0),
                        IERC20(token1),
                        instructions.fee,
                        instructions.tickLower,
                        instructions.tickUpper,
                        amount0,
                        amount1,
                        instructions.recipient,
                        instructions.recipientNFT,
                        instructions.deadline,
                        IERC20(address(0)),
                        0,
                        0,
                        "",
                        0,
                        0,
                        "",
                        instructions.amountAddMin0,
                        instructions.amountAddMin1,
                        instructions.swapAndMintReturnData,
                        ""
                    ),
                    instructions.unwrap
                );
            }
            emit ChangeRange(tokenId, newTokenId);
        } else if (instructions.whatToDo == WhatToDo.WITHDRAW_AND_COLLECT_AND_SWAP) {
            uint256 targetAmount;
            if (token0 != instructions.targetToken) {
                (uint256 amountInDelta, uint256 amountOutDelta) = _routerSwap(
                    Swapper.RouterSwapParams(
                        IERC20(token0),
                        IERC20(instructions.targetToken),
                        amount0,
                        instructions.amountOut0Min,
                        instructions.swapData0
                    )
                );
                if (amountInDelta < amount0) {
                    _transferToken(instructions.recipient, IERC20(token0), amount0 - amountInDelta, instructions.unwrap);
                }
                targetAmount += amountOutDelta;
            } else {
                targetAmount += amount0;
            }
            if (token1 != instructions.targetToken) {
                (uint256 amountInDelta, uint256 amountOutDelta) = _routerSwap(
                    Swapper.RouterSwapParams(
                        IERC20(token1),
                        IERC20(instructions.targetToken),
                        amount1,
                        instructions.amountOut1Min,
                        instructions.swapData1
                    )
                );
                if (amountInDelta < amount1) {
                    _transferToken(instructions.recipient, IERC20(token1), amount1 - amountInDelta, instructions.unwrap);
                }
                targetAmount += amountOutDelta;
            } else {
                targetAmount += amount1;
            }

            // send complete target amount
            if (targetAmount != 0 && instructions.targetToken != address(0)) {
                _transferToken(
                    instructions.recipient, IERC20(instructions.targetToken), targetAmount, instructions.unwrap
                );
            }

            emit WithdrawAndCollectAndSwap(tokenId, instructions.targetToken, targetAmount);
        } else {
            revert NotSupportedWhatToDo();
        }
    }

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L115-L352

## [G-9] Use assembly in place of abi.decode to extract calldata values more efficiently

Instead of using abi.decode, we can use assembly to decode our desired calldata values directly. This will allow us to avoid decoding calldata values that we will not use.

```solidity
file: blob/main/src/V3Vault.sol

444   owner = abi.decode(data, (address));

719   abi.decode(params.permitData, (ISignatureTransfer.PermitTransferFrom, bytes));

895   abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));

980   abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L444

```solidity
file: blob/main/src/transformers/V3Utils.sol

370   Instructions memory instructions = abi.decode(data, (Instructions));

404   abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));

478   abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));

541   abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L370

```solidity
file: blob/main/src/utils/FlashloanLiquidator.sol

70   FlashCallbackData memory data = abi.decode(callbackData, (FlashCallbackData));

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L70

```solidity
file: blob/main/src/utils/Swapper.sol

82   (address router, bytes memory routerData) = abi.decode(params.swapData, (address, bytes));

85    ZeroxRouterData memory data = abi.decode(routerData, (ZeroxRouterData));

96   UniversalRouterData memory data = abi.decode(routerData, (UniversalRouterData));

160  (address tokenIn, address tokenOut, uint24 fee) = abi.decode(data, (address, address, uint24));

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L82

## [G-10] Using calldata instead of memory for read-only arguments in external functions saves gas

When a function with a memory array is called externally, the abi.decode() step has to use a for-loop to copy each index of the calldata to the memory index. Each iteration of this for-loop costs at least 60 gas (i.e. 60 * <mem_array>.length). Using calldata directly, obliviates the need for such a loop in the contract code and runtime execution.


```solidity
file: blob/main/src/V3Vault.sol

170   string memory name,

171   string memory symbol,

954   function _repay(uint256 tokenId, uint256 amount, bool isShare, bytes memory permitData) internal {

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L170


```solidity
file: blob/main/src/transformers/V3Utils.sol

98    function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)

115   function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) 

598   function _prepareAddPermit2(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther,
        IPermit2.PermitBatchTransferFrom memory permit,
        bytes memory signature
    ) internal {

705  function _swapAndMint(SwapAndMintParams memory params, bool unwrap)

779   function _swapAndPrepareAmounts(SwapAndMintParams memory params, bool unwrap)

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L98

```solidity
file: blob/main/src/utils/Swapper.sol

73   function _routerSwap(RouterSwapParams memory params)

132  function _poolSwap(PoolSwapParams memory params) internal returns (uint256 amountInDelta, uint256 amountOutDelta) {

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L73

## [G-11] Using assembly to revert with an error message

Issue Description - When reverting in solidity code, it is common practice to use a require or revert statement to revert execution with an error message. This can in most cases be further optimized by using assembly to revert with the error message.

Estimated Gas Savings - Here’s an example:

```solidity
/// calling restrictedAction(2) with a non-owner address: 24042
contract SolidityRevert {
    address owner;
    uint256 specialNumber = 1;
    constructor() {
        owner = msg.sender;
    }
    function restrictedAction(uint256 num)  external {
        require(owner == msg.sender, "caller is not owner");
        specialNumber = num;
    }
}
/// calling restrictedAction(2) with a non-owner address: 23734
contract AssemblyRevert {
    address owner;
    uint256 specialNumber = 1;
    constructor() {
        owner = msg.sender;
    }
    function restrictedAction(uint256 num)  external {
        assembly {
            if sub(caller(), sload(owner.slot)) {
                mstore(0x00, 0x20) // store offset to where length of revert message is stored
                mstore(0x20, 0x13) // store length (19)
                mstore(0x40, 0x63616c6c6572206973206e6f74206f776e657200000000000000000000000000) // store hex representation of message
                revert(0x00, 0x60) // revert with data
            }
        }
        specialNumber = num;
    }
}
```
From the example above, we can see that we get a gas saving of over 300 gas when reverting with the same error message with assembly against doing so in solidity. This gas savings come from the memory expansion costs and extra type checks the solidity compiler does under the hood.

```solidity
file: blob/main/src/transformers/AutoCompound.sol

244   require(_totalRewardX64 <= totalRewardX64, ">totalRewardX64");

269   require(amount <= balance, "amount>balance");

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L244

## [G-12] Shorten arrays with inline assembly

Issue Description - When shortening an array in Solidity, it creates a new shorter array and copies the elements over. This wastes gas by duplicating storage.

Proposed Optimization - Use inline assembly to shorten the array in place by changing its length slot, avoiding the need to copy elements to a new array.

Estimated Gas Savings - Shortening a length-n array avoids ~n SSTORE operations to copy elements. Benchmarking shows savings of 5000-15000 gas depending on original length.

```solidity
function shorten(uint[] storage array, uint newLen) internal {
  assembly {
    sstore(array_slot, newLen)
  }
}
// Rather than:
function shorten(uint[] storage array, uint newLen) internal {
  uint[] memory newArray = new uint[](newLen);
  for(uint i = 0; i < newLen; i++) {
    newArray[i] = array[i];
  }
  delete array;
  array = newArray;
}
```
Using inline assembly allows shortening arrays without copying elements to a new storage slot, providing significant gas savings.

```solidity
file: blob/main/src/V3Oracle.sol

365   uint32[] memory secondsAgos = new uint32[](2);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L365

```solidity 
file:  blob/main/src/automators/Automator.sol

181   uint32[] memory secondsAgos = new uint32[](2);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L181

```solidity 
file: blob/main/src/transformers/V3Utils.sol

613    ISignatureTransfer.SignatureTransferDetails[] memory transferDetails =
            new ISignatureTransfer.SignatureTransferDetails[](permit.permitted.length);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L613-L614

## [G-13] Use hardcoded address instead of address(this)

Instead of using address(this), it is more gas-efficient to pre-calculate and use the hardcoded address. Foundry’s script.sol and solmate’s LibRlp.sol contracts can help achieve this. Refrences

```solidity
file: blob/main/src/V3Vault.sol

285  return IERC20(asset).balanceOf(address(this));

401  nonfungiblePositionManager.safeTransferFrom(msg.sender, address(this), tokenId, abi.encode(recipient));

423  nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);

424  nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));

435  if (msg.sender != address(nonfungiblePositionManager) || from == address(this)) {

532  if (owner != address(this)) {

561  if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {

722  ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost),

728  SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);

791  transformer == address(0) || transformer == address(this) || transformer == asset

897  permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature

901  SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);

982  permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature

986  SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L285


```solidity
file: blob/main/src/automators/Automator.sol

112  uint256 balance = IERC20(tokens[i]).balanceOf(address(this));

128  uint256 balance = address(this).balance;

209  INonfungiblePositionManager.CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max)

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L112


```solidity
file: blob/main/src/transformers/AutoCompound.sol

92    params.tokenId, address(this), abi.encodeWithSelector(AutoCompound.execute.selector, params)

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L92


```solidity
file: blob/main/src/transformers/AutoRange.sol

102  params.tokenId, address(this), abi.encodeWithSelector(AutoRange.execute.selector, params)

232  nonfungiblePositionManager.safeTransferFrom(address(this), state.owner, state.newTokenId);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L102

```solidity
file: blob/main/src/transformers/V3Utils.sol

106  nonfungiblePositionManager.permit(address(this), tokenId, instructions.deadline, v, r, s);

367  if (from == address(this)) {

376   nonfungiblePositionManager.safeTransferFrom(address(this), from, tokenId, instructions.returnData);

578   SafeERC20.safeTransferFrom(token0, msg.sender, address(this), needed0);

581  SafeERC20.safeTransferFrom(token1, msg.sender, address(this), needed1);

584  SafeERC20.safeTransferFrom(otherToken, msg.sender, address(this), neededOther);

618   state.balanceBefore0 = token0.balanceOf(address(this));

619  transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed0);
        }
622  state.balanceBefore1 = token1.balanceOf(address(this));

623    transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed1);

626   state.balanceBeforeOther = otherToken.balanceOf(address(this));

627      transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.neededOther);
        }

635     if (token0.balanceOf(address(this)) - state.balanceBefore0 != state.needed0) {

640   if (token1.balanceOf(address(this)) - state.balanceBefore1 != state.needed1) {

645      if (otherToken.balanceOf(address(this)) - state.balanceBeforeOther != state.neededOther) {

727   nonfungiblePositionManager.safeTransferFrom(address(this), params.recipientNFT, tokenId, params.returnData);


```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L106


## [G-14] Do not calculate Constant 

```solidity
file: blob/main/src/InterestRateModel.sol

12   uint256 private constant Q96 = 2 ** 96;

15   uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10; // 10%

16   uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L12

```solidity
file: blob/main/src/V3Oracle.sol

27   uint256 private constant Q96 = 2 ** 96;

26    uint256 private constant Q128 = 2 ** 128;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L27


```solidity
file: blob/main/src/V3Vault.sol

33     uint256 private constant Q32 = 2 ** 32;
    uint256 private constant Q96 = 2 ** 96;

    uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%

    uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
    uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%

    uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%

    uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%
    uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L33-L44


```solidity
file: blob/main/src/automators/Automator.sol

20  uint256 internal constant Q64 = 2 ** 64;

21  uint256 internal constant Q96 = 2 ** 96;

```

https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L20


```solidity
file: blob/main/src/transformers/AutoCompound.sol
 
47   uint64 public constant MAX_REWARD_X64 = uint64(Q64 / 50); // 2%

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L47