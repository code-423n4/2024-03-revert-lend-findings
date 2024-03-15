### [Gas-01] `tokenConfigs[token]` could be used as `storage` rather than re-calling it again
```diff
    function setTokenConfig(address token, uint32 collateralFactorX32, uint32 collateralValueLimitFactorX32)
        external
        onlyOwner
    {
        if (collateralFactorX32 > MAX_COLLATERAL_FACTOR_X32) {
            revert CollateralFactorExceedsMax();
        }
+       TokenConfig storage config = tokenConfigs[token];

-       tokenConfigs[token].collateralFactorX32 = collateralFactorX32; 
-       tokenConfigs[token].collateralValueLimitFactorX32 = collateralValueLimitFactorX32;

+       config.collateralFactorX32 = collateralFactorX32; 
+       config.collateralValueLimitFactorX32 = collateralValueLimitFactorX32;
        emit SetTokenConfig(token, collateralFactorX32, collateralValueLimitFactorX32);
    }
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L863-L864
```

### [Gas-02] Some state varible could be cached in memory rather than calling it again and again in same function

#### `nonfungiblePositionManager` could be cached in multiple functions and in multiple contracts
```diff
    function _sendPositionValue(
        uint256 tokenId,
  .....
.......
+       INonfungiblePositionManager _nonfungiblePositionManager = nonfungiblePositionManager;
        // if full position is liquidated - no analysis needed
        if (liquidationValue == fullValue) {
-           (,,,,,,, liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);

+           (,,,,,,, liquidity,,,,) = _nonfungiblePositionManager.positions(tokenId);
            fees0 = type(uint128).max;
            fees1 = type(uint128).max;
        } 
....
....

        if (liquidity > 0) {
-           nonfungiblePositionManager.decreaseLiquidity( 

+           _nonfungiblePositionManager.decreaseLiquidity( 
                INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp)
            );
        }

-       (amount0, amount1) = nonfungiblePositionManager.collect(
+       (amount0, amount1) = _nonfungiblePositionManager.collect(
            INonfungiblePositionManager.CollectParams(tokenId, recipient, fees0, fees1)
        );
    }
```
```File: V3Vault.sol```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1045
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1065
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1070
```

```File: Automator.sol```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L202
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L208
```

```File: AutoCompound.sol```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L163
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L108
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L116
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L201
```

```File: LevarageTransformer.sol```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L47
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L77
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L78
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L84
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L125
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L134
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L142
```

#### `dailyLendIncreaseLimitMin` could be cached in memory
```diff
    function _resetDailyLendIncreaseLimit(uint256 newLendExchangeRateX96, bool force) internal {
        // daily lend limit reset handling
        uint256 time = block.timestamp / 1 days;
        if (force || time > dailyLendIncreaseLimitLastReset) {
...
...
+           uint256 _dailyLendIncreaseLimitMin = dailyLendIncreaseLimitMin;
-           dailyLendIncreaseLimitLeft =
                dailyLendIncreaseLimitMin > lendIncreaseLimit ? dailyLendIncreaseLimitMin : lendIncreaseLimit; 

+           dailyLendIncreaseLimitLeft =
                _dailyLendIncreaseLimitMin > lendIncreaseLimit ? _dailyLendIncreaseLimitMin : lendIncreaseLimit;
            dailyLendIncreaseLimitLastReset = time;
        }
    }

    function _resetDailyDebtIncreaseLimit(uint256 newLendExchangeRateX96, bool force) internal {
...
...
+           uint256 _dailyLendIncreaseLimitMin = dailyLendIncreaseLimitMin;
            dailyDebtIncreaseLimitLeft =
-               dailyDebtIncreaseLimitMin > debtIncreaseLimit ? dailyDebtIncreaseLimitMin : debtIncreaseLimit; 
+               _dailyDebtIncreaseLimitMin > debtIncreaseLimit ? _dailyDebtIncreaseLimitMin : debtIncreaseLimit; 
            dailyDebtIncreaseLimitLastReset = time;
        }
    }
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1253
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1265
```

