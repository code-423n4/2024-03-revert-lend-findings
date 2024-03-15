### [Gas-0] `tokenConfigs[token]` could be used as `storage` rather than re-calling it again
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

### [Gas-0] Some state varible could be cached in memory rather than calling it again and again in same function

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

### [Gas-0] Mapping could cached in memory rather than recalling it again
```diff
   
```
```File: .sol```
```

```

### [Gas-0] No need to create memory variable as result could directly used
```diff
```
```
```

### [Gas-0] Instead of reading state `enum` multiple times those `enum could cached into memory

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

### [Gas-0] Struct can be optimizable

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

### [Gas-0] `memory` variable should created out-side of loop and with each iteration of loop it get overriden. 
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

### [Gas-0] frequently used could refactor into a modifier(in case of msg.sender check) or into a private function.

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

### [Gas-0] Mathematical calculation could cached in memory rather than calculating it again
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

### [Gas-0]
```diff
```
```
```

### [Gas-0]
```diff
```
```
```

### [Gas-0]
```diff
```
```
```

### [Gas-0]
```diff
```
```
```

### [Gas-0]
```diff
```
```
```

### [Gas-0]
```diff
```
```
```

### [Gas-0]
```diff
```
```
```
