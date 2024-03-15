## Use assembly for math (add, sub, mul, div)
Use assembly for math instead of Solidity. You can check for overflow/underflow in assembly to ensure safety.


### Befor
| src/InterestRateModel.sol:InterestRateModel contract |                 |      |        |      |         |
|------------------------------------------------------|-----------------|------|--------|------|---------|
| Deployment Cost                                      | Deployment Size |      |        |      |         |
| 415204                                               | 2390            |      |        |      |         |
| Function Name                                        | min             | avg  | median | max  | # calls |
| getUtilizationRateX96                                | 387             | 535  | 609    | 609  | 3       |
```solidity
50   return debt * Q96 / (cash + debt);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L50


### After
| src/InterestRateModel.sol:InterestRateModel contract |                 |      |        |      |         |
|------------------------------------------------------|-----------------|------|--------|------|---------|
| Deployment Cost                                      | Deployment Size |      |        |      |         |
| 410404                                               | 2366            |      |        |      |         |
| Function Name                                        | min             | avg  | median | max  | # calls |
| getUtilizationRateX96                                | 387             | 399  | 405    | 405  | 3       |


```diff
    function getUtilizationRateX96(uint256 cash, uint256 debt) public pure returns (uint256) {
        if (debt == 0) {
            return 0;
        }
-       return debt * Q96 / (cash + debt);
+       uint256 result;
+       assembly {
+           // Calculate debt * Q96
+          let debtQ96 := mul(debt, Q96)

+           // Calculate cash + debt
+           let total := add(cash, debt)

+           // Perform debtQ96 / total
+           result := div(debtQ96, total)
+       }

+       return result;
+  }
```

### Befor
| src/InterestRateModel.sol:InterestRateModel contract |                 |      |        |      |         |
|------------------------------------------------------|-----------------|------|--------|------|---------|
| Deployment Cost                                      | Deployment Size |      |        |      |         |
| 410404                                               | 2366            |      |        |      |         |
| Function Name                                        | min             | avg  | median | max  | # calls |
| getRatesPerSecondX96                                 | 1251            | 3766 | 1251   | 7251 | 44      |

```solidity
70   supplyRateX96 = utilizationRateX96 * borrowRateX96 / Q96;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L74


### after
| src/InterestRateModel.sol:InterestRateModel contract |                 |      |        |      |         |
|------------------------------------------------------|-----------------|------|--------|------|---------|
| Deployment Cost                                      | Deployment Size |      |        |      |         |
| 412404                                               | 2376            |      |        |      |         |
| Function Name                                        | min             | avg  | median | max  | # calls |
| getRatesPerSecondX96                                 | 1121            | 3645 | 1121   | 7121 | 44      |

```diff
-       supplyRateX96 = utilizationRateX96 * borrowRateX96 / Q96;
+       assembly {
+           // Multiply utilizationRateX96 and borrowRateX96
+           let product := mul(utilizationRateX96, borrowRateX96)

+           // Divide product by Q96
+           supplyRateX96 := div(product, Q96)
+       }
```

## Optimization of Condition Ordering in `setOracleMode` Function

### Explanation

When evaluating the original code, if the first condition (`if (msg.sender != emergencyAdmin && msg.sender != owner())`) does not trigger a revert, and if the second condition (`if (mode == Mode.NOT_SET)`) does trigger a revert, then the first condition unnecessarily accesses the `emergencyAdmin` storage variable, leading to gas wastage.

### Original Code (Not Optimized)