#### `PoolAddress` could be cached in memory
```diff
function _getPool(address tokenA, address tokenB, uint24 fee) internal view returns (IUniswapV3Pool) {
        return IUniswapV3Pool(PoolAddress.computeAddress(address(factory), PoolAddress.getPoolKey(tokenA, tokenB, fee))); 
    }
```
```File: Swapper.sol```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L172
```

#### `Swapper` could be chached in `memory` in case of 2nd `else-if` it will be gas efficient as it calls 2 times `Swapper.`
```diff
    function _swapAndPrepareAmounts(SwapAndMintParams memory params, bool unwrap)
        internal
        returns (uint256 total0, uint256 total1)
    {
        if (params.swapSourceToken == params.token0) {
            if (params.amount0 < params.amountIn1) {
                revert AmountError();
            }
            (uint256 amountInDelta, uint256 amountOutDelta) = _routerSwap( 
                Swapper.RouterSwapParams( // @audit G:: chace Swapper
                    params.token0, params.token1, params.amountIn1, params.amountOut1Min, params.swapData1
                )
            );
            total0 = params.amount0 - amountInDelta;
            total1 = params.amount1 + amountOutDelta;
        } else if (params.swapSourceToken == params.token1) {
            if (params.amount1 < params.amountIn0) {
                revert AmountError();
            }
            (uint256 amountInDelta, uint256 amountOutDelta) = _routerSwap(
                Swapper.RouterSwapParams(
                    params.token1, params.token0, params.amountIn0, params.amountOut0Min, params.swapData0
                )
            );
            total1 = params.amount1 - amountInDelta;
            total0 = params.amount0 + amountOutDelta;
        } else if (address(params.swapSourceToken) != address(0)) {
            (uint256 amountInDelta0, uint256 amountOutDelta0) = _routerSwap(
                Swapper.RouterSwapParams(
                    params.swapSourceToken, params.token0, params.amountIn0, params.amountOut0Min, params.swapData0
                )
            );
            (uint256 amountInDelta1, uint256 amountOutDelta1) = _routerSwap(
                Swapper.RouterSwapParams(
                    params.swapSourceToken, params.token1, params.amountIn1, params.amountOut1Min, params.swapData1
                )
            );
...
...
```
```File: V3Utils.sol```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L788
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L807
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L812
```


### [Gas-03] No need to create memory variable as result could directly used
```diff
    function _checkApprovals(address token0, address token1) internal {
        // approve tokens once if not yet approved - to save gas during compounds
-       uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager)); 
-       if (allowance0 == 0) {
+       if (IERC20(token0).allowance(address(this), address(nonfungiblePositionManager)) == 0) {
            SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max);
        }
-       uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager)); // @audit G::
-       if (allowance1 == 0) {
+       if (IERC20(token1).allowance(address(this), address(nonfungiblePositionManager)); == 0) {
            SafeERC20.safeApprove(IERC20(token1), address(nonfungiblePositionManager), type(uint256).max);
        }
    }
```
```File: AutoCompound.sol```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L278
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L282
```


#### No need to create `amountToPay` variable
```diff
function uniswapV3SwapCallback(int256 amount0Delta, int256 amount1Delta, bytes calldata data) external override {
        require(amount0Delta > 0 || amount1Delta > 0);
...
...
        // transfer needed amount of tokenIn
-       uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta); 
-       SafeERC20.safeTransfer(IERC20(tokenIn), msg.sender, amountToPay);

+       SafeERC20.safeTransfer(IERC20(tokenIn), msg.sender, amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta));
```
```File: Swapper.sol```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L166
```

### [Gas-04] Instead of reading state `enum` multiple times those `enum could cached into memory

Here `Mode.CHAINLINK_TWAP_VERIFY` & `Mode.TWAP_CHAINLINK_VERIFY` could both cached into memory storage rather than fetching those from storage multiple times.

```diff
function _getReferenceTokenPriceX96(address token, uint256 cachedChainlinkReferencePriceX96)
        internal
        view
        returns (uint256 priceX96, uint256 chainlinkReferencePriceX96)
    {
        if (token == referenceToken) {
            return (Q96, chainlinkReferencePriceX96);
        }

        TokenConfig memory feedConfig = feedConfigs[token];

        if (feedConfig.mode == Mode.NOT_SET) {
            revert NotConfigured();
        }

        uint256 verifyPriceX96;

        bool usesChainlink = (
            feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY // @audit G:: can these mode be cached
                || feedConfig.mode == Mode.CHAINLINK
        );
        bool usesTWAP = (
            feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY
                || feedConfig.mode == Mode.TWAP
        );

        if (usesChainlink) {
            uint256 chainlinkPriceX96 = _getChainlinkPriceX96(token);
            chainlinkReferencePriceX96 = cachedChainlinkReferencePriceX96 == 0
                ? _getChainlinkPriceX96(referenceToken)
                : cachedChainlinkReferencePriceX96;

            chainlinkPriceX96 = (10 ** referenceTokenDecimals) * chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96
                / (10 ** feedConfig.tokenDecimals);

            if (feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY) {
                verifyPriceX96 = chainlinkPriceX96;
            } else {
                priceX96 = chainlinkPriceX96;
            }
        }

        if (usesTWAP) {
            uint256 twapPriceX96 = _getTWAPPriceX96(feedConfig);
            if (feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY) {
                verifyPriceX96 = twapPriceX96;
            } else {
                priceX96 = twapPriceX96;
            }
        }

        if (feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY) {
            _requireMaxDifference(priceX96, verifyPriceX96, feedConfig.maxDifference);
        }
    }
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L290
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L294
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L307
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L316
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L323

```

### [Gas-05] Struct can be optimizable

#### `PositionState` struct could be optimized and save 1 storage slot via decreasing size of `feeGrowthInside0LastX128` and `feeGrowthInside1LastX128` variable.
```diff
 struct PositionState {
...
...
-       uint256 feeGrowthInside0LastX128; 
-       uint256 feeGrowthInside1LastX128;

+       uint128 feeGrowthInside0LastX128; 
+       uint128 feeGrowthInside1LastX128;
...
...
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L384
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L385
```

#### Struct can be re-arrange to save 1 extra storage slot
`bool swap0To1` here `bool` present between 2 `uints` so it consume 1 whole slot,
We could move that to other small ones(like uint128 or uint64) to save that storage slot.
```diff
    struct ExecuteParams {
        uint256 tokenId;
-       bool swap0To1; // @audit rearrange
        uint256 amountIn; // if this is set to 0 no swap happens
        bytes swapData;
        uint128 liquidity; // liquidity the calculations are based on
        uint256 amountRemoveMin0; // min amount to be removed from liquidity
        uint256 amountRemoveMin1; // min amount to be removed from liquidity
        uint256 deadline; // for uniswap operations - operator promises fair value
+       bool swap0To1;
        uint64 rewardX64; // which reward will be used for protocol, can be max configured amount (considering onlyFees)
    }
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L55
```

#### `uint256 deadline` could be decreased in size, (maybe to uint32/uint64) and struct could re-order to save 1 extra storage slot.

3 instances so `3 storage slot saved`
```diff
struct Instructions {
        // what action to perform on provided Uniswap v3 position
        WhatToDo whatToDo;
        // target token for swaps (if this is address(0) no swaps are executed)
        address targetToken;
        // for removing liquidity slippage
        uint256 amountRemoveMin0;
        uint256 amountRemoveMin1;
        // amountIn0 is used for swap and also as minAmount0 for decreased liquidity + collected fees
        uint256 amountIn0;
        // if token0 needs to be swapped to targetToken - set values
        uint256 amountOut0Min;
        bytes swapData0; // encoded data from 0x api call (address,bytes) - allowanceTarget,data
        // amountIn1 is used for swap and also as minAmount1 for decreased liquidity + collected fees
        uint256 amountIn1;
        // if token1 needs to be swapped to targetToken - set values
        uint256 amountOut1Min;
        bytes swapData1; // encoded data from 0x api call (address,bytes) - allowanceTarget,data
        // collect fee amount for COMPOUND_FEES / CHANGE_RANGE / WITHDRAW_AND_COLLECT_AND_SWAP (if uint256(128).max - ALL)
        uint128 feeAmount0;
        uint128 feeAmount1;
        // for creating new positions with CHANGE_RANGE
        uint24 fee;
        int24 tickLower;
        int24 tickUpper;
        // remove liquidity amount for COMPOUND_FEES (in this case should be probably 0) / CHANGE_RANGE / WITHDRAW_AND_COLLECT_AND_SWAP
        uint128 liquidity;
        // for adding liquidity slippage
        uint256 amountAddMin0;
        uint256 amountAddMin1;
        // for all uniswap deadlineable functions
-       uint256 deadline; // @audit G::
        // left over tokens will be sent to this address
+       uint64 deadline;
        address recipient;
        // recipient of newly minted nft (the incoming NFT will ALWAYS be returned to from)
        address recipientNFT;
        // if tokenIn or tokenOut is WETH - unwrap
        bool unwrap;
        // data sent with returned token to IERC721Receiver (optional)
        bytes returnData;
        // data sent with minted token to IERC721Receiver (optional)
        bytes swapAndMintReturnData;
    }

```
```File: V3Utils.sol```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L79
```
```diff
    struct SwapAndMintParams {
...
...
        address recipient; // recipient of leftover tokens
        address recipientNFT; // recipient of nft
-       uint256 deadline;
+       uint256 deadline;
...
...
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L443
```
```diff
struct SwapAndIncreaseLiquidityParams {
...
...
        address recipient; // recipient of leftover tokens
-       uint256 deadline; 
+       uint64 deadline; 
...
...
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L510
```

### [Gas-06] `memory` variable should created out-side of loop and with each iteration of loop it get overriden. 
In this way every time(each iteration) variable creation costs save
```diff
    function withdrawBalances(address[] calldata tokens, address to) external virtual {
        if (msg.sender != withdrawer) {
            revert Unauthorized();
        }

        uint256 i;
        uint256 count = tokens.length;
+       uint256 balance;
        for (; i < count; ++i) {
-           balance = IERC20(tokens[i]).balanceOf(address(this)); 
            if (balance > 0) {
                _transferToken(to, IERC20(tokens[i]), balance, true);
            }
        }
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L112
```

### [Gas-07] frequently used could refactor into a modifier(in case of msg.sender check) or into a private function.

Below block of code used repeatedly in 2 places in `Automator.sol` contract, so it could be refator into a modifier and used those places.

This could save deployment gas cost and follow DRY-Principle of coding.
```diff
if (msg.sender != withdrawer) { 
            revert Unauthorized();
        }
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L105
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L124
```

### [Gas-08] Mathematical calculation could cached in memory rather than calculating it again
```diff
 (int24 twapTick, bool twapOk) = _getTWAPTick(pool, twapPeriod);
        if (twapOk) {
-          return twapTick - currentTick >= -int16(maxDifference) && twapTick - currentTick <= int16(maxDifference);

+       uint256 res = twapTick - currentTick;
-          return res >= -int16(maxDifference) && res <= int16(maxDifference);
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L173
```

### [Gas-09] If clause check should be present on top, before making external call
```diff
    function withdrawLeftoverBalances(uint256 tokenId, address to) external nonReentrant {
        address owner = nonfungiblePositionManager.ownerOf(tokenId); // @audit cache nonfungiblePositionManager

+       if (owner != msg.sender) { 
+           revert Unauthorized();
+       }

        if (vaults[owner]) {
            owner = IVault(owner).ownerOf(tokenId);
        }
-       if (owner != msg.sender) { 
-           revert Unauthorized();
-       }

        (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(tokenId);
...
...
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L205
```

### [Gas-10] `memory` variable should created after `if` clause, so that if `if` condition failed then gas used for `memory` variable will not wasted
```diff
    function execute(ExecuteParams calldata params) external { 
        if (!operators[msg.sender] && !vaults[msg.sender]) {
            revert Unauthorized();
        }
-       ExecuteState memory state; 
        PositionConfig memory config = positionConfigs[params.tokenId];

        if (config.lowerTickDelta == config.upperTickDelta) {
            revert NotConfigured();
        }

+       ExecuteState memory state;
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L115
```

### [Gas-11] Instead of creating `balance` memory variable 3 times, it can created 1 time and overriden in further steps
```diff
.....
.....
+      uint256 balance;

        // return all leftover tokens to liquidator // @audit G:: create above so that 2 time creation ot occur
        if (data.swap0.tokenIn != data.asset) {
-           uint256 balance = data.swap0.tokenIn.balanceOf(address(this));

+           balance = data.swap0.tokenIn.balanceOf(address(this));
            if (balance > 0) {
                SafeERC20.safeTransfer(data.swap0.tokenIn, data.liquidator, balance);
            }
        }
        if (data.swap1.tokenIn != data.asset) {
-           uint256 balance = data.swap1.tokenIn.balanceOf(address(this));
+           balance = data.swap1.tokenIn.balanceOf(address(this));
            if (balance > 0) {
                SafeERC20.safeTransfer(data.swap1.tokenIn, data.liquidator, balance);
            }
        }
        {
-           uint256 balance = data.asset.balanceOf(address(this));
+           balance = data.asset.balanceOf(address(this));
            if (balance < data.minReward) {
                revert NotEnoughReward();
            }
            if (balance > 0) {
                SafeERC20.safeTransfer(data.asset, data.liquidator, balance);
            }
        }
    }
```
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L89
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L95
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L101
```

