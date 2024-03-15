# REVERT LEND GAS OPTIMIZATIONS



## INTRODUCTION

Highlighted below are optimizations exclusively targeting state-mutating functions and view/pure functions invoked by state-mutating functions. In the discussion that follows, only runtime gas is emphasized, given its inevitable dominance over deployment gas costs throughout the protocol's lifetime. 

Please be aware that some code snippets may be shortened to conserve space, and certain code snippets may include @audit tags in comments to facilitate issue explanations."






## [G-01] Use the existing Local variable/global variable when equal to a state variable to avoid reading from state

### 1 Instances
1. #### Use `currentShares` in-place of `loan.debtShares` in the statement `uint256 loanDebtShares = loan.debtShares - shares`
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L990

In the `_repay()` function as shown below on [line 959](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L959) the state variable `loan.debtShares` is being cached in `currentShares` variable. Therefore we could use `currentShares` in place of `loan.debtShares` subsequently but this was not the case on line [line 959](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L959) where `loan.debtShares` was used in the statement `uint256 loanDebtShares = loan.debtShares - shares` thereby incurring an `SLOAD` Gwarmaccess `100` gas units where we could have use a stack variable. The diff below shows how the code should be refactored: 

```solidity
file: src/V3Vault.sol

954:     function _repay(uint256 tokenId, uint256 amount, bool isShare, bytes memory permitData) internal {
955:         (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
956: 
957:         Loan storage loan = loans[tokenId];
958: 
959:         uint256 currentShares = loan.debtShares;
960: 
961:         uint256 shares;
962:         uint256 assets;
963: 
964:         if (isShare) {
965:             shares = amount;
966:             assets = _convertToAssets(amount, newDebtExchangeRateX96, Math.Rounding.Up);
967:         } else {
968:             assets = amount;
969:             shares = _convertToShares(amount, newDebtExchangeRateX96, Math.Rounding.Down);
970:         }
971:
972:         // fails if too much repayed
973:         if (shares > currentShares) {
974:             revert RepayExceedsDebt();
975:         }
976:
977:         if (assets > 0) {
978:             if (permitData.length > 0) {
979:                 (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
980:                     abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
981:                 permit2.permitTransferFrom(
982:                     permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
983:                 );
984:             } else {
985:                 // fails if not enough token approved
986:                 SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
987:             }
988:         }
989: 
990:         uint256 loanDebtShares = loan.debtShares - shares;    //@audit use stack variable currentShares in place of loan.debtShares
991:         loan.debtShares = loanDebtShares;
992:         debtSharesTotal -= shares;
993: 
994:         // when amounts are repayed - they maybe borrowed again
995:         dailyDebtIncreaseLimitLeft += assets;
.
.
.
1014:    }
```

```diff
diff --git a/src/V3Vault.sol b/src/V3Vault.sol
index 64141ec..a363516 100644
--- a/src/V3Vault.sol
+++ b/src/V3Vault.sol
@@ -987,7 +987,7 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
             }
         }

-        uint256 loanDebtShares = loan.debtShares - shares;
+        uint256 loanDebtShares = currentShares - shares;
         loan.debtShares = loanDebtShares;
         debtSharesTotal -= shares;
```





## [G-02] Calculations should be memoized rather than re-calculating them
In computing, memoization or memoisation is an optimization technique used primarily to speed up computer programs by storing the results of expensive function calls to pure functions and returning the cached result when the same inputs occur again.


### 2 Instances
1. ####  We can memoize the computations of `SafeCast.toUint192(oldShares - newShares)`
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1217
2. ####  We can memoize the computations of `SafeCast.toUint192(newShares - oldShares)`
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1220

We can reduce the gas usage of the `_updateAndCheckCollateral()` function by memoizing the computations of `SafeCast.toUint192(oldShares - newShares)` and `SafeCast.toUint192(newShares - oldShares)` i.e cache the results of their computation so that for subsequent computations we can use the cached values rather than having to recompute the values. The diff below shows how the code could be refactored:

```solidity
file: src/V3Vault.sol

1205:    function _updateAndCheckCollateral(
1206:        uint256 tokenId,
1207:        uint256 debtExchangeRateX96,
1208:        uint256 lendExchangeRateX96,
1209:        uint256 oldShares,
1210:        uint256 newShares
1211:    ) internal {
1212:        if (oldShares != newShares) {
1213:            (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(tokenId);
1214:
1215:            // remove previous collateral - add new collateral
1216:            if (oldShares > newShares) {
1217:                tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares); //@audit memoize `SafeCast.toUint192(oldShares - newShares)` computation
1218:                tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1219:            } else {
1220:                tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares); //@audit memoize `SafeCast.toUint192(newShares - oldShares)` computation
1221:                tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
.
.
.
1244:     }
```

```diff
diff --git a/src/V3Vault.sol b/src/V3Vault.sol
index 64141ec..4fd7feb 100644
--- a/src/V3Vault.sol
+++ b/src/V3Vault.sol
@@ -1214,11 +1214,13 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors

             // remove previous collateral - add new collateral
             if (oldShares > newShares) {
-                tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
-                tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
+                uint192 _totaldebts = SafeCast.toUint192(oldShares - newShares);
+                tokenConfigs[token0].totalDebtShares -= _totaldebts;
+                tokenConfigs[token1].totalDebtShares -= _totaldebts;
             } else {
-                tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
-                tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
+                uint192 _totaldebts = SafeCast.toUint192(newShares - oldShares);
+                tokenConfigs[token0].totalDebtShares += _totaldebts;
+                tokenConfigs[token1].totalDebtShares += _totaldebts;
```




