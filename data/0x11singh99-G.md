# Gas Optimizations

**Note : _G-01_ and _G-12_ contains only those instances which were missed by bot. Since they are major gas savings so I included those missed instances. Gas Mentioned in these findings title is total gas saved by all instances of that finding covered in this report.**

## Table of Contents

- [G-01] [State variables can be packed into fewer storage slot by reducing their size (**Gas Saved: ~8000 Gas**)(Instances missed by bot)](#g-01-state-variables-can-be-packed-into-fewer-storage-slots-by-reducing-their-sizes-gas-saved-8000-gasinstances-missed-by-bot)

- [G-02] [State variable can be packed into fewer storage slots by truncating timestamp(**Gas Saved: ~2000 Gas**)](#g-02-state-variable-can-be-packed-into-fewer-storage-slots-by-truncating-timestampgas-saved-2000-gas)

- [G-03] [Pack the struct variable into fewer storage slots by re-ordering the variables(**Gas Saved: ~2000 Gas**)](#g-03-pack-the-struct-variables-into-fewer-storage-slots-by-re-ordering-the-variablesgas-saved-2000-gas)

- [G-04] [Refactor `borrow` function to avoid 1 sload](#g-04-refactor-borrow-function-to-avoid-1-sload)

- [G-05] [Refactor `configToken` function to fail early and `saves 1 external call` on failing](#g-05-refactor-configtoken-function-to-fail-early-and-saves-1-external-call-on-failing)
- [G-06] [Cache state variable outside of the else block to save 1 sload(**Gas Saved: ~100 Gas**)](#g-06-cache-state-variable-outside-of-the-else-block-to-save-1-sloadgas-saved-100-gas)
- [G-07] [Use direct global msg.sender instead of taking it as function parameter](#g-07-use-direct-global-msgsender-instead-of-taking-it-as-function-parameter)
- [G-08] [Cache calculations instead of re-calculating saves 3 checked subtraction(**Gas Saved: ~540 Gas**)](#g-08-cache-calculations-instead-of-re-calculating-saves-3-checked-subtraction)
- [G-09] [Struct can be packed into fewer storage slot by truncating time(**Gas Saved: ~4000 Gas**)](#g-09-struct-can-be-packed-into-fewer-storage-slot-by-truncating-timegas-saved-4000-gas)
- [G-10] [Make `calculation` constant instead of calculating every time on function call(**Gas Saved: ~540 Gas**)](#g-10-make-calculation-constant-instead-of-calculating-every-time-on-function-call-saves-1-checked-multiplication)
- [G-11] [`Check` before updating `bool` with same value](#g-11-check-before-updating-bool-with-same-value)
- [G-12] [Switch the order around && to use shortcircuit to save gas(Instances missed by bot)](#g-12-switch-the-order-around--to-use-shortcircuit-to-save-gasinstances-missed-by-bot)
- [G-13] [No need to cache a function call if used only once](#g-13-no-need-to-cache-a-function-call-if-used-only-once)

## Auditor's Disclaimer :

All these findings are good findings and 100% safe to implement at no security/logic risk. They all are found by thorough manual review.

## [G-01] State variables can be packed into fewer storage slots by reducing their sizes (**Gas Saved: ~8000 Gas**)(_Instances missed by bot_)

The EVM works with 32 byte words. Variables less than 32 bytes can be declared next to each other in storage and this will pack the values together into a single 32 byte storage slot (if values combined are <= 32 bytes). If the variables packed together are retrieved together in functions (more likely with structs), we will effectively save ~2000 gas with every subsequent SLOAD for that storage slot. This is due to us incurring a Gwarmaccess (100 gas) versus a Gcoldsload (2100 gas).

### `SAVE: ~8000 GAS, 4 SLOT`

### `multiplierPerSecondX96`, `baseRatePerSecondX96` and `jumpMultiplierPerSecondX96` can be packed in single slot by reducing their sizes to `uint80` each `SAVES: ~4000 Gas, 2 Slot`

All these three variables are set inside only `setValues` function where a check is implemented for passed function params and then after dividing by `YEAR_SECS` constant values are assigned into these state variables. It will make sure that `multiplierPerSecondX96`, `baseRatePerSecondX96` and `jumpMultiplierPerSecondX96` maximum values can be `MAX_MULTIPLIER_X96 / YEAR_SECS`, `MAX_BASE_RATE_X96 / YEAR_SECS` and `MAX_MULTIPLIER_X96 / YEAR_SECS` respectively not more than that.
Since these constants are defined in same contract. So their approx. values are
`MAX_MULTIPLIER_X96 / YEAR_SECS` < 10\*\*22
`MAX_BASE_RATE_X96 / YEAR_SECS` < 7.5\*10\*\*20  
While `uint80` can hold > ~10\*\*24  
So we can easily say that `uint80` is sufficient to hold these max values So we can safely reduce the above mentioned storage var. sizes to each `uint80` to pack all three into 1 slot and **save 2 Storage slots**.

```solidity
File : InterestRateModel.sol

23:    uint256 public multiplierPerSecondX96;
24:    uint256 public baseRatePerSecondX96;
25:    uint256 public jumpMultiplierPerSecondX96;

```

[InterestRateModel.sol#L23-L25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L23-L25)

**Relevant code to prove why these state var. can be truncated**

```solidity
File : InterestRateModel.sol

13:  uint256 public constant YEAR_SECS = 31557600; // taking into account leap years
14:
15:  uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10; // 10%
16:  uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%
...
...

82:  function setValues(
         uint256 baseRatePerYearX96,
         uint256 multiplierPerYearX96,
         uint256 jumpMultiplierPerYearX96,
         uint256 _kinkX96
87:     ) public onlyOwner {
88:    if (
89:        baseRatePerYearX96 > MAX_BASE_RATE_X96 || multiplierPerYearX96 > MAX_MULTIPLIER_X96
90:             || jumpMultiplierPerYearX96 > MAX_MULTIPLIER_X96
91:        ) {
92:            revert InvalidConfig();
93:        }
94:
95:  baseRatePerSecondX96 = baseRatePerYearX96 / YEAR_SECS;
96:  multiplierPerSecondX96 = multiplierPerYearX96 / YEAR_SECS;
97:  jumpMultiplierPerSecondX96 = jumpMultiplierPerYearX96 / YEAR_SECS;

```

[InterestRateModel.sol#L13-L16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L13-L16), [InterestRateModel.sol#L88-L97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L88-L97)

**Recommended Mitigation Steps:**

```diff
File : InterestRateModel.sol

-23:    uint256 public multiplierPerSecondX96;
-24:    uint256 public baseRatePerSecondX96;
-25:    uint256 public jumpMultiplierPerSecondX96;
+23:    uint80 public multiplierPerSecondX96;
+24:    uint80 public baseRatePerSecondX96;
+25:    uint80 public jumpMultiplierPerSecondX96;

```

### `dailyLendIncreaseLimitLastReset` and `dailyDebtIncreaseLimitLastReset` can be packed with `reserveProtectionFactorX32` `SAVES: ~4000 Gas, 2 Slot`

Since values in these variables are only assigned in `_resetDailyLendIncreaseLimit` and `_resetDailyDebtIncreaseLimit` functions respectively with the value of `block.timestamp/1 Days` for both So it is sufficient to hold these values in `uint32`. So reduce those var. sizes to uint32 each and pack with `reserveProtectionFactorX32` **Saves 2 Storage Slots**

```solidity
File : V3Vault.sol


121: uint32 public reserveProtectionFactorX32 = MIN_RESERVE_PROTECTION_FACTOR_X32;
...
...
140: uint256 public dailyLendIncreaseLimitLastReset = 0;
...
145: uint256 public dailyDebtIncreaseLimitLastReset = 0;
```

[V3Vault.sol#L121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L121), [V3Vault.sol#L140-L145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L140-L145)

**Recommended Mitigation Steps:**

```diff
File : V3Vault.sol


121: uint32 public reserveProtectionFactorX32 = MIN_RESERVE_PROTECTION_FACTOR_X32;
+140: uint32 public dailyLendIncreaseLimitLastReset = 0;
+145: uint32 public dailyDebtIncreaseLimitLastReset = 0;
...
...
-140: uint256 public dailyLendIncreaseLimitLastReset = 0;
...
-145: uint256 public dailyDebtIncreaseLimitLastReset = 0;
```

## [G-02] State variable can be packed into fewer storage slots by truncating timestamp(**Gas Saved: ~2000 Gas**)

The EVM works with 32 byte words. Variables less than 32 bytes can be declared next to each other in storage and this will pack the values together into a single 32 byte storage slot (if values combined are <= 32 bytes). If the variables packed together are retrieved together in functions (more likely with structs), we will effectively save ~2000 gas with every subsequent SLOAD for that storage slot. This is due to us incurring a Gwarmaccess (100 gas) versus a Gcoldsload (2100 gas).

### Truncate uint256 `lastExchangeRateUpdate` to `uint64` and can be packed with address `emergencyAdmin` `SAVES: ~2000 Gas, 1 Slot`

`lastExchangeRateUpdate` can safely be truncated to `uint64` since it holds timestamp. `uint64` is much more sufficient to hold realistic time. It can also saves **1 Storage slot**.

A `uint64` data type can represent values from `0` to `18,446,744,073,709,551,615`. To convert this range into years we need to define the unit of time being represented.

If we consider seconds then: 1 year = 31,536,000 seconds

So the maximum value a uint64 can represent in years is:

18,446,744,073,709,551,615 seconds / 31,536,000 seconds per year ≈ `584,942,417 years`

This is an astronomically large value and far exceeds any practical use case in most software applications including smart contracts. Therefore for most practical purposes a uint64 range is sufficient for representing `time durations` in years.

```solidity
File : V3Vault.sol

127:  uint256 public lastExchangeRateUpdate = 0;
...
167:  address public emergencyAdmin;
```

[V3Vault.sol#L127](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L127), [V3Vault.sol#L167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L167)

**Recommended Mitigation Steps:**

```diff
File : V3Vault.sol

-127:  uint256 public lastExchangeRateUpdate = 0;
...
167:  address public emergencyAdmin;
+127:  uint64 public lastExchangeRateUpdate = 0;
```

## [G-03] Pack the struct variables into fewer storage slots by re-ordering the variables(**Gas Saved: ~2000 Gas**)

To pack the struct efficiently you can rearrange the storage variables to minimize padding between variables. This optimization can help save gas costs by reducing the number of storage slots used.

Below recommended optimization can be made to this struct to save 1 Storage Slot per key in the mapping where this TokenConfig struct used.

_Note: I have tested this by adding test var. of `TokenConfig` type and run forge command `forge inspect src/V3Oracle.sol:V3Oracle storage --pretty` for both struct.Optimized and Un-optimized , Unotimized will take 3 storage slots while optimized one will take only **2 storage slots**._

```solidity
File : V3Oracle.sol

43:  struct TokenConfig {
44:     AggregatorV3Interface feed; // chainlink feed
45:     uint32 maxFeedAge;
46:     uint8 feedDecimals;
47:     uint8 tokenDecimals;
48:     IUniswapV3Pool pool; // reference pool
49:     bool isToken0;
50:     uint32 twapSeconds;
51:     Mode mode;
52:     uint16 maxDifference; // max price difference x10000
53: }

```

[V3Oracle.sol#L43-L53](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L43-L53)

**Recommended Mitigation Steps:**

```diff
File : V3Oracle.sol

43:  struct TokenConfig {
44:     AggregatorV3Interface feed; // chainlink feed
45:     uint32 maxFeedAge;
46:     uint8 feedDecimals;
47:     uint8 tokenDecimals;
+50:     uint32 twapSeconds;
48:     IUniswapV3Pool pool; // reference pool
49:     bool isToken0;
-50:     uint32 twapSeconds;
51:     Mode mode;
52:     uint16 maxDifference; // max price difference x10000
53: }

```

## [G-04] Refactor `borrow` function to avoid 1 sload

Since `transformedTokenId == tokenId` check that both should be equal so we can use tokenId instead of transformedTokenId and check tokenId for 0 and also we don't have check the second condition we can can remove `transformedTokenId == tokenId` this check.

```solidity
File : V3Vault.sol

550: function borrow(uint256 tokenId, uint256 assets) external override {
551:      bool isTransformMode =
552:       transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];

```

[V3Vault.sol#L550-L552](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L550-L552)

**Recommended Mitigation Steps:**

```diff
File : V3Vault.sol

550: function borrow(uint256 tokenId, uint256 assets) external override {
551:      bool isTransformMode =
-552:       transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];
+552:       tokenId > 0 && transformerAllowList[msg.sender];

```

## [G-05] Refactor `configToken` function to fail early and `saves 1 external call` on failing

To refactor the `configToken` function to fail early and save one external call on failing condition. You can move the check for `config.isActive` and the subsequent check for `config.token0TriggerTick >= config.token1TriggerTick` up before the external call to `nonfungiblePositionManager.ownerOf(tokenId)`. This way if any of the conditions fail the function will revert before making the `external call`.

```solidity
File : automators/AutoExit.sol

218:    function configToken(uint256 tokenId, PositionConfig calldata config) external {
219:        address owner = nonfungiblePositionManager.ownerOf(tokenId);
220:        if (owner != msg.sender) {
221:            revert Unauthorized();
222:        }
223:
224:        if (config.isActive) {
225:            if (config.token0TriggerTick >= config.token1TriggerTick) {
226:                revert InvalidConfig();
227:            }
228:        }
```

[AutoExit.sol#L218-L228](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L218-L228)

**Recommended Mitigation Steps:**

```diff
File : automators/AutoExit.sol

218:    function configToken(uint256 tokenId, PositionConfig calldata config) external {
+224:        if (config.isActive) {
+225:            if (config.token0TriggerTick >= config.token1TriggerTick) {
+226:                revert InvalidConfig();
+227:            }
+228:        }

219:        address owner = nonfungiblePositionManager.ownerOf(tokenId);
220:        if (owner != msg.sender) {
221:            revert Unauthorized();
222:        }
223:
-224:        if (config.isActive) {
-225:            if (config.token0TriggerTick >= config.token1TriggerTick) {
-226:                revert InvalidConfig();
-227:            }
-228:        }
```

## [G-06] Cache state variable outside of the else block to save 1 sload(Gas Saved: ~100 Gas)

Cache `transformedTokenId` outside of the else block saves 1 sload(~100 gas) on above if statement false.

```solidity
File : V3Vault.sol

441: if (transformedTokenId == 0) {
...
450:     } else {
451:          uint256 oldTokenId = transformedTokenId;

```

[V3Vault.sol#L441-L451](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L441-L451)

**Recommended Mitigation Steps:**

```diff
File : V3Vault.sol

+451:          uint256 oldTokenId = transformedTokenId;
441: if (transformedTokenId == 0) {
...
450:     } else {
-451:          uint256 oldTokenId = transformedTokenId;

```

## [G-07] Use direct global msg.sender instead of taking it as function parameter

Use directly `msg.sender` instead of taking it as `owner` function parameter.

```solidity
File : V3Vault.sol

410:    function createWithPermit(
411:        uint256 tokenId,
412:        address owner,
413:        address recipient,
414:        uint256 deadline,
415:        uint8 v,
416:        bytes32 r,
417:        bytes32 s
418:    ) external override {
419:        if (msg.sender != owner) {
420:            revert Unauthorized();
421:        }
422:
423:        nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);
424:        nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));
425:    }

```

[V3Vault.sol#L410-L425](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L410-L425)

**Recommended Mitigation Steps:**

```diff
File : V3Vault.sol

410:    function createWithPermit(
411:        uint256 tokenId,
-412:        address owner,
413:        address recipient,
414:        uint256 deadline,
415:        uint8 v,
416:        bytes32 r,
417:        bytes32 s
418:    ) external override {
-419:        if (msg.sender != owner) {
-420:            revert Unauthorized();
-421:        }
422:
423:        nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);
-424:        nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));
+424:        nonfungiblePositionManager.safeTransferFrom(msg.sender, address(this), tokenId, abi.encode(recipient));
425:    }

```

## [G-08] Cache calculations instead of re-calculating saves 3 checked subtraction

#### Instance 1

Cache `block.timestamp - lastRateUpdate` to save 1 checked subtraction

```solidity
File : V3Vault.sol

1188:    + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;
1189:         newLendExchangeRateX96 = oldLendExchangeRateX96
1190:            + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;

```

V3Vault.sol#L1188-L1190[](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1188-L1190)

**Recommended Mitigation Steps:**

```diff
File : V3Vault.sol

+         uint256 block.timestampSUBlastRateUpdate = block.timestamp - lastRateUpdate;

-1188:    + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;
+1188:    + oldDebtExchangeRateX96 * (block.timestampSUBlastRateUpdate) * borrowRateX96 / Q96;
1189:         newLendExchangeRateX96 = oldLendExchangeRateX96
-1190:            + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;
+1190:            + oldLendExchangeRateX96 * (block.timestampSUBlastRateUpdate) * supplyRateX96 / Q96;

```

#### Instance 2

Cache `SafeCast.toUint192(oldShares - newShares)` and `SafeCast.toUint192(newShares - oldShares)` can save 2 checked subtraction.

```solidity
File : V3Vault.sol


1216:  if (oldShares > newShares) {
1217:      tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1218:      tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1219:  } else {
1220:      tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
1221:      tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);

```

[V3Vault.sol#L1216-L1221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1216-L1221)

**Recommended Mitigation Steps:**

```diff
File : V3Vault.sol

1216:  if (oldShares > newShares) {
+         uint192 safecast_to192_oldShares = SafeCast.toUint192(oldShares - newShares);
-1217:      tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
-1218:      tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
+1217:      tokenConfigs[token0].totalDebtShares -= safecast_to192_oldShares;
+1218:      tokenConfigs[token1].totalDebtShares -= safecast_to192_oldShares;
1219:  } else {
+         uint192 safecast_to192_newshares = SafeCast.toUint192(newShares - oldShares);
-1220:      tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
-1221:      tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
+1220:      tokenConfigs[token0].totalDebtShares += safecast_to192_newshares;
+1221:      tokenConfigs[token1].totalDebtShares += safecast_to192_newshares;

```

## [G-09] Struct can be packed into fewer storage slot by truncating time(Gas Saved: ~4000 Gas)

### `deadline`, `rewardX64` and `liquidity` can be packed in a single slot `SAVES: 4000 Gas, 2 Slot`

You can pack the ExecuteParams struct into fewer storage slots by truncating the `deadline` to a smaller data type such as uint64. `deadline` can be represented within this range.

A `uint64` data type can represent values from `0` to `18,446,744,073,709,551,615`. To convert this range into years we need to define the unit of time being represented.

If we consider seconds then: 1 year = 31,536,000 seconds

So the maximum value a uint64 can represent in years is:

18,446,744,073,709,551,615 seconds / 31,536,000 seconds per year ≈ `584,942,417 years`

This is an astronomically large value and far exceeds any practical use case in most software applications including smart contracts. Therefore for most practical purposes a uint64 range is sufficient for representing `time durations` in years.

```solidity
File : automators/AutoExit.sol

63:    struct ExecuteParams {
64:        uint256 tokenId; // tokenid to process
65:        bytes swapData; // if its a swap order - must include swap data
66:        uint128 liquidity; // liquidity the calculations are based on
67:        uint256 amountRemoveMin0; // min amount to be removed from liquidity
68:        uint256 amountRemoveMin1; // min amount to be removed from liquidity
69:        uint256 deadline; // for uniswap operations - operator promises fair value
70:        uint64 rewardX64; // which reward will be used for protocol, can be max configured amount (considering onlyFees)
71:    }

```

[AutoExit.sol#L63-L71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L63-L71)

**Recommended Mitigation Steps:**

```diff
File : automators/AutoExit.sol

63:    struct ExecuteParams {
64:        uint256 tokenId; // tokenid to process
65:        bytes swapData; // if its a swap order - must include swap data
-66:        uint128 liquidity; // liquidity the calculations are based on
67:        uint256 amountRemoveMin0; // min amount to be removed from liquidity
68:        uint256 amountRemoveMin1; // min amount to be removed from liquidity
-69:        uint256 deadline; // for uniswap operations - operator promises fair value
+69:        uint64 deadline; // for uniswap operations - operator promises fair value
70:        uint64 rewardX64; // which reward will be used for protocol, can be max configured amount (considering onlyFees)
+66:        uint128 liquidity; // liquidity the calculations are based on
71:    }

```

## [G-10] Make `calculation` constant instead of calculating every time on function call `saves 1 checked multiplication`

### Mark `Q96 * Q64` constant saves 1 checked multiplication

You can make the calculation involving `Q96 * Q64` constant. This will avoid recalculating the result every time the function is called saving 1 checked multiplication.

```solidity
File : automators/Automator.sol

158:  amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), priceX96, Q96 * Q64);
```

[Automator.sol#L158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L158)

**Recommended Mitigation Steps:**

```diff
File : automators/Automator.sol

+  // Define Q96_TIMES_Q64 as a constant
+  uint256 constant Q96_TIMES_Q64 = Q96 * Q64;

-158:  amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), priceX96, Q96 * Q64);
+158:  amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), priceX96, Q96_TIMES_Q64);
```

### Make `Q32 + MAX_DAILY_LEND_INCREASE_X32` constant save (~180 Gas)

```solidity
File : V3Vault.sol

1251: * (Q32 + MAX_DAILY_LEND_INCREASE_X32) / Q32;

```

[V3Vault.sol#L1251](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1251)

**Recommended Mitigation Steps:**

```diff
File : V3Vault.sol

+  uint256 constant Q32PlusMAX_DAILY_LEND_INCREASE_X32 = Q32 + MAX_DAILY_LEND_INCREASE_X32;

-1251: * (Q32 + MAX_DAILY_LEND_INCREASE_X32) / Q32;
+1251: * (Q32PlusMAX_DAILY_LEND_INCREASE_X32) / Q32;

```

## [G-11] `Check` before updating `bool` with same value

#### Instance 1

Lack of a check could potentially result in unnecessary state changes and gas costs if the `_active` value passed to the function is the same as the current value stored in the `operators` mapping.

Adding a simple check to compare the new `_active` value with the current value stored in the mapping before updating it could optimize gas usage and prevent unnecessary state changes.

```solidity
File : automators/Automator.sol

69:   function setOperator(address _operator, bool _active) public onlyOwner {
70:       emit OperatorChanged(_operator, _active);
71:        operators[_operator] = _active;
72:    }
```

[Automator.sol#L69-L72](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L69-L72)

**Recommended Mitigation Steps:**

```diff
File : automators/Automator.sol

69:   function setOperator(address _operator, bool _active) public onlyOwner {
+       if (operators[_operator] != _active) {
70:       emit OperatorChanged(_operator, _active);
71:        operators[_operator] = _active;
+         }
72:    }
```

#### Instance 2

As with the previous `Instance 1` there is no explicit check to determine whether the `_active` value being set is different from the current value stored in the `vaults` mapping for the given `_vault` address. This lack of a check could result in unnecessary state changes and gas costs if the `_active` value passed to the function is the same as the current value stored in the mapping.

```solidity
File : automators/Automator.sol

79:    function setVault(address _vault, bool _active) public onlyOwner {
80:      emit VaultChanged(_vault, _active);
81:       vaults[_vault] = _active;
82:    }

```

[Automator.sol#L79-L82](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L79-L82)

**Recommended Mitigation Steps:**

```diff
File : automators/Automator.sol

79:    function setVault(address _vault, bool _active) public onlyOwner {
+       if (vaults[_vaults] != _active) {
80:      emit VaultChanged(_vault, _active);
81:       vaults[_vault] = _active;
+        }
82:    }

```

## [G-12] Switch the order around && to use shortcircuit to save gas(Instances missed by bot)

#### Instance 1

You can switch the order of conditions in the if statement to utilize short-circuit evaluation. This ensures that if the first condition `(unwrap)` is `false` the second condition `(address(weth) == address(token))` won't even be evaluated.

```solidity
File : automators/Automator.sol

219:  if (address(weth) == address(token) && unwrap) {

```

[Automator.sol#L219](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L219)

**Recommended Mitigation Steps:**

```diff
File : automators/Automator.sol

-219:  if (address(weth) == address(token) && unwrap) {
+219:  if (unwrap && address(weth) == address(token)) {

```

## [G-13] No need to cache a function call if used only once

#### Instance 1

No need to cache `params.tokenIn.balanceOf(address(this))` and `params.tokenOut.balanceOf(address(this))` in stack variable in `balanceInAfter` and `balanceOutAfter` respectively since they are used only once.

```solidity
File  : utils/Swapper.sol

104:   uint256 balanceInAfter = params.tokenIn.balanceOf(address(this));
105:   uint256 balanceOutAfter = params.tokenOut.balanceOf(address(this));
...
107:   amountInDelta = balanceInBefore - balanceInAfter;
108:   amountOutDelta = balanceOutAfter - balanceOutBefore;
```

[Swapper.sol#L104-L108](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L104-L108)

**Recommended Mitigation Steps:**

```diff
File  : utils/Swapper.sol

-104:   uint256 balanceInAfter = params.tokenIn.balanceOf(address(this));
-105:   uint256 balanceOutAfter = params.tokenOut.balanceOf(address(this));
...
-107:   amountInDelta = balanceInBefore - balanceInAfter;
-108:   amountOutDelta = balanceOutAfter - balanceOutBefore;
+107:   amountInDelta = balanceInBefore - params.tokenIn.balanceOf(address(this));
+108:   amountOutDelta = params.tokenOut.balanceOf(address(this)) - balanceOutBefore;
```

#### Instance 2

No need to cache `nonfungiblePositionManager.ownerOf(tokenId)` in stack variable `owner` since this is used only once in the function.

```solidity
File : automators/AutoExit.sol

219:  address owner = nonfungiblePositionManager.ownerOf(tokenId);
220:     if (owner != msg.sender) {
221:        revert Unauthorized();
222:     }

```

[AutoExit.sol#L219-L222](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L219-L222)

**Recommended Mitigation Steps:**

```diff
File : automators/AutoExit.sol

-219:  address owner = nonfungiblePositionManager.ownerOf(tokenId);
-220:     if (owner != msg.sender) {
+220:     if (nonfungiblePositionManager.ownerOf(tokenId) != msg.sender) {
221:        revert Unauthorized();
222:     }

```
