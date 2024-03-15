
## REVRT LEND GAS OPTIMIZATIONS

## INTRODUCTION

Highlighted below are optimizations exclusively targeting state-mutating functions and view/pure functions invoked by state-mutating functions. In the discussion that follows, only runtime gas is emphasized, given its inevitable dominance over deployment gas costs throughout the protocol's lifetime.

Please be aware that some code snippets may be shortened to conserve space, and certain code snippets may include @audit tags in comments to facilitate issue explanations.

- [Re-arrange state variable order to save storage slots (Saves ~4000 Gas)](#g-01-re-arrange-state-variable-order-to-save-storage-slots-saves-4000-gas)
- [Reduce the size of struct variables and pack them together to save storage slots(Instances Missed by bot)(Gas Saved ~ 4000 Gas)](#g-02-reduce-the-size-of-struct-variables-and-pack-them-together-to-save-storage-slotsinstances-missed-by-botgas-saved--4000-gas)
- [Reorder accessing state variables in `execute` function to save gas 
](#g-03-reorder-accessing-state-variables-in-execute-function-to-save-gas)
- [Cache repeated calculations to avoid recalculating the same values multiple times](#g-04-cache-repeated-calculations-to-avoid-recalculating-the-same-values-multiple-times)
- [Cache calculations in loop to avoid re-calculating on each iteration](#g-05-cache-calculations-in-loop-to-avoid-re-calculating-on-each-iteration)
- [Using YUL's selfbalance is cheaper than address(this).balance](#g-06-using-yuls-selfbalance-is-cheaper-than-addressthisbalance)
- [Reduce Storage Access By not accessing positionBalances[tokenId][token] a second time to subtract amount](#g-07-reduce-storage-access-by-not-accessing-positionbalancestokenidtoken-a-second-time-to-subtract-amount)
- [Utilize local variables instead of repeatedly accessing storage variables](#g-08-utilize-local-variables-instead-of-repeatedly-accessing-storage-variables)


## Gas report

**Note: The issues addressed here were not reported by the bot, for packing variables, notes explaining the how and why are included**


## [G-01] Re-arrange state variable order to save storage slots (Saves ~4000 Gas)
We can re-arrange the order of V30racle to save 1 storage slot (~2000 Gas) pack MIN_RANGE_DIFFRENCE with factory address
### Details

### Proof of Code
- [V3Oracle.sol#L25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L25)
```solidity
File: src/V3Oracle.sol
25: uint16 public constant MIN_PRICE_DIFFERENCE = 200; //2% /@audit pack

    uint256 private constant Q96 = 2 ** 96;
    uint256 private constant Q128 = 2 ** 128;
```
### Optimized code:

```diff
diff --git a/src/V3Oracle.sol b/src/V3Oracle.sol
index 1ad544a..6e173a6 100644
--- a/src/V3Oracle.sol
+++ b/src/V3Oracle.sol
@@ -22,7 +22,6 @@ import "./interfaces/IErrors.sol";
 /// @title V3Oracle to be used in V3Vault to calculate position values
 /// @notice It uses both chainlink and uniswap v3 TWAP and provides emergency fallback mode
 contract V3Oracle is IV3Oracle, Ownable, IErrors {
-    uint16 public constant MIN_PRICE_DIFFERENCE = 200; //2%
 
     uint256 private constant Q96 = 2 ** 96;
     uint256 private constant Q128 = 2 ** 128;
@@ -54,7 +53,7 @@ contract V3Oracle is IV3Oracle, Ownable, IErrors {
 
     // token => config mapping
     mapping(address => TokenConfig) public feedConfigs;
-
+    uint16 public constant MIN_PRICE_DIFFERENCE = 200;
     address public immutable factory;
     INonfungiblePositionManager public immutable nonfungiblePositionManager;
```
### Instances 2

We can re-arrange the order of V3vault.sol to save 1 storage slot (~2000 Gas) pack emergencyAdmin address with MIN_RESERVE_PROTECTION_FACTOR_X32address
### Proof of Code
- [V3Vault.sol#L167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L167)
```solidity
File: src/V3Vault.sol
161:   uint256 private transformedTokenId = 0; // transient storage (when available in dencun)

    mapping(address => bool) public transformerAllowList; // contracts allowed to transform positions (selected audited contracts e.g. V3Utils)
    mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; // owners permissions for other addresses to call transform on owners behalf (e.g. AutoRange contract)

    // address which can call special emergency actions without timelock
@>    address public emergencyAdmin;

```
### Optimized code:

```diff
diff --git a/src/V3Vault.sol b/src/V3Vault.sol
index 64141ec..556ee1d 100644
--- a/src/V3Vault.sol
+++ b/src/V3Vault.sol
@@ -120,6 +120,9 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
     // percentage of lend amount which needs to be in reserves before withdrawn
     uint32 public reserveProtectionFactorX32 = MIN_RESERVE_PROTECTION_FACTOR_X32;
 
+    // address which can call special emergency actions without timelock
+    address public emergencyAdmin;
+
     // total of debt shares - increases when borrow - decreases when repay
     uint256 public debtSharesTotal = 0;
@@ -163,8 +166,7 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
     mapping(address => bool) public transformerAllowList; // contracts allowed to transform positions (selected audited contracts e.g. V3Utils)
     mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; // owners permissions for other addresses to call transform 
on owners behalf (e.g. AutoRange contract)
 
-    // address which can call special emergency actions without timelock
-    address public emergencyAdmin;
+
```
## [G-02] Reduce the size of struct variables and pack them together to save storage slots(Instances Missed by bot)(Gas Saved ~ 4000 Gas)
collect fee amount (if type(uint128).max - ALL) So we can pac this variable in small data type by doing this we can save i slots. Which save around 2k gas. 

In `AutoRange.sol` feeAmount1 and feeAmount1 can be packed together into 1 slot saves 1 Storage Slot.(~2000 Gas)
### Details

### Proof of Code
- [AutoRange.sol#L65C3-L90C6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L65C3-L90C6)
```solidity
File: src/transformers/AutoRange.sol
65:   struct ExecuteState {
        address owner;
        address realOwner;
        IUniswapV3Pool pool;
        address token0;
        address token1;
        uint24 fee;
        int24 tickLower;
        int24 tickUpper;
        int24 currentTick;
        uint256 amount0;
        uint256 amount1;
        uint256 feeAmount0; //@audit we can pack uint128
        uint256 feeAmount1; //this also
        uint256 maxAddAmount0;
        uint256 maxAddAmount1;
        uint256 amountAdded0;
        uint256 amountAdded1;
        uint128 liquidity; //@audit look for struct pack 
        uint256 protocolReward0;
        uint256 protocolReward1;
        uint256 amountOutMin;
        uint256 amountInDelta;
        uint256 amountOutDelta;
        uint256 newTokenId;
    }
```
```diff
diff --git a/src/transformers/AutoRange.sol b/src/transformers/AutoRange.sol
index 05e63d6..e5f9285 100644
--- a/src/transformers/AutoRange.sol
+++ b/src/transformers/AutoRange.sol
@@ -1,4 +1,4 @@
// SPDX-License-Identifier: BUSL-1.1
 pragma solidity ^0.8.0;
 
 import "./Automator.sol";
@@ -79,8 +79,8 @@ contract AutoExit is Automator {
         uint128 liquidity;
         uint256 amount0;
         uint256 amount1;
-        uint256 feeAmount0;
-        uint256 feeAmount1;
+        uint128 feeAmount0; //@audit uint128
+        uint128 feeAmount1;
         uint256 amountOutMin;
         uint256 amountInDelta;
         uint256 amountOutDelta;
```
### Instances 2

collect fee amount (if type(uint128).max - ALL) So we can pac this variable in small data type by doing this we can save i slots. Which save around 2k gas. 

In `AutoExit.sol` feeAmount1 and feeAmount1 can be packed together into 1 slot saves 1 Storage Slot.(~2000 Gas)

### Proof of Code
- [AutoExit.sol#L74C3-L93C6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L74C3-L93C6)
```solidity
File: src/automators/AutoExit.sol
73:  struct ExecuteState {
        address token0;
        address token1;
        uint24 fee;
        int24 tickLower;
        int24 tickUpper;
        uint128 liquidity;
        uint256 amount0;
        uint256 amount1;
        uint128 feeAmount0; //@audit uint128
        uint128 feeAmount1; //@audit uint128
        uint256 amountOutMin;
        uint256 amountInDelta;
        uint256 amountOutDelta;
        IUniswapV3Pool pool;
        uint256 swapAmount;
        int24 tick;
        bool isSwap;
        bool isAbove;
        address owner;
    }
```
### Optimized code:

```diff
diff --git a/src/automators/AutoExit.sol b/src/automators/AutoExit.sol
index 05e63d6..e5f9285 100644
--- a/src/automators/AutoExit.sol
+++ b/src/automators/AutoExit.sol
@@ -1,4 +1,4 @@
// SPDX-License-Identifier: BUSL-1.1
 pragma solidity ^0.8.0;
 
 import "./Automator.sol";
@@ -79,8 +79,8 @@ contract AutoExit is Automator {
         uint128 liquidity;
         uint256 amount0;
         uint256 amount1;
-        uint256 feeAmount0;
-        uint256 feeAmount1;
+        uint128 feeAmount0; //@audit uint128
+        uint128 feeAmount1;
         uint256 amountOutMin;
         uint256 amountInDelta;
         uint256 amountOutDelta;
```
## [G-03] Reorder accessing state variables in `execute` function to save gas 

### Details
In `execute()`, multiple conditions are checked after reading the state, which generally consumes more gas; if one of the if conditions reverts, gas is wasted. As a result, whenever a state variable is required, it is best to create one.

In below code access state varibale in line after 119.
### Proof of Code
- [AutoExit.sol#L105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L105)
```solidity
File: src/automators/AutoExit.sol
100:  function execute(ExecuteParams calldata params) external {
        if (!operators[msg.sender]) {
            revert Unauthorized();
        }

        ExecuteState memory state; //@audit cache when its necessary move before state access
        PositionConfig memory config = positionConfigs[params.tokenId];

        if (!config.isActive) {
            revert NotConfigured();
        }
```
### Optimized code:

```diff
diff --git a/src/automators/AutoExit.sol b/src/automators/AutoExit.sol
index 05e63d6..20833bb 100644
--- a/src/automators/AutoExit.sol
+++ b/src/automators/AutoExit.sol
@@ -102,7 +102,6 @@ contract AutoExit is Automator {
             revert Unauthorized();
         }
 
-        ExecuteState memory state;
         PositionConfig memory config = positionConfigs[params.tokenId];
 
         if (!config.isActive) {
@@ -115,7 +114,7 @@ contract AutoExit is Automator {
         ) {
             revert ExceedsMaxReward();
         }
-
+        ExecuteState memory state;
         // get position info
         (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
             nonfungiblePositionManager.positions(params.tokenId);
```
### Details
In `execute()`, multiple conditions are checked after reading the state, which generally consumes more gas; if one of the if conditions reverts, gas is wasted. As a result, whenever a state variable is required, it is best to create one.

In below code access state varibale in line after 129.

### Proof of Code
- [AutoRange.sol#L115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L115)
```solidity
File: src/transformers/AutoRange.sol
111: function execute(ExecuteParams calldata params) external {
        if (!operators[msg.sender] && !vaults[msg.sender]) {
            revert Unauthorized();
        }
        ExecuteState memory state; //@audit make state variable when its necessary
        PositionConfig memory config = positionConfigs[params.tokenId];

        if (config.lowerTickDelta == config.upperTickDelta) {
            revert NotConfigured();
        }
```
### Optimized code:

```diff
diff --git a/src/transformers/AutoRange.sol b/src/transformers/AutoRange.sol
index 8c29e6a..f5e83d0 100644
--- a/src/transformers/AutoRange.sol
+++ b/src/transformers/AutoRange.sol
@@ -112,7 +112,6 @@ contract AutoRange is Automator {
         if (!operators[msg.sender] && !vaults[msg.sender]) {
             revert Unauthorized();
         }
-        ExecuteState memory state;
         PositionConfig memory config = positionConfigs[params.tokenId];
 
         if (config.lowerTickDelta == config.upperTickDelta) {
@@ -125,7 +124,7 @@ contract AutoRange is Automator {
         ) {
             revert ExceedsMaxReward();
         }
-
+        ExecuteState memory state;
         // get position info
         (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
             nonfungiblePositionManager.positions(params.tokenId);
```
## [G-04] Cache repeated calculations to avoid recalculating the same values multiple times

### Details
In `_calculateGlobalInterest()` calculate `block.timestamp - lastRateUpdate` in if condition which is redundant. So we can avoid that multiple computation by caching this logic in local variable once then use multiple times.This way we can save gas.

### Proof of Code
- [V3Vault.sol#L1167C4-L1195C6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1167C4-L1195C6)
```solidity
File: src/V3Vault.sol
1167: function _calculateGlobalInterest()
        internal
        view
        returns (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96)
    {
        uint256 oldDebtExchangeRateX96 = lastDebtExchangeRateX96;
        uint256 oldLendExchangeRateX96 = lastLendExchangeRateX96;

        (, uint256 available,) = _getAvailableBalance(oldDebtExchangeRateX96, oldLendExchangeRateX96);

        uint256 debt = _convertToAssets(debtSharesTotal, oldDebtExchangeRateX96, Math.Rounding.Up);

        (uint256 borrowRateX96, uint256 supplyRateX96) = interestRateModel.getRatesPerSecondX96(available, debt);

        supplyRateX96 = supplyRateX96.mulDiv(Q32 - reserveFactorX32, Q32);

        // always growing or equal
        uint256 lastRateUpdate = lastExchangeRateUpdate;

        if (lastRateUpdate > 0) {
            newDebtExchangeRateX96 = oldDebtExchangeRateX96
                + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96; //@audit cache calculation
            newLendExchangeRateX96 = oldLendExchangeRateX96
                + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;
        } else {
            newDebtExchangeRateX96 = oldDebtExchangeRateX96;
            newLendExchangeRateX96 = oldLendExchangeRateX96;
        }
    }

```
### Optimized code:

```diff
diff --git a/src/V3Vault.sol b/src/V3Vault.sol
index 64141ec..69791fa 100644
--- a/src/V3Vault.sol
+++ b/src/V3Vault.sol
@@ -1182,12 +1182,13 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
 
         // always growing or equal
         uint256 lastRateUpdate = lastExchangeRateUpdate;
+        uint256 timeSinceLastUpdate = block.timestamp - lastRateUpdate;
 
         if (lastRateUpdate > 0) {
             newDebtExchangeRateX96 = oldDebtExchangeRateX96
-                + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;
+                + oldDebtExchangeRateX96 * timeSinceLastUpdate * borrowRateX96 / Q96;
             newLendExchangeRateX96 = oldLendExchangeRateX96
-                + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;
+                + oldLendExchangeRateX96 * timeSinceLastUpdate * supplyRateX96 / Q96;
         } else {
             newDebtExchangeRateX96 = oldDebtExchangeRateX96;
             newLendExchangeRateX96 = oldLendExchangeRateX96;
```
## [G-05] Cache calculations in loop to avoid re-calculating on each iteration

### Details
In `Automator.sol:withdrawBalances()` : `tokens[i]` we can cache once and use multiple times. Instead of repeatedly calling _newFees[i] in the loop, you can calculate it once and use the result.

### Proof of Code
- [Automator.sol#L104C4-L117C6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L104C4-L117C6)
```solidity
File: src/automators/Automator.sol
104: function withdrawBalances(address[] calldata tokens, address to) external virtual {
        if (msg.sender != withdrawer) {
            revert Unauthorized();
        }

        uint256 i;
        uint256 count = tokens.length;
        for (; i < count; ++i) {
            uint256 balance = IERC20(tokens[i]).balanceOf(address(this)); //@audit cache token[i]
            if (balance > 0) {
                _transferToken(to, IERC20(tokens[i]), balance, true);
            }
        }
    }
```
### Optimized code:

```diff
diff --git a/src/automators/Automator.sol b/src/automators/Automator.sol
index 1d20e99..8a9eaee 100644
--- a/src/automators/Automator.sol
+++ b/src/automators/Automator.sol
@@ -109,9 +109,10 @@ abstract contract Automator is Swapper, Ownable {
         uint256 i;
         uint256 count = tokens.length;
         for (; i < count; ++i) {
-            uint256 balance = IERC20(tokens[i]).balanceOf(address(this));
+            address token = tokens[i];
+            uint256 balance = IERC20(token).balanceOf(address(this));
             if (balance > 0) {
-                _transferToken(to, IERC20(tokens[i]), balance, true);
+                _transferToken(to, IERC20(token), balance, true);
             }
         }
     }
```
## Instances 2
In `AutoCompund.sol:withdrawBalances()` : `tokens[i]` we can cache once and use multiple times. Instead of repeatedly calling _newFees[i] in the loop, you can calculate it once and use the result.

### Optimized code:
- [AutoCompound.sol#L227C1-L236C10](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L227C1-L236C10)
```diff
diff --git a/src/transformers/AutoCompound.sol b/src/transformers/AutoCompound.sol
index a948bae..30eb110 100644
--- a/src/transformers/AutoCompound.sol
+++ b/src/transformers/AutoCompound.sol
@@ -231,8 +231,9 @@ contract AutoCompound is Automator, Multicall, ReentrancyGuard {
         uint256 i;
         uint256 count = tokens.length;
         for (; i < count; ++i) {
-            uint256 balance = positionBalances[0][tokens[i]];
-            _withdrawBalanceInternal(0, tokens[i], to, balance, balance);
+            address token = tokens[i];
+            uint256 balance = positionBalances[0][token];
+            _withdrawBalanceInternal(0, token, to, balance, balance);
         }
     }
```
## [G-06] Using YUL's selfbalance is cheaper than address(this).balance
selfbalance() function from yul is the best gas-effective alternative for The solidity code address(this).balance Across the whole WiseLending codebase, there are only two instances of it that can be optimized to save lot of gas as they are being inherited by lot of functions

### Details

### Proof of Code
- [Automator.sol#L128](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L128C1-L128C46)
```solidity
File: src/automators/Automator.sol
123:  function withdrawETH(address to) external {
        if (msg.sender != withdrawer) {
            revert Unauthorized();
        }

        uint256 balance = address(this).balance; //@audit
        if (balance > 0) {
            (bool sent,) = to.call{value: balance}("");
            if (!sent) {
                revert EtherSendFailed();
            }
        }
    }
```
### Optimized code:

```diff
diff --git a/src/automators/Automator.sol b/src/automators/Automator.sol
index 1d20e99..7c61eb7 100644
--- a/src/automators/Automator.sol
+++ b/src/automators/Automator.sol
@@ -124,10 +124,12 @@ abstract contract Automator is Swapper, Ownable {
         if (msg.sender != withdrawer) {
             revert Unauthorized();
         }
-
-        uint256 balance = address(this).balance;
-        if (balance > 0) {
-            (bool sent,) = to.call{value: balance}("");
+        uint256 Balance;
+        assembly {
+          Balance := selfbalance()
+        } 
+        if (Balance > 0) {
+            (bool sent,) = to.call{value: Balance}("");
             if (!sent) {
                 revert EtherSendFailed();
             }
```
## [G-07] Reduce Storage Access By not accessing positionBalances[tokenId][token] a second time to subtract amount

### Details
The balance parameter is already the current balance, so you can subtract amount from it and then update the mapping directly.Directly update the balance in storage.No need to read from storage again since we already have the 'balance' variable

### Proof of Code
- [AutoCompound.sol#L266C3-L274C6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L266C3-L274C6)
```solidity
File: src/transformers/AutoCompound.sol
267:  function _withdrawBalanceInternal(uint256 tokenId, address token, address to, uint256 balance, uint256 amount)
        internal
    {
        require(amount <= balance, "amount>balance");
        positionBalances[tokenId][token] = positionBalances[tokenId][token] - amount;
        emit BalanceRemoved(tokenId, token, amount);
        SafeERC20.safeTransfer(IERC20(token), to, amount);
        emit BalanceWithdrawn(tokenId, token, to, amount);
    }
```
### Optimized code:

```diff
diff --git a/src/transformers/AutoCompound.sol b/src/transformers/AutoCompound.sol
index a948bae..c9bd822 100644
--- a/src/transformers/AutoCompound.sol
+++ b/src/transformers/AutoCompound.sol
@@ -267,7 +268,8 @@ contract AutoCompound is Automator, Multicall, ReentrancyGuard {
         internal
     {
         require(amount <= balance, "amount>balance");
-        positionBalances[tokenId][token] = positionBalances[tokenId][token] - amount;
+        balance -= amount;
+        positionBalances[tokenId][token] = balance;
         emit BalanceRemoved(tokenId, token, amount);
         SafeERC20.safeTransfer(IERC20(token), to, amount);
         emit BalanceWithdrawn(tokenId, token, to, amount);
```
## [G-08] Utilize local variables instead of repeatedly accessing storage variables

### Details
In line 959 cached `uint256 currentShares = loan.debtShares;`. Use this local variable for all subsequent operations within that function.Especially on line `992`.

### Proof of Code
- [V3Vault.sol#L990C7-L1015C1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L990C7-L1015C1)
```solidity
File:
956: function _repay(uint256 tokenId, uint256 amount, bool isShare, bytes memory permitData) internal {
        (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();

        Loan storage loan = loans[tokenId];

@>        uint256 currentShares = loan.debtShares;

992:        uint256 loanDebtShares = currentShares - shares; //@audit  Utilize local variables instead of repeatedly accessing storage variables.
        loan.debtShares = loanDebtShares;
        debtSharesTotal -= shares;

        // when amounts are repayed - they maybe borrowed again
        dailyDebtIncreaseLimitLeft += assets;
```
### Optimized code:

```diff
diff --git a/src/V3Vault.sol b/src/V3Vault.sol
index 64141ec..57fe5ef 100644
--- a/src/V3Vault.sol
+++ b/src/V3Vault.sol
@@ -987,14 +989,14 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
             }
         }
 
-        uint256 loanDebtShares = loan.debtShares - shares;
+        uint256 loanDebtShares = currentShares - shares;
         loan.debtShares = loanDebtShares;
         debtSharesTotal -= shares;
 
         // when amounts are repayed - they maybe borrowed again
         dailyDebtIncreaseLimitLeft += assets;
         _updateAndCheckCollateral(  
             tokenId, newDebtExchangeRateX96, newLendExchangeRateX96, loanDebtShares + shares, loanDebtShares
         );
 
```