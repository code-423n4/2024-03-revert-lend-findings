## Summary

### Gas Optimization

no | Issue |Instances||
|-|:-|:-:|:-:|
| [G-01] | Can make the variable outside the loop to save gas | 1 | - |
| [G-02] | Don't initialize variables with default value | 12 | - |
| [G-03] | Using storage instead of memory for structs/arrays saves gas | 3 | - |
| [G-04] | Duplicated require()/if() checks should be refactored to a modifier or function | 1 | - |
| [G-05] |  Use constants instead of type(uintx).max | 9 | - |
| [G-06] | Use selfbalance() instead of address(this).balance | 1 | - |
| [G-07] | Using ERC721A instead of ERC721 for more gas-efficient  | 3 | - |
| [G-08] | Use hardcode address instead address(this) | 4 | - |
| [G-09] | Avoid fetching a low-level call's return data by using assembly | 2 | - |
| [G-10] | Using assembly to check for zero can save gas | 2 | - |
| [G-11] | Pre-increment and pre-decrement are cheaper than + 1 ,- 1 | 2 | - |
| [G-12] | address(this) should be cached | 10 | - |

## Gas Optimizations  

## [G-01]  Can make the variable outside the loop to save gas
 

```solidity
file: /src/automators/Automator.sol

112            uint256 balance = IERC20(tokens[i]).balanceOf(address(this));

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L112C1-L112C74


## [G-02]  Don't initialize variables with default value
 

```solidity
file: /src/V3Vault.so

118    uint32 public reserveFactorX32 = 0;

124    uint256 public debtSharesTotal = 0;

127    uint256 public lastExchangeRateUpdate = 0;

131    uint256 public globalDebtLimit = 0;

132    uint256 public globalLendLimit = 0;

135    uint256 public minLoanSize = 0;

138    uint256 public dailyLendIncreaseLimitMin = 0;
139    uint256 public dailyLendIncreaseLimitLeft = 0;
140    uint256 public dailyLendIncreaseLimitLastReset = 0;

143    uint256 public dailyDebtIncreaseLimitMin = 0;
144    uint256 public dailyDebtIncreaseLimitLeft = 0;
145    uint256 public dailyDebtIncreaseLimitLastReset = 0;


```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L118C1-L118C40


## [G-03]  Using storage instead of memory for structs/arrays saves gas

When fetching data from a storage location, assigning the data to a memory variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (2100 gas) for each field of the struct/array. If the fields are read from the new memory variable, they incur an additional MLOAD rather than a cheap stack read. Instead of declearing the variable with the memory keyword, declaring the variable with the storage keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incuring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a memory variable, is if the full struct/array is being returned by the function, is being passed to a function that requires memory, or if the array/struct is being read from another memory array/struct

```solidity
file: /src/automators/Automator.sol

181        uint32[] memory secondsAgos = new uint32[](2);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L181C1-L181C55


```solidity
file: /src/transformers/V3Utils.sol

613        ISignatureTransfer.SignatureTransferDetails[] memory transferDetails =
614            new ISignatureTransfer.SignatureTransferDetails[](permit.permitted.length);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L613C1-L614C88


```solidity
file: /src/V3Oracle.sol

365            uint32[] memory secondsAgos = new uint32[](2);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L365C1-L365C59


## [G-04] Duplicated require()/if() checks should be refactored to a modifier or function   

   to reduce code duplication and improve readability.
•  Modifiers can be used to perform additional checks on the function inputs or state before it is executed. By defining a modifier to perform a specific check, we can reuse it across multiple functions that require the same check.
• A function can also be used to perform a specific check and return a boolean value indicating whether the check has passed or failed. This can be useful when the check is more complex and cannot be performed easily in a modifier.


```solidity
file: /src/V3Vault.sol

118        if (transformedTokenId > 0) {

615        if (transformedTokenId > 0) {

687        if (transformedTokenId > 0) { 

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L118C1-L118C40


## [G-05] Use constants instead of type(uintx).max

type(uint120).max or type(uint128).max, etc. it uses more gas in the distribution process and also for each transaction than constant usage.


```solidity
file: /src/V3Vault.sol

636            params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
637            params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)

1046            fees0 = type(uint128).max;
1047            fees1 = type(uint128).max;

1058                fees0 = type(uint128).max;
1059                fees1 = type(uint128).max;