## [G-03] Refactor external/internal function to avoid unnecessary SLOAD
The internal function below read storage slots that are previously read in the external function that invoke them. We can refactor the external function to pass cached storage variables as stack variables and avoid the extra storage reads that would otherwise take place in the internal functions

### Instances
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L254-#L264 (internal function)
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L101-#L193 (external function)

The `execute()` function as shown below invokes the `_setBalance()` but both function reads the `positionBalances[tokenId][token]` mapping and the `_setBalance()` function is only called in the `execute()` function. We can refactor both functions such that the `execute()` function passes the cached value of `positionBalances[tokenId][token]` as an argument to the `_setBalance()` function since this function just reads and do not modify the `positionBalances[tokenId][token]` mapping variable. Refactoring the code this way would help make the `_setBalance()` function cheaper as it does not have to read the `positionBalances[tokenId][token]` mapping and by extension make the `execute()` function cheaper: The diff below shows how the code should be refactored: 

```solidity
file: src/transformers/AutoCompound.sol

101:    function execute(ExecuteParams calldata params) external nonReentrant {
102:        if (!operators[msg.sender] && !vaults[msg.sender]) {
103:            revert Unauthorized();
104:        }
105:        ExecuteState memory state;
.
.
.
115:        (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper,,,,,) =
116:            nonfungiblePositionManager.positions(params.tokenId);
117:
118:        // add previous balances from given tokens
119:        state.amount0 = state.amount0 + positionBalances[params.tokenId][state.token0]; //@audit  token0 balance read in external function
120:        state.amount1 = state.amount1 + positionBalances[params.tokenId][state.token1]; //@audit  token1 balance read in external function
.
.
.
174:            // calculate remaining tokens for owner
175:            _setBalance(params.tokenId, state.token0, state.amount0 - state.compounded0 - state.amount0Fees);
176:            _setBalance(params.tokenId, state.token1, state.amount1 - state.compounded1 - state.amount1Fees);
177:
178:            // add reward to protocol balance (token 0)
179:            _increaseBalance(0, state.token0, state.amount0Fees);
180:            _increaseBalance(0, state.token1, state.amount1Fees);
181:        }
.
.
.
193:    }
.
.
.
254:    function _setBalance(uint256 tokenId, address token, uint256 amount) internal {
255:        uint256 currentBalance = positionBalances[tokenId][token];  @audit re-reading token balance in internal function
256:        if (amount != currentBalance) {
257:            positionBalances[tokenId][token] = amount;
258:            if (amount > currentBalance) {
259:                emit BalanceAdded(tokenId, token, amount - currentBalance);
260:            } else {
261:                emit BalanceRemoved(tokenId, token, currentBalance - amount);
262:            }
263:        }
264:    }
```

```diff
diff --git a/src/transformers/AutoCompound.sol b/src/transformers/AutoCompound.sol
index a948bae..0697ea9 100644
--- a/src/transformers/AutoCompound.sol
+++ b/src/transformers/AutoCompound.sol
@@ -116,8 +116,10 @@ contract AutoCompound is Automator, Multicall, ReentrancyGuard {
             nonfungiblePositionManager.positions(params.tokenId);

         // add previous balances from given tokens
-        state.amount0 = state.amount0 + positionBalances[params.tokenId][state.token0];
-        state.amount1 = state.amount1 + positionBalances[params.tokenId][state.token1];
+        uint256 prevBalanceToken0 = positionBalances[params.tokenId][state.token0];
+        uint256 prevBalanceToken1 = positionBalances[params.tokenId][state.token1];
+        state.amount0 = state.amount0 + prevBalanceToken0;
+        state.amount1 = state.amount1 + prevBalanceToken1;

         // only if there are balances to work with - start autocompounding process
         if (state.amount0 > 0 || state.amount1 > 0) {
@@ -172,8 +174,8 @@ contract AutoCompound is Automator, Multicall, ReentrancyGuard {
             }

             // calculate remaining tokens for owner
-            _setBalance(params.tokenId, state.token0, state.amount0 - state.compounded0 - state.amount0Fees);
-            _setBalance(params.tokenId, state.token1, state.amount1 - state.compounded1 - state.amount1Fees);
+            _setBalance(params.tokenId, state.token0, state.amount0 - state.compounded0 - state.amount0Fees, prevBalanceToken0);
+            _setBalance(params.tokenId, state.token1, state.amount1 - state.compounded1 - state.amount1Fees, prevBalanceToken1);

             // add reward to protocol balance (token 0)
             _increaseBalance(0, state.token0, state.amount0Fees);
@@ -251,14 +253,13 @@ contract AutoCompound is Automator, Multicall, ReentrancyGuard {
         emit BalanceAdded(tokenId, token, amount);
     }

-    function _setBalance(uint256 tokenId, address token, uint256 amount) internal {
-        uint256 currentBalance = positionBalances[tokenId][token];
-        if (amount != currentBalance) {
+    function _setBalance(uint256 tokenId, address token, uint256 amount, uint256 balance) internal {
+        if (amount != balance) {
             positionBalances[tokenId][token] = amount;
-            if (amount > currentBalance) {
-                emit BalanceAdded(tokenId, token, amount - currentBalance);
+            if (amount > balance) {
             } else {
-                emit BalanceRemoved(tokenId, token, currentBalance - amount);
+                emit BalanceRemoved(tokenId, token, balance - amount);
             }
         }
     }
```