```solidity
function setOracleMode(address token, Mode mode) external {
    if (msg.sender != emergencyAdmin && msg.sender != owner()) {
        revert Unauthorized();
    }
    
    // can not be unset
    if (mode == Mode.NOT_SET) {
        revert InvalidConfig();
    }

    feedConfigs[token].mode = mode;
    emit OracleModeUpdated(token, mode);
}
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L249-L261

### Optimized Code

```solidity
function setOracleMode(address token, Mode mode) external {
    // can not be unset
    if (mode == Mode.NOT_SET) {
        revert InvalidConfig();
    }

    if (msg.sender != emergencyAdmin && msg.sender != owner()) {
        revert Unauthorized();
    }

    feedConfigs[token].mode = mode;
    emit OracleModeUpdated(token, mode);
}
```

In the optimized code, the condition `if (mode == Mode.NOT_SET)` is checked first. If this condition evaluates to true, the function reverts with an `InvalidConfig` error, and the subsequent condition `if (msg.sender != emergencyAdmin && msg.sender != owner())` is not executed. This avoids the unnecessary access of the `emergencyAdmin` storage variable, resulting in potential gas savings.


## Enhancing Gas Efficiency: Inline Assembly Optimization in `setTokenConfig` Function
**Original Code:**
The original function performs pool validation using straightforward Solidity conditionals. However, this approach can lead to higher gas consumption due to the multiple comparisons and conditional branching involved.
### Befor
| src/V3Oracle.sol:V3Oracle contract |                 |       |        |       |         |
|------------------------------------|-----------------|-------|--------|-------|---------|
| Deployment Cost                    | Deployment Size |       |        |       |         |
| 2478820                            | 12900           |       |        |       |         |
| Function Name                      | min             | avg   | median | max   | # calls |
| setTokenConfig                     | 21410           | 66708 | 68373  | 70643 | 91      |

```solidity
            if (!(token0 == token && token1 == referenceToken || token0 == referenceToken && token1 == token)) {
                revert InvalidPool();
            }
```
src/V3Oracle.sol#L227
**Optimization Technique:**
To optimize gas usage, we utilize inline assembly to condense the pool validation logic. By directly implementing the condition `(token0 == token && token1 == referenceToken) || (token0 == referenceToken && token1 == token)` using assembly language, we avoid unnecessary branching and comparison operations.


| src/V3Oracle.sol:V3Oracle contract |                 |       |        |       |         |
|------------------------------------|-----------------|-------|--------|-------|---------|
| Deployment Cost                    | Deployment Size |       |        |       |         |
| 2458782                            | 12793           |       |        |       |         |
| Function Name                      | min             | avg   | median | max   | # calls |
| setTokenConfig                     | 21313           | 66636 | 68299  | 70503 | 91      |

```solidity
        address _referenceToken = referenceToken;           
        bool isValidPool;
        assembly {
            isValidPool := or(and(eq(token0, token), eq(token1, _referenceToken)), and(eq(token0, _referenceToken), eq(token1, token)))
        }
```


## State variables should be cached in stack variables rather than re-reading them from storage
The instances below point to the second+ access of a state variable within a function. Caching of a state variable replaces each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses.

Saves 100 gas per instance

- `transformedTokenId` is State variables should be cached in stack variables to save 100 gas.
```solidity
551      bool isTransformMode =
            transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L551-L552 



## Can Make The Variable Outside The Loop To Save Gas 
When you declare a variable inside a loop, Solidity creates a new instance of the variable for each iteration of the loop. This can lead to unnecessary gas costs, especially if the loop is executed frequently or iterates over a large number of elements.

By declaring the variable outside the loop, you can avoid the creation of multiple instances of the variable and reduce the gas cost of your contract. Here's an example:

```
contract MyContract {
    function sum(uint256[] memory values) public pure returns (uint256) {
        uint256 total = 0;
        
        for (uint256 i = 0; i < values.length; i++) {
            total += values[i];
        }
        
        return total;
    }
}
```

There are 2 instances of this issue:

```solidity
112   uint256 balance = IERC20(tokens[i]).balanceOf(address(this));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L112


```solidity
234  uint256 balance = positionBalances[0][tokens[i]];
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L234


## Make 3 event parameters indexed when possible
It is the most gas efficient to make up to 3 event parameters indexed. If there are less than 3 parameters, you need to make all parameters indexed.

- all most of all events



## Amounts should be checked for 0 before calling a transfer
Checking non-zero transfer values can avoid an expensive external call and save gas.



```solidity
226  SafeERC20.safeTransfer(token, to, amount);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L226



## With assembly, .call (bool success) transfer can be done gas-optimized
return data (bool success,) has to be stored due to EVM architecture, but in a usage like below, ‘out’ and ‘outsize’ values are given (0,0), this storage disappears and gas optimization is provided.
https://code4rena.com/reports/2023-01-biconomy#g-01-with-assembly-call-bool-success-transfer-can-be-done-gas-optimized



```solidity
130  (bool sent,) = to.call{value: balance}("");