1228                    collateralValueLimitFactorX32 < type(uint32).max

1236                    collateralValueLimitFactorX32 < type(uint32).max

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L636C1-L637C121


```solidity
file: /src/automators/Automator.sol
 
209            INonfungiblePositionManager.CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max)

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L209C1-L209C116


## [G-06] Use selfbalance() instead of address(this).balance

Using selfbalance() instead of address(this).balance can save gas in Solidity because selfbalance() is a built-in function that returns the balance of the current contract directly as a uint256 value, without the need to create a new address object.
On the other hand, using address(this).balance to get the balance of the current contract creates a new address object, which consumes more gas and can make the code less efficient.
By using selfbalance(), you can reduce the amount of gas consumed by your Solidity code and make your contracts more efficient.


```solidity
file: /src/automators/Automator.sol

128        uint256 balance = address(this).balance;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L128C1-L128C49


## [G-07] Using ERC721A instead of ERC721 for more gas-efficient 

ERC721A is a proposed extension to the ERC721 standard that aims to improve gas efficiency and reduce the cost of deploying and using non-fungible tokens (NFTs) on the Ethereum blockchain. 

```solidity
file: /src/V3Vault.sol

30  contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {

429    function onERC721Received(address, address from, uint256 tokenId, bytes calldata data) 

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30C1-L30C82


```solidity
file: /src/transformers/V3Utils.sol

15  contract V3Utils is Swapper, IERC721Receiver {

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L15C1-L15C47


## [G-08] Use hardcode address instead address(this)
 
Instead of using address(this), it is more gas-efficient to pre-calculate and use the hardcoded address. Foundry’s script.sol and solmate’s LibRlp.sol contracts can help achieve this.
References: https://book.getfoundry.sh/reference/forge-std/compute-create-address

```solidity
file: /src/V3Vault.sol

401        nonfungiblePositionManager.safeTransferFrom(msg.sender, address(this), tokenId, abi.encode(recipient));

423        nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L401C1-L401C112


```solidity
file: /src/transformers/AutoCompound.sol

278        uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager));

282        uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager));

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L278C1-L278C107


## [G-09] Avoid fetching a low-level call's return data by using assembly

Even if you don't assign the call's second return value, it still gets copied to memory. Use assembly instead to prevent this and save 159 gas:
`(bool success,) = payable(receiver).call{gas: gas, value: value}("");` -> `bool success; assembly { success := call(gas, receiver, value, 0, 0, 0, 0) }`

```solidity
file: /src/automators/Automator.sol

130            (bool sent,) = to.call{value: balance}("");

221            (bool sent,) = to.call{value: amount}("");

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L130C1-L130C56


## [G-10] Using assembly to check for zero can save gas

Using assembly to check for zero can save gas by allowing more direct access to the evm and reducing some of the overhead associated with high-level operations in solidity.

```solidity
file: /src/V3Vault.sol

441        if (transformedTokenId == 0) {

502        if (tokenId == 0 || !transformerAllowList[transformer]) { 

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L441C1-L441C39


```solidity
file: /src/automators/AutoExit.sol

124        if (state.liquidity == 0) {

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L124C1-L124C36


## [G-11] Pre-increment and pre-decrement are cheaper than + 1 ,- 1

```solidity
file: /src/utils/Swapper.sol

138                (params.swap0For1 ? TickMath.MIN_SQRT_RATIO + 1 : TickMath.MAX_SQRT_RATIO - 1),

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L138C1-L138C96


```solidity
file: /src/V3Vault.sol

1304        uint256 lastTokenIndex = ownedTokens[from].length - 1;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1304C1-L1304C63


## [G-12] address(this) should be cached

Cacheing saves gas when compared to repeating the calculation at each point it is used in the contract.The instance below represents the second+ time of calling address(this) in a specific function

```solidity
file: /src/V3Vault.sol

285        return IERC20(asset).balanceOf(address(this));

401        return IERC20(asset).balanceOf(address(this));

423        nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);

424        nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));

435        if (msg.sender != address(nonfungiblePositionManager) || from == address(this)) {

532        if (owner != address(this)) {

561        if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {

722                ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost),

728            SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);

791            transformer == address(0) || transformer == address(this) || transformer == asset

897                permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L285C1-L285C55