## [G-04]  Move lesser gas costing require checks to the top
Require() or revert() statements that check input arguments or cost lesser gas should be at the top of the function.
Checks that involve constants should come before checks that involve state variables, function calls, and calculations. By doing these checks first, the function is able to revert before wasting alot of gas in a function that may ultimately revert in the unhappy case.

#### Please note these instances were not included in the bots report

### Instances
1. #### Move the `if (transformedTokenId > 0) {revert Reentrancy()}` check to the top of the function.
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L502-#L508

In the `transform()` function as shown below the if-revert statement `if (tokenId == 0 || !transformerAllowList[transformer]) {revert TransformNotAllowed()}` is more gas consumimg than the if-revert statement `if (transformedTokenId > 0) {revert Reentrancy()}` as the former reads a mapping which cost about `2600` gas units. We can make the `transform()` function more gas efficient by moving the cheaper if-revert statement `if (transformedTokenId > 0) {revert Reentrancy()}` to the top of the function so that in scenarios where the cheaper revert statement fails the function would revert without having to read from state which is expensive. The diff below shows how the code should be refactored:

```solidity
file: src/V3Vault.sol

497:    function transform(uint256 tokenId, address transformer, bytes calldata data)
498:        external
499:        override
500:        returns (uint256 newTokenId)
501:    {
502:        if (tokenId == 0 || !transformerAllowList[transformer]) {
503:            revert TransformNotAllowed();
504:        }
505:        if (transformedTokenId > 0) {   //@audit move check to the top
506:            revert Reentrancy();
507:        }
508:        transformedTokenId = tokenId;
509:
510:        (uint256 newDebtExchangeRateX96,) = _updateGlobalInterest();
.
.
.
545:    }
```

```diff
diff --git a/src/V3Vault.sol b/src/V3Vault.sol
index 64141ec..e531185 100644
--- a/src/V3Vault.sol
+++ b/src/V3Vault.sol
@@ -499,12 +499,15 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
         override
         returns (uint256 newTokenId)
     {
-        if (tokenId == 0 || !transformerAllowList[transformer]) {
-            revert TransformNotAllowed();
-        }
+
         if (transformedTokenId > 0) {
             revert Reentrancy();
         }
+
+        if (tokenId == 0 || !transformerAllowList[transformer]) {
+            revert TransformNotAllowed();
+        }
+
```
```
Estimated gas saved: 2600 gas units
```

2. #### Move the `if (mode == Mode.NOT_SET) {revert InvalidConfig()}` check to the top of the function.
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L250-#L257

In the `setOracleMode()` function as shown below the if-revert statement `if (msg.sender != emergencyAdmin && msg.sender != owner()) {revert Unauthorized()}` is more gas consumimg than the if-revert statement `if (mode == Mode.NOT_SET) {revert InvalidConfig()}` as the former contains two conditions that involves reading from state which cost 2 `SLOAD` Gcoldaccess `4200` gas units. We can make the `transform()` function more gas efficient by moving the cheaper if-revert statement `if (mode == Mode.NOT_SET) {revert InvalidConfig()}` to the top of the function so that in scenarios where the cheaper revert statement fails the function would revert without having to read from state which is expensive. The diff below shows how the code should be refactored:

```solidity
file: src/V3Oracle.sol

249:    function setOracleMode(address token, Mode mode) external {
250:        if (msg.sender != emergencyAdmin && msg.sender != owner()) {
251:            revert Unauthorized();
252:        }
253:
254:        // can not be unset
255:        if (mode == Mode.NOT_SET) {
256:            revert InvalidConfig();
257:        }
258:
259:        feedConfigs[token].mode = mode;
260:        emit OracleModeUpdated(token, mode);
261:    }
```

```diff
diff --git a/src/V3Oracle.sol b/src/V3Oracle.sol
index 1ad544a..32bd2a8 100644
--- a/src/V3Oracle.sol
+++ b/src/V3Oracle.sol
@@ -247,15 +247,16 @@ contract V3Oracle is IV3Oracle, Ownable, IErrors {
     /// @param token Token to configure
     /// @param mode Mode to set
     function setOracleMode(address token, Mode mode) external {
-        if (msg.sender != emergencyAdmin && msg.sender != owner()) {
-            revert Unauthorized();
-        }
-
         // can not be unset
         if (mode == Mode.NOT_SET) {
             revert InvalidConfig();
         }

+        if (msg.sender != emergencyAdmin && msg.sender != owner()) {
+            revert Unauthorized();
+        }
+
+
         feedConfigs[token].mode = mode;
         emit OracleModeUpdated(token, mode);
     }
```
```
Estimated gas saved: 4200 gas units
```

3. #### Move the `if (config.isActive) {if (config.token0TriggerTick >= config.token1TriggerTick) {revert InvalidConfig()}}` check to the top of the function.
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L219-#L228