221  (bool sent,) = to.call{value: amount}("");
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L130



```solidity
867  (bool sent,) = to.call{value: amount}("");
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L867



## Use constants instead of type(uintx).max
Using constants instead of type(uintx).max can save gas in some cases because constants are precomputed at compile-time and can be reused throughout the code, whereas type(uintx).max requires computation at runtime


- in side V3Vault contract in 10 time use.
- in side AutoCompound contract 4 time use. 
- in side LeverageTransformer contract 4 time use.



## Use assembly to perform efficient back-to-back calls
If a similar external call is performed back-to-back, we can use assembly to reuse any function signatures and function parameters that stay the same. In addition, we can also reuse the same memory space for each function call (scratch space + free memory pointer + zero slot), which can potentially allow us to avoid memory expansion costs.
Note: In order to do this optimization safely we will cache the free memory pointer value and restore it once we are done with our function calls. We will also set the zero slot back to 0 if neccessary.
[Reffrence](https://code4rena.com/reports/2023-05-ajna#g-10-use-assembly-to-perform-efficient-back-to-back-calls)


```solidity
43      address token = IVault(msg.sender).asset();
45      IVault(msg.sender).borrow(params.tokenId, amount);      
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L43-L45



```solidity
896        uint256 balanceBefore0 = token0.balanceOf(address(this));
           uint256 balanceBefore1 = token1.balanceOf(address(this));  


901         uint256 balanceAfter0 = token0.balanceOf(address(this));
            uint256 balanceAfter1 = token1.balanceOf(address(this));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L896



```solidity
225            address token0 = pool.token0();
               address token1 = pool.token1();
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L225-L226


## Using constants instead of enum can save gas
Enum is expensive and it is more efficient to use constants instead. An illustrative example of this approach can be found in the ReentrancyGuard.sol.

```solidity
35    enum Mode {
        NOT_SET,
        CHAINLINK_TWAP_VERIFY, // using chainlink for price and TWAP to verify
        TWAP_CHAINLINK_VERIFY, // using TWAP for price and chainlink to verify
        CHAINLINK, // using only chainlink directly
        TWAP // using TWAP directly
    }
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L35-L41



```solidity
41    enum WhatToDo {
        CHANGE_RANGE,
        WITHDRAW_AND_COLLECT_AND_SWAP,
        COMPOUND_FEES
    }
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L41-L45


## Move storage pointer to top of function to avoid offset calculation
We can avoid unnecessary offset calculations by moving the storage pointer to the top of the function.

```solidity
558  Loan storage loan = loans[tokenId];
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L558



## Consider using OZ EnumerateSet in place of nested mappings             
Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).
A possible optimization involves manually concatenating the keys followed by a single hash operation and an sstore. However, this technique introduces the risk of storage collision, especially when there are other nested hash maps in the contract that use the same key types. Because Solidity is unaware of the number and structure of nested hash maps in a contract, it follows a conservative approach in computing the storage slot to avoid possible collisions.
OpenZeppelin's EnumerableSet provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios



```solidity
164   mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L164



```solidity
45    mapping(uint256 => mapping(address => uint256)) public positionBalances;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L45



## Instead of counting down in for statements, count up
Counting down is more gas efficient than counting up because neither we are making zero variable to non-zero variable and also we will get gas refund in the last transaction when making non-zero to zero variable.



```solidity
109     uint256 i;
        uint256 count = tokens.length;
        for (; i < count; ++i) {
            uint256 balance = IERC20(tokens[i]).balanceOf(address(this));
            if (balance > 0) {
                _transferToken(to, IERC20(tokens[i]), balance, true);
            }
        }
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L109-L116



```solidity
231     uint256 i;
        uint256 count = tokens.length;
        for (; i < count; ++i) {
            uint256 balance = positionBalances[0][tokens[i]];
            _withdrawBalanceInternal(0, tokens[i], to, balance, balance);
        }
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L231-L236