In the `configToken()` function as shown below the if-revert statement `if (owner != msg.sender) {revert Unauthorized()}` is more gas consumimg than the if-revert statement `if (config.isActive) {if (config.token0TriggerTick >= config.token1TriggerTick) {revert InvalidConfig()}}` as the former makes an external call while the latter just read calldata values. We can make the `configToken()` function more gas efficient by moving the cheaper if-revert statement `if (config.isActive) {if (config.token0TriggerTick >= config.token1TriggerTick) {revert InvalidConfig()}}` to the top of the function so that in scenarios where the cheaper revert statement fails the function would revert without having to read from state which is expensive. The diff below shows how the code should be refactored:

```solidity
file: src/automators/AutoExit.sol

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
229:
230:        positionConfigs[tokenId] = config;
231:
.
.
.
244:    }
```

```diff
diff --git a/src/automators/AutoExit.sol b/src/automators/AutoExit.sol
index 05e63d6..0876e91 100644
--- a/src/automators/AutoExit.sol
+++ b/src/automators/AutoExit.sol
@@ -216,17 +216,17 @@ contract AutoExit is Automator {
     // function to configure a token to be used with this runner
     // it needs to have approvals set for this contract beforehand
     function configToken(uint256 tokenId, PositionConfig calldata config) external {
-        address owner = nonfungiblePositionManager.ownerOf(tokenId);
-        if (owner != msg.sender) {
-            revert Unauthorized();
-        }
-
         if (config.isActive) {
             if (config.token0TriggerTick >= config.token1TriggerTick) {
                 revert InvalidConfig();
             }
         }

+        address owner = nonfungiblePositionManager.ownerOf(tokenId);
+        if (owner != msg.sender) {
+            revert Unauthorized();
+        }
+
         positionConfigs[tokenId] = config;

         emit PositionConfigured(
```
```
Estimated gas saved: 100 gas units
```


## [G-05]  Refactor the following function to reduce number of `SLOAD`


### Instances
1. #### Refactor the `onERC721Received()` function such that the number of storage reads is reduced
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L429-#L477

We can make the `onERC721Received()` function better gas efficient if we reduce the number of state reads in the function . We can do this by caching `loans[oldTokenId].debtShares` into a stack variable then use the stack variable in-place of `loans[oldTokenId].debtShares` in the statement `loans[tokenId] = Loan(loans[oldTokenId].debtShares)` also the stack variable would be used in-place of `loans[tokenId].debtShares` in the statement `_updateAndCheckCollateral(tokenId, debtExchangeRateX96, lendExchangeRateX96, 0, loans[tokenId].debtShares)` (since they would be of the same value). In implementing this we would avoid having to read `loans[tokenId].debtShares` in the statement `_updateAndCheckCollateral(tokenId, debtExchangeRateX96, lendExchangeRateX96, 0, loans[tokenId].debtShares)` thereby saving about `2600` gas units for read a mapping from state. The diff below shows how the function should be refactored:

```solidity
file: src/V3Vault.sol

429:    function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
430:        external
431:        override
432:        returns (bytes4)
433:    {
.
.
.
450:        } else {
451:            uint256 oldTokenId = transformedTokenId;
452:
453:            // if in transform mode - and a new position is sent - current position is replaced and returned
454:            if (tokenId != oldTokenId) {
455:                address owner = tokenOwner[oldTokenId];
456:
457:                // set transformed token to new one
458:                transformedTokenId = tokenId;
459:
460:                // copy debt to new token
461:                loans[tokenId] = Loan(loans[oldTokenId].debtShares);
462:
463:                _addTokenToOwner(owner, tokenId);
464:                emit Add(tokenId, owner, oldTokenId);
465:
466:                // clears data of old loan
467:                _cleanupLoan(oldTokenId, debtExchangeRateX96, lendExchangeRateX96, owner);
468:
469:                // sets data of new loan
470:                _updateAndCheckCollateral(
471:                    tokenId, debtExchangeRateX96, lendExchangeRateX96, 0, loans[tokenId].debtShares
472:                );
473:            }
474:        }
475:
476:        return IERC721Receiver.onERC721Received.selector;
477:    }
```

```diff
diff --git a/src/V3Vault.sol b/src/V3Vault.sol
index 64141ec..39f88de 100644
--- a/src/V3Vault.sol
+++ b/src/V3Vault.sol
@@ -458,7 +458,8 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
                 transformedTokenId = tokenId;

                 // copy debt to new token
-                loans[tokenId] = Loan(loans[oldTokenId].debtShares);
+                uint256 _debtShares = loans[oldTokenId].debtShares;
+                loans[tokenId] = Loan(_debtShares);

                 _addTokenToOwner(owner, tokenId);
                 emit Add(tokenId, owner, oldTokenId);
@@ -468,7 +469,7 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors

                 // sets data of new loan
                 _updateAndCheckCollateral(
-                    tokenId, debtExchangeRateX96, lendExchangeRateX96, 0, loans[tokenId].debtShares
+                    tokenId, debtExchangeRateX96, lendExchangeRateX96, 0, _debtShares
                 );
             }
         }
```

```
Estimated gas saved: 2600 gas units
```

1. #### Refactor the `borrow()` function such that the number of storage reads is reduced
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L550-#L602 (check line 552, 556, 557)

We can make the `borrow()` function better gas efficient if we reduce the number of state reads in the function . We can do this by caching state variables that are read more than once into stack variables. The `transformedTokenId` variable was read twice in the function we should instead read it once and cache its value into a stack variable then use the statck variable for subsequent reads for the variable. Implementing this would avoid `SLOAD`(warmaccess) `100` gas units and replace it with cheaper stack read. The diff below shows how the function should be refactored.

```solidity
file: src/V3Vault.sol

550:    function borrow(uint256 tokenId, uint256 assets) external override {
551:        bool isTransformMode =
552:            transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];
553:
554:        (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
555:
556:        _resetDailyDebtIncreaseLimit(newLendExchangeRateX96, false);
.
.
.
603:    }
```

```diff
diff --git a/src/V3Vault.sol b/src/V3Vault.sol
index 64141ec..b30616e 100644
--- a/src/V3Vault.sol
+++ b/src/V3Vault.sol
@@ -548,8 +548,9 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
     /// @param tokenId The token ID to use as collateral
     /// @param assets How much assets to borrow
     function borrow(uint256 tokenId, uint256 assets) external override {
+        uint256 _transformedTokenId = transformedTokenId;
         bool isTransformMode =
-            transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];
+            _transformedTokenId > 0 && _transformedTokenId == tokenId && transformerAllowList[msg.sender];

         (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
```

```
Estimated gas saved: 194 gas units
```




## [G-06]  Using `storage` instead of `memory` for struct saves gas

#### Please note this instances was not included in the bots report

### Instances
1. #### Make `feedConfig` a storage variable
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L281

We could make the `_getReferenceTokenPriceX96()` function more gas efficient if we declare the `feedConfig` struct variable as  `storage` rather than `memory` . In implementing this we would avoid having to copy all the members of `TokenConfig` struct from storage to memory which would incur a Gcoldsload (2100 gas) for each storage slot read which totals to 4200 gas units also reading the members from the new memory variable would incur an additional MLOAD rather than a cheap stack read. Declaring the `TokenConfig` struct variable as a `storage` variable would only Gcoldsload for the fields actually read then we cache any member that is read multiple times in stack variables.

```solidity
file: src/V3Oracle.sol

272:    function _getReferenceTokenPriceX96(address token, uint256 cachedChainlinkReferencePriceX96)
273:        internal
274:        view
275:        returns (uint256 priceX96, uint256 chainlinkReferencePriceX96)
276:    {
277:        if (token == referenceToken) {
278:            return (Q96, chainlinkReferencePriceX96);
279:        }
280:
281:        TokenConfig memory feedConfig = feedConfigs[token];     //@audit use storage in-place of memory
282:
283:        if (feedConfig.mode == Mode.NOT_SET) {
284:            revert NotConfigured();
285:        }
286:
287:        uint256 verifyPriceX96;
288:
289:        bool usesChainlink = (
290:            feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY
291:                || feedConfig.mode == Mode.CHAINLINK
292:        );
293:        bool usesTWAP = (
294:            feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY
295:                || feedConfig.mode == Mode.TWAP
296:        );
297:
298:        if (usesChainlink) {
299:            uint256 chainlinkPriceX96 = _getChainlinkPriceX96(token);
300:            chainlinkReferencePriceX96 = cachedChainlinkReferencePriceX96 == 0
301:                ? _getChainlinkPriceX96(referenceToken)
302:                : cachedChainlinkReferencePriceX96;
303:
304:            chainlinkPriceX96 = (10 ** referenceTokenDecimals) * chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96
305:                / (10 ** feedConfig.tokenDecimals);
306:
307:            if (feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY) {
308:                verifyPriceX96 = chainlinkPriceX96;
309:            } else {
310:                priceX96 = chainlinkPriceX96;
311:            }
312:        }
313:
314:        if (usesTWAP) {
315:            uint256 twapPriceX96 = _getTWAPPriceX96(feedConfig);
316:            if (feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY) {
317:                verifyPriceX96 = twapPriceX96;
318:            } else {
319:                priceX96 = twapPriceX96;
320:            }
321:        }
322:
323:        if (feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY) {
324:            _requireMaxDifference(priceX96, verifyPriceX96, feedConfig.maxDifference);
325:        }
326:    }
```

```diff
diff --git a/src/V3Oracle.sol b/src/V3Oracle.sol
index 1ad544a..51761d0 100644
--- a/src/V3Oracle.sol
+++ b/src/V3Oracle.sol
@@ -278,21 +278,22 @@ contract V3Oracle is IV3Oracle, Ownable, IErrors {
             return (Q96, chainlinkReferencePriceX96);
         }

-        TokenConfig memory feedConfig = feedConfigs[token];
+        TokenConfig storage feedConfig = feedConfigs[token];
+        Mode feedConfigMode = feedConfig.mode;

-        if (feedConfig.mode == Mode.NOT_SET) {
+        if (feedConfigMode == Mode.NOT_SET) {
             revert NotConfigured();
         }

         uint256 verifyPriceX96;

         bool usesChainlink = (
-            feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY
-                || feedConfig.mode == Mode.CHAINLINK
+            feedConfigMode == Mode.CHAINLINK_TWAP_VERIFY || feedConfigMode == Mode.TWAP_CHAINLINK_VERIFY
+                || feedConfigMode == Mode.CHAINLINK
         );
         bool usesTWAP = (
-            feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY
-                || feedConfig.mode == Mode.TWAP
+            feedConfigMode == Mode.CHAINLINK_TWAP_VERIFY || feedConfigMode == Mode.TWAP_CHAINLINK_VERIFY
+                || feedConfigMode == Mode.TWAP
         );

         if (usesChainlink) {
@@ -304,7 +305,7 @@ contract V3Oracle is IV3Oracle, Ownable, IErrors {
             chainlinkPriceX96 = (10 ** referenceTokenDecimals) * chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96
                 / (10 ** feedConfig.tokenDecimals);

-            if (feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY) {
+            if (feedConfigMode == Mode.TWAP_CHAINLINK_VERIFY) {
                 verifyPriceX96 = chainlinkPriceX96;
             } else {
                priceX96 = chainlinkPriceX96;
@@ -313,14 +314,14 @@ contract V3Oracle is IV3Oracle, Ownable, IErrors {

         if (usesTWAP) {
             uint256 twapPriceX96 = _getTWAPPriceX96(feedConfig);
-            if (feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY) {
+            if (feedConfigMode == Mode.CHAINLINK_TWAP_VERIFY) {
                 verifyPriceX96 = twapPriceX96;
             } else {
                 priceX96 = twapPriceX96;
             }
         }

-        if (feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY) {
+        if (feedConfigMode == Mode.CHAINLINK_TWAP_VERIFY || feedConfigMode == Mode.TWAP_CHAINLINK_VERIFY) {
             _requireMaxDifference(priceX96, verifyPriceX96, feedConfig.maxDifference);
         }
     }
```




## [G-07] Caching the length of calldata increases gas cost instead of reducing it

### Proof of Concept
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract CacheCallDataLength {
    

    function calculateTotal(uint256[5] memory numbers) public pure returns(uint256 total) {
        uint256 len = numbers.length;

        for(uint i; i < len; ++i) {
            total += numbers[i];
        }

    }
}

```
```
test for test/CacheCallDataLength.t.sol:CacheCallDataLengthTest
[PASS] test_calculateTotal() (gas: 1633)
```

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract NoCacheCallDataLength {
    

    function calculateTotal(uint256[5] memory numbers) public pure returns(uint256 total) {

        for(uint i; i < numbers.length; ++i) {
            total += numbers[i];
        }
        
    }
}
```
```
test for test/NoCacheCallDataLength.t.sol:NoCacheCallDataLengthTest
[PASS] test_calculateTotal() (gas: 1628)
```

### Instances
1. #### Reduce gas cost of `withdrawBalances()` function by not caching the length of calldata variable `tokens`
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L232

```solidity
file: src/transformers/AutoCompound.sol

227:    function withdrawBalances(address[] calldata tokens, address to) external override nonReentrant {
228:        if (msg.sender != withdrawer) {
229:            revert Unauthorized();
230:        }
231:        uint256 i;
232:        uint256 count = tokens.length;  //@audit caching calldata is expensive
233:        for (; i < count; ++i) {
234:            uint256 balance = positionBalances[0][tokens[i]];
235:            _withdrawBalanceInternal(0, tokens[i], to, balance, balance);
236:        }
237:    }
```

```diff
diff --git a/src/transformers/AutoCompound.sol b/src/transformers/AutoCompound.sol
index a948bae..796153a 100644
--- a/src/transformers/AutoCompound.sol
+++ b/src/transformers/AutoCompound.sol
@@ -229,8 +229,7 @@ contract AutoCompound is Automator, Multicall, ReentrancyGuard {
             revert Unauthorized();
         }
         uint256 i;
-        uint256 count = tokens.length;
-        for (; i < count; ++i) {
+        for (; i < tokens.length; ++i) {
             uint256 balance = positionBalances[0][tokens[i]];
             _withdrawBalanceInternal(0, tokens[i], to, balance, balance);
         }
```

2. #### Reduce gas cost of `withdrawBalances()` function by not caching the length of calldata variable `tokens`
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L110

```solidity
file: src/automators/Automator.sol

104:    function withdrawBalances(address[] calldata tokens, address to) external virtual {
105:        if (msg.sender != withdrawer) {
106:            revert Unauthorized();
107:        }
108:
109:        uint256 i;
110:        uint256 count = tokens.length;  //@audit caching calldata is expensive
111:        for (; i < count; ++i) {
112:            uint256 balance = IERC20(tokens[i]).balanceOf(address(this));
113:            if (balance > 0) {
114:                _transferToken(to, IERC20(tokens[i]), balance, true);
115:            }
116:        }
117:    }
```

```diff
diff --git a/src/automators/Automator.sol b/src/automators/Automator.sol
index 1d20e99..5324312 100644
--- a/src/automators/Automator.sol
+++ b/src/automators/Automator.sol
@@ -107,8 +107,7 @@ abstract contract Automator is Swapper, Ownable {
         }

         uint256 i;
-        uint256 count = tokens.length;
-        for (; i < count; ++i) {
+        for (; i < tokens.length; ++i) {
             uint256 balance = IERC20(tokens[i]).balanceOf(address(this));
             if (balance > 0) {
                 _transferToken(to, IERC20(tokens[i]), balance, true);
```




## [G-08] memory variable should created outside of loop
memory variable should created outside of loop, and get overriden with each iteration of loop, By doing so we save gas cost for memory variable creation in each iteration.

### Proof of Concept
```solidity
contract VarInLoop {

    uint256[] numbers = [1,2,3,4,5];
    uint256 total;

    function double(uint256 num) public pure returns(uint256 ans) {
        ans = num * 2;
    }

    function doubleNumbers() public {
        uint256 len = numbers.length;

        for(uint256 i; i < len; ++i) {
            uint256 doubleNum =  double(numbers[i]);
            total = total + doubleNum;
        }
    }
}
```
```
test for test/VarInLoop.t.sol:VarInLoopTest
[PASS] test_doubleNumbers() (gas: 38185)
```


```
contract VarOutLoop {

    uint256[] numbers = [1,2,3,4,5];
    uint256 total;

    function double(uint256 num) public pure returns(uint256 ans) {
        ans = num * 2;
    }

    function doubleNumbers() public {
        uint256 len = numbers.length;

        uint256 doubleNum;
        for(uint256 i; i < len; ++i) {
            doubleNum =  double(numbers[i]);
            total = total + doubleNum;
        }
    }
}
```
```
test for test/VarOutLoop.t.sol:VarOutLoopTest
[PASS] test_doubleNumbers() (gas: 38170)
```


### Instances
1. #### Declare `balance` outside the loop
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L234

```solidity
file: src/transformers/AutoCompound.sol

227:    function withdrawBalances(address[] calldata tokens, address to) external override nonReentrant {
228:        if (msg.sender != withdrawer) {
229:            revert Unauthorized();
230:        }
231:        uint256 i;
232:        uint256 count = tokens.length;
233:        for (; i < count; ++i) {
234:            uint256 balance = positionBalances[0][tokens[i]];   //@audit declare balance outside the loop
235:            _withdrawBalanceInternal(0, tokens[i], to, balance, balance);
236:        }
237:    }
```

```diff
diff --git a/src/transformers/AutoCompound.sol b/src/transformers/AutoCompound.sol
index a948bae..bcdc246 100644
--- a/src/transformers/AutoCompound.sol
+++ b/src/transformers/AutoCompound.sol
@@ -230,8 +230,9 @@ contract AutoCompound is Automator, Multicall, ReentrancyGuard {
         }
         uint256 i;
         uint256 count = tokens.length;
+        uint256 balance;
         for (; i < count; ++i) {
-            uint256 balance = positionBalances[0][tokens[i]];
+            balance = positionBalances[0][tokens[i]];
             _withdrawBalanceInternal(0, tokens[i], to, balance, balance);
         }
     }
```

2. #### Declare `balance` outside the loop
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L112


```solidity
file: src/automators/Automator.sol

104:    function withdrawBalances(address[] calldata tokens, address to) external virtual {
105:        if (msg.sender != withdrawer) {
106:            revert Unauthorized();
107:        }
108:
109:        uint256 i;
110:        uint256 count = tokens.length;
112:        for (; i < count; ++i) {
113:            uint256 balance = IERC20(tokens[i]).balanceOf(address(this));;   //@audit declare balance outside the loop
114:            if (balance > 0) {
115:                _transferToken(to, IERC20(tokens[i]), balance, true);
116:            }
117:        }
118:    }
```

```diff
diff --git a/src/automators/Automator.sol b/src/automators/Automator.sol
index 1d20e99..c66dddc 100644
--- a/src/automators/Automator.sol
+++ b/src/automators/Automator.sol
@@ -108,8 +108,9 @@ abstract contract Automator is Swapper, Ownable {

         uint256 i;
         uint256 count = tokens.length;
+        uint256 balance;
         for (; i < count; ++i) {
-            uint256 balance = IERC20(tokens[i]).balanceOf(address(this));
+            balance = IERC20(tokens[i]).balanceOf(address(this));
             if (balance > 0) {
                 _transferToken(to, IERC20(tokens[i]), balance, true);
             }
```



## [G-09] Mappings used within a function more than once should be cached to save gas
#### Please note this instance was not included in the bots report

### 1 Instance
1. #### `tokenOwner[tokenId]` read multiple times in the function
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L561&&#L595


```solidity
file: src/V3Vault.sol

550:    function borrow(uint256 tokenId, uint256 assets) external override {
.
.
.
560:        // if not in transfer mode - must be called from owner or the vault itself
561:        if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {     //@audit tokenOwner[tokenId] 1st read
562:            revert Unauthorized();
563:        }
564:
565:        uint256 shares = _convertToShares(assets, newDebtExchangeRateX96, Math.Rounding.Up);
566:
567:        uint256 loanDebtShares = loan.debtShares + shares;
568:        loan.debtShares = loanDebtShares;
569:        debtSharesTotal += shares;
570:
571:        if (debtSharesTotal > _convertToShares(globalDebtLimit, newDebtExchangeRateX96, Math.Rounding.Down)) {
572:            revert GlobalDebtLimit();
573:        }
574:        if (assets > dailyDebtIncreaseLimitLeft) {
575:            revert DailyDebtIncreaseLimit();
576:        } else {
577:            dailyDebtIncreaseLimitLeft -= assets;
578:        }
579:
580:        _updateAndCheckCollateral(
581:            tokenId, newDebtExchangeRateX96, newLendExchangeRateX96, loanDebtShares - shares, loanDebtShares
582:        );
583:
584:        uint256 debt = _convertToAssets(loanDebtShares, newDebtExchangeRateX96, Math.Rounding.Up);
585:
586:        if (debt < minLoanSize) {
587:            revert MinLoanSize();
588:        }
589:
590:        // only does check health here if not in transform mode
591:        if (!isTransformMode) {
592:            _requireLoanIsHealthy(tokenId, debt);
593:        }
594:
595:        address owner = tokenOwner[tokenId];     //@audit tokenOwner[tokenId] 2nd read
.
.
.
602:    }
```

```diff
diff --git a/src/V3Vault.sol b/src/V3Vault.sol
index 64141ec..ef13592 100644
--- a/src/V3Vault.sol
+++ b/src/V3Vault.sol
@@ -556,9 +556,9 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
         _resetDailyDebtIncreaseLimit(newLendExchangeRateX96, false);

         Loan storage loan = loans[tokenId];
-
+        address owner = tokenOwner[tokenId];
         // if not in transfer mode - must be called from owner or the vault itself
-        if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {
+        if (!isTransformMode && owner != msg.sender && address(this) != msg.sender) {
             revert Unauthorized();
         }

@@ -592,8 +592,6 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
             _requireLoanIsHealthy(tokenId, debt);
         }

-        address owner = tokenOwner[tokenId];
-
         // fails if not enough asset available
         // if called from transform mode - send funds to transformer contract
         SafeERC20.safeTransfer(IERC20(asset), isTransformMode ? msg.sender : owner, assets);
```

```
Estimated gas saved: 140 gas units
```





## [G-10] Multiple accesses of a array should use a local variable cache
The instances below point to the second+ access of a value inside an array, within a function. Caching an array's struct avoids re-calculating the array offsets into memory.

### Proof of concept 
```solidity
struct Person {
    string name;
    uint age;
    uint id;
}

contract NoCacheArrayElement {

    Person[] students;

    function createStudents() external  {
        Person[] memory arrayOfPersons = new Person[](3); 
        Person memory newPerson1 = Person("Emmanuel", 15,1);
        Person memory newPerson2 = Person("Faustina", 16,2);
        Person memory newPerson3 = Person("Emmanuela", 14,3);

        arrayOfPersons[0] = newPerson1;
        arrayOfPersons[1] = newPerson2;
        arrayOfPersons[2] = newPerson3;

        _addNewSet(arrayOfPersons);
    }

    function _addNewSet(Person[] memory _persons) internal {
        uint len = _persons.length;
        unchecked {
            for(uint i; i < len; ++i) {
                Person memory newStudent = Person(_persons[i].name, _persons[i].age, _persons[i].id);
                students.push(newStudent);
            }
        }

    }
}
```
```
test for test/NoCacheArrayElement.t.sol:NoCacheArrayElementTest
[PASS] test_createStudents() (gas: 230357)
```

```solidity

struct Person {
    string name;
    uint age;
    uint id;
}

contract CacheArrayElement {

    Person[] students;

    function createStudents() external  {
        Person[] memory arrayOfPersons = new Person[](3); 
        Person memory newPerson1 = Person("Emmanuel", 15,1);
        Person memory newPerson2 = Person("Faustina", 16,2);
        Person memory newPerson3 = Person("Emmanuela", 14,3);

        arrayOfPersons[0] = newPerson1;
        arrayOfPersons[1] = newPerson2;
        arrayOfPersons[2] = newPerson3;

        _addNewSet(arrayOfPersons);
    }

    function _addNewSet(Person[] memory _persons) internal {
        uint len = _persons.length;
        unchecked {
            for(uint i; i < len; ++i) {
                Person memory myPerson = _persons[i];
                Person memory newStudent = Person(myPerson.name, myPerson.age, myPerson.id);
                students.push(newStudent);
            }
        }

    }
}
```
```
test for test/Counter.t.sol:CacheArrayElementTest
[PASS] test_createStudents() (gas: 230096)
```

### Instances
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L112-#L114
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L234-#L235




## [G-11] Initializing state variables to their default values in the `V3Vault` contract
The state variables `reserveFactorX32`, `debtSharesTotal`, `lastExchangeRateUpdate`, `globalDebtLimit`, `globalLendLimit`, `minLoanSize`, `dailyLendIncreaseLimitMin`, `dailyLendIncreaseLimitLeft`, `dailyLendIncreaseLimitLastReset`, `dailyDebtIncreaseLimitMin`, `dailyDebtIncreaseLimitLeft` and `dailyDebtIncreaseLimitLastReset` were all initialized to their default value 0 but solidity does not recognize null as a value, so uint variables by default are initialized to zero. Having to set a uint variable to zero is redundant and increases deployment cost.

### Proof of concept
Using a simple Remix test

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;


contract InitializeDefaultValue {
    
    uint256 public variable = 0;
}
```
```
Deployment gas cost: 26478
```


```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract NoInitializeDefaultValue {
    
    uint256 public variable;

}
```
```
Deployment gas cost: 24273
```


### Links
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L118
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L124
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L127
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L131
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L132
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L135
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L138
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L139
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L140
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L143
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L144
- https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L145





## CONCLUSION
As you embark on incorporating the recommended optimizations, we want to emphasize the utmost importance of proceeding with vigilance and dedicating thorough efforts to comprehensive testing. It is of paramount significance to ensure that the proposed alterations do not inadvertently introduce fresh vulnerabilities, while also successfully achieving the anticipated enhancements in performance.

We strongly advise conducting a meticulous and exhaustive evaluation of the modifications made to the codebase. This rigorous scrutiny and exhaustive assessment will play a pivotal role in affirming both the security and efficacy of the refactored code. Your careful attention to detail, coupled with the implementation of a robust testing framework, will provide the necessary assurance that the refined code aligns with your security objectives and effectively fulfills the intended performance optimizations.







