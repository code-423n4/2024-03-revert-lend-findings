## Low Findings

|    | Issue | Instances |
|----|-------|:---------:|
| [L-01] | Centralization risk for privileged functions | 15 |
| [L-02] | Subtraction may underflow if multiplication is too large | 1 |
| [L-03] | `decimals()` is not part of the ERC20 standard | 4 |
| [L-04] | `type(uint256).max` Approvals Aren't Universal in All Tokens | 2 |
| [L-05] | Some tokens may revert on large transfers | 23 |
| [L-06] | Code does not follow the best practice of check-effects-interaction | 5 |
| [L-07] | Use `abi.encodeCall()` instead of `abi.encodeWithSignature()`/`abi.encodeWithSelector()` | 2 |
| [L-08] | `internal/private` Function calls within for loops | 2 |
| [L-09] | Upgradable contracts not taken into account | 94 |
| [L-10] | Lack of index element validation in external/public function | 31 |
| [L-11] | Consider checking that transfer to `address(this)` is disabled | 1 |
| [L-12] | Use `forceApprove/safeIncreaseAllowance` from SafeERC20 instead of `approve/safeApprove` | 7 |
| [L-13] | Potential Gas Griefing Due to Non-Handling of Return Data in External Calls | 3 |
| [L-14] | Low Level Calls to Custom Addresses | 3 |
| [L-15] | Prevent Division by Zero | 4 |
| [L-16] | Solidity version 0.8.20 may not work on other chains due to `PUSH0` | 11 |
| [L-17] | Missing checks for `address(0x0)` when updating address state variables | 2 |
| [L-18] | Lack of Parameter Validation in Constructor/Initializer | 10 |
| [L-19] | Owner can renounce Ownership | 4 |
| [L-20] | State variables are not limited to a reasonable range | 11 |
| [L-21] | Missing Contract-Existence Checks Before Low-Level Calls | 3 |
| [L-22] | Events may be emitted out of order due to reentrancy | 13 |
| [L-23] | External calls in an un-bounded `for-`loop may result in a DOS | 1 |
| [L-24] | For loops in public or external functions should be avoided due to high gas costs and possible DOS | 2 |
| [L-25] | Critical functions should be a two step procedure | 16 |
| [L-26] | Deprecated Function `safeApprove` Usage | 15 |
| [L-27] | Loss of precision | 30 |
| [L-28] | Unsafe Conversion from various type `int/uint` values | 4 |
| [L-29] | Mapping arrays can grow in size without a way to shrink them | 1 |
| [L-30] | Unbounded Gas Consumption on External Calls | 3 |
| [L-31] | Unsafe downcast from larger to smaller integer types | 2 |
| [L-32] | Consider implementing two-step procedure for updating protocol addresses | 3 |
| [L-33] | Possible Revert ERC20 Transfers with Zero Value | 10 |
| [L-34] | Function Parameters in Public Accessible Functions Need `address(0)` Check | 36 |
| [L-35] | Missing `address(0)` Check in Constructor | 5 |
| [L-36] | Functions calling tokens with transfer hooks are missing reentrancy guards | 29 |
| [L-37] | Consider Using `Ownable2Step` rather than `Ownable` | 6 |


## NonCritical Findings

|    | Issue | Instances |
|----|-------|:---------:|
| [N-01] | Ensure `payable` Functions Properly Handle Ether Transfers | 1 |
| [N-02] | Non-library/interface files should use fixed compiler versions, not floating ones | 11 |
| [N-03] | Array indices should be referenced via `enum`s rather than via numeric literals | 9 |
| [N-04] | Consider splitting long calculations | 6 |
| [N-05] | Use custom errors instead of `require()/assert()` | 3 |
| [N-06] | Variables need not be initialized to zero | 13 |
| [N-07] | `require()/revert()` statements without reason strings | 1 |
| [N-08] | Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability | 9 |
| [N-09] | Consider returning a `struct` rather than having multiple `return` values | 15 |
| [N-10] | Consider using a `struct` rather than having many function input parameters | 21 |
| [N-11] | Consider using descriptive `constant`s when passing zero as a function argument | 32 |
| [N-12] | Consider using OpenZeppelin's SafeCast for any casting | 21 |
| [N-13] | Consider using `delete` rather than assigning `zero` to clear values | 5 |
| [N-14] | Consider emitting an event at the end of the constructor | 11 |
| [N-15] | Consider using named returns | 31 |
| [N-16] | Style guide: Initialisms should be capitalized | 1 |
| [N-17] | Expressions for constant values should use `immutable` rather than `constant` | 16 |
| [N-18] | Consider using named function arguments | 30 |
| [N-19] | Events are missing sender information | 30 |
| [N-20] | Leverage Recent Solidity Features with `0.8.23` | 11 |
| [N-21] | NatSpec: Function `@param` tag is missing | 80 |
| [N-22] | High cyclomatic complexity | 15 |
| [N-23] | Contract should expose an `interface` | 16 |
| [N-24] | NatSpec: Function declarations should have descriptions | 16 |
| [N-25] | Contract uses both `require()`/`revert()` as well as custom errors | 8 |
| [N-26] | Inconsistent spacing in comments | 1 |
| [N-27] | Critical system parameter changes should be behind a timelock | 16 |
| [N-28] | Outdated Solidity Version | 11 |
| [N-29] | Ensure Non-Empty Check for Bytes in Function Parameters | 11 |
| [N-30] | Adding a `return` statement when the function defines a named return variable, is redundant | 1 |
| [N-31] | Function/Constructor Argument Names Not in mixedCase | 16 |
| [N-32] | NatSpec: Function `@return` tag is missing | 47 |
| [N-33] | State-Altering Functions Should Emit Events | 3 |
| [N-34] | Contract Doesn't Handle All NFT Types | 2 |
| [N-35] | Upgrade `openzeppelin` to the Latest Version - 5.0.0 | 21 |
| [N-36] | Duplicated `require()`/`revert()` checks should be refactored to a modifier or function | 10 |
| [N-37] | Non-specific Imports | 70 |
| [N-38] | Event is not properly `indexed` | 38 |
| [N-39] | Consider Using `safePermit()` Instead of `permit()` | 2 |
| [N-40] | Consider Adding Emergency-Stop Functionality | 1 |
| [N-41] | NatSpec: Public State variable declarations should have descriptions | 55 |
| [N-42] | Consider adding a block/deny-list | 1 |
| [N-43] | Non-uppercase/Constant-case Naming for `immutable` Variables | 18 |
| [N-44] | Not using the named return variables anywhere in the function is confusing | 5 |
| [N-45] | Function Names Not in mixedCase | 5 |
| [N-46] | Insufficient Comments in Complex Functions | 15 |
| [N-47] | Common functions should be refactored to a common base contract | 8 |
| [N-48] | NatSpec: Non-public state variable declarations should use `@dev` tags | 11 |
| [N-49] | `constant`s should be defined rather than using magic numbers | 8 |
| [N-50] | Consider moving `msg.sender` checks to a common authorization `modifier` | 24 |
| [N-51] | NatSpec: Contract declarations should have descriptions | 2 |
| [N-52] | NatSpec: Contract declarations should have `@author` tag | 9 |
| [N-53] | Missing NatSpec Descriptions for Event Declarations | 36 |
| [N-54] | Invalid NatSpec comment style | 1 |
| [N-55] | Consider defining system-wide constants in a single file | 20 |
| [N-56] | Add inline comments for unnamed variables | 4 |
| [N-57] | Consider making contracts `Upgradeable` | 11 |
| [N-58] | Events that mark critical parameter changes should contain both the old and the new value | 3 |
| [N-59] | Style guide: Non-`external`/`public` variable names should begin with an underscore | 12 |
| [N-60] | Style guide: Contract does not follow the Solidity style guide's suggested layout ordering | 24 |
| [N-61] | Using Low-Level Call for Transfers | 3 |
| [N-62] | Consider bounding input array length | 2 |
| [N-63] | NatSpec: Function declarations should have `@notice` tag | 17 |
| [N-64] | Constants in comparisons should appear on the left side | 70 |
| [N-65] | NatSpec: Contract declarations should have `@notice` tag | 1 |
| [N-66] | Large numeric literals should use underscores for readability | 5 |
| [N-67] | Named Imports of Parent Contracts Are Missing | 22 |
| [N-68] | Long functions should be refactored into multiple, smaller, functions | 15 |
| [N-69] | NatSpec: Contract declarations should have `@dev` tags | 9 |
| [N-70] | `public` functions not called by the contract should be declared `external` instead | 7 |
| [N-71] | Large multiples of ten should use scientific notation | 4 |
| [N-72] | Complex casting | 2 |
| [N-73] | Equal `block.timestamp` Cases Not Handled | 2 |
| [N-74] | `else`-block not required | 6 |
| [N-75] | Polymorphic functions make security audits more time-consuming and error-prone | 6 |
| [N-76] | Style guide: Function ordering does not follow the Solidity style guide | 18 |
| [N-77] | Style guide: Lines are too long | 50 |
| [N-78] | Numeric Values Related to Time Lacking Units | 1 |
| [N-79] | Style guide: Extraneous whitespace | 28 |
| [N-80] | Avoid the use of sensitive terms | 1 |
| [N-81] | Unused import | 12 |
| [N-82] | `if`-statement can be converted to a ternary | 2 |
| [N-83] | Consider using named mappings | 13 |
| [N-84] | Use of `override` is unnecessary | 40 |
| [N-85] | Setters should prevent re-setting of the same value | 25 |
| [N-86] | Use Unchecked for Divisions on Constant or Immutable Values | 20 |
| [N-87] | Contracts should have full test coverage | 1 |
| [N-88] | Large or complicated code bases should implement invariant tests | 1 |
| [N-89] | Implement Formal Verification Proofs to Improve Security | 1 |


## Low Findings Details

### [L-01] Centralization risk for privileged functions

Functions that grant centralized privileges introduce a notable security risk.
Such functions can act as a single point of vulnerability, especially if they control critical operations or access to sensitive data.
        
If the account or entity with these privileges gets compromised, it could lead to the unauthorized alteration of the contract's state, asset misappropriation, or other malicious activities.
It's essential to implement robust access controls, frequent audits, and potentially decentralize critical functions to mitigate this risk.

<details>
<summary><i>15 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

765: function withdrawReserves(uint256 amount, address receiver) external onlyOwner
788: function setTransformer(address transformer, bool active) external onlyOwner
837: function setReserveFactor(uint32 _reserveFactorX32) external onlyOwner
844: function setReserveProtectionFactor(uint32 _reserveProtectionFactorX32) external onlyOwner
856: function setTokenConfig(address token, uint32 collateralFactorX32, uint32 collateralValueLimitFactorX32)
        external
        onlyOwner
870: function setEmergencyAdmin(address admin) external onlyOwner
```
[765](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L765) | [788](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L788) | [837](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L837) | [844](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L844) | [856](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L856) | [870](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L870)

```solidity
File: src/V3Oracle.sol

185: function setMaxPoolPriceDifference(uint16 _maxPoolPriceDifference) external onlyOwner
201: function setTokenConfig(
        address token,
        AggregatorV3Interface feed,
        uint32 maxFeedAge,
        IUniswapV3Pool pool,
        uint32 twapSeconds,
        Mode mode,
        uint16 maxDifference
    ) external onlyOwner
265: function setEmergencyAdmin(address admin) external onlyOwner
```
[185](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L185) | [201](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L201) | [265](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L265)

```solidity
File: src/InterestRateModel.sol

82: function setValues(
        uint256 baseRatePerYearX96,
        uint256 multiplierPerYearX96,
        uint256 jumpMultiplierPerYearX96,
        uint256 _kinkX96
    ) public onlyOwner
```
[82](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L82)

```solidity
File: src/automators/Automator.sol

59: function setWithdrawer(address _withdrawer) public onlyOwner
69: function setOperator(address _operator, bool _active) public onlyOwner
79: function setVault(address _vault, bool _active) public onlyOwner
87: function setTWAPConfig(uint16 _maxTWAPTickDifference, uint32 _TWAPSeconds) public onlyOwner
```
[59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L59) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L69) | [79](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L79) | [87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L87)

```solidity
File: src/transformers/AutoCompound.sol

243: function setReward(uint64 _totalRewardX64) external onlyOwner
```
[243](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L243)
</details>

### [L-02] Subtraction may underflow if multiplication is too large

In scenarios where a large multiplication precedes a subtraction, there is a heightened risk of underflow. This can occur if the multiplication results in a significantly large value, potentially leading to an underflow when it is subsequently subtracted.
Such underflows can cause critical miscalculations, affecting the contract's logic and integrity.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

1107: (Q96 - ((fullValue - maxPenaltyValue) * Q96 / (startLiquidationValue - maxPenaltyValue)));
```
[1107](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1107)
</details>

### [L-03] `decimals()` is not part of the ERC20 standard

It's often used, but `decimals()` is not part of the original ERC-20 standard. It was added later as an optional extension. 
Some valid ERC-20 tokens do not support this function, so casting all tokens to an interface that includes `decimals()` can be unsafe.
Consider revising your code to account for tokens that may not implement the `decimals()` function.

<details>
<summary><i>4 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

179: assetDecimals = IERC20Metadata(_asset).decimals();
```
[179](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L179)

```solidity
File: src/V3Oracle.sol

82: referenceTokenDecimals = IERC20Metadata(_referenceToken).decimals();
215: uint8 feedDecimals = feed.decimals();
216: uint8 tokenDecimals = IERC20Metadata(token).decimals();
```
[82](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L82) | [215](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L215) | [216](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L216)
</details>

### [L-04] `type(uint256).max` Approvals Aren't Universal in All Tokens

Certain tokens, do not recognize `type(uint256).max` as signifying an infinite approval.
            
- [COMP (Compound Protocol)](https://github.com/compound-finance/compound-protocol/blob/a3214f67b73310d547e00fc578e8355911c9d376/contracts/Governance/Comp.sol#L86-L98)
- [UNI (Uniswap)](https://github.com/Uniswap/governance/blob/eabd8c71ad01f61fb54ed6945162021ee419998e/contracts/Uni.sol#L149-L161)

Instead, they downcast such approvals to `uint96`, treating it as a standard numerical limit rather than an infinite allowance.
Once these approvals are depleted, the dependent contract operations could be hampered or halted entirely.

<details>
<summary><i>2 issue instances in 1 files:</i></summary>

```solidity
File: src/transformers/AutoCompound.sol

280: SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max)
284: SafeERC20.safeApprove(IERC20(token1), address(nonfungiblePositionManager), type(uint256).max)
```
[280](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L280) | [284](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L284)
</details>

### [L-05] Some tokens may revert on large transfers

Tokens like:
            
- [COMP (Compound Protocol)](https://github.com/compound-finance/compound-protocol/blob/a3214f67b73310d547e00fc578e8355911c9d376/contracts/Governance/Comp.sol#L115-L142)
- [UNI (Uniswap)](https://github.com/Uniswap/governance/blob/eabd8c71ad01f61fb54ed6945162021ee419998e/contracts/Uni.sol#L209-L236)
            
have limit set by `uint96`.
            
Transfers that approach or exceed this limit will revert.
Be cautious of such transfers, especially if batching is not implemented to handle these scenarios.

<details>
<summary><i>23 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

599: SafeERC20.safeTransfer(IERC20(asset), isTransformMode ? msg.sender : owner, assets)
728: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost)
779: SafeERC20.safeTransfer(IERC20(asset), receiver, amount)
901: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets)
946: SafeERC20.safeTransfer(IERC20(asset), receiver, assets)
986: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets)
```
[599](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L599) | [728](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L728) | [779](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L779) | [901](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L901) | [946](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L946) | [986](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L986)

```solidity
File: src/automators/Automator.sol

226: SafeERC20.safeTransfer(token, to, amount)
```
[226](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L226)

```solidity
File: src/transformers/AutoCompound.sol

272: SafeERC20.safeTransfer(IERC20(token), to, amount)
```
[272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L272)

```solidity
File: src/transformers/LeverageTransformer.sol

88: SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0 - added0)
91: SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1 - added1)
94: SafeERC20.safeTransfer(IERC20(token), params.recipient, amount)
170: SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0)
173: SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1)
```
[88](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L88) | [91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L91) | [94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L94) | [170](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L170) | [173](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L173)

```solidity
File: src/transformers/V3Utils.sol

578: SafeERC20.safeTransferFrom(token0, msg.sender, address(this), needed0)
581: SafeERC20.safeTransferFrom(token1, msg.sender, address(this), needed1)
584: SafeERC20.safeTransferFrom(otherToken, msg.sender, address(this), neededOther)
872: SafeERC20.safeTransfer(token, to, amount)
```
[578](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L578) | [581](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L581) | [584](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L584) | [872](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L872)

```solidity
File: src/utils/FlashloanLiquidator.sol

85: SafeERC20.safeTransfer(data.asset, msg.sender, data.liquidationCost + (fee0 + fee1))
91: SafeERC20.safeTransfer(data.swap0.tokenIn, data.liquidator, balance)
97: SafeERC20.safeTransfer(data.swap1.tokenIn, data.liquidator, balance)
106: SafeERC20.safeTransfer(data.asset, data.liquidator, balance)
```
[85](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L85) | [91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L91) | [97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L97) | [106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L106)

```solidity
File: src/utils/Swapper.sol

98: SafeERC20.safeTransfer(params.tokenIn, universalRouter, params.amountIn)
167: SafeERC20.safeTransfer(IERC20(tokenIn), msg.sender, amountToPay)
```
[98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L98) | [167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L167)
</details>

### [L-06] Code does not follow the best practice of check-effects-interaction

Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

<details>
<summary><i>5 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit - State change after external call: `SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost)`
731: debtSharesTotal -= debtShares
/// @audit - State change after external call: `SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets)`
913: dailyLendIncreaseLimitLeft -= assets
/// @audit - State change after external call: `SafeERC20.safeTransfer(IERC20(asset), receiver, assets)`
949: dailyLendIncreaseLimitLeft += assets
/// @audit - State change after external call: `SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets)`
992: debtSharesTotal -= shares
```
[731](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L731) | [913](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L913) | [949](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L949) | [992](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L992)

```solidity
File: src/transformers/AutoRange.sol

/// @audit - State change after external call: `nonfungiblePositionManager.safeTransferFrom(address(this), state.owner, state.newTokenId)`
251: positionConfigs[state.newTokenId] = config
```
[251](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L251)
</details>

### [L-07] Use `abi.encodeCall()` instead of `abi.encodeWithSignature()`/`abi.encodeWithSelector()`

As of Solidity version 0.8.11, `abi.encodeCall()` provides type-safe encoding utility, a notable enhancement over `abi.encodeWithSelector()`.
While the latter can prevent typographical errors, it doesn't provide type checking.
The use of `abi.encodeCall()` introduces type safety at compile time, leading to safer and more robust smart contracts.
[Read more about type safety](https://github.com/OpenZeppelin/openzeppelin-contracts/issues/3693)

Please note that adopting `abi.encodeCall()` requires bumping the Solidity pragma, which could introduce breaking changes.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/transformers/AutoCompound.sol

92: abi.encodeWithSelector(AutoCompound.execute.selector, params)
```
[92](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L92)

```solidity
File: src/transformers/AutoRange.sol

102: abi.encodeWithSelector(AutoRange.execute.selector, params)
```
[102](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L102)
</details>

### [L-08] `internal/private` Function calls within for loops

Making function calls or external calls within loops in Solidity can lead to inefficient gas usage, potential bottlenecks, and increased vulnerability to attacks.
Each function call or external call consumes gas, and when executed within a loop, the gas cost multiplies, potentially causing the transaction to run out of gas or exceed block gas limits.
This can result in transaction failure or unpredictable behavior.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/automators/Automator.sol

114: _transferToken(to, IERC20(tokens[i]), balance, true);
```
[114](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L114)

```solidity
File: src/transformers/AutoCompound.sol

235: _withdrawBalanceInternal(0, tokens[i], to, balance, balance)
```
[235](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L235)
</details>

### [L-09] Upgradable contracts not taken into account

In the realm of blockchain development, it's crucial to consider the impact of upgradable contracts, especially when handling token addresses through interfaces like IERC20.
These contracts can evolve over time, potentially altering their behavior or interface. Such changes may lead to compatibility issues or security vulnerabilities in the protocol that relies on them.

<details>
<summary><i>94 issue instances in 10 files:</i></summary>

```solidity
File: src/V3Vault.sol

179: assetDecimals = IERC20Metadata(_asset).decimals();
285: return IERC20(asset).balanceOf(address(this));
599: SafeERC20.safeTransfer(IERC20(asset), isTransformMode ? msg.sender : owner, assets);
728: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);
779: SafeERC20.safeTransfer(IERC20(asset), receiver, amount);
901: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
946: SafeERC20.safeTransfer(IERC20(asset), receiver, assets);
986: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
```
[179](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L179) | [285](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L285) | [599](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L599) | [728](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L728) | [779](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L779) | [901](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L901) | [946](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L946) | [986](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L986)

```solidity
File: src/V3Oracle.sol

82: referenceTokenDecimals = IERC20Metadata(_referenceToken).decimals();
216: uint8 tokenDecimals = IERC20Metadata(token).decimals();
```
[82](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L82) | [216](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L216)

```solidity
File: src/automators/AutoExit.sol

173: state.isAbove ? IERC20(state.token1) : IERC20(state.token0),
173: state.isAbove ? IERC20(state.token1) : IERC20(state.token0),
174: state.isAbove ? IERC20(state.token0) : IERC20(state.token1),
174: state.isAbove ? IERC20(state.token0) : IERC20(state.token1),
200: _transferToken(state.owner, IERC20(state.token0), state.amount0, true);
203: _transferToken(state.owner, IERC20(state.token1), state.amount1, true);
```
[173](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L173) | [173](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L173) | [174](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L174) | [174](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L174) | [200](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L200) | [203](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L203)

```solidity
File: src/automators/Automator.sol

112: uint256 balance = IERC20(tokens[i]).balanceOf(address(this));
114: _transferToken(to, IERC20(tokens[i]), balance, true);
```
[112](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L112) | [114](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L114)

```solidity
File: src/transformers/AutoCompound.sol

144: pool, IERC20(state.token0), IERC20(state.token1), state.fee, params.swap0To1, amountIn, 0
144: pool, IERC20(state.token0), IERC20(state.token1), state.fee, params.swap0To1, amountIn, 0
272: SafeERC20.safeTransfer(IERC20(token), to, amount);
278: uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager));
280: SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max);
282: uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager));
284: SafeERC20.safeApprove(IERC20(token1), address(nonfungiblePositionManager), type(uint256).max);
```
[144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L144) | [144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L144) | [272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L272) | [278](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L278) | [280](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L280) | [282](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L282) | [284](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L284)

```solidity
File: src/transformers/AutoRange.sol

183: params.swap0To1 ? IERC20(state.token0) : IERC20(state.token1),
183: params.swap0To1 ? IERC20(state.token0) : IERC20(state.token1),
184: params.swap0To1 ? IERC20(state.token1) : IERC20(state.token0),
184: params.swap0To1 ? IERC20(state.token1) : IERC20(state.token0),
213: SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), state.maxAddAmount0);
214: SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), state.maxAddAmount1);
220: SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), 0);
221: SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), 0);
244: _transferToken(state.realOwner, IERC20(state.token0), state.amount0 - state.amountAdded0, true);
247: _transferToken(state.realOwner, IERC20(state.token1), state.amount1 - state.amountAdded1, true);
```
[183](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L183) | [183](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L183) | [184](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L184) | [184](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L184) | [213](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L213) | [214](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L214) | [220](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L220) | [221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L221) | [244](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L244) | [247](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L247)

```solidity
File: src/transformers/LeverageTransformer.sol

55: IERC20(token), IERC20(token0), params.amountIn0, params.amountOut0Min, params.swapData0
55: IERC20(token), IERC20(token0), params.amountIn0, params.amountOut0Min, params.swapData0
67: IERC20(token), IERC20(token1), params.amountIn1, params.amountOut1Min, params.swapData1
67: IERC20(token), IERC20(token1), params.amountIn1, params.amountOut1Min, params.swapData1
77: SafeERC20.safeIncreaseAllowance(IERC20(token0), address(nonfungiblePositionManager), amount0);
78: SafeERC20.safeIncreaseAllowance(IERC20(token1), address(nonfungiblePositionManager), amount1);
88: SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0 - added0);
91: SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1 - added1);
94: SafeERC20.safeTransfer(IERC20(token), params.recipient, amount);
149: IERC20(token0), IERC20(token), params.amountIn0, params.amountOut0Min, params.swapData0
149: IERC20(token0), IERC20(token), params.amountIn0, params.amountOut0Min, params.swapData0
158: IERC20(token1), IERC20(token), params.amountIn1, params.amountOut1Min, params.swapData1
158: IERC20(token1), IERC20(token), params.amountIn1, params.amountOut1Min, params.swapData1
165: SafeERC20.safeApprove(IERC20(token), msg.sender, amount);
170: SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0);
173: SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1);
```
[55](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L55) | [55](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L55) | [67](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L67) | [67](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L67) | [77](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L77) | [78](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L78) | [88](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L88) | [91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L91) | [94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L94) | [149](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L149) | [149](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L149) | [158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L158) | [158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L158) | [165](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L165) | [170](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L170) | [173](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L173)

```solidity
File: src/transformers/V3Utils.sol

131: IERC20(token0),
132: IERC20(token1),
155: IERC20(token1),
166: IERC20(token0),
167: IERC20(token1),
178: IERC20(token0),
189: IERC20(token0),
190: IERC20(token1),
202: IERC20(address(0)),
213: IERC20(token0),
214: IERC20(token1),
223: IERC20(token0),
224: IERC20(token1),
233: IERC20(token1),
250: IERC20(token0),
251: IERC20(token1),
260: IERC20(token0),
278: IERC20(token0),
279: IERC20(token1),
288: IERC20(address(0)),
309: IERC20(token0),
310: IERC20(instructions.targetToken),
317: _transferToken(instructions.recipient, IERC20(token0), amount0 - amountInDelta, instructions.unwrap);
326: IERC20(token1),
327: IERC20(instructions.targetToken),
334: _transferToken(instructions.recipient, IERC20(token1), amount1 - amountInDelta, instructions.unwrap);
344: instructions.recipient, IERC20(instructions.targetToken), targetAmount, instructions.unwrap
406: params.tokenIn, IERC20(address(0)), IERC20(address(0)), params.amountIn, 0, 0, pbtf, signature
406: params.tokenIn, IERC20(address(0)), IERC20(address(0)), params.amountIn, 0, 0, pbtf, signature
409: _prepareAddApproved(params.tokenIn, IERC20(address(0)), IERC20(address(0)), params.amountIn, 0, 0);
409: _prepareAddApproved(params.tokenIn, IERC20(address(0)), IERC20(address(0)), params.amountIn, 0, 0);
543: IERC20(token0),
544: IERC20(token1),
554: IERC20(token0),
555: IERC20(token1),
563: (liquidity, amount0, amount1) = _swapAndIncrease(params, IERC20(token0), IERC20(token1), msg.value != 0);
563: (liquidity, amount0, amount1) = _swapAndIncrease(params, IERC20(token0), IERC20(token1), msg.value != 0);
```
[131](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L131) | [132](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L132) | [155](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L155) | [166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L166) | [167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L167) | [178](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L178) | [189](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L189) | [190](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L190) | [202](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L202) | [213](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L213) | [214](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L214) | [223](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L223) | [224](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L224) | [233](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L233) | [250](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L250) | [251](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L251) | [260](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L260) | [278](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L278) | [279](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L279) | [288](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L288) | [309](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L309) | [310](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L310) | [317](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L317) | [326](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L326) | [327](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L327) | [334](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L334) | [344](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L344) | [406](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L406) | [406](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L406) | [409](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L409) | [409](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L409) | [543](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L543) | [544](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L544) | [554](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L554) | [555](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L555) | [563](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L563) | [563](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L563)

```solidity
File: src/utils/FlashloanLiquidator.sol

57: IERC20(asset),
58: RouterSwapParams(IERC20(token0), IERC20(asset), params.amount0In, 0, params.swapData0),
58: RouterSwapParams(IERC20(token0), IERC20(asset), params.amount0In, 0, params.swapData0),
59: RouterSwapParams(IERC20(token1), IERC20(asset), params.amount1In, 0, params.swapData1),
59: RouterSwapParams(IERC20(token1), IERC20(asset), params.amount1In, 0, params.swapData1),
```
[57](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L57) | [58](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L58) | [58](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L58) | [59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L59) | [59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L59)

```solidity
File: src/utils/Swapper.sol

167: SafeERC20.safeTransfer(IERC20(tokenIn), msg.sender, amountToPay);
```
[167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L167)
</details>

### [L-10] Lack of index element validation in external/public function

There's no validation to check whether the index element provided as an argument actually exists in the call. This omission could lead to unintended behavior if an element that does not exist in the call is passed to the function.

The function should validate that the provided index element exists in the call before proceeding.

Without this validation, the function could cause unintended behaviour as it will call an non-existing index element. This could lead to inconsistencies in data and potentially affect the integrity of the call structure.

<details>
<summary><i>31 issue instances in 6 files:</i></summary>

```solidity
File: src/V3Vault.sol

245: loans[tokenId]
259: tokenOwner[tokenId]
265: ownedTokens[owner]
272: ownedTokens[owner][index]
272: ownedTokens[owner]
446: loans[tokenId]
461: loans[tokenId]
471: loans[tokenId]
484: tokenOwner[tokenId]
487: transformApprovals[msg.sender][tokenId][target]
487: transformApprovals[msg.sender][tokenId]
502: transformerAllowList[transformer]
512: tokenOwner[tokenId]
515: transformApprovals[loanOwner][tokenId]
539: loans[tokenId]
558: loans[tokenId]
561: tokenOwner[tokenId]
595: tokenOwner[tokenId]
797: transformerAllowList[transformer]
863: tokenConfigs[token]
864: tokenConfigs[token]
```
[245](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L245) | [259](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L259) | [265](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L265) | [272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L272) | [272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L272) | [446](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L446) | [461](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L461) | [471](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L471) | [484](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L484) | [487](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L487) | [487](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L487) | [502](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L502) | [512](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L512) | [515](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L515) | [539](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L539) | [558](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L558) | [561](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L561) | [595](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L595) | [797](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L797) | [863](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L863) | [864](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L864)

```solidity
File: src/V3Oracle.sol

240: feedConfigs[token]
259: feedConfigs[token]
```
[240](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L240) | [259](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L259)

```solidity
File: src/automators/AutoExit.sol

230: positionConfigs[tokenId]
```
[230](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L230)

```solidity
File: src/automators/Automator.sol

71: operators[_operator]
81: vaults[_vault]
```
[71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L71) | [81](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L81)

```solidity
File: src/transformers/AutoCompound.sol

88: vaults[vault]
211: positionBalances[tokenId]
215: positionBalances[tokenId]
```
[88](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L88) | [211](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L211) | [215](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L215)

```solidity
File: src/transformers/AutoRange.sol

98: vaults[vault]
284: positionConfigs[tokenId]
```
[98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L98) | [284](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L284)
</details>

### [L-11] Consider checking that transfer to `address(this)` is disabled

Functions allowing users to specify the receiving address should check whether the referenced address is not `address(this)`.

This would prevent tokens to remain lock inside the contract due to an incorrect `transfer` or `mint`.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

904: _mint(receiver, shares)
```
[904](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L904)
</details>

### [L-12] Use `forceApprove/safeIncreaseAllowance` from SafeERC20 instead of `approve/safeApprove`

Certain tokens, exemplified by USDT, have quirks where adjusting an allowance directly from a non-zero value can be problematic. For such tokens, it's a common requirement to first reset the allowance to zero before setting a new value. Failing to do so can result in transaction reverts, disrupting protocol functionality.

To gracefully handle this, consider using the `forceApprove` method from OpenZeppelin's SafeERC20 library. This method ensures the contract's allowance towards a `spender` is set to the specified `value`. If the token doesn't return a value, the non-reverting calls are assumed successful, offering a seamless solution for tokens like USDT.

Since `safeIncreaseAllowance` calls `forceApprove` internally, it's also a viable alternative.

[Reference the SafeERC20 Library for more details](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/9e3f4d60c581010c4a3979480e07cc7752f124cc/contracts/token/ERC20/utils/SafeERC20.sol#L71C8-L83).

<details>
<summary><i>7 issue instances in 5 files:</i></summary>

```solidity
File: src/transformers/AutoCompound.sol

280: SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max);
284: SafeERC20.safeApprove(IERC20(token1), address(nonfungiblePositionManager), type(uint256).max);
```
[280](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L280) | [284](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L284)

```solidity
File: src/transformers/AutoRange.sol

213: SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), state.maxAddAmount0);
214: SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), state.maxAddAmount1);
```
[213](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L213) | [214](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L214)

```solidity
File: src/transformers/LeverageTransformer.sol

165: SafeERC20.safeApprove(IERC20(token), msg.sender, amount);
```
[165](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L165)

```solidity
File: src/utils/FlashloanLiquidator.sol

72: SafeERC20.safeApprove(data.asset, address(data.vault), data.liquidationCost);
```
[72](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L72)

```solidity
File: src/utils/Swapper.sol

87: SafeERC20.safeApprove(params.tokenIn, data.allowanceTarget, params.amountIn);
```
[87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L87)
</details>

### [L-13] Potential Gas Griefing Due to Non-Handling of Return Data in External Calls

Due to the EVM architecture, return data (bool success,) has to be stored.
However, when 'out' and 'outsize' values are given (0,0), this storage disappears.
This can lead to potential gas griefing/theft issues, especially when dealing with external contracts.
```solidity
assembly {
    success: = call(gas(), dest, amount, 0, 0)
}
require(success, "transfer failed");

```
Consider using a safe call pattern above to avoid these issues.
The following instances show the unsafe external call patterns found in the code.

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: src/automators/Automator.sol

130: (bool sent,) = to.call{value: balance}("");
221: (bool sent,) = to.call{value: amount}("");
```
[130](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L130) | [221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L221)

```solidity
File: src/transformers/V3Utils.sol

867: (bool sent,) = to.call{value: amount}("");
```
[867](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L867)
</details>

### [L-14] Low Level Calls to Custom Addresses

Contracts should avoid making low-level calls to custom addresses, especially if these calls are based on address parameters in the function. 
Such behavior can lead to unexpected execution of untrusted code. Instead, consider using Solidity's high-level function calls or contract interactions.

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: src/automators/Automator.sol

130: (bool sent,) = to.call{value: balance}("");
221: (bool sent,) = to.call{value: amount}("");
```
[130](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L130) | [221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L221)

```solidity
File: src/transformers/V3Utils.sol

867: (bool sent,) = to.call{value: amount}("");
```
[867](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L867)
</details>

### [L-15] Prevent Division by Zero

On several locations in the code, precautions are not being taken for not dividing by 0. This will revert the code.
These functions can be called with a 0 value in the input, this value is not checked for being bigger than 0,
that means in some scenarios this can potentially trigger a division by zero.

<details>
<summary><i>4 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit collatralValu - can be zero
1105: uint256 startLiquidationValue = debt * fullValue / collateralValue;
/// @audit startLiquidationValu - can be zero
1107: (Q96 - ((fullValue - maxPenaltyValue) * Q96 / (startLiquidationValue - maxPenaltyValue)));
/// @audit totalLnt - can be zero
1137: newLendExchangeRateX96 = (totalLent - missing) * newLendExchangeRateX96 / totalLent;
```
[1105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1105) | [1107](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1107) | [1137](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1137)

```solidity
File: src/InterestRateModel.sol

/// @audit cash - can be zero
50: return debt * Q96 / (cash + debt);
```
[50](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L50)
</details>

### [L-16] Solidity version 0.8.20 may not work on other chains due to `PUSH0`

Solidity 0.8.20, by default, targets the Shanghai version of the EVM, which includes the new `PUSH0` opcode.
However, this opcode may not yet be implemented on all Layer-2 chains.
For instance Arbitrum does not yet support `PUSH0`. See [Documentation](https://developer.arbitrum.io/solidity-support) for more information.
As such, deploying contracts compiled with Solidity 0.8.20 on these chains could lead to failures.

To avoid this, consider specifying an older EVM version as the target, or ensure that the Layer-2 chain used supports the Shanghai EVM.

<details>
<summary><i>11 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L2)

```solidity
File: src/V3Oracle.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L2)

```solidity
File: src/InterestRateModel.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L2)

```solidity
File: src/automators/AutoExit.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L2)

```solidity
File: src/automators/Automator.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L2)

```solidity
File: src/transformers/AutoCompound.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L2)

```solidity
File: src/transformers/AutoRange.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L2)

```solidity
File: src/transformers/LeverageTransformer.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L2)

```solidity
File: src/transformers/V3Utils.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L2)

```solidity
File: src/utils/FlashloanLiquidator.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L2)

```solidity
File: src/utils/Swapper.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L2)
</details>

### [L-17] Missing checks for `address(0x0)` when updating address state variables

State variables that are of type `address` should always be checked to ensure that they are not being assigned the null address (address(0x0)).
A null address often implies an error or omission in the code.
Without proper checks, such a scenario can lead to unexpected behavior and potential vulnerabilities in the smart contract.
Therefore, it is considered good practice to implement checks for `address(0x0)` prior to assigning new values to address state variables.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

871: emergencyAdmin = admin;
```
[871](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L871)

```solidity
File: src/V3Oracle.sol

266: emergencyAdmin = admin;
```
[266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L266)
</details>

### [L-18] Lack of Parameter Validation in Constructor/Initializer

The constructor/initializer doesn't validate input parameters before assigning them to state variables.
It is crucial to ensure that input parameters meet certain conditions to avoid unexpected states or behaviors in the contract.
Consider adding appropriate checks or constraints.

<details>
<summary><i>10 issue instances in 10 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit `_nonfungiblePositionManager` is not validated before use
/// @audit `_interestRateModel` is not validated before use
/// @audit `_oracle` is not validated before use
/// @audit `_permit2` is not validated before use
169: constructor(
        string memory name,
        string memory symbol,
        address _asset,
        INonfungiblePositionManager _nonfungiblePositionManager,
        IInterestRateModel _interestRateModel,
        IV3Oracle _oracle,
        IPermit2 _permit2
    ) ERC20(name, symbol) {
```
[169](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L169)

```solidity
File: src/V3Oracle.sol

/// @audit `_nonfungiblePositionManager` is not validated before use
74: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _referenceToken,
        address _chainlinkReferenceToken
    ) {
```
[74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L74)

```solidity
File: src/InterestRateModel.sol

/// @audit `baseRatePerYearX96` is not validated before use
/// @audit `multiplierPerYearX96` is not validated before use
/// @audit `jumpMultiplierPerYearX96` is not validated before use
/// @audit `_kinkX96` is not validated before use
33: constructor(
        uint256 baseRatePerYearX96,
        uint256 multiplierPerYearX96,
        uint256 jumpMultiplierPerYearX96,
        uint256 _kinkX96
    ) {
```
[33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L33)

```solidity
File: src/automators/AutoExit.sol

/// @audit `_TWAPSeconds` passed to inherited constructor is not validated
/// @audit `_maxTWAPTickDifference` passed to inherited constructor is not validated
33: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
```
[33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L33)

```solidity
File: src/automators/Automator.sol

/// @audit `_maxTWAPTickDifference` is not validated before use
41: constructor(
        INonfungiblePositionManager npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Swapper(npm, _zeroxRouter, _universalRouter) {
```
[41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L41)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit `_TWAPSeconds` passed to inherited constructor is not validated
/// @audit `_maxTWAPTickDifference` passed to inherited constructor is not validated
37: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, address(0), address(0)) {}
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L37)

```solidity
File: src/transformers/AutoRange.sol

/// @audit `_TWAPSeconds` passed to inherited constructor is not validated
/// @audit `_maxTWAPTickDifference` passed to inherited constructor is not validated
25: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
```
[25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L25)

```solidity
File: src/transformers/V3Utils.sol

/// @audit `_nonfungiblePositionManager` passed to inherited constructor is not validated
31: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _zeroxRouter,
        address _universalRouter,
        address _permit2
    ) Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter) {
```
[31](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L31)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit `_nonfungiblePositionManager` passed to inherited constructor is not validated
24: constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)
        Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter)
    {}
```
[24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L24)

```solidity
File: src/utils/Swapper.sol

/// @audit `_nonfungiblePositionManager` is not validated before use
37: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _zeroxRouter,
        address _universalRouter
    ) {
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L37)
</details>

### [L-19] Owner can renounce Ownership

The contract uses solady/OpenZeppelin's `Ownable(Upgradable).sol` and contains `onlyOwner` functions.
Consider implementing custom logic for `renounceOwnership()` to handle renouncing ownership.
`onlyOwner` functions:

<details>
<summary><i>4 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

16: import "@openzeppelin/contracts/access/Ownable.sol";
```
[16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L16)

```solidity
File: src/V3Oracle.sol

15: import "@openzeppelin/contracts/access/Ownable.sol";
```
[15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L15)

```solidity
File: src/InterestRateModel.sol

4: import "@openzeppelin/contracts/access/Ownable.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L4)

```solidity
File: src/automators/Automator.sol

4: import "@openzeppelin/contracts/access/Ownable.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L4)
</details>

### [L-20] State variables are not limited to a reasonable range

It's advisable to introduce minimum and maximum value constraints for state variables.
By not setting bounds, there's a potential for users to face adverse effects, including potential griefing attacks.
Ensuring that state variables operate within a known range can enhance safety and predictability.

<details>
<summary><i>11 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

817: minLoanSize = _minLoanSize;
819: globalLendLimit = _globalLendLimit;
820: globalDebtLimit = _globalDebtLimit;
821: dailyLendIncreaseLimitMin = _dailyLendIncreaseLimitMin;
822: dailyDebtIncreaseLimitMin = _dailyDebtIncreaseLimitMin;
838: reserveFactorX32 = _reserveFactorX32;
886: shares = amount;
889: assets = amount;
927: shares = amount;
965: shares = amount;
```
[817](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L817) | [819](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L819) | [820](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L820) | [821](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L821) | [822](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L822) | [838](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L838) | [886](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L886) | [889](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L889) | [927](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L927) | [965](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L965)

```solidity
File: src/InterestRateModel.sol

98: kinkX96 = _kinkX96;
```
[98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L98)
</details>

### [L-21] Missing Contract-Existence Checks Before Low-Level Calls

When making low-level calls, it's crucial to ensure the existence of the contract at the specified address. 
If the contract doesn't exist at the given address, low-level calls will still return success, potentially causing errors in the code execution.
Therefore, alongside zero-address checks, adding an additional check to verify that <address>.code.length > 0 before making low-level calls would be recommended.

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: src/automators/Automator.sol

130: (bool sent,) = to.call{value: balance}("");
221: (bool sent,) = to.call{value: amount}("");
```
[130](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L130) | [221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L221)

```solidity
File: src/transformers/V3Utils.sol

867: (bool sent,) = to.call{value: amount}("");
```
[867](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L867)
</details>

### [L-22] Events may be emitted out of order due to reentrancy

It's essential to ensure that events follow the best practice of check-effects-interaction and are emitted before any external calls to prevent out-of-order events due to reentrancy.
Emitting events post external interactions may cause them to be out of order due to reentrancy, which can be misleading or erroneous for event listeners.
[Refer to the Solidity Documentation for best practices.](https://solidity.readthedocs.io/en/latest/security-considerations.html#reentrancy)

<details>
<summary><i>13 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit `safeTransfer()` before `Borrow` event emit
600: emit Borrow(tokenId, owner, assets, shares);
/// @audit `safeTransferFrom()` before `Liquidate` event emit
745: emit Liquidate(
            params.tokenId,
            msg.sender,
            owner,
            state.fullValue,
            state.liquidatorCost,
            amount0,
            amount1,
            state.reserveCost,
            state.missing
        );
/// @audit `safeTransfer()` before `WithdrawReserves` event emit
781: emit WithdrawReserves(amount, receiver);
/// @audit `safeTransferFrom()` before `Deposit` event emit
915: emit Deposit(msg.sender, receiver, assets, shares);
/// @audit `safeTransfer()` before `Withdraw` event emit
950: emit Withdraw(msg.sender, receiver, owner, assets, shares);
/// @audit `safeTransferFrom()` before `Repay` event emit
1012: emit Repay(tokenId, msg.sender, owner, assets, shares);
/// @audit `safeTransferFrom()` before `Remove` event emit
1084: emit Remove(tokenId, owner);
```
[600](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L600) | [745](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L745) | [781](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L781) | [915](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L915) | [950](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L950) | [1012](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1012) | [1084](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1084)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit `safeTransfer()` before `BalanceWithdrawn` event emit
273: emit BalanceWithdrawn(tokenId, token, to, amount);
```
[273](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L273)

```solidity
File: src/transformers/AutoRange.sol

/// @audit `safeTransferFrom()` before `PositionConfigured` event emit
252: emit PositionConfigured(
                state.newTokenId,
                config.lowerTickLimit,
                config.upperTickLimit,
                config.lowerTickDelta,
                config.upperTickDelta,
                config.token0SlippageX64,
                config.token1SlippageX64,
                config.onlyFees,
                config.maxRewardX64
            );
/// @audit `safeTransferFrom()` before `PositionConfigured` event emit
266: emit PositionConfigured(params.tokenId, 0, 0, 0, 0, 0, 0, false, 0);
/// @audit `safeTransferFrom()` before `RangeChanged` event emit
267: emit RangeChanged(params.tokenId, state.newTokenId);
```
[252](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L252) | [266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L266) | [267](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L267)

```solidity
File: src/transformers/V3Utils.sol

/// @audit `safeTransferFrom()` before `SwapAndMint` event emit
728: emit SwapAndMint(tokenId, liquidity, added0, added1);
```
[728](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L728)

```solidity
File: src/utils/Swapper.sol

/// @audit `call()` before `Swap` event emit
116: emit Swap(address(params.tokenIn), address(params.tokenOut), amountInDelta, amountOutDelta);
```
[116](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L116)
</details>

### [L-23] External calls in an un-bounded `for-`loop may result in a DOS

Executing external calls within unbounded for-loops poses a significant risk of transaction revert.
A failure in one of the iterations can lead to the entire transaction being reverted.
Furthermore, excessive iterations may consume an exorbitant amount of gas, potentially reaching the block gas limit, causing the transaction to fail.
This can result in unintended outcomes, especially if a majority of the iterations would have otherwise succeeded without the problematic call.
To enhance contract reliability and manage gas consumption efficiently, consider limiting the number of iterations in such loops, and implement robust error-handling mechanisms for potential failures in the looped external calls.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/automators/Automator.sol

/// @audit 1 external calls in unbounded for-loop -> 111: for (; i < count; ++i) {
112: uint256 balance = IERC20(tokens[i]).balanceOf(address(this));
```
[112](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L112)
</details>

### [L-24] For loops in public or external functions should be avoided due to high gas costs and possible DOS

Using loops within `public` or `external` functions can pose risks and inefficiencies.
Unpredictable gas consumption due to loop iterations can hinder a function's usability and cost-effectiveness. 
Furthermore, if the loop's logic can be externally influenced or altered, it might be exploited to intentionally drain gas, making the function impractical or uneconomical to call.
To ensure consistent performance and avoid potential vulnerabilities, it's advisable to avoid or limit loops in public functions, especially if their logic can change.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/automators/Automator.sol

111: for (; i < count; ++i) {
```
[111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L111)

```solidity
File: src/transformers/AutoCompound.sol

233: for (; i < count; ++i) {
```
[233](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L233)
</details>

### [L-25] Critical functions should be a two step procedure

Critical functions in Solidity contracts should follow a two-step procedure to enhance security, minimize human error, and ensure proper access control. By dividing sensitive operations into distinct phases, such as initiation and confirmation, developers can introduce a safeguard against unintended actions or unauthorized access.

<details>
<summary><i>16 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

788: function setTransformer(address transformer, bool active) external onlyOwner {
807: function setLimits(
        uint256 _minLoanSize,
        uint256 _globalLendLimit,
        uint256 _globalDebtLimit,
        uint256 _dailyLendIncreaseLimitMin,
        uint256 _dailyDebtIncreaseLimitMin
    ) external {
837: function setReserveFactor(uint32 _reserveFactorX32) external onlyOwner {
844: function setReserveProtectionFactor(uint32 _reserveProtectionFactorX32) external onlyOwner {
856: function setTokenConfig(address token, uint32 collateralFactorX32, uint32 collateralValueLimitFactorX32)
        external
        onlyOwner
    {
870: function setEmergencyAdmin(address admin) external onlyOwner {
```
[788](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L788) | [807](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L807) | [837](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L837) | [844](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L844) | [856](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L856) | [870](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L870)

```solidity
File: src/V3Oracle.sol

185: function setMaxPoolPriceDifference(uint16 _maxPoolPriceDifference) external onlyOwner {
201: function setTokenConfig(
        address token,
        AggregatorV3Interface feed,
        uint32 maxFeedAge,
        IUniswapV3Pool pool,
        uint32 twapSeconds,
        Mode mode,
        uint16 maxDifference
    ) external onlyOwner {
249: function setOracleMode(address token, Mode mode) external {
265: function setEmergencyAdmin(address admin) external onlyOwner {
```
[185](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L185) | [201](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L201) | [249](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L249) | [265](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L265)

```solidity
File: src/InterestRateModel.sol

82: function setValues(
        uint256 baseRatePerYearX96,
        uint256 multiplierPerYearX96,
        uint256 jumpMultiplierPerYearX96,
        uint256 _kinkX96
    ) public onlyOwner {
```
[82](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L82)

```solidity
File: src/automators/Automator.sol

59: function setWithdrawer(address _withdrawer) public onlyOwner {
69: function setOperator(address _operator, bool _active) public onlyOwner {
79: function setVault(address _vault, bool _active) public onlyOwner {
87: function setTWAPConfig(uint16 _maxTWAPTickDifference, uint32 _TWAPSeconds) public onlyOwner {
```
[59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L59) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L69) | [79](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L79) | [87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L87)

```solidity
File: src/transformers/AutoCompound.sol

243: function setReward(uint64 _totalRewardX64) external onlyOwner {
```
[243](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L243)
</details>

### [L-26] Deprecated Function `safeApprove` Usage

The function `safeApprove` has been deprecated and is not recommended for use. The preferred methods are `increaseAllowance` and `decreaseAllowance`. 

The `safeApprove` method should only be used for setting an initial value. Instead of `safeApprove`, using the `increaseAllowance` and `decreaseAllowance` functions is recommended, as they offer a more secure and efficient way to manage allowances.

<details>
<summary><i>15 issue instances in 6 files:</i></summary>

```solidity
File: src/transformers/AutoCompound.sol

280: SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max);
284: SafeERC20.safeApprove(IERC20(token1), address(nonfungiblePositionManager), type(uint256).max);
```
[280](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L280) | [284](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L284)

```solidity
File: src/transformers/AutoRange.sol

213: SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), state.maxAddAmount0);
214: SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), state.maxAddAmount1);
220: SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), 0);
221: SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), 0);
```
[213](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L213) | [214](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L214) | [220](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L220) | [221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L221)

```solidity
File: src/transformers/LeverageTransformer.sol

165: SafeERC20.safeApprove(IERC20(token), msg.sender, amount);
```
[165](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L165)

```solidity
File: src/transformers/V3Utils.sol

831: SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), 0);
832: SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), total0);
835: SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), 0);
836: SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), total1);
```
[831](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L831) | [832](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L832) | [835](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L835) | [836](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L836)

```solidity
File: src/utils/FlashloanLiquidator.sol

72: SafeERC20.safeApprove(data.asset, address(data.vault), data.liquidationCost);
78: SafeERC20.safeApprove(data.asset, address(data.vault), 0);
```
[72](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L72) | [78](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L78)

```solidity
File: src/utils/Swapper.sol

87: SafeERC20.safeApprove(params.tokenIn, data.allowanceTarget, params.amountIn);
94: SafeERC20.safeApprove(params.tokenIn, data.allowanceTarget, 0);
```
[87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L87) | [94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L94)
</details>

### [L-27] Loss of precision

Division by large numbers may result in the result being zero, due to Solidity not supporting fractions. Consider requiring a minimum amount for the numerator to ensure that it is always larger than the denominator.

<details>
<summary><i>30 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

1054: fees0 = uint128(liquidationValue * fees0 / feeValue);
1055: fees1 = uint128(liquidationValue * fees1 / feeValue);
1060: liquidity = uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue));
1105: uint256 startLiquidationValue = debt * fullValue / collateralValue;
1137: newLendExchangeRateX96 = (totalLent - missing) * newLendExchangeRateX96 / totalLent;
```
[1054](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1054) | [1055](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1055) | [1060](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1060) | [1105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1105) | [1137](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1137)

```solidity
File: src/V3Oracle.sol

120: value = (price0X96 * (amount0 + fees0) / Q96 + price1X96 * (amount1 + fees1) / Q96) * Q96 / priceTokenX96;
120: value = (price0X96 * (amount0 + fees0) / Q96 + price1X96 * (amount1 + fees1) / Q96) * Q96 / priceTokenX96;
120: value = (price0X96 * (amount0 + fees0) / Q96 + price1X96 * (amount1 + fees1) / Q96) * Q96 / priceTokenX96;
121: feeValue = (price0X96 * fees0 / Q96 + price1X96 * fees1 / Q96) * Q96 / priceTokenX96;
121: feeValue = (price0X96 * fees0 / Q96 + price1X96 * fees1 / Q96) * Q96 / priceTokenX96;
121: feeValue = (price0X96 * fees0 / Q96 + price1X96 * fees1 / Q96) * Q96 / priceTokenX96;
122: price0X96 = price0X96 * Q96 / priceTokenX96;
123: price1X96 = price1X96 * Q96 / priceTokenX96;
129: uint256 derivedPoolPriceX96 = price0X96 * Q96 / price1X96;
144: ? (priceX96 - verifyPriceX96) * 10000 / priceX96
145: : (verifyPriceX96 - priceX96) * 10000 / verifyPriceX96;
304: chainlinkPriceX96 = (10 ** referenceTokenDecimals) * chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96
304: chainlinkPriceX96 = (10 ** referenceTokenDecimals) * chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96
                / (10 ** feedConfig.tokenDecimals);
342: return uint256(answer) * Q96 / (10 ** feedConfig.feedDecimals);
353: poolTWAPPriceX96 = Q96 * Q96 / priceX96;
369: int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)));
```
[120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L120) | [120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L120) | [120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L120) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L121) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L121) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L121) | [122](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L122) | [123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L123) | [129](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L129) | [144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L144) | [145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L145) | [304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L304) | [304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L304) | [342](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L342) | [353](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L353) | [369](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L369)

```solidity
File: src/InterestRateModel.sol

50: return debt * Q96 / (cash + debt);
67: borrowRateX96 = (utilizationRateX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
69: uint256 normalRateX96 = (kinkX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
71: borrowRateX96 = (excessUtilX96 * jumpMultiplierPerSecondX96 / Q96) + normalRateX96;
74: supplyRateX96 = utilizationRateX96 * borrowRateX96 / Q96;
95: baseRatePerSecondX96 = baseRatePerYearX96 / YEAR_SECS;
96: multiplierPerSecondX96 = multiplierPerYearX96 / YEAR_SECS;
97: jumpMultiplierPerSecondX96 = jumpMultiplierPerYearX96 / YEAR_SECS;
```
[50](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L50) | [67](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L67) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L69) | [71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L71) | [74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L74) | [95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L95) | [96](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L96) | [97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L97)

```solidity
File: src/automators/Automator.sol

187: return (int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapPeriod))), true);
```
[187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L187)
</details>

### [L-28] Unsafe Conversion from various type `int/uint` values

Solidity follows two's complement rules for its integers. It's always unsafe to cast from one type to another.
Therefore, casting an unsigned integer to a signed one may result in an unexpected change of the sign or magnitude of the value.
For instance, `int8(type(uint8).max)` doesn't equal `type(int8).max` but is -1. [More information about Two's complement](https://en.wikipedia.org/wiki/Two%27s_complement)

Additionally, if the value from the source type exceeds the maximum value of the target type, it gets truncated by the modulo operation, leading to unpredictable outcomes.
This might introduce unintended behaviors in the contract logic.

<details>
<summary><i>4 issue instances in 3 files:</i></summary>

```solidity
File: src/V3Oracle.sol

/// @audit cast from `uint56` to `int56`
369: int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)));
```
[369](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L369)

```solidity
File: src/automators/Automator.sol

/// @audit cast from `uint16` to `int16`
173: return twapTick - currentTick >= -int16(maxDifference) && twapTick - currentTick <= int16(maxDifference);
/// @audit cast from `uint56` to `int56`
187: return (int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapPeriod))), true);
```
[173](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L173) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L187)

```solidity
File: src/utils/Swapper.sol

/// @audit cast from `uint256` to `int256`
137: int256(params.amountIn),
```
[137](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L137)
</details>

### [L-29] Mapping arrays can grow in size without a way to shrink them

In Solidity, it's vital to manage the size of mapping arrays, particularly when they are subject to dynamic updates.
A common issue arises when contracts allow items to be added to an array but lack a corresponding method to remove them.
Unlike some programming languages where arrays automatically resize, Solidity requires explicit resizing. Without a 'pop' function or similar mechanism, arrays can become bloated, leading to inefficiencies.
This bloating can not only increase gas costs, particularly during iterations, but also pose a risk of hitting the block gas limit.
Furthermore, if array elements are flagged for deletion but not actually removed, it can result in the retention of outdated or irrelevant data, potentially causing logical errors in contract execution. To maintain a streamlined and efficient contract, it's advisable to implement methods for removing items from mapping arrays.
Such practices help in keeping the contract's state manageable and guard against issues related to gas limits or data accuracy.
Additionally, it's crucial to handle underflows carefully when implementing removal logic to ensure the contract's robustness.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

1299: ownedTokens[to].push(tokenId);
```
[1299](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1299)
</details>

### [L-30] Unbounded Gas Consumption on External Calls

External calls in your code don't specify a gas limit, which can lead to scenarios where the recipient consumes all transaction's gas causing it to revert. 
Consider using `addr.call{gas: <amount>}("")` to set a gas limit and prevent potential reversion due to gas consumption.

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: src/automators/Automator.sol

130: (bool sent,) = to.call{value: balance}("");
221: (bool sent,) = to.call{value: amount}("");
```
[130](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L130) | [221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L221)

```solidity
File: src/transformers/V3Utils.sol

867: (bool sent,) = to.call{value: amount}("");
```
[867](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L867)
</details>

### [L-31] Unsafe downcast from larger to smaller integer types

Casting from larger types to smaller ones can potentially lead to overflows and thus unexpected behavior.
For instance, when a `uint256` value gets cast to `uint8`, it could end up as an entirely different, much smaller number due to the reduction in bits. 

OpenZeppelin's `SafeCast` library provides functions for safe type conversions, throwing an error whenever an overflow would occur.
It is generally recommended to use `SafeCast` or similar protective measures when performing type conversions to ensure the accuracy of your computations and the security of your contracts.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Oracle.sol

/// @audit casted from `int56` to `int24`
369: int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)));
```
[369](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L369)

```solidity
File: src/automators/Automator.sol

/// @audit casted from `int56` to `int24`
187: return (int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapPeriod))), true);
```
[187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L187)
</details>

### [L-32] Consider implementing two-step procedure for updating protocol addresses

Direct state address changes in a function can be risky, as they don't allow for a verification step before the change is made.
It's safer to implement a two-step process where the new address is first proposed, then later confirmed, allowing for more control and the chance to catch errors or malicious activity.

<details>
<summary><i>3 issue instances in 3 files:</i></summary>

```solidity
File: src/V3Vault.sol

871: emergencyAdmin = admin;
```
[871](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L871)

```solidity
File: src/V3Oracle.sol

/// @audit `emergencyAdmin` is changed
266: emergencyAdmin = admin;
```
[266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L266)

```solidity
File: src/automators/Automator.sol

/// @audit `withdrawer` is changed
61: withdrawer = _withdrawer;
```
[61](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L61)
</details>

### [L-33] Possible Revert ERC20 Transfers with Zero Value

Some ERC20 tokens (for example, LEND) revert on attempts to transfer a zero value.
This can become a problem in any contract that doesn't handle these cases correctly.

If a token transfer fails, any additional logic in a function might also be affected or even fail entirely.
Therefore, contracts interacting with ERC20 tokens should account for the possibility that a zero-value transfer might revert.

<details>
<summary><i>10 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit `address(this), state.liquidatorCost` has not been checked for zero value before transfer
728: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);
/// @audit `address(this), assets` has not been checked for zero value before transfer
901: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
/// @audit `address(this), assets` has not been checked for zero value before transfer
986: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
```
[728](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L728) | [901](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L901) | [986](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L986)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit `amount0 - added0` has not been checked for zero value before transfer
88: SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0 - added0);
/// @audit `amount1 - added1` has not been checked for zero value before transfer
91: SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1 - added1);
```
[88](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L88) | [91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L91)

```solidity
File: src/transformers/V3Utils.sol

/// @audit `address(this), needed0` has not been checked for zero value before transfer
578: SafeERC20.safeTransferFrom(token0, msg.sender, address(this), needed0);
/// @audit `address(this), needed1` has not been checked for zero value before transfer
581: SafeERC20.safeTransferFrom(token1, msg.sender, address(this), needed1);
/// @audit `address(this), neededOther` has not been checked for zero value before transfer
584: SafeERC20.safeTransferFrom(otherToken, msg.sender, address(this), neededOther);
```
[578](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L578) | [581](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L581) | [584](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L584)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit `data.liquidationCost + (fee0 + fee1)` has not been checked for zero value before transfer
85: SafeERC20.safeTransfer(data.asset, msg.sender, data.liquidationCost + (fee0 + fee1));
```
[85](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L85)

```solidity
File: src/utils/Swapper.sol

/// @audit `amountToPay` has not been checked for zero value before transfer
167: SafeERC20.safeTransfer(IERC20(tokenIn), msg.sender, amountToPay);
```
[167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L167)
</details>

### [L-34] Function Parameters in Public Accessible Functions Need `address(0)` Check

Parameters of type `address` in your functions should be checked to ensure that they are not assigned the null address (`address(0x0)`). 
Failure to validate these parameters can lead to transaction reverts, wasted gas, the need for transaction resubmission, and may even require redeployment of contracts within the protocol in certain situations.
Implement checks for `address(0x0)` to avoid these potential issues.

<details>
<summary><i>36 issue instances in 6 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit `account` parameter without address(0) check
219: function lendInfo(address account) external view override returns (uint256 amount) {
/// @audit `owner` parameter without address(0) check
264: function loanCount(address owner) external view override returns (uint256) {
/// @audit `owner` parameter without address(0) check
271: function loanAtIndex(address owner, uint256 index) external view override returns (uint256) {
/// @audit `address` parameter without address(0) check
301: function maxDeposit(address) external view override returns (uint256) {
/// @audit `address` parameter without address(0) check
312: function maxMint(address) external view override returns (uint256) {
/// @audit `owner` parameter without address(0) check
323: function maxWithdraw(address owner) external view override returns (uint256) {
/// @audit `owner` parameter without address(0) check
329: function maxRedeem(address owner) external view override returns (uint256) {
/// @audit `receiver` parameter without address(0) check
360: function deposit(uint256 assets, address receiver) external override returns (uint256) {
/// @audit `receiver` parameter without address(0) check
366: function mint(uint256 shares, address receiver) external override returns (uint256) {
/// @audit `receiver` parameter without address(0) check
/// @audit `owner` parameter without address(0) check
372: function withdraw(uint256 assets, address receiver, address owner) external override returns (uint256) {
/// @audit `receiver` parameter without address(0) check
/// @audit `owner` parameter without address(0) check
378: function redeem(uint256 shares, address receiver, address owner) external override returns (uint256) {
/// @audit `receiver` parameter without address(0) check
384: function deposit(uint256 assets, address receiver, bytes calldata permitData) external override returns (uint256) {
/// @audit `receiver` parameter without address(0) check
390: function mint(uint256 shares, address receiver, bytes calldata permitData) external override returns (uint256) {
/// @audit `recipient` parameter without address(0) check
400: function create(uint256 tokenId, address recipient) external override {
/// @audit `owner` parameter without address(0) check
/// @audit `recipient` parameter without address(0) check
410: function createWithPermit(
        uint256 tokenId,
        address owner,
        address recipient,
        uint256 deadline,
        uint8 v,
        bytes32 r,
        bytes32 s
    ) external override {
/// @audit `address` parameter without address(0) check
/// @audit `from` parameter without address(0) check
429: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
    {
/// @audit `target` parameter without address(0) check
483: function approveTransform(uint256 tokenId, address target, bool isActive) external override {
/// @audit `transformer` parameter without address(0) check
497: function transform(uint256 tokenId, address transformer, bytes calldata data)
        external
        override
        returns (uint256 newTokenId)
    {
/// @audit `receiver` parameter without address(0) check
765: function withdrawReserves(uint256 amount, address receiver) external onlyOwner {
/// @audit `token` parameter without address(0) check
856: function setTokenConfig(address token, uint32 collateralFactorX32, uint32 collateralValueLimitFactorX32)
        external
        onlyOwner
    {
/// @audit `admin` parameter without address(0) check
870: function setEmergencyAdmin(address admin) external onlyOwner {
```
[219](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L219) | [264](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L264) | [271](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L271) | [301](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L301) | [312](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L312) | [323](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L323) | [329](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L329) | [360](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L360) | [366](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L366) | [372](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L372) | [378](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L378) | [384](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L384) | [390](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L390) | [400](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L400) | [410](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L410) | [429](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L429) | [483](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L483) | [497](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L497) | [765](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L765) | [856](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L856) | [870](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L870)

```solidity
File: src/V3Oracle.sol

/// @audit `token` parameter without address(0) check
95: function getValue(uint256 tokenId, address token)
        external
        view
        override
        returns (uint256 value, uint256 feeValue, uint256 price0X96, uint256 price1X96)
    {
/// @audit `token` parameter without address(0) check
201: function setTokenConfig(
        address token,
        AggregatorV3Interface feed,
        uint32 maxFeedAge,
        IUniswapV3Pool pool,
        uint32 twapSeconds,
        Mode mode,
        uint16 maxDifference
    ) external onlyOwner {
/// @audit `token` parameter without address(0) check
249: function setOracleMode(address token, Mode mode) external {
/// @audit `admin` parameter without address(0) check
265: function setEmergencyAdmin(address admin) external onlyOwner {
```
[95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L95) | [201](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L201) | [249](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L249) | [265](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L265)

```solidity
File: src/automators/Automator.sol

/// @audit `_withdrawer` parameter without address(0) check
59: function setWithdrawer(address _withdrawer) public onlyOwner {
/// @audit `_operator` parameter without address(0) check
69: function setOperator(address _operator, bool _active) public onlyOwner {
/// @audit `_vault` parameter without address(0) check
79: function setVault(address _vault, bool _active) public onlyOwner {
/// @audit `tokens` parameter without address(0) check
/// @audit `to` parameter without address(0) check
104: function withdrawBalances(address[] calldata tokens, address to) external virtual {
/// @audit `to` parameter without address(0) check
123: function withdrawETH(address to) external {
```
[59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L59) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L69) | [79](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L79) | [104](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L104) | [123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L123)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit `vault` parameter without address(0) check
87: function executeWithVault(ExecuteParams calldata params, address vault) external {
/// @audit `to` parameter without address(0) check
200: function withdrawLeftoverBalances(uint256 tokenId, address to) external nonReentrant {
/// @audit `tokens` parameter without address(0) check
/// @audit `to` parameter without address(0) check
227: function withdrawBalances(address[] calldata tokens, address to) external override nonReentrant {
```
[87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L87) | [200](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L200) | [227](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L227)

```solidity
File: src/transformers/AutoRange.sol

/// @audit `vault` parameter without address(0) check
97: function executeWithVault(ExecuteParams calldata params, address vault) external {
/// @audit `vault` parameter without address(0) check
276: function configToken(uint256 tokenId, address vault, PositionConfig calldata config) external {
```
[97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L97) | [276](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L276)

```solidity
File: src/transformers/V3Utils.sol

/// @audit `address` parameter without address(0) check
/// @audit `from` parameter without address(0) check
356: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
    {
```
[356](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L356)
</details>

### [L-35] Missing `address(0)` Check in Constructor

The constructor does not include a check for `address(0)` when set state variables that hold addresses.
Initializing a state variable with `address(0)` can lead to unintended behavior and vulnerabilities in the contract, such as sending funds to an inaccessible address. 
It is recommended to include a validation step to ensure that address parameters are not set to `address(0)`.

<details>
<summary><i>5 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit `_asset` has lack of `address(0)` check before use
/// @audit `_nonfungiblePositionManager` has lack of `address(0)` check before use
/// @audit `_interestRateModel` has lack of `address(0)` check before use
/// @audit `_oracle` has lack of `address(0)` check before use
/// @audit `_permit2` has lack of `address(0)` check before use
168: constructor(
        string memory name,
        string memory symbol,
        address _asset,
        INonfungiblePositionManager _nonfungiblePositionManager,
        IInterestRateModel _interestRateModel,
        IV3Oracle _oracle,
        IPermit2 _permit2
    ) ERC20(name, symbol) {
```
[168](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L168)

```solidity
File: src/V3Oracle.sol

/// @audit `_nonfungiblePositionManager` has lack of `address(0)` check before use
/// @audit `_referenceToken` has lack of `address(0)` check before use
/// @audit `_chainlinkReferenceToken` has lack of `address(0)` check before use
74: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _referenceToken,
        address _chainlinkReferenceToken
    ) {
```
[74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L74)

```solidity
File: src/automators/Automator.sol

/// @audit `_operator` has lack of `address(0)` check before use
/// @audit `_withdrawer` has lack of `address(0)` check before use
40: constructor(
        INonfungiblePositionManager npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Swapper(npm, _zeroxRouter, _universalRouter) {
```
[40](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L40)

```solidity
File: src/transformers/V3Utils.sol

/// @audit `_permit2` has lack of `address(0)` check before use
31: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _zeroxRouter,
        address _universalRouter,
        address _permit2
    ) Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter) {
```
[31](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L31)

```solidity
File: src/utils/Swapper.sol

/// @audit `_nonfungiblePositionManager` has lack of `address(0)` check before use
/// @audit `_zeroxRouter` has lack of `address(0)` check before use
/// @audit `_universalRouter` has lack of `address(0)` check before use
37: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _zeroxRouter,
        address _universalRouter
    ) {
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L37)
</details>

### [L-36] Functions calling tokens with transfer hooks are missing reentrancy guards

Functions that call contracts or addresses with transfer hooks should use reentrancy guards for protection. 
Even if these functions adhere to the check-effects-interaction best practice, absence of reentrancy guards can expose the protocol users to read-only reentrancies.
Without the guards, the only protective measure is to block-list the entire protocol, which isn't an optimal solution.

<details>
<summary><i>29 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit function `create()` 
401: nonfungiblePositionManager.safeTransferFrom(msg.sender, address(this), tokenId, abi.encode(recipient));
/// @audit function `createWithPermit()` 
424: nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));
/// @audit function `transform()` 
522: (bool success,) = transformer.call(data);
/// @audit function `borrow()` 
599: SafeERC20.safeTransfer(IERC20(asset), isTransformMode ? msg.sender : owner, assets);
/// @audit function `liquidate()` 
728: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);
/// @audit function `withdrawReserves()` 
779: SafeERC20.safeTransfer(IERC20(asset), receiver, amount);
/// @audit function `_deposit()` 
901: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
/// @audit function `_withdraw()` 
946: SafeERC20.safeTransfer(IERC20(asset), receiver, assets);
/// @audit function `_repay()` 
986: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
/// @audit function `_cleanupLoan()` 
1083: nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId);
```
[401](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L401) | [424](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L424) | [522](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L522) | [599](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L599) | [728](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L728) | [779](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L779) | [901](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L901) | [946](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L946) | [986](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L986) | [1083](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1083)

```solidity
File: src/automators/Automator.sol

/// @audit function `_transferToken()` 
226: SafeERC20.safeTransfer(token, to, amount);
```
[226](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L226)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit function `_withdrawBalanceInternal()` 
272: SafeERC20.safeTransfer(IERC20(token), to, amount);
```
[272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L272)

```solidity
File: src/transformers/AutoRange.sol

/// @audit function `execute()` 
232: nonfungiblePositionManager.safeTransferFrom(address(this), state.owner, state.newTokenId);
```
[232](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L232)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit function `leverageUp()` 
88: SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0 - added0);
/// @audit function `leverageUp()` 
91: SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1 - added1);
/// @audit function `leverageUp()` 
94: SafeERC20.safeTransfer(IERC20(token), params.recipient, amount);
/// @audit function `leverageDown()` 
170: SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0);
/// @audit function `leverageDown()` 
173: SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1);
```
[88](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L88) | [91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L91) | [94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L94) | [170](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L170) | [173](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L173)

```solidity
File: src/transformers/V3Utils.sol

/// @audit function `_prepareAddApproved()` 
578: SafeERC20.safeTransferFrom(token0, msg.sender, address(this), needed0);
/// @audit function `_prepareAddApproved()` 
581: SafeERC20.safeTransferFrom(token1, msg.sender, address(this), needed1);
/// @audit function `_prepareAddApproved()` 
584: SafeERC20.safeTransferFrom(otherToken, msg.sender, address(this), neededOther);
/// @audit function `_transferToken()` 
872: SafeERC20.safeTransfer(token, to, amount);
```
[578](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L578) | [581](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L581) | [584](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L584) | [872](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L872)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit function `uniswapV3FlashCallback()` 
85: SafeERC20.safeTransfer(data.asset, msg.sender, data.liquidationCost + (fee0 + fee1));
/// @audit function `uniswapV3FlashCallback()` 
91: SafeERC20.safeTransfer(data.swap0.tokenIn, data.liquidator, balance);
/// @audit function `uniswapV3FlashCallback()` 
97: SafeERC20.safeTransfer(data.swap1.tokenIn, data.liquidator, balance);
/// @audit function `uniswapV3FlashCallback()` 
106: SafeERC20.safeTransfer(data.asset, data.liquidator, balance);
```
[85](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L85) | [91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L91) | [97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L97) | [106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L106)

```solidity
File: src/utils/Swapper.sol

/// @audit function `_routerSwap()` 
89: (bool success,) = zeroxRouter.call(data.data);
/// @audit function `_routerSwap()` 
98: SafeERC20.safeTransfer(params.tokenIn, universalRouter, params.amountIn);
/// @audit function `uniswapV3SwapCallback()` 
167: SafeERC20.safeTransfer(IERC20(tokenIn), msg.sender, amountToPay);
```
[89](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L89) | [98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L98) | [167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L167)
</details>

### [L-37] Consider Using `Ownable2Step` rather than `Ownable`

To enhance the security and prevent inadvertent ownership transfers, it's advisable to use `Ownable2Step` or `Ownable2StepUpgradeable`.
Contracts necessitate an active confirmation from the recipient before the ownership transfer is finalized.
This mechanism serves as a safeguard against scenarios where, for instance, a typo in the address could lead to unintentional ownership changes.

By implementing a two-step confirmation process, contracts can better ensure the accurate and intentional transfer of ownership.

<details>
<summary><i>6 issue instances in 3 files:</i></summary>

```solidity
File: src/V3Vault.sol

16: import "@openzeppelin/contracts/access/Ownable.sol";
30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {
```
[16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L16) | [30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30)

```solidity
File: src/V3Oracle.sol

15: import "@openzeppelin/contracts/access/Ownable.sol";
24: contract V3Oracle is IV3Oracle, Ownable, IErrors {
```
[15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L15) | [24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L24)

```solidity
File: src/InterestRateModel.sol

4: import "@openzeppelin/contracts/access/Ownable.sol";
11: contract InterestRateModel is Ownable, IInterestRateModel, IErrors {
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L4) | [11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L11)
</details>


## NonCritical Findings Details

### [N-01] Ensure `payable` Functions Properly Handle Ether Transfers

A `payable` function that does not make use of `msg.value` can result in the loss of Ether sent with the function call. 
Make sure that if a function is marked as `payable`, it appropriately handles the transfer of Ether.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/transformers/V3Utils.sol

397: function swap(SwapParams calldata params) external payable returns (uint256 amountOut) {
```
[397](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L397)
</details>

### [N-02] Non-library/interface files should use fixed compiler versions, not floating ones

Floating pragmas may lead to unintended vulnerabilities due to different compiler versions.
It is recommended to lock the Solidity version in pragma statements.

<details>
<summary><i>11 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L2)

```solidity
File: src/V3Oracle.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L2)

```solidity
File: src/InterestRateModel.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L2)

```solidity
File: src/automators/AutoExit.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L2)

```solidity
File: src/automators/Automator.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L2)

```solidity
File: src/transformers/AutoCompound.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L2)

```solidity
File: src/transformers/AutoRange.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L2)

```solidity
File: src/transformers/LeverageTransformer.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L2)

```solidity
File: src/transformers/V3Utils.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L2)

```solidity
File: src/utils/FlashloanLiquidator.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L2)

```solidity
File: src/utils/Swapper.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L2)
</details>

### [N-03] Array indices should be referenced via `enum`s rather than via numeric literals

Using constant array indexes can make your Solidity code harder to read and maintain.
To improve clarity, consider using commented enum values in place of constant array indexes.

Enums provide a way to define a type that has a few pre-defined values, making your code more self-explanatory and easy to understand.
This can be particularly helpful in large codebases or when working with a team.

<details>
<summary><i>9 issue instances in 3 files:</i></summary>

```solidity
File: src/V3Oracle.sol

366: secondsAgos[0]
367: secondsAgos[1]
369: tickCumulatives[0]
369: tickCumulatives[1]
```
[366](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L366) | [367](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L367) | [369](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L369) | [369](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L369)

```solidity
File: src/automators/Automator.sol

182: secondsAgos[0]
183: secondsAgos[1]
187: tickCumulatives[0]
187: tickCumulatives[1]
```
[182](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L182) | [183](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L183) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L187) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L187)

```solidity
File: src/transformers/AutoCompound.sol

234: positionBalances[0]
```
[234](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L234)
</details>

### [N-04] Consider splitting long calculations

For improved readability and maintainability, it's suggested to limit arithmetic operations to 3 per expression.
Excessive operations can convolute the code, making it more prone to errors and more difficult to debug or review.
Splitting operations across multiple lines is often a good approach.
Special care should be taken with division operations. The number of arithmetic operations per line ideally shouldn't exceed three.

<details>
<summary><i>6 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

1060: uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue))
1187: oldDebtExchangeRateX96
                + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96
1189: oldLendExchangeRateX96
                + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96
```
[1060](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1060) | [1187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1187) | [1189](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1189)

```solidity
File: src/V3Oracle.sol

120: (price0X96 * (amount0 + fees0) / Q96 + price1X96 * (amount1 + fees1) / Q96) * Q96 / priceTokenX96
121: (price0X96 * fees0 / Q96 + price1X96 * fees1 / Q96) * Q96 / priceTokenX96
304: (10 ** referenceTokenDecimals) * chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96
                / (10 ** feedConfig.tokenDecimals)
```
[120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L120) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L121) | [304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L304)
</details>

### [N-05] Use custom errors instead of `require()/assert()`

Starting from Solidity 0.8.4, custom errors have been introduced to improve readability and clarity in your code. Instead of using `require()/assert()` with strings, custom errors can provide more expressive and understandable error conditions.

This change not only reduces unnecessary clutter in your codebase but also promotes a more streamlined contract structure, ultimately improving the quality of your Solidity code.

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: src/transformers/AutoCompound.sol

244: require(_totalRewardX64 <= totalRewardX64, ">totalRewardX64")
269: require(amount <= balance, "amount>balance")
```
[244](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L244) | [269](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L269)

```solidity
File: src/utils/Swapper.sol

157: require(amount0Delta > 0 || amount1Delta > 0)
```
[157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L157)
</details>

### [N-06] Variables need not be initialized to zero

By default, `int/uint` variables in Solidity are initialized to `zero`.
Explicitly setting variables to zero during their declaration is redundant and might cause confusion.
Removing the explicit zero initialization can improve code readability and understanding.

<details>
<summary><i>13 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

118: uint32 public reserveFactorX32 = 0;
124: uint256 public debtSharesTotal = 0;
127: uint256 public lastExchangeRateUpdate = 0;
131: uint256 public globalDebtLimit = 0;
132: uint256 public globalLendLimit = 0;
135: uint256 public minLoanSize = 0;
138: uint256 public dailyLendIncreaseLimitMin = 0;
139: uint256 public dailyLendIncreaseLimitLeft = 0;
140: uint256 public dailyLendIncreaseLimitLastReset = 0;
143: uint256 public dailyDebtIncreaseLimitMin = 0;
144: uint256 public dailyDebtIncreaseLimitLeft = 0;
145: uint256 public dailyDebtIncreaseLimitLastReset = 0;
161: uint256 private transformedTokenId = 0; // transient storage (when available in dencun)
```
[118](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L118) | [124](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L124) | [127](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L127) | [131](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L131) | [132](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L132) | [135](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L135) | [138](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L138) | [139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L139) | [140](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L140) | [143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L143) | [144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L144) | [145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L145) | [161](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L161)
</details>

### [N-07] `require()/revert()` statements without reason strings

In Solidity, require() and revert() functions can include an optional 'reason' string that describes what caused the function to fail. This string can be incredibly helpful during testing and debugging, as it provides more context for what went wrong.

Some `require()/revert()` statements do not have these descriptive reason strings. For better error handling and debugging, it is strongly recommended to add descriptive reason strings to all `require()/revert()` statements.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/utils/Swapper.sol

157: require(amount0Delta > 0 || amount1Delta > 0)
```
[157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L157)
</details>

### [N-08] Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability

Combining multiple address/ID mappings into a single mapping to a struct can enhance code clarity and maintainability. 
Consider refactoring multiple mappings into a single mapping with a struct for cleaner code structure.
This arrangement also promotes a more organized contract structure, making it easier for developers to navigate and understand.

<details>
<summary><i>9 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

115: mapping(address => TokenConfig) public tokenConfigs
157: mapping(address => uint256[]) private ownedTokens
163: mapping(address => bool) public transformerAllowList
164: mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals
154: mapping(uint256 => Loan) public loans
158: mapping(uint256 => uint256) private ownedTokensIndex
159: mapping(uint256 => address) private tokenOwner
```
[115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L115) | [157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L157) | [163](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L163) | [164](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L164) | [154](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L154) | [158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L158) | [159](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L159)

```solidity
File: src/automators/Automator.sol

34: mapping(address => bool) public operators
35: mapping(address => bool) public vaults
```
[34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L34) | [35](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L35)
</details>

### [N-09] Consider returning a `struct` rather than having multiple `return` values

Functions that return many variables can become difficult to read and maintain.
Using a struct to encapsulate these return values can improve code readability, increase reusability, and reduce the likelihood of errors.
Consider refactoring functions that return more than three variables to use a struct instead.

<details>
<summary><i>15 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

195: function vaultInfo()
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
231: function loanInfo(uint256 tokenId)
        external
        view
        override
        returns (
            uint256 debt,
            uint256 fullValue,
            uint256 collateralValue,
            uint256 liquidationCost,
            uint256 liquidationValue
        )
1017: function _getAvailableBalance(uint256 debtExchangeRateX96, uint256 lendExchangeRateX96)
        internal
        view
        returns (uint256 balance, uint256 available, uint256 reserves)
1090: function _calculateLiquidation(uint256 debt, uint256 fullValue, uint256 collateralValue)
        internal
        pure
        returns (uint256 liquidationValue, uint256 liquidatorCost, uint256 reserveCost)
1270: function _checkLoanIsHealthy(uint256 tokenId, uint256 debt)
        internal
        view
        returns (bool isHealthy, uint256 fullValue, uint256 collateralValue, uint256 feeValue)
```
[195](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L195) | [231](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L231) | [1017](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1017) | [1090](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1090) | [1270](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1270)

```solidity
File: src/V3Oracle.sol

95: function getValue(uint256 tokenId, address token)
        external
        view
        override
        returns (uint256 value, uint256 feeValue, uint256 price0X96, uint256 price1X96)
162: function getPositionBreakdown(uint256 tokenId)
        public
        view
        override
        returns (
            address token0,
            address token1,
            uint24 fee,
            uint128 liquidity,
            uint256 amount0,
            uint256 amount1,
            uint128 fees0,
            uint128 fees1
        )
426: function _getAmounts(PositionState memory state)
        internal
        view
        returns (uint256 amount0, uint256 amount1, uint128 fees0, uint128 fees1)
```
[95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L95) | [162](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L162) | [426](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L426)

```solidity
File: src/automators/Automator.sol

139: function _validateSwap(
        bool swap0For1,
        uint256 amountIn,
        IUniswapV3Pool pool,
        uint32 twapPeriod,
        uint16 maxTickDifference,
        uint64 maxPriceDifferenceX64
    ) internal view returns (uint256 amountOutMin, int24 currentTick, uint160 sqrtPriceX96, uint256 priceX96)
193: function _decreaseFullLiquidityAndCollect(
        uint256 tokenId,
        uint128 liquidity,
        uint256 amountRemoveMin0,
        uint256 amountRemoveMin1,
        uint256 deadline
    ) internal returns (uint256 amount0, uint256 amount1, uint256 feeAmount0, uint256 feeAmount1)
```
[139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L139) | [193](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L193)

```solidity
File: src/transformers/V3Utils.sol

467: function swapAndMint(SwapAndMintParams calldata params)
        external
        payable
        returns (uint256 tokenId, uint128 liquidity, uint256 amount0, uint256 amount1)
532: function swapAndIncreaseLiquidity(SwapAndIncreaseLiquidityParams calldata params)
        external
        payable
        returns (uint128 liquidity, uint256 amount0, uint256 amount1)
653: function _prepareAdd(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther
    ) internal returns (uint256 needed0, uint256 needed1, uint256 neededOther)
705: function _swapAndMint(SwapAndMintParams memory params, bool unwrap)
        internal
        returns (uint256 tokenId, uint128 liquidity, uint256 added0, uint256 added1)
735: function _swapAndIncrease(SwapAndIncreaseLiquidityParams memory params, IERC20 token0, IERC20 token1, bool unwrap)
        internal
        returns (uint128 liquidity, uint256 added0, uint256 added1)
```
[467](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L467) | [532](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L532) | [653](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L653) | [705](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L705) | [735](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L735)
</details>

### [N-10] Consider using a `struct` rather than having many function input parameters

Functions with many parameters can become difficult to read and maintain. 
Using a struct to encapsulate these parameters can improve code readability, increase reusability, and reduce the likelihood of errors.
Consider refactoring functions that take more than three parameters to use a struct instead.

<details>
<summary><i>21 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

169: constructor(
        string memory name,
        string memory symbol,
        address _asset,
        INonfungiblePositionManager _nonfungiblePositionManager,
        IInterestRateModel _interestRateModel,
        IV3Oracle _oracle,
        IPermit2 _permit2
    ) ERC20(name, symbol)
410: function createWithPermit(
        uint256 tokenId,
        address owner,
        address recipient,
        uint256 deadline,
        uint8 v,
        bytes32 r,
        bytes32 s
    ) external override
807: function setLimits(
        uint256 _minLoanSize,
        uint256 _globalLendLimit,
        uint256 _globalDebtLimit,
        uint256 _dailyLendIncreaseLimitMin,
        uint256 _dailyDebtIncreaseLimitMin
    ) external
1032: function _sendPositionValue(
        uint256 tokenId,
        uint256 liquidationValue,
        uint256 fullValue,
        uint256 feeValue,
        address recipient
    ) internal returns (uint256 amount0, uint256 amount1)
1205: function _updateAndCheckCollateral(
        uint256 tokenId,
        uint256 debtExchangeRateX96,
        uint256 lendExchangeRateX96,
        uint256 oldShares,
        uint256 newShares
    ) internal
```
[169](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L169) | [410](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L410) | [807](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L807) | [1032](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1032) | [1205](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1205)

```solidity
File: src/V3Oracle.sol

201: function setTokenConfig(
        address token,
        AggregatorV3Interface feed,
        uint32 maxFeedAge,
        IUniswapV3Pool pool,
        uint32 twapSeconds,
        Mode mode,
        uint16 maxDifference
    ) external onlyOwner
472: function _getFeeGrowthInside(
        IUniswapV3Pool pool,
        int24 tickLower,
        int24 tickUpper,
        int24 tickCurrent,
        uint256 feeGrowthGlobal0X128,
        uint256 feeGrowthGlobal1X128
    ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128)
```
[201](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L201) | [472](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L472)

```solidity
File: src/automators/AutoExit.sol

33: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter)
```
[33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L33)

```solidity
File: src/automators/Automator.sol

41: constructor(
        INonfungiblePositionManager npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Swapper(npm, _zeroxRouter, _universalRouter)
139: function _validateSwap(
        bool swap0For1,
        uint256 amountIn,
        IUniswapV3Pool pool,
        uint32 twapPeriod,
        uint16 maxTickDifference,
        uint64 maxPriceDifferenceX64
    ) internal view returns (uint256 amountOutMin, int24 currentTick, uint160 sqrtPriceX96, uint256 priceX96)
193: function _decreaseFullLiquidityAndCollect(
        uint256 tokenId,
        uint128 liquidity,
        uint256 amountRemoveMin0,
        uint256 amountRemoveMin1,
        uint256 deadline
    ) internal returns (uint256 amount0, uint256 amount1, uint256 feeAmount0, uint256 feeAmount1)
```
[41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L41) | [139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L139) | [193](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L193)

```solidity
File: src/transformers/AutoCompound.sol

37: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, address(0), address(0))
266: function _withdrawBalanceInternal(uint256 tokenId, address token, address to, uint256 balance, uint256 amount)
        internal
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L37) | [266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L266)

```solidity
File: src/transformers/AutoRange.sol

25: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter)
```
[25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L25)

```solidity
File: src/transformers/V3Utils.sol

98: function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)
        public
        returns (uint256 newTokenId)
566: function _prepareAddApproved(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther
    ) internal
598: function _prepareAddPermit2(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther,
        IPermit2.PermitBatchTransferFrom memory permit,
        bytes memory signature
    ) internal
653: function _prepareAdd(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther
    ) internal returns (uint256 needed0, uint256 needed1, uint256 neededOther)
841: function _returnLeftoverTokens(
        address to,
        IERC20 token0,
        IERC20 token1,
        uint256 total0,
        uint256 total1,
        uint256 added0,
        uint256 added1,
        bool unwrap
    ) internal
877: function _decreaseLiquidity(
        uint256 tokenId,
        uint128 liquidity,
        uint256 deadline,
        uint256 token0Min,
        uint256 token1Min
    ) internal returns (uint256 amount0, uint256 amount1)
892: function _collectFees(uint256 tokenId, IERC20 token0, IERC20 token1, uint128 collectAmount0, uint128 collectAmount1)
        internal
        returns (uint256 amount0, uint256 amount1)
```
[98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L98) | [566](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L566) | [598](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L598) | [653](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L653) | [841](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L841) | [877](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L877) | [892](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L892)
</details>

### [N-11] Consider using descriptive `constant`s when passing zero as a function argument

In instances where utilizing a zero parameter is essential, it is recommended to employ descriptive constants or an enum instead of directly integrating zero within function calls.
This strategy aids in clearly articulating the caller's intention and minimizes the risk of errors.
Emitting zero also not recomended, as it is not clear what the intention is.

<details>
<summary><i>32 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

446: Loan(0)
449: Add(tokenId, owner, 0)
470: _updateAndCheckCollateral(
                    tokenId, debtExchangeRateX96, lendExchangeRateX96, 0, loans[tokenId].debtShares
                )
1066: INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp)
1081: _updateAndCheckCollateral(tokenId, debtExchangeRateX96, lendExchangeRateX96, loans[tokenId].debtShares, 0)
```
[446](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L446) | [449](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L449) | [470](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L470) | [1066](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1066) | [1081](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1081)

```solidity
File: src/V3Oracle.sol

135: _getReferencePoolPriceX96(pool, 0)
235: TokenConfig(
                feed, maxFeedAge, feedDecimals, tokenDecimals, IUniswapV3Pool(address(0)), false, 0, Mode.CHAINLINK, 0
            )
```
[135](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L135) | [235](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L235)

```solidity
File: src/automators/AutoExit.sol

208: PositionConfigured(params.tokenId, false, false, false, 0, 0, 0, 0, false, 0)
```
[208](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L208)

```solidity
File: src/transformers/AutoCompound.sol

143: Swapper.PoolSwapParams(
                            pool, IERC20(state.token0), IERC20(state.token1), state.fee, params.swap0To1, amountIn, 0
                        )
164: INonfungiblePositionManager.IncreaseLiquidityParams(
                        params.tokenId, state.maxAddAmount0, state.maxAddAmount1, 0, 0, block.timestamp
                    )
179: _increaseBalance(0, state.token0, state.amount0Fees)
180: _increaseBalance(0, state.token1, state.amount1Fees)
235: _withdrawBalanceInternal(0, tokens[i], to, balance, balance)
```
[143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L143) | [164](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L164) | [179](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L179) | [180](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L180) | [235](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L235)

```solidity
File: src/transformers/AutoRange.sol

198: INonfungiblePositionManager.MintParams(
                address(state.token0),
                address(state.token1),
                state.fee,
                SafeCast.toInt24(baseTick + config.lowerTickDelta), // reverts if out of valid range
                SafeCast.toInt24(baseTick + config.upperTickDelta), // reverts if out of valid range
                state.maxAddAmount0,
                state.maxAddAmount1,
                0,
                0,
                address(this), // is sent to real recipient aftwards
                params.deadline
            )
220: SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), 0)
221: SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), 0)
266: PositionConfigured(params.tokenId, 0, 0, 0, 0, 0, 0, false, 0)
```
[198](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L198) | [220](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L220) | [221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L221) | [266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L266)

```solidity
File: src/transformers/V3Utils.sol

149: SwapAndIncreaseLiquidityParams(
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
                    )
172: SwapAndIncreaseLiquidityParams(
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
                    )
196: SwapAndIncreaseLiquidityParams(
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
                    )
222: SwapAndMintParams(
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
                    )
249: SwapAndMintParams(
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
                    )
277: SwapAndMintParams(
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
                    )
405: _prepareAddPermit2(
                params.tokenIn, IERC20(address(0)), IERC20(address(0)), params.amountIn, 0, 0, pbtf, signature
            )
409: _prepareAddApproved(params.tokenIn, IERC20(address(0)), IERC20(address(0)), params.amountIn, 0, 0)
740: SwapAndMintParams(
                token0,
                token1,
                0,
                0,
                0,
                params.amount0,
                params.amount1,
                params.recipient,
                params.recipient,
                params.deadline,
                params.swapSourceToken,
                params.amountIn0,
                params.amountOut0Min,
                params.swapData0,
                params.amountIn1,
                params.amountOut1Min,
                params.swapData1,
                params.amountAddMin0,
                params.amountAddMin1,
                "",
                params.permitData
            )
831: SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), 0)
835: SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), 0)
```
[149](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L149) | [172](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L172) | [196](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L196) | [222](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L222) | [249](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L249) | [277](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L277) | [405](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L405) | [409](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L409) | [740](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L740) | [831](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L831) | [835](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L835)

```solidity
File: src/utils/FlashloanLiquidator.sol

58: RouterSwapParams(IERC20(token0), IERC20(asset), params.amount0In, 0, params.swapData0)
59: RouterSwapParams(IERC20(token1), IERC20(asset), params.amount1In, 0, params.swapData1)
78: SafeERC20.safeApprove(data.asset, address(data.vault), 0)
```
[58](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L58) | [59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L59) | [78](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L78)

```solidity
File: src/utils/Swapper.sol

94: SafeERC20.safeApprove(params.tokenIn, data.allowanceTarget, 0)
```
[94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L94)
</details>

### [N-12] Consider using OpenZeppelin's SafeCast for any casting

OpenZeppelin's has `SafeCast` library that provides functions to safely cast. Recommended to use it instead of casting directly in any case.

<details>
<summary><i>21 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

1054: uint128(liquidationValue * fees0 / feeValue)
1055: uint128(liquidationValue * fees1 / feeValue)
1060: uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue))
```
[1054](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1054) | [1055](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1055) | [1060](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1060)

```solidity
File: src/V3Oracle.sol

342: uint256(answer)
369: int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)))
369: int56(uint56(twapSeconds))
369: uint56(twapSeconds)
467: uint128(FullMath.mulDiv(feeGrowth0, position.liquidity, Q128))
468: uint128(FullMath.mulDiv(feeGrowth1, position.liquidity, Q128))
```
[342](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L342) | [369](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L369) | [369](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L369) | [369](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L369) | [467](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L467) | [468](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L468)

```solidity
File: src/automators/Automator.sol

173: int16(maxDifference)
173: int16(maxDifference)
187: int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapPeriod)))
187: int56(uint56(twapPeriod))
187: uint56(twapPeriod)
```
[173](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L173) | [173](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L173) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L187) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L187) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L187)

```solidity
File: src/utils/Swapper.sol

137: int256(params.amountIn)
145: uint256(amount0Delta)
145: uint256(amount1Delta)
146: uint256(-amount1Delta)
146: uint256(-amount0Delta)
166: uint256(amount0Delta)
166: uint256(amount1Delta)
```
[137](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L137) | [145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L145) | [145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L145) | [146](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L146) | [146](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L146) | [166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L166) | [166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L166)
</details>

### [N-13] Consider using `delete` rather than assigning `zero` to clear values

Rather than merely setting a variable to zero, you can use the `delete` keyword to reset it to its default value.
This action is especially relevant for complex data types like arrays or mappings where the default is not necessarily zero.
Using `delete` not only provides explicit clarity that you intend to reset a variable, but it can also result in more concise and intuitive code.

<details>
<summary><i>5 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

542: transformedTokenId = 0
1053: liquidity = 0
```
[542](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L542) | [1053](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1053)

```solidity
File: src/V3Oracle.sol

366: secondsAgos[0] = 0
```
[366](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L366)

```solidity
File: src/automators/Automator.sol

182: secondsAgos[0] = 0
```
[182](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L182)

```solidity
File: src/transformers/AutoCompound.sol

136: amountIn = 0
```
[136](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L136)
</details>

### [N-14] Consider emitting an event at the end of the constructor

This will allow users to easily exactly pinpoint when and by whom a contract was constructed.

<details>
<summary><i>11 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

169: constructor(
        string memory name,
        string memory symbol,
        address _asset,
        INonfungiblePositionManager _nonfungiblePositionManager,
        IInterestRateModel _interestRateModel,
        IV3Oracle _oracle,
        IPermit2 _permit2
    ) ERC20(name, symbol)
```
[169](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L169)

```solidity
File: src/V3Oracle.sol

74: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _referenceToken,
        address _chainlinkReferenceToken
    )
```
[74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L74)

```solidity
File: src/InterestRateModel.sol

33: constructor(
        uint256 baseRatePerYearX96,
        uint256 multiplierPerYearX96,
        uint256 jumpMultiplierPerYearX96,
        uint256 _kinkX96
    )
```
[33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L33)

```solidity
File: src/automators/AutoExit.sol

33: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter)
```
[33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L33)

```solidity
File: src/automators/Automator.sol

41: constructor(
        INonfungiblePositionManager npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Swapper(npm, _zeroxRouter, _universalRouter)
```
[41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L41)

```solidity
File: src/transformers/AutoCompound.sol

37: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, address(0), address(0))
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L37)

```solidity
File: src/transformers/AutoRange.sol

25: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter)
```
[25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L25)

```solidity
File: src/transformers/LeverageTransformer.sol

13: constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)
        Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter)
```
[13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L13)

```solidity
File: src/transformers/V3Utils.sol

31: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _zeroxRouter,
        address _universalRouter,
        address _permit2
    ) Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter)
```
[31](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L31)

```solidity
File: src/utils/FlashloanLiquidator.sol

24: constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)
        Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter)
```
[24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L24)

```solidity
File: src/utils/Swapper.sol

37: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _zeroxRouter,
        address _universalRouter
    )
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L37)
</details>

### [N-15] Consider using named returns

Using named returns makes the code more self-documenting, makes it easier to fill out NatSpec, and in some cases can save gas.
The cases below are where there currently is at most one return statement, which is ideal for named returns.

<details>
<summary><i>31 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

264: function loanCount(address owner) external view override returns (uint256)
271: function loanAtIndex(address owner, uint256 index) external view override returns (uint256)
277: function decimals() public view override(IERC20Metadata, ERC20) returns (uint8)
284: function totalAssets() public view override returns (uint256)
301: function maxDeposit(address) external view override returns (uint256)
312: function maxMint(address) external view override returns (uint256)
323: function maxWithdraw(address owner) external view override returns (uint256)
329: function maxRedeem(address owner) external view override returns (uint256)
334: function previewDeposit(uint256 assets) public view override returns (uint256)
340: function previewMint(uint256 shares) public view override returns (uint256)
346: function previewWithdraw(uint256 assets) public view override returns (uint256)
352: function previewRedeem(uint256 shares) public view override returns (uint256)
360: function deposit(uint256 assets, address receiver) external override returns (uint256)
366: function mint(uint256 shares, address receiver) external override returns (uint256)
372: function withdraw(uint256 assets, address receiver, address owner) external override returns (uint256)
378: function redeem(uint256 shares, address receiver, address owner) external override returns (uint256)
384: function deposit(uint256 assets, address receiver, bytes calldata permitData) external override returns (uint256)
390: function mint(uint256 shares, address receiver, bytes calldata permitData) external override returns (uint256)
429: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
1143: function _calculateTokenCollateralFactorX32(uint256 tokenId) internal view returns (uint32)
1281: function _convertToShares(uint256 amount, uint256 exchangeRateX96, Math.Rounding rounding)
        internal
        pure
        returns (uint256)
1289: function _convertToAssets(uint256 shares, uint256 exchangeRateX96, Math.Rounding rounding)
        internal
        pure
        returns (uint256)
```
[264](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L264) | [271](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L271) | [277](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L277) | [284](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L284) | [301](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L301) | [312](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L312) | [323](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L323) | [329](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L329) | [334](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L334) | [340](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L340) | [346](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L346) | [352](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L352) | [360](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L360) | [366](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L366) | [372](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L372) | [378](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L378) | [384](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L384) | [390](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L390) | [429](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L429) | [1143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1143) | [1281](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1281) | [1289](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1289)

```solidity
File: src/V3Oracle.sol

329: function _getChainlinkPriceX96(address token) internal view returns (uint256)
359: function _getReferencePoolPriceX96(IUniswapV3Pool pool, uint32 twapSeconds) internal view returns (uint256)
499: function _getPool(address tokenA, address tokenB, uint24 fee) internal view returns (IUniswapV3Pool)
```
[329](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L329) | [359](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L359) | [499](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L499)

```solidity
File: src/InterestRateModel.sol

46: function getUtilizationRateX96(uint256 cash, uint256 debt) public pure returns (uint256)
```
[46](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L46)

```solidity
File: src/automators/Automator.sol

166: function _hasMaxTWAPTickDifference(IUniswapV3Pool pool, uint32 twapPeriod, int24 currentTick, uint16 maxDifference)
        internal
        view
        returns (bool)
180: function _getTWAPTick(IUniswapV3Pool pool, uint32 twapPeriod) internal view returns (int24, bool)
```
[166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L166) | [180](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L180)

```solidity
File: src/transformers/AutoRange.sol

300: function _getTickSpacing(uint24 fee) internal view returns (int24)
```
[300](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L300)

```solidity
File: src/transformers/V3Utils.sol

356: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
```
[356](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L356)

```solidity
File: src/utils/Swapper.sol

171: function _getPool(address tokenA, address tokenB, uint24 fee) internal view returns (IUniswapV3Pool)
```
[171](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L171)
</details>

### [N-16] Style guide: Initialisms should be capitalized

According to the Solidity [style guide](https://docs.soliditylang.org/en/latest/style-guide.html#naming-styles) initialisms such as "NFT", "ERC", etc should be capitalized.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/utils/Swapper.sol

21: IWETH9 public immutable weth
```
[21](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L21)
</details>

### [N-17] Expressions for constant values should use `immutable` rather than `constant`

While it does not save gas for some simple binary expressions because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between `constant` variables and immutable variables, and they should each be used in their appropriate contexts.
`constant`s should be used for literal values written into the code, and immutable variables should be used for expressions, or values calculated in, or passed into the constructor.

<details>
<summary><i>16 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

33: uint256 private constant Q32 = 2 ** 32
34: uint256 private constant Q96 = 2 ** 96
36: uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100)
38: uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100)
39: uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100)
41: uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100)
43: uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10)
44: uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10)
```
[33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L33) | [34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L34) | [36](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L36) | [38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L38) | [39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L39) | [41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L41) | [43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L43) | [44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L44)

```solidity
File: src/V3Oracle.sol

27: uint256 private constant Q96 = 2 ** 96
28: uint256 private constant Q128 = 2 ** 128
```
[27](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L27) | [28](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L28)

```solidity
File: src/InterestRateModel.sol

12: uint256 private constant Q96 = 2 ** 96
15: uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10
16: uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2
```
[12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L12) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L15) | [16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L16)

```solidity
File: src/automators/Automator.sol

20: uint256 internal constant Q64 = 2 ** 64
21: uint256 internal constant Q96 = 2 ** 96
```
[20](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L20) | [21](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L21)

```solidity
File: src/transformers/AutoCompound.sol

47: uint64 public constant MAX_REWARD_X64 = uint64(Q64 / 50)
```
[47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L47)
</details>

### [N-18] Consider using named function arguments

When calling functions in external contracts with multiple arguments, consider using named function parameters, rather than positional ones.

<details>
<summary><i>30 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

628: INonfungiblePositionManager.DecreaseLiquidityParams(
                params.tokenId, params.liquidity, params.amount0Min, params.amount1Min, params.deadline
            )
633: INonfungiblePositionManager.CollectParams(
            params.tokenId,
            params.recipient,
            params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
            params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)
        )
720: permit2.permitTransferFrom(
                permit,
                ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost),
                msg.sender,
                signature
            )
722: ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost)
896: permit2.permitTransferFrom(
                permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
            )
897: ISignatureTransfer.SignatureTransferDetails(address(this), assets)
981: permit2.permitTransferFrom(
                    permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
                )
982: ISignatureTransfer.SignatureTransferDetails(address(this), assets)
1066: INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp)
1071: INonfungiblePositionManager.CollectParams(tokenId, recipient, fees0, fees1)
1179: interestRateModel.getRatesPerSecondX96(available, debt)
1275: oracle.getValue(tokenId, address(asset))
```
[628](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L628) | [633](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L633) | [720](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L720) | [722](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L722) | [896](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L896) | [897](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L897) | [981](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L981) | [982](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L982) | [1066](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1066) | [1071](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1071) | [1179](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1179) | [1275](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1275)

```solidity
File: src/V3Oracle.sol

434: LiquidityAmounts.getAmountsForLiquidity(
                state.sqrtPriceX96, state.sqrtPriceX96Lower, state.sqrtPriceX96Upper, state.liquidity
            )
500: PoolAddress.computeAddress(factory, PoolAddress.getPoolKey(tokenA, tokenB, fee))
500: PoolAddress.getPoolKey(tokenA, tokenB, fee)
```
[434](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L434) | [500](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L500) | [500](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L500)

```solidity
File: src/automators/AutoExit.sol

172: Swapper.RouterSwapParams(
                    state.isAbove ? IERC20(state.token1) : IERC20(state.token0),
                    state.isAbove ? IERC20(state.token0) : IERC20(state.token1),
                    state.swapAmount,
                    state.amountOutMin,
                    params.swapData
                )
```
[172](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L172)

```solidity
File: src/automators/Automator.sol

203: INonfungiblePositionManager.DecreaseLiquidityParams(
                    tokenId, liquidity, amountRemoveMin0, amountRemoveMin1, deadline
                )
209: INonfungiblePositionManager.CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max)
```
[203](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L203) | [209](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L209)

```solidity
File: src/transformers/AutoCompound.sol

109: INonfungiblePositionManager.CollectParams(
                params.tokenId, address(this), type(uint128).max, type(uint128).max
            )
143: Swapper.PoolSwapParams(
                            pool, IERC20(state.token0), IERC20(state.token1), state.fee, params.swap0To1, amountIn, 0
                        )
164: INonfungiblePositionManager.IncreaseLiquidityParams(
                        params.tokenId, state.maxAddAmount0, state.maxAddAmount1, 0, 0, block.timestamp
                    )
```
[109](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L109) | [143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L143) | [164](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L164)

```solidity
File: src/transformers/AutoRange.sol

101: IVault(vault).transform(
            params.tokenId, address(this), abi.encodeWithSelector(AutoRange.execute.selector, params)
        )
182: Swapper.RouterSwapParams(
                    params.swap0To1 ? IERC20(state.token0) : IERC20(state.token1),
                    params.swap0To1 ? IERC20(state.token1) : IERC20(state.token0),
                    params.amountIn,
                    state.amountOutMin,
                    params.swapData
                )
198: INonfungiblePositionManager.MintParams(
                address(state.token0),
                address(state.token1),
                state.fee,
                SafeCast.toInt24(baseTick + config.lowerTickDelta), // reverts if out of valid range
                SafeCast.toInt24(baseTick + config.upperTickDelta), // reverts if out of valid range
                state.maxAddAmount0,
                state.maxAddAmount1,
                0,
                0,
                address(this), // is sent to real recipient aftwards
                params.deadline
            )
```
[101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L101) | [182](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L182) | [198](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L198)

```solidity
File: src/utils/FlashloanLiquidator.sol

64: params.flashLoanPool.flash(address(this), isAsset0 ? liquidationCost : 0, !isAsset0 ? liquidationCost : 0, data)
74: IVault.LiquidateParams(
                data.tokenId, data.debtShares, data.swap0.amountIn, data.swap1.amountIn, address(this), ""
            )
```
[64](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L64) | [74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L74)

```solidity
File: src/utils/Swapper.sol

99: IUniversalRouter(universalRouter).execute(data.commands, data.inputs, data.deadline)
134: params.pool.swap(
                address(this),
                params.swap0For1,
                int256(params.amountIn),
                (params.swap0For1 ? TickMath.MIN_SQRT_RATIO + 1 : TickMath.MAX_SQRT_RATIO - 1),
                abi.encode(
                    params.swap0For1 ? params.token0 : params.token1,
                    params.swap0For1 ? params.token1 : params.token0,
                    params.fee
                )
            )
172: PoolAddress.computeAddress(address(factory), PoolAddress.getPoolKey(tokenA, tokenB, fee))
172: PoolAddress.getPoolKey(tokenA, tokenB, fee)
```
[99](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L99) | [134](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L134) | [172](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L172) | [172](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L172)
</details>

### [N-19] Events are missing sender information

Events should include the sender information when emitted in `public` or `external` functions for better traceability.

<details>
<summary><i>30 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit external function `onERC721Received()` emits an event without sender information
449: emit Add(tokenId, owner, 0);
/// @audit external function `onERC721Received()` emits an event without sender information
464: emit Add(tokenId, owner, oldTokenId);
/// @audit external function `borrow()` emits an event without sender information
600: emit Borrow(tokenId, owner, assets, shares);
/// @audit external function `decreaseLiquidityAndCollect()` emits an event without sender information
644: emit WithdrawCollateral(params.tokenId, owner, params.recipient, params.liquidity, amount0, amount1);
/// @audit external function `withdrawReserves()` emits an event without sender information
781: emit WithdrawReserves(amount, receiver);
/// @audit external function `setTransformer()` emits an event without sender information
798: emit SetTransformer(transformer, active);
/// @audit external function `setLimits()` emits an event without sender information
829: emit SetLimits(
            _minLoanSize, _globalLendLimit, _globalDebtLimit, _dailyLendIncreaseLimitMin, _dailyDebtIncreaseLimitMin
        );
/// @audit external function `setReserveFactor()` emits an event without sender information
839: emit SetReserveFactor(_reserveFactorX32);
/// @audit external function `setReserveProtectionFactor()` emits an event without sender information
849: emit SetReserveProtectionFactor(_reserveProtectionFactorX32);
/// @audit external function `setTokenConfig()` emits an event without sender information
865: emit SetTokenConfig(token, collateralFactorX32, collateralValueLimitFactorX32);
/// @audit external function `setEmergencyAdmin()` emits an event without sender information
872: emit SetEmergencyAdmin(admin);
```
[449](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L449) | [464](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L464) | [600](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L600) | [644](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L644) | [781](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L781) | [798](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L798) | [829](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L829) | [839](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L839) | [849](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L849) | [865](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L865) | [872](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L872)

```solidity
File: src/V3Oracle.sol

/// @audit external function `setMaxPoolPriceDifference()` emits an event without sender information
190: emit SetMaxPoolPriceDifference(_maxPoolPriceDifference);
/// @audit external function `setTokenConfig()` emits an event without sender information
241: emit TokenConfigUpdated(token, config);
/// @audit external function `setTokenConfig()` emits an event without sender information
243: emit OracleModeUpdated(token, mode);
/// @audit external function `setOracleMode()` emits an event without sender information
260: emit OracleModeUpdated(token, mode);
/// @audit external function `setEmergencyAdmin()` emits an event without sender information
267: emit SetEmergencyAdmin(admin);
```
[190](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L190) | [241](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L241) | [243](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L243) | [260](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L260) | [267](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L267)

```solidity
File: src/InterestRateModel.sol

/// @audit public function `setValues()` emits an event without sender information
99: emit SetValues(baseRatePerYearX96, multiplierPerYearX96, jumpMultiplierPerYearX96, _kinkX96);
```
[99](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L99)

```solidity
File: src/automators/AutoExit.sol

/// @audit external function `execute()` emits an event without sender information
208: emit PositionConfigured(params.tokenId, false, false, false, 0, 0, 0, 0, false, 0);
/// @audit external function `configToken()` emits an event without sender information
231: emit PositionConfigured(
            tokenId,
            config.isActive,
            config.token0Swap,
            config.token1Swap,
            config.token0TriggerTick,
            config.token1TriggerTick,
            config.token0SlippageX64,
            config.token1SlippageX64,
            config.onlyFees,
            config.maxRewardX64
        );
```
[208](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L208) | [231](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L231)

```solidity
File: src/automators/Automator.sol

/// @audit public function `setWithdrawer()` emits an event without sender information
60: emit WithdrawerChanged(_withdrawer);
/// @audit public function `setOperator()` emits an event without sender information
70: emit OperatorChanged(_operator, _active);
/// @audit public function `setVault()` emits an event without sender information
80: emit VaultChanged(_vault, _active);
/// @audit public function `setTWAPConfig()` emits an event without sender information
94: emit TWAPConfigChanged(_TWAPSeconds, _maxTWAPTickDifference);
```
[60](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L60) | [70](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L70) | [80](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L80) | [94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L94)

```solidity
File: src/transformers/AutoRange.sol

/// @audit external function `execute()` emits an event without sender information
252: emit PositionConfigured(
                state.newTokenId,
                config.lowerTickLimit,
                config.upperTickLimit,
                config.lowerTickDelta,
                config.upperTickDelta,
                config.token0SlippageX64,
                config.token1SlippageX64,
                config.onlyFees,
                config.maxRewardX64
            );
/// @audit external function `execute()` emits an event without sender information
266: emit PositionConfigured(params.tokenId, 0, 0, 0, 0, 0, 0, false, 0);
/// @audit external function `execute()` emits an event without sender information
267: emit RangeChanged(params.tokenId, state.newTokenId);
/// @audit external function `configToken()` emits an event without sender information
285: emit PositionConfigured(
            tokenId,
            config.lowerTickLimit,
            config.upperTickLimit,
            config.lowerTickDelta,
            config.upperTickDelta,
            config.token0SlippageX64,
            config.token1SlippageX64,
            config.onlyFees,
            config.maxRewardX64
        );
```
[252](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L252) | [266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L266) | [267](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L267) | [285](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L285)

```solidity
File: src/transformers/V3Utils.sol

/// @audit public function `execute()` emits an event without sender information
218: emit CompoundFees(tokenId, liquidity, amount0, amount1);
/// @audit public function `execute()` emits an event without sender information
303: emit ChangeRange(tokenId, newTokenId);
/// @audit public function `execute()` emits an event without sender information
347: emit WithdrawAndCollectAndSwap(tokenId, instructions.targetToken, targetAmount);
```
[218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L218) | [303](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L303) | [347](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L347)
</details>

### [N-20] Leverage Recent Solidity Features with `0.8.23`

The recent updates in Solidity provide several features and optimizations that, when leveraged appropriately, can significantly improve your contract's code clarity and maintainability.
Key enhancements include the use of push0 for placing 0 on the stack for EVM versions starting from "Shanghai", making your code simpler and more straightforward.
Moreover, Solidity has extended NatSpec documentation support to enum and struct definitions, facilitating more comprehensive and insightful code documentation.

Additionally, the re-implementation of the UnusedAssignEliminator and UnusedStoreEliminator in the Solidity optimizer provides the ability to remove unused assignments in deeply nested loops.
This results in a cleaner, more efficient contract code, reducing clutter and potential points of confusion during code review or debugging.
It's recommended to make full use of these features and optimizations to enhance the robustness and readability of your smart contracts.

<details>
<summary><i>11 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L2)

```solidity
File: src/V3Oracle.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L2)

```solidity
File: src/InterestRateModel.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L2)

```solidity
File: src/automators/AutoExit.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L2)

```solidity
File: src/automators/Automator.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L2)

```solidity
File: src/transformers/AutoCompound.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L2)

```solidity
File: src/transformers/AutoRange.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L2)

```solidity
File: src/transformers/LeverageTransformer.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L2)

```solidity
File: src/transformers/V3Utils.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L2)

```solidity
File: src/utils/FlashloanLiquidator.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L2)

```solidity
File: src/utils/Swapper.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L2)
</details>

### [N-21] NatSpec: Function `@param` tag is missing

Natural Specification (NatSpec) comments are crucial for understanding the role of function arguments in your Solidity code.
Including `@param` tags will not only improve your code's readability but also its maintainability by clearly defining each argument's purpose.

[More information in Documentation](https://docs.soliditylang.org/en/develop/natspec-format.html)

<details>
<summary><i>80 issue instances in 10 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit Missed @param `name, symbol, _asset, _nonfungiblePositionManager, _interestRateModel, _oracle, _permit2`
169: constructor(
        string memory name,
        string memory symbol,
        address _asset,
        INonfungiblePositionManager _nonfungiblePositionManager,
        IInterestRateModel _interestRateModel,
        IV3Oracle _oracle,
        IPermit2 _permit2
    ) ERC20(name, symbol) {
/// @audit Missed @param `assets, receiver, permitData`
384: function deposit(uint256 assets, address receiver, bytes calldata permitData) external override returns (uint256) {
/// @audit Missed @param `shares, receiver, permitData`
390: function mint(uint256 shares, address receiver, bytes calldata permitData) external override returns (uint256) {
/// @audit Missed @param `v, r, s`
410: function createWithPermit(
        uint256 tokenId,
        address owner,
        address recipient,
        uint256 deadline,
        uint8 v,
        bytes32 r,
        bytes32 s
    ) external override {
/// @audit Missed @param `receiver, amount, isShare, permitData`
877: function _deposit(address receiver, uint256 amount, bool isShare, bytes memory permitData)
        internal
        returns (uint256 assets, uint256 shares)
    {
/// @audit Missed @param `receiver, owner, amount, isShare`
920: function _withdraw(address receiver, address owner, uint256 amount, bool isShare)
        internal
        returns (uint256 assets, uint256 shares)
    {
/// @audit Missed @param `tokenId, amount, isShare, permitData`
954: function _repay(uint256 tokenId, uint256 amount, bool isShare, bytes memory permitData) internal {
/// @audit Missed @param `debtExchangeRateX96, lendExchangeRateX96`
1017: function _getAvailableBalance(uint256 debtExchangeRateX96, uint256 lendExchangeRateX96)
        internal
        view
        returns (uint256 balance, uint256 available, uint256 reserves)
    {
/// @audit Missed @param `tokenId, liquidationValue, fullValue, feeValue, recipient`
1032: function _sendPositionValue(
        uint256 tokenId,
        uint256 liquidationValue,
        uint256 fullValue,
        uint256 feeValue,
        address recipient
    ) internal returns (uint256 amount0, uint256 amount1) {
/// @audit Missed @param `tokenId, debtExchangeRateX96, lendExchangeRateX96, owner`
1077: function _cleanupLoan(uint256 tokenId, uint256 debtExchangeRateX96, uint256 lendExchangeRateX96, address owner)
        internal
    {
/// @audit Missed @param `debt, fullValue, collateralValue`
1090: function _calculateLiquidation(uint256 debt, uint256 fullValue, uint256 collateralValue)
        internal
        pure
        returns (uint256 liquidationValue, uint256 liquidatorCost, uint256 reserveCost)
    {
/// @audit Missed @param `reserveCost, newDebtExchangeRateX96, newLendExchangeRateX96`
1123: function _handleReserveLiquidation(
        uint256 reserveCost,
        uint256 newDebtExchangeRateX96,
        uint256 newLendExchangeRateX96
    ) internal returns (uint256 missing) {
/// @audit Missed @param `tokenId`
1143: function _calculateTokenCollateralFactorX32(uint256 tokenId) internal view returns (uint32) {
/// @audit Missed @param `tokenId, debt`
1197: function _requireLoanIsHealthy(uint256 tokenId, uint256 debt) internal view {
/// @audit Missed @param `tokenId, debtExchangeRateX96, lendExchangeRateX96, oldShares, newShares`
1205: function _updateAndCheckCollateral(
        uint256 tokenId,
        uint256 debtExchangeRateX96,
        uint256 lendExchangeRateX96,
        uint256 oldShares,
        uint256 newShares
    ) internal {
/// @audit Missed @param `newLendExchangeRateX96, force`
1246: function _resetDailyLendIncreaseLimit(uint256 newLendExchangeRateX96, bool force) internal {
/// @audit Missed @param `newLendExchangeRateX96, force`
1258: function _resetDailyDebtIncreaseLimit(uint256 newLendExchangeRateX96, bool force) internal {
/// @audit Missed @param `tokenId, debt`
1270: function _checkLoanIsHealthy(uint256 tokenId, uint256 debt)
        internal
        view
        returns (bool isHealthy, uint256 fullValue, uint256 collateralValue, uint256 feeValue)
    {
/// @audit Missed @param `amount, exchangeRateX96, rounding`
1281: function _convertToShares(uint256 amount, uint256 exchangeRateX96, Math.Rounding rounding)
        internal
        pure
        returns (uint256)
    {
/// @audit Missed @param `shares, exchangeRateX96, rounding`
1289: function _convertToAssets(uint256 shares, uint256 exchangeRateX96, Math.Rounding rounding)
        internal
        pure
        returns (uint256)
    {
/// @audit Missed @param `to, tokenId`
1297: function _addTokenToOwner(address to, uint256 tokenId) internal {
/// @audit Missed @param `from, tokenId`
1303: function _removeTokenFromOwner(address from, uint256 tokenId) internal {
```
[169](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L169) | [384](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L384) | [390](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L390) | [410](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L410) | [877](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L877) | [920](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L920) | [954](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L954) | [1017](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1017) | [1032](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1032) | [1077](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1077) | [1090](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1090) | [1123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1123) | [1143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1143) | [1197](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1197) | [1205](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1205) | [1246](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1246) | [1258](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1258) | [1270](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1270) | [1281](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1281) | [1289](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1289) | [1297](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1297) | [1303](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1303)

```solidity
File: src/V3Oracle.sol

/// @audit Missed @param `_nonfungiblePositionManager, _referenceToken, _chainlinkReferenceToken`
74: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _referenceToken,
        address _chainlinkReferenceToken
    ) {
/// @audit Missed @param `token0, token1, fee, derivedPoolPriceX96`
133: function _checkPoolPrice(address token0, address token1, uint24 fee, uint256 derivedPoolPriceX96) internal view {
/// @audit Missed @param `priceX96, verifyPriceX96, maxDifferenceX10000`
139: function _requireMaxDifference(uint256 priceX96, uint256 verifyPriceX96, uint256 maxDifferenceX10000)
        internal
        pure
    {
/// @audit Missed @param `token, cachedChainlinkReferencePriceX96`
272: function _getReferenceTokenPriceX96(address token, uint256 cachedChainlinkReferencePriceX96)
        internal
        view
        returns (uint256 priceX96, uint256 chainlinkReferencePriceX96)
    {
/// @audit Missed @param `token`
329: function _getChainlinkPriceX96(address token) internal view returns (uint256) {
/// @audit Missed @param `feedConfig`
346: function _getTWAPPriceX96(TokenConfig memory feedConfig) internal view returns (uint256 poolTWAPPriceX96) {
/// @audit Missed @param `pool, twapSeconds`
359: function _getReferencePoolPriceX96(IUniswapV3Pool pool, uint32 twapSeconds) internal view returns (uint256) {
/// @audit Missed @param `tokenId`
395: function _initializeState(uint256 tokenId) internal view returns (PositionState memory state) {
/// @audit Missed @param `state`
426: function _getAmounts(PositionState memory state)
        internal
        view
        returns (uint256 amount0, uint256 amount1, uint128 fees0, uint128 fees1)
    {
/// @audit Missed @param `position, tick`
445: function _getUncollectedFees(PositionState memory position, int24 tick)
        internal
        view
        returns (uint128 fees0, uint128 fees1)
    {
/// @audit Missed @param `pool, tickLower, tickUpper, tickCurrent, feeGrowthGlobal0X128, feeGrowthGlobal1X128`
472: function _getFeeGrowthInside(
        IUniswapV3Pool pool,
        int24 tickLower,
        int24 tickUpper,
        int24 tickCurrent,
        uint256 feeGrowthGlobal0X128,
        uint256 feeGrowthGlobal1X128
    ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {
/// @audit Missed @param `tokenA, tokenB, fee`
499: function _getPool(address tokenA, address tokenB, uint24 fee) internal view returns (IUniswapV3Pool) {
```
[74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L74) | [133](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L133) | [139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L139) | [272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L272) | [329](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L329) | [346](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L346) | [359](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L359) | [395](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L395) | [426](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L426) | [445](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L445) | [472](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L472) | [499](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L499)

```solidity
File: src/automators/AutoExit.sol

/// @audit Missed @param `_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter`
33: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
/// @audit Missed @param `params`
100: function execute(ExecuteParams calldata params) external {
/// @audit Missed @param `tokenId, config`
218: function configToken(uint256 tokenId, PositionConfig calldata config) external {
```
[33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L33) | [100](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L100) | [218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L218)

```solidity
File: src/automators/Automator.sol

/// @audit Missed @param `npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter`
41: constructor(
        INonfungiblePositionManager npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Swapper(npm, _zeroxRouter, _universalRouter) {
/// @audit Missed @param `_maxTWAPTickDifference, _TWAPSeconds`
87: function setTWAPConfig(uint16 _maxTWAPTickDifference, uint32 _TWAPSeconds) public onlyOwner {
/// @audit Missed @param `swap0For1, amountIn, pool, twapPeriod, maxTickDifference, maxPriceDifferenceX64`
139: function _validateSwap(
        bool swap0For1,
        uint256 amountIn,
        IUniswapV3Pool pool,
        uint32 twapPeriod,
        uint16 maxTickDifference,
        uint64 maxPriceDifferenceX64
    ) internal view returns (uint256 amountOutMin, int24 currentTick, uint160 sqrtPriceX96, uint256 priceX96) {
/// @audit Missed @param `pool, twapPeriod, currentTick, maxDifference`
166: function _hasMaxTWAPTickDifference(IUniswapV3Pool pool, uint32 twapPeriod, int24 currentTick, uint16 maxDifference)
        internal
        view
        returns (bool)
    {
/// @audit Missed @param `pool, twapPeriod`
180: function _getTWAPTick(IUniswapV3Pool pool, uint32 twapPeriod) internal view returns (int24, bool) {
/// @audit Missed @param `tokenId, liquidity, amountRemoveMin0, amountRemoveMin1, deadline`
193: function _decreaseFullLiquidityAndCollect(
        uint256 tokenId,
        uint128 liquidity,
        uint256 amountRemoveMin0,
        uint256 amountRemoveMin1,
        uint256 deadline
    ) internal returns (uint256 amount0, uint256 amount1, uint256 feeAmount0, uint256 feeAmount1) {
/// @audit Missed @param `to, token, amount, unwrap`
218: function _transferToken(address to, IERC20 token, uint256 amount, bool unwrap) internal {
/// @audit Missed @param `tokenId, vault`
230: function _validateOwner(uint256 tokenId, address vault) internal returns (address owner) {
```
[41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L41) | [87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L87) | [139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L139) | [166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L166) | [180](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L180) | [193](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L193) | [218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L218) | [230](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L230)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit Missed @param `_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference`
37: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, address(0), address(0)) {}
/// @audit Missed @param `params, vault`
87: function executeWithVault(ExecuteParams calldata params, address vault) external {
/// @audit Missed @param `params`
101: function execute(ExecuteParams calldata params) external nonReentrant {
/// @audit Missed @param `tokenId, token, amount`
249: function _increaseBalance(uint256 tokenId, address token, uint256 amount) internal {
/// @audit Missed @param `tokenId, token, amount`
254: function _setBalance(uint256 tokenId, address token, uint256 amount) internal {
/// @audit Missed @param `tokenId, token, to, balance, amount`
266: function _withdrawBalanceInternal(uint256 tokenId, address token, address to, uint256 balance, uint256 amount)
        internal
    {
/// @audit Missed @param `token0, token1`
276: function _checkApprovals(address token0, address token1) internal {
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L37) | [87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L87) | [101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L101) | [249](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L249) | [254](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L254) | [266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L266) | [276](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L276)

```solidity
File: src/transformers/AutoRange.sol

/// @audit Missed @param `_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter`
25: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
/// @audit Missed @param `params, vault`
97: function executeWithVault(ExecuteParams calldata params, address vault) external {
/// @audit Missed @param `params`
111: function execute(ExecuteParams calldata params) external {
/// @audit Missed @param `tokenId, vault, config`
276: function configToken(uint256 tokenId, address vault, PositionConfig calldata config) external {
/// @audit Missed @param `fee`
300: function _getTickSpacing(uint24 fee) internal view returns (int24) {
```
[25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L25) | [97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L97) | [111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L111) | [276](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L276) | [300](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L300)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit Missed @param `_nonfungiblePositionManager, _zeroxRouter, _universalRouter`
13: constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)
        Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter)
    {}
/// @audit Missed @param `params`
40: function leverageUp(LeverageUpParams calldata params) external {
/// @audit Missed @param `params`
123: function leverageDown(LeverageDownParams calldata params) external {
```
[13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L13) | [40](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L40) | [123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L123)

```solidity
File: src/transformers/V3Utils.sol

/// @audit Missed @param `_universalRouter, _permit2`
31: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _zeroxRouter,
        address _universalRouter,
        address _permit2
    ) Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter) {
/// @audit Missed @param `address, from, tokenId, data`
356: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
    {
/// @audit Missed @param `token0, token1, otherToken, amount0, amount1, amountOther`
566: function _prepareAddApproved(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther
    ) internal {
/// @audit Missed @param `token0, token1, otherToken, amount0, amount1, amountOther, permit, signature`
598: function _prepareAddPermit2(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther,
        IPermit2.PermitBatchTransferFrom memory permit,
        bytes memory signature
    ) internal {
/// @audit Missed @param `token0, token1, otherToken, amount0, amount1, amountOther`
653: function _prepareAdd(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther
    ) internal returns (uint256 needed0, uint256 needed1, uint256 neededOther) {
/// @audit Missed @param `params, unwrap`
705: function _swapAndMint(SwapAndMintParams memory params, bool unwrap)
        internal
        returns (uint256 tokenId, uint128 liquidity, uint256 added0, uint256 added1)
    {
/// @audit Missed @param `params, token0, token1, unwrap`
735: function _swapAndIncrease(SwapAndIncreaseLiquidityParams memory params, IERC20 token0, IERC20 token1, bool unwrap)
        internal
        returns (uint128 liquidity, uint256 added0, uint256 added1)
    {
/// @audit Missed @param `params, unwrap`
779: function _swapAndPrepareAmounts(SwapAndMintParams memory params, bool unwrap)
        internal
        returns (uint256 total0, uint256 total1)
    {
/// @audit Missed @param `to, token0, token1, total0, total1, added0, added1, unwrap`
841: function _returnLeftoverTokens(
        address to,
        IERC20 token0,
        IERC20 token1,
        uint256 total0,
        uint256 total1,
        uint256 added0,
        uint256 added1,
        bool unwrap
    ) internal {
/// @audit Missed @param `to, token, amount, unwrap`
864: function _transferToken(address to, IERC20 token, uint256 amount, bool unwrap) internal {
/// @audit Missed @param `tokenId, liquidity, deadline, token0Min, token1Min`
877: function _decreaseLiquidity(
        uint256 tokenId,
        uint128 liquidity,
        uint256 deadline,
        uint256 token0Min,
        uint256 token1Min
    ) internal returns (uint256 amount0, uint256 amount1) {
/// @audit Missed @param `tokenId, token0, token1, collectAmount0, collectAmount1`
892: function _collectFees(uint256 tokenId, IERC20 token0, IERC20 token1, uint128 collectAmount0, uint128 collectAmount1)
        internal
        returns (uint256 amount0, uint256 amount1)
    {
```
[31](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L31) | [356](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L356) | [566](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L566) | [598](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L598) | [653](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L653) | [705](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L705) | [735](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L735) | [779](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L779) | [841](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L841) | [864](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L864) | [877](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L877) | [892](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L892)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit Missed @param `_nonfungiblePositionManager, _zeroxRouter, _universalRouter`
24: constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)
        Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter)
    {}
/// @audit Missed @param `params`
41: function liquidate(LiquidateParams calldata params) external {
/// @audit Missed @param `fee0, fee1, callbackData`
67: function uniswapV3FlashCallback(uint256 fee0, uint256 fee1, bytes calldata callbackData) external {
```
[24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L24) | [41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L41) | [67](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L67)

```solidity
File: src/utils/Swapper.sol

/// @audit Missed @param `_universalRouter`
37: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _zeroxRouter,
        address _universalRouter
    ) {
/// @audit Missed @param `params`
73: function _routerSwap(RouterSwapParams memory params)
        internal
        returns (uint256 amountInDelta, uint256 amountOutDelta)
    {
/// @audit Missed @param `params`
132: function _poolSwap(PoolSwapParams memory params) internal returns (uint256 amountInDelta, uint256 amountOutDelta) {
/// @audit Missed @param `amount0Delta, amount1Delta, data`
156: function uniswapV3SwapCallback(int256 amount0Delta, int256 amount1Delta, bytes calldata data) external override {
/// @audit Missed @param `tokenA, tokenB, fee`
171: function _getPool(address tokenA, address tokenB, uint24 fee) internal view returns (IUniswapV3Pool) {
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L37) | [73](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L73) | [132](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L132) | [156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L156) | [171](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L171)
</details>

### [N-22] High cyclomatic complexity

Functions with high cyclomatic complexity are harder to understand, test, and maintain.
Consider breaking down these blocks into more manageable units, by splitting things into utility functions,
by reducing nesting, and by using early returns.

[Learn More About Cyclomatic Complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity)

<details>
<summary><i>15 issue instances in 9 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit function `borrow` has a cyclomatic complexity of 6
550: function borrow(uint256 tokenId, uint256 assets) external override {
/// @audit function `liquidate` has a cyclomatic complexity of 7
685: function liquidate(LiquidateParams calldata params) external override returns (uint256 amount0, uint256 amount1) {
/// @audit function `_deposit` has a cyclomatic complexity of 7
876: function _deposit(address receiver, uint256 amount, bool isShare, bytes memory permitData)
        internal
        returns (uint256 assets, uint256 shares)
    {
/// @audit function `_repay` has a cyclomatic complexity of 9
953: function _repay(uint256 tokenId, uint256 amount, bool isShare, bytes memory permitData) internal {
```
[550](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L550) | [685](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L685) | [876](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L876) | [953](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L953)

```solidity
File: src/V3Oracle.sol

/// @audit function `_getReferenceTokenPriceX96` has a cyclomatic complexity of 9
272: function _getReferenceTokenPriceX96(address token, uint256 cachedChainlinkReferencePriceX96)
        internal
        view
        returns (uint256 priceX96, uint256 chainlinkReferencePriceX96)
    {
```
[272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L272)

```solidity
File: src/automators/AutoExit.sol

/// @audit function `execute` has a cyclomatic complexity of 15
100: function execute(ExecuteParams calldata params) external {
```
[100](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L100)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit function `execute` has a cyclomatic complexity of 7
101: function execute(ExecuteParams calldata params) external nonReentrant {
```
[101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L101)

```solidity
File: src/transformers/AutoRange.sol

/// @audit function `execute` has a cyclomatic complexity of 13
111: function execute(ExecuteParams calldata params) external {
```
[111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L111)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit function `leverageUp` has a cyclomatic complexity of 7
40: function leverageUp(LeverageUpParams calldata params) external {
```
[40](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L40)

```solidity
File: src/transformers/V3Utils.sol

/// @audit function `execute` has a cyclomatic complexity of 19
115: function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {
/// @audit function `_prepareAddPermit2` has a cyclomatic complexity of 9
597: function _prepareAddPermit2(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther,
        IPermit2.PermitBatchTransferFrom memory permit,
        bytes memory signature
    ) internal {
/// @audit function `_prepareAdd` has a cyclomatic complexity of 11
653: function _prepareAdd(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther
    ) internal returns (uint256 needed0, uint256 needed1, uint256 neededOther) {
/// @audit function `_swapAndPrepareAmounts` has a cyclomatic complexity of 9
779: function _swapAndPrepareAmounts(SwapAndMintParams memory params, bool unwrap)
        internal
        returns (uint256 total0, uint256 total1)
    {
```
[115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L115) | [597](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L597) | [653](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L653) | [779](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L779)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit function `uniswapV3FlashCallback` has a cyclomatic complexity of 6
66: function uniswapV3FlashCallback(uint256 fee0, uint256 fee1, bytes calldata callbackData) external {
```
[66](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L66)

```solidity
File: src/utils/Swapper.sol

/// @audit function `_routerSwap` has a cyclomatic complexity of 6
73: function _routerSwap(RouterSwapParams memory params)
        internal
        returns (uint256 amountInDelta, uint256 amountOutDelta)
    {
```
[73](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L73)
</details>

### [N-23] Contract should expose an `interface`

Exposing an interface in a smart contract allows for easier integration by other projects and developers.
Without an interface, there's a risk that other projects will have to develop non-standard variants to interact with your contract.
It's highly recommended to define an interface for clearer and more robust collaboration.

<details>
<summary><i>16 issue instances in 4 files:</i></summary>

```solidity
File: src/automators/AutoExit.sol

100: function execute(ExecuteParams calldata params) external {
218: function configToken(uint256 tokenId, PositionConfig calldata config) external {
```
[100](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L100) | [218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L218)

```solidity
File: src/transformers/AutoCompound.sol

87: function executeWithVault(ExecuteParams calldata params, address vault) external {
101: function execute(ExecuteParams calldata params) external nonReentrant {
200: function withdrawLeftoverBalances(uint256 tokenId, address to) external nonReentrant {
243: function setReward(uint64 _totalRewardX64) external onlyOwner {
248: function _increaseBalance(uint256 tokenId, address token, uint256 amount) internal {
253: function _setBalance(uint256 tokenId, address token, uint256 amount) internal {
265: function _withdrawBalanceInternal(uint256 tokenId, address token, address to, uint256 balance, uint256 amount)
        internal
    {
275: function _checkApprovals(address token0, address token1) internal {
```
[87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L87) | [101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L101) | [200](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L200) | [243](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L243) | [248](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L248) | [253](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L253) | [265](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L265) | [275](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L275)

```solidity
File: src/transformers/AutoRange.sol

97: function executeWithVault(ExecuteParams calldata params, address vault) external {
111: function execute(ExecuteParams calldata params) external {
276: function configToken(uint256 tokenId, address vault, PositionConfig calldata config) external {
300: function _getTickSpacing(uint24 fee) internal view returns (int24) {
```
[97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L97) | [111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L111) | [276](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L276) | [300](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L300)

```solidity
File: src/transformers/LeverageTransformer.sol

40: function leverageUp(LeverageUpParams calldata params) external {
123: function leverageDown(LeverageDownParams calldata params) external {
```
[40](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L40) | [123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L123)
</details>

### [N-24] NatSpec: Function declarations should have descriptions

The Ethereum Natural Specification Format (NatSpec) is an integral part of the Solidity language, serving as a rich, machine-readable, language-agnostic metadata tool.

Documenting all functions, irrespective of their visibility, significantly enhances code readability and auditability.
This is especially vital in complex projects, where clear comprehension of functions, their arguments, and returns is paramount.

Specifically, the `@notice` tag should be used for explanations that anyone should understand, making it a key element in providing a clear understanding of a function's intention.
[More information in Documentation](https://docs.soliditylang.org/en/develop/natspec-format.html)

<details>
<summary><i>16 issue instances in 9 files:</i></summary>

```solidity
File: src/V3Vault.sol

169: constructor(
        string memory name,
        string memory symbol,
        address _asset,
        INonfungiblePositionManager _nonfungiblePositionManager,
        IInterestRateModel _interestRateModel,
        IV3Oracle _oracle,
        IPermit2 _permit2
    ) ERC20(name, symbol) {
384: function deposit(uint256 assets, address receiver, bytes calldata permitData) external override returns (uint256) {
390: function mint(uint256 shares, address receiver, bytes calldata permitData) external override returns (uint256) {
```
[169](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L169) | [384](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L384) | [390](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L390)

```solidity
File: src/V3Oracle.sol

74: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _referenceToken,
        address _chainlinkReferenceToken
    ) {
```
[74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L74)

```solidity
File: src/automators/AutoExit.sol

33: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
218: function configToken(uint256 tokenId, PositionConfig calldata config) external {
```
[33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L33) | [218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L218)

```solidity
File: src/automators/Automator.sol

41: constructor(
        INonfungiblePositionManager npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Swapper(npm, _zeroxRouter, _universalRouter) {
```
[41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L41)

```solidity
File: src/transformers/AutoCompound.sol

37: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, address(0), address(0)) {}
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L37)

```solidity
File: src/transformers/AutoRange.sol

25: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
276: function configToken(uint256 tokenId, address vault, PositionConfig calldata config) external {
```
[25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L25) | [276](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L276)

```solidity
File: src/transformers/LeverageTransformer.sol

13: constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)
        Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter)
    {}
40: function leverageUp(LeverageUpParams calldata params) external {
123: function leverageDown(LeverageDownParams calldata params) external {
```
[13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L13) | [40](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L40) | [123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L123)

```solidity
File: src/utils/FlashloanLiquidator.sol

24: constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)
        Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter)
    {}
67: function uniswapV3FlashCallback(uint256 fee0, uint256 fee1, bytes calldata callbackData) external {
```
[24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L24) | [67](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L67)

```solidity
File: src/utils/Swapper.sol

156: function uniswapV3SwapCallback(int256 amount0Delta, int256 amount1Delta, bytes calldata data) external override {
```
[156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L156)
</details>

### [N-25] Contract uses both `require()`/`revert()` as well as custom errors

The contract uses both `require()/revert()` and `custom errors` for error handling.

It's recommended to use a consistent approach for error handling in a single file.

<details>
<summary><i>8 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {
```
[30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30)

```solidity
File: src/V3Oracle.sol

24: contract V3Oracle is IV3Oracle, Ownable, IErrors {
```
[24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L24)

```solidity
File: src/InterestRateModel.sol

11: contract InterestRateModel is Ownable, IInterestRateModel, IErrors {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L11)

```solidity
File: src/automators/AutoExit.sol

10: contract AutoExit is Automator {
```
[10](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L10)

```solidity
File: src/transformers/AutoCompound.sol

16: contract AutoCompound is Automator, Multicall, ReentrancyGuard {
```
[16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L16)

```solidity
File: src/transformers/AutoRange.sol

11: contract AutoRange is Automator {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L11)

```solidity
File: src/transformers/V3Utils.sol

15: contract V3Utils is Swapper, IERC721Receiver {
```
[15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L15)

```solidity
File: src/utils/FlashloanLiquidator.sol

11: contract FlashloanLiquidator is Swapper, IUniswapV3FlashCallback {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L11)
</details>

### [N-26] Inconsistent spacing in comments

Some lines use // x and some use //x. The instances below point out the usages that don't follow the majority, within each file:

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Oracle.sol

25: uint16 public constant MIN_PRICE_DIFFERENCE = 200; //2%
```
[25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L25)
</details>

### [N-27] Critical system parameter changes should be behind a timelock

It is a good practice to give time for users to react and adjust to critical changes. A timelock provides more guarantees and reduces the level of trust required, thus decreasing risk for users. It also indicates that the project is legitimate (less risk of a malicious owner making a sandwich attack on a user).

<details>
<summary><i>16 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

788: function setTransformer(address transformer, bool active) external onlyOwner {
807: function setLimits(
        uint256 _minLoanSize,
        uint256 _globalLendLimit,
        uint256 _globalDebtLimit,
        uint256 _dailyLendIncreaseLimitMin,
        uint256 _dailyDebtIncreaseLimitMin
    ) external {
837: function setReserveFactor(uint32 _reserveFactorX32) external onlyOwner {
844: function setReserveProtectionFactor(uint32 _reserveProtectionFactorX32) external onlyOwner {
856: function setTokenConfig(address token, uint32 collateralFactorX32, uint32 collateralValueLimitFactorX32)
        external
        onlyOwner
    {
870: function setEmergencyAdmin(address admin) external onlyOwner {
```
[788](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L788) | [807](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L807) | [837](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L837) | [844](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L844) | [856](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L856) | [870](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L870)

```solidity
File: src/V3Oracle.sol

185: function setMaxPoolPriceDifference(uint16 _maxPoolPriceDifference) external onlyOwner {
201: function setTokenConfig(
        address token,
        AggregatorV3Interface feed,
        uint32 maxFeedAge,
        IUniswapV3Pool pool,
        uint32 twapSeconds,
        Mode mode,
        uint16 maxDifference
    ) external onlyOwner {
249: function setOracleMode(address token, Mode mode) external {
265: function setEmergencyAdmin(address admin) external onlyOwner {
```
[185](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L185) | [201](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L201) | [249](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L249) | [265](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L265)

```solidity
File: src/InterestRateModel.sol

82: function setValues(
        uint256 baseRatePerYearX96,
        uint256 multiplierPerYearX96,
        uint256 jumpMultiplierPerYearX96,
        uint256 _kinkX96
    ) public onlyOwner {
```
[82](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L82)

```solidity
File: src/automators/Automator.sol

59: function setWithdrawer(address _withdrawer) public onlyOwner {
69: function setOperator(address _operator, bool _active) public onlyOwner {
79: function setVault(address _vault, bool _active) public onlyOwner {
87: function setTWAPConfig(uint16 _maxTWAPTickDifference, uint32 _TWAPSeconds) public onlyOwner {
```
[59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L59) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L69) | [79](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L79) | [87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L87)

```solidity
File: src/transformers/AutoCompound.sol

243: function setReward(uint64 _totalRewardX64) external onlyOwner {
```
[243](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L243)
</details>

### [N-28] Outdated Solidity Version

The current Solidity version used in the contract is outdated.
Consider using a more recent version for improved features and security.

0.8.4: bytes.concat() instead of abi.encodePacked(,)

0.8.12: string.concat() instead of abi.encodePacked(,)

0.8.13: Ability to use using for with a list of free functions

0.8.14:
    ABI Encoder: When ABI-encoding values from calldata that contain nested arrays, correctly validate the nested array length against calldatasize() in all cases. Override Checker: Allow changing data location for parameters only when overriding external functions.

0.8.15:
    Code Generation: Avoid writing dirty bytes to storage when copying bytes arrays. Yul Optimizer: Keep all memory side-effects of inline assembly blocks.

0.8.16:
    Code Generation: Fix data corruption that affected ABI-encoding of calldata values represented by tuples: structs at any nesting level; argument lists of external functions, events and errors; return value lists of external functions. The 32 leading bytes of the first dynamically-encoded value in the tuple would get zeroed when the last component contained a statically-encoded array.

0.8.17:
    Yul Optimizer: Prevent the incorrect removal of storage writes before calls to Yul functions that conditionally terminate the external EVM call.

<details>
<summary><i>11 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L2)

```solidity
File: src/V3Oracle.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L2)

```solidity
File: src/InterestRateModel.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L2)

```solidity
File: src/automators/AutoExit.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L2)

```solidity
File: src/automators/Automator.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L2)

```solidity
File: src/transformers/AutoCompound.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L2)

```solidity
File: src/transformers/AutoRange.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L2)

```solidity
File: src/transformers/LeverageTransformer.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L2)

```solidity
File: src/transformers/V3Utils.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L2)

```solidity
File: src/utils/FlashloanLiquidator.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L2)

```solidity
File: src/utils/Swapper.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L2)
</details>

### [N-29] Ensure Non-Empty Check for Bytes in Function Parameters

To avoid mistakenly accepting empty bytes as valid parameters, it is advisable to implement checks for non-empty bytes within functions.
This ensures that empty bytes are not treated as valid inputs, preventing potential issues.

<details>
<summary><i>11 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

384: function deposit(uint256 assets, address receiver, bytes calldata permitData) external override returns (uint256) {
390: function mint(uint256 shares, address receiver, bytes calldata permitData) external override returns (uint256) {
410: function createWithPermit(
        uint256 tokenId,
        address owner,
        address recipient,
        uint256 deadline,
        uint8 v,
        bytes32 r,
        bytes32 s
    ) external override {
410: function createWithPermit(
        uint256 tokenId,
        address owner,
        address recipient,
        uint256 deadline,
        uint8 v,
        bytes32 r,
        bytes32 s
    ) external override {
497: function transform(uint256 tokenId, address transformer, bytes calldata data)
        external
        override
        returns (uint256 newTokenId)
    {
661: function repay(uint256 tokenId, uint256 amount, bool isShare, bytes calldata permitData) external override {
```
[384](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L384) | [390](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L390) | [410](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L410) | [410](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L410) | [497](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L497) | [661](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L661)

```solidity
File: src/transformers/V3Utils.sol

98: function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)
        public
        returns (uint256 newTokenId)
    {
98: function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)
        public
        returns (uint256 newTokenId)
    {
356: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
    {
```
[98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L98) | [98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L98) | [356](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L356)

```solidity
File: src/utils/FlashloanLiquidator.sol

66: function uniswapV3FlashCallback(uint256 fee0, uint256 fee1, bytes calldata callbackData) external {
```
[66](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L66)

```solidity
File: src/utils/Swapper.sol

156: function uniswapV3SwapCallback(int256 amount0Delta, int256 amount1Delta, bytes calldata data) external override {
```
[156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L156)
</details>

### [N-30] Adding a `return` statement when the function defines a named return variable, is redundant

Functions in Solidity can use named return variables which can enhance readability and reduce the complexity of the code. When using named return variables, a return statement without any parameters is implicitly added to the end of the function.
This means that explicitly writing return in a function that uses named return variables is redundant.
This redundancy could lead to confusion and misinterpretation of the function's behavior, particularly for developers who are new to the Solidity language or to the codebase.

Moreover, explicitly stating the return statement with the named variables might give the impression that the function could have different exit points or that it might return different values, which is not the case here.
Therefore, removing these redundant return statements can lead to cleaner, more maintainable code with reduced cognitive load for developers.
This helps in understanding the flow and the logic of the function at a quick glance and aids in faster debugging and fewer mistakes.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Oracle.sol

/// @audit - Redundant `return (Q96, chainlinkReferencePriceX96);` when function has named return variables
272: function _getReferenceTokenPriceX96(address token, uint256 cachedChainlinkReferencePriceX96)
        internal
        view
        returns (uint256 priceX96, uint256 chainlinkReferencePriceX96)
    {
```
[272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L272)
</details>

### [N-31] Function/Constructor Argument Names Not in mixedCase

Underscore before of after function argument names is a common convention in Solidity NOT a documentation requirement.

Function arguments should use mixedCase for better readability and consistency with Solidity style guidelines. 
Examples of good practice include: initialSupply, account, recipientAddress, senderAddress, newOwner. 
[More information in Documentation](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#function-argument-names)

Rule exceptions
- Allow constant variable name/symbol/decimals to be lowercase (ERC20).
- Allow `_` at the beginning of the mixedCase match for `private variables` and `unused parameters`.

<details>
<summary><i>16 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

807: function setLimits(
        uint256 _minLoanSize,
        uint256 _globalLendLimit,
        uint256 _globalDebtLimit,
        uint256 _dailyLendIncreaseLimitMin,
        uint256 _dailyDebtIncreaseLimitMin
    ) external {
837: function setReserveFactor(uint32 _reserveFactorX32) external onlyOwner {
844: function setReserveProtectionFactor(uint32 _reserveProtectionFactorX32) external onlyOwner {
168: constructor(
        string memory name,
        string memory symbol,
        address _asset,
        INonfungiblePositionManager _nonfungiblePositionManager,
        IInterestRateModel _interestRateModel,
        IV3Oracle _oracle,
        IPermit2 _permit2
    ) ERC20(name, symbol) {
```
[807](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L807) | [837](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L837) | [844](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L844) | [168](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L168)

```solidity
File: src/V3Oracle.sol

185: function setMaxPoolPriceDifference(uint16 _maxPoolPriceDifference) external onlyOwner {
74: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _referenceToken,
        address _chainlinkReferenceToken
    ) {
```
[185](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L185) | [74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L74)

```solidity
File: src/InterestRateModel.sol

82: function setValues(
        uint256 baseRatePerYearX96,
        uint256 multiplierPerYearX96,
        uint256 jumpMultiplierPerYearX96,
        uint256 _kinkX96
    ) public onlyOwner {
33: constructor(
        uint256 baseRatePerYearX96,
        uint256 multiplierPerYearX96,
        uint256 jumpMultiplierPerYearX96,
        uint256 _kinkX96
    ) {
```
[82](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L82) | [33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L33)

```solidity
File: src/automators/Automator.sol

59: function setWithdrawer(address _withdrawer) public onlyOwner {
69: function setOperator(address _operator, bool _active) public onlyOwner {
79: function setVault(address _vault, bool _active) public onlyOwner {
87: function setTWAPConfig(uint16 _maxTWAPTickDifference, uint32 _TWAPSeconds) public onlyOwner {
40: constructor(
        INonfungiblePositionManager npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Swapper(npm, _zeroxRouter, _universalRouter) {
```
[59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L59) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L69) | [79](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L79) | [87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L87) | [40](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L40)

```solidity
File: src/transformers/AutoCompound.sol

243: function setReward(uint64 _totalRewardX64) external onlyOwner {
```
[243](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L243)

```solidity
File: src/transformers/V3Utils.sol

31: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _zeroxRouter,
        address _universalRouter,
        address _permit2
    ) Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter) {
```
[31](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L31)

```solidity
File: src/utils/Swapper.sol

37: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _zeroxRouter,
        address _universalRouter
    ) {
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L37)
</details>

### [N-32] NatSpec: Function `@return` tag is missing

Natural Specification (NatSpec) comments are crucial for understanding the role of function arguments in your Solidity code.
Including `@return` tag will not only improve your code's readability but also its maintainability by clearly defining each argument's purpose.

[More information in Documentation](https://docs.soliditylang.org/en/develop/natspec-format.html)

<details>
<summary><i>47 issue instances in 6 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit Missed @return `debtExchangeRateX96, lendExchangeRateX96`
195: function vaultInfo()
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
/// @audit Missed @return ``
264: function loanCount(address owner) external view override returns (uint256) {
/// @audit Missed @return ``
271: function loanAtIndex(address owner, uint256 index) external view override returns (uint256) {
/// @audit Missed @return ``
384: function deposit(uint256 assets, address receiver, bytes calldata permitData) external override returns (uint256) {
/// @audit Missed @return ``
390: function mint(uint256 shares, address receiver, bytes calldata permitData) external override returns (uint256) {
/// @audit Missed @return `assets, shares`
877: function _deposit(address receiver, uint256 amount, bool isShare, bytes memory permitData)
        internal
        returns (uint256 assets, uint256 shares)
/// @audit Missed @return `assets, shares`
920: function _withdraw(address receiver, address owner, uint256 amount, bool isShare)
        internal
        returns (uint256 assets, uint256 shares)
/// @audit Missed @return `balance, available, reserves`
1017: function _getAvailableBalance(uint256 debtExchangeRateX96, uint256 lendExchangeRateX96)
        internal
        view
        returns (uint256 balance, uint256 available, uint256 reserves)
/// @audit Missed @return `amount0, amount1`
1032: function _sendPositionValue(
        uint256 tokenId,
        uint256 liquidationValue,
        uint256 fullValue,
        uint256 feeValue,
        address recipient
    ) internal returns (uint256 amount0, uint256 amount1) {
/// @audit Missed @return `liquidationValue, liquidatorCost, reserveCost`
1090: function _calculateLiquidation(uint256 debt, uint256 fullValue, uint256 collateralValue)
        internal
        pure
        returns (uint256 liquidationValue, uint256 liquidatorCost, uint256 reserveCost)
/// @audit Missed @return `missing`
1123: function _handleReserveLiquidation(
        uint256 reserveCost,
        uint256 newDebtExchangeRateX96,
        uint256 newLendExchangeRateX96
    ) internal returns (uint256 missing) {
/// @audit Missed @return ``
1143: function _calculateTokenCollateralFactorX32(uint256 tokenId) internal view returns (uint32) {
/// @audit Missed @return `newDebtExchangeRateX96, newLendExchangeRateX96`
1150: function _updateGlobalInterest()
        internal
        returns (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96)
/// @audit Missed @return `newDebtExchangeRateX96, newLendExchangeRateX96`
1167: function _calculateGlobalInterest()
        internal
        view
        returns (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96)
/// @audit Missed @return `isHealthy, fullValue, collateralValue, feeValue`
1270: function _checkLoanIsHealthy(uint256 tokenId, uint256 debt)
        internal
        view
        returns (bool isHealthy, uint256 fullValue, uint256 collateralValue, uint256 feeValue)
/// @audit Missed @return ``
1281: function _convertToShares(uint256 amount, uint256 exchangeRateX96, Math.Rounding rounding)
        internal
        pure
        returns (uint256)
/// @audit Missed @return ``
1289: function _convertToAssets(uint256 shares, uint256 exchangeRateX96, Math.Rounding rounding)
        internal
        pure
        returns (uint256)
```
[195](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L195) | [264](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L264) | [271](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L271) | [384](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L384) | [390](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L390) | [877](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L877) | [920](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L920) | [1017](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1017) | [1032](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1032) | [1090](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1090) | [1123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1123) | [1143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1143) | [1150](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1150) | [1167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1167) | [1270](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1270) | [1281](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1281) | [1289](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1289)

```solidity
File: src/V3Oracle.sol

/// @audit Missed @return `priceX96, chainlinkReferencePriceX96`
272: function _getReferenceTokenPriceX96(address token, uint256 cachedChainlinkReferencePriceX96)
        internal
        view
        returns (uint256 priceX96, uint256 chainlinkReferencePriceX96)
/// @audit Missed @return ``
329: function _getChainlinkPriceX96(address token) internal view returns (uint256) {
/// @audit Missed @return `poolTWAPPriceX96`
346: function _getTWAPPriceX96(TokenConfig memory feedConfig) internal view returns (uint256 poolTWAPPriceX96) {
/// @audit Missed @return ``
359: function _getReferencePoolPriceX96(IUniswapV3Pool pool, uint32 twapSeconds) internal view returns (uint256) {
/// @audit Missed @return `state`
395: function _initializeState(uint256 tokenId) internal view returns (PositionState memory state) {
/// @audit Missed @return `amount0, amount1, fees0, fees1`
426: function _getAmounts(PositionState memory state)
        internal
        view
        returns (uint256 amount0, uint256 amount1, uint128 fees0, uint128 fees1)
/// @audit Missed @return `fees0, fees1`
445: function _getUncollectedFees(PositionState memory position, int24 tick)
        internal
        view
        returns (uint128 fees0, uint128 fees1)
/// @audit Missed @return `feeGrowthInside0X128, feeGrowthInside1X128`
472: function _getFeeGrowthInside(
        IUniswapV3Pool pool,
        int24 tickLower,
        int24 tickUpper,
        int24 tickCurrent,
        uint256 feeGrowthGlobal0X128,
        uint256 feeGrowthGlobal1X128
    ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {
/// @audit Missed @return ``
499: function _getPool(address tokenA, address tokenB, uint24 fee) internal view returns (IUniswapV3Pool) {
```
[272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L272) | [329](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L329) | [346](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L346) | [359](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L359) | [395](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L395) | [426](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L426) | [445](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L445) | [472](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L472) | [499](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L499)

```solidity
File: src/automators/Automator.sol

/// @audit Missed @return `amountOutMin, currentTick, sqrtPriceX96, priceX96`
139: function _validateSwap(
        bool swap0For1,
        uint256 amountIn,
        IUniswapV3Pool pool,
        uint32 twapPeriod,
        uint16 maxTickDifference,
        uint64 maxPriceDifferenceX64
    ) internal view returns (uint256 amountOutMin, int24 currentTick, uint160 sqrtPriceX96, uint256 priceX96) {
/// @audit Missed @return ``
166: function _hasMaxTWAPTickDifference(IUniswapV3Pool pool, uint32 twapPeriod, int24 currentTick, uint16 maxDifference)
        internal
        view
        returns (bool)
/// @audit Missed @return `, `
180: function _getTWAPTick(IUniswapV3Pool pool, uint32 twapPeriod) internal view returns (int24, bool) {
/// @audit Missed @return `amount0, amount1, feeAmount0, feeAmount1`
193: function _decreaseFullLiquidityAndCollect(
        uint256 tokenId,
        uint128 liquidity,
        uint256 amountRemoveMin0,
        uint256 amountRemoveMin1,
        uint256 deadline
    ) internal returns (uint256 amount0, uint256 amount1, uint256 feeAmount0, uint256 feeAmount1) {
/// @audit Missed @return `owner`
230: function _validateOwner(uint256 tokenId, address vault) internal returns (address owner) {
```
[139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L139) | [166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L166) | [180](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L180) | [193](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L193) | [230](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L230)

```solidity
File: src/transformers/AutoRange.sol

/// @audit Missed @return ``
300: function _getTickSpacing(uint24 fee) internal view returns (int24) {
```
[300](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L300)

```solidity
File: src/transformers/V3Utils.sol

/// @audit Missed @return `newTokenId`
98: function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)
        public
        returns (uint256 newTokenId)
/// @audit Missed @return `newTokenId`
115: function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {
/// @audit Missed @return ``
356: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
/// @audit Missed @return `amountOut`
397: function swap(SwapParams calldata params) external payable returns (uint256 amountOut) {
/// @audit Missed @return `tokenId, liquidity, amount0, amount1`
467: function swapAndMint(SwapAndMintParams calldata params)
        external
        payable
        returns (uint256 tokenId, uint128 liquidity, uint256 amount0, uint256 amount1)
/// @audit Missed @return `liquidity, amount0, amount1`
532: function swapAndIncreaseLiquidity(SwapAndIncreaseLiquidityParams calldata params)
        external
        payable
        returns (uint128 liquidity, uint256 amount0, uint256 amount1)
/// @audit Missed @return `needed0, needed1, neededOther`
653: function _prepareAdd(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther
    ) internal returns (uint256 needed0, uint256 needed1, uint256 neededOther) {
/// @audit Missed @return `tokenId, liquidity, added0, added1`
705: function _swapAndMint(SwapAndMintParams memory params, bool unwrap)
        internal
        returns (uint256 tokenId, uint128 liquidity, uint256 added0, uint256 added1)
/// @audit Missed @return `liquidity, added0, added1`
735: function _swapAndIncrease(SwapAndIncreaseLiquidityParams memory params, IERC20 token0, IERC20 token1, bool unwrap)
        internal
        returns (uint128 liquidity, uint256 added0, uint256 added1)
/// @audit Missed @return `total0, total1`
779: function _swapAndPrepareAmounts(SwapAndMintParams memory params, bool unwrap)
        internal
        returns (uint256 total0, uint256 total1)
/// @audit Missed @return `amount0, amount1`
877: function _decreaseLiquidity(
        uint256 tokenId,
        uint128 liquidity,
        uint256 deadline,
        uint256 token0Min,
        uint256 token1Min
    ) internal returns (uint256 amount0, uint256 amount1) {
/// @audit Missed @return `amount0, amount1`
892: function _collectFees(uint256 tokenId, IERC20 token0, IERC20 token1, uint128 collectAmount0, uint128 collectAmount1)
        internal
        returns (uint256 amount0, uint256 amount1)
```
[98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L98) | [115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L115) | [356](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L356) | [397](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L397) | [467](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L467) | [532](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L532) | [653](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L653) | [705](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L705) | [735](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L735) | [779](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L779) | [877](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L877) | [892](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L892)

```solidity
File: src/utils/Swapper.sol

/// @audit Missed @return `amountInDelta, amountOutDelta`
73: function _routerSwap(RouterSwapParams memory params)
        internal
        returns (uint256 amountInDelta, uint256 amountOutDelta)
/// @audit Missed @return `amountInDelta, amountOutDelta`
132: function _poolSwap(PoolSwapParams memory params) internal returns (uint256 amountInDelta, uint256 amountOutDelta) {
/// @audit Missed @return ``
171: function _getPool(address tokenA, address tokenB, uint24 fee) internal view returns (IUniswapV3Pool) {
```
[73](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L73) | [132](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L132) | [171](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L171)
</details>

### [N-33] State-Altering Functions Should Emit Events

Functions that alter state should emit events to inform users of the state change.
This is crucial for functions that modify the state and don't return a value.
The absence of events in such scenarios could lead to lack of transparency and traceability, undermining the contract's reliability.

<details>
<summary><i>3 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

508: transformedTokenId = tokenId;
1252: dailyLendIncreaseLimitLeft =
                dailyLendIncreaseLimitMin > lendIncreaseLimit ? dailyLendIncreaseLimitMin : lendIncreaseLimit;
1264: dailyDebtIncreaseLimitLeft =
                dailyDebtIncreaseLimitMin > debtIncreaseLimit ? dailyDebtIncreaseLimitMin : debtIncreaseLimit;
```
[508](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L508) | [1252](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1252) | [1264](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1264)
</details>

### [N-34] Contract Doesn't Handle All NFT Types

Supporting both ERC-721 and ERC-1155 standards increases the potential market for your NFT contract.
Consider implementing both standards to reach a broader audience.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit - noERC1155Received() not implemented
429: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
```
[429](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L429)

```solidity
File: src/transformers/V3Utils.sol

/// @audit - noERC1155Received() not implemented
356: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
```
[356](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L356)
</details>

### [N-35] Upgrade `openzeppelin` to the Latest Version - 5.0.0

These contracts import contracts from @openzeppelin/contracts but they are not using the latest version.
For more information, please visit: [OpenZeppelin GitHub Releases](https://github.com/OpenZeppelin/openzeppelin-contracts/releases)
It is recommended to always use the latest version to take advantage of updates and security fixes.

<details>
<summary><i>21 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

12: import "@openzeppelin/contracts/utils/math/Math.sol";
13: import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
14: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
15: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
16: import "@openzeppelin/contracts/access/Ownable.sol";
17: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
18: import "@openzeppelin/contracts/utils/Multicall.sol";
```
[12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L12) | [13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L13) | [14](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L14) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L15) | [16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L16) | [17](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L17) | [18](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L18)

```solidity
File: src/V3Oracle.sol

14: import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";
15: import "@openzeppelin/contracts/access/Ownable.sol";
```
[14](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L14) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L15)

```solidity
File: src/InterestRateModel.sol

4: import "@openzeppelin/contracts/access/Ownable.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L4)

```solidity
File: src/automators/Automator.sol

4: import "@openzeppelin/contracts/access/Ownable.sol";
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
6: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L4) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L5) | [6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L6)

```solidity
File: src/transformers/AutoCompound.sol

4: import "@openzeppelin/contracts/security/ReentrancyGuard.sol";
5: import "@openzeppelin/contracts/utils/Multicall.sol";
6: import "@openzeppelin/contracts/utils/math/SafeMath.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L4) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L5) | [6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L6)

```solidity
File: src/transformers/LeverageTransformer.sol

4: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L4) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L5)

```solidity
File: src/transformers/V3Utils.sol

4: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
5: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L4) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L5)

```solidity
File: src/utils/Swapper.sol

4: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L4)
</details>

### [N-36] Duplicated `require()`/`revert()` checks should be refactored to a modifier or function

Duplicated require() or revert() checks should be refactored to a modifier or function.
This helps in maintaining a clean and organized codebase and saves deployment costs.

<details>
<summary><i>10 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

615: if (transformedTokenId > 0) {
            revert TransformNotAllowed();
687: if (transformedTokenId > 0) {
            revert TransformNotAllowed();
```
[615](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L615) | [687](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L687)

```solidity
File: src/V3Oracle.sol

211: if (mode == Mode.NOT_SET) {
            revert InvalidConfig();
255: if (mode == Mode.NOT_SET) {
            revert InvalidConfig();
```
[211](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L211) | [255](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L255)

```solidity
File: src/automators/Automator.sol

105: if (msg.sender != withdrawer) {
            revert Unauthorized();
124: if (msg.sender != withdrawer) {
            revert Unauthorized();
131: if (!sent) {
                revert EtherSendFailed();
222: if (!sent) {
                revert EtherSendFailed();
```
[105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L105) | [124](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L124) | [131](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L131) | [222](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L222)

```solidity
File: src/utils/Swapper.sol

111: if (amountOutDelta < params.amountOutMin) {
                revert SlippageError();
149: if (amountOutDelta < params.amountOutMin) {
                revert SlippageError();
```
[111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L111) | [149](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L149)
</details>

### [N-37] Non-specific Imports

The current form of relative path import is not recommended for use because it can unpredictably pollute the namespace.
Instead, the Solidity docs recommend specifying imported symbols explicitly.
https://docs.soliditylang.org/en/v0.8.15/layout-of-source-files.html#importing-other-source-files

Example:
import {OwnableUpgradeable} from "openzeppelin-contracts-upgradeable/contracts/access/OwnableUpgradeable.sol";
import {SafeTransferLib} from "solmate/utils/SafeTransferLib.sol";

<details>
<summary><i>70 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

4: import "v3-core/interfaces/IUniswapV3Factory.sol";
5: import "v3-core/interfaces/IUniswapV3Pool.sol";
6: import "v3-core/libraries/TickMath.sol";
7: import "v3-core/libraries/FixedPoint128.sol";
9: import "v3-periphery/libraries/LiquidityAmounts.sol";
10: import "v3-periphery/interfaces/INonfungiblePositionManager.sol";
12: import "@openzeppelin/contracts/utils/math/Math.sol";
13: import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
14: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
15: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
16: import "@openzeppelin/contracts/access/Ownable.sol";
17: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
18: import "@openzeppelin/contracts/utils/Multicall.sol";
20: import "permit2/interfaces/IPermit2.sol";
22: import "./interfaces/IVault.sol";
23: import "./interfaces/IV3Oracle.sol";
24: import "./interfaces/IInterestRateModel.sol";
25: import "./interfaces/IErrors.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L4) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L5) | [6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L6) | [7](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L7) | [9](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L9) | [10](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L10) | [12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L12) | [13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L13) | [14](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L14) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L15) | [16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L16) | [17](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L17) | [18](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L18) | [20](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L20) | [22](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L22) | [23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L23) | [24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L24) | [25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L25)

```solidity
File: src/V3Oracle.sol

4: import "v3-core/interfaces/IUniswapV3Factory.sol";
5: import "v3-core/interfaces/IUniswapV3Pool.sol";
7: import "v3-core/libraries/TickMath.sol";
9: import "v3-periphery/libraries/PoolAddress.sol";
10: import "v3-periphery/libraries/LiquidityAmounts.sol";
12: import "v3-periphery/interfaces/INonfungiblePositionManager.sol";
14: import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";
15: import "@openzeppelin/contracts/access/Ownable.sol";
17: import "../lib/AggregatorV3Interface.sol";
19: import "./interfaces/IV3Oracle.sol";
20: import "./interfaces/IErrors.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L4) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L5) | [7](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L7) | [9](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L9) | [10](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L10) | [12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L12) | [14](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L14) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L15) | [17](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L17) | [19](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L19) | [20](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L20)

```solidity
File: src/InterestRateModel.sol

4: import "@openzeppelin/contracts/access/Ownable.sol";
6: import "./interfaces/IInterestRateModel.sol";
7: import "./interfaces/IErrors.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L4) | [6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L6) | [7](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L7)

```solidity
File: src/automators/AutoExit.sol

4: import "./Automator.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L4)

```solidity
File: src/automators/Automator.sol

4: import "@openzeppelin/contracts/access/Ownable.sol";
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
6: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
8: import "v3-core/interfaces/IUniswapV3Factory.sol";
9: import "v3-core/interfaces/IUniswapV3Pool.sol";
10: import "v3-core/libraries/TickMath.sol";
11: import "v3-core/libraries/FullMath.sol";
13: import "v3-periphery/interfaces/INonfungiblePositionManager.sol";
15: import "../../lib/IWETH9.sol";
16: import "../utils/Swapper.sol";
17: import "../interfaces/IVault.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L4) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L5) | [6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L6) | [8](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L8) | [9](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L9) | [10](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L10) | [11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L11) | [13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L13) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L15) | [16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L16) | [17](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L17)

```solidity
File: src/transformers/AutoCompound.sol

4: import "@openzeppelin/contracts/security/ReentrancyGuard.sol";
5: import "@openzeppelin/contracts/utils/Multicall.sol";
6: import "@openzeppelin/contracts/utils/math/SafeMath.sol";
8: import "v3-periphery/interfaces/INonfungiblePositionManager.sol";
10: import "../automators/Automator.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L4) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L5) | [6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L6) | [8](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L8) | [10](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L10)

```solidity
File: src/transformers/AutoRange.sol

4: import "../automators/Automator.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L4)

```solidity
File: src/transformers/LeverageTransformer.sol

4: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
7: import "../utils/Swapper.sol";
8: import "../interfaces/IVault.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L4) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L5) | [7](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L7) | [8](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L8)

```solidity
File: src/transformers/V3Utils.sol

4: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
5: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
7: import "permit2/interfaces/IPermit2.sol";
9: import "../utils/Swapper.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L4) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L5) | [7](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L7) | [9](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L9)

```solidity
File: src/utils/FlashloanLiquidator.sol

4: import "v3-core/interfaces/IUniswapV3Pool.sol";
5: import "v3-core/interfaces/callback/IUniswapV3FlashCallback.sol";
7: import "../interfaces/IVault.sol";
8: import "./Swapper.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L4) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L5) | [7](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L7) | [8](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L8)

```solidity
File: src/utils/Swapper.sol

4: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
6: import "v3-core/interfaces/callback/IUniswapV3SwapCallback.sol";
7: import "v3-core/interfaces/IUniswapV3Pool.sol";
8: import "v3-core/libraries/TickMath.sol";
10: import "v3-periphery/interfaces/INonfungiblePositionManager.sol";
12: import "../../lib/IWETH9.sol";
13: import "../../lib/IUniversalRouter.sol";
14: import "../interfaces/IErrors.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L4) | [6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L6) | [7](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L7) | [8](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L8) | [10](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L10) | [12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L12) | [13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L13) | [14](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L14)
</details>

### [N-38] Event is not properly `indexed`

Index event fields make the field more quickly accessible to off-chain tools that parse events.
This is especially useful when it comes to filtering based on an address. However, note that each index field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields).
Where applicable, each event should use three indexed fields if there are three or more fields, and gas usage is not particularly of concern for the events in question.
If there are fewer than three applicable fields, all of the applicable fields should be indexed.

<details>
<summary><i>38 issue instances in 9 files:</i></summary>

```solidity
File: src/V3Vault.sol

68: event ApprovedTransform(uint256 indexed tokenId, address owner, address target, bool isActive);
70: event Add(uint256 indexed tokenId, address owner, uint256 oldTokenId); // when a token is added replacing another token - oldTokenId > 0
71: event Remove(uint256 indexed tokenId, address recipient);
73: event ExchangeRateUpdate(uint256 debtExchangeRateX96, uint256 lendExchangeRateX96);
75: event WithdrawCollateral(
        uint256 indexed tokenId, address owner, address recipient, uint128 liquidity, uint256 amount0, uint256 amount1
    );
78: event Borrow(uint256 indexed tokenId, address owner, uint256 assets, uint256 shares);
79: event Repay(uint256 indexed tokenId, address repayer, address owner, uint256 assets, uint256 shares);
80: event Liquidate(
        uint256 indexed tokenId,
        address liquidator,
        address owner,
        uint256 value,
        uint256 cost,
        uint256 amount0,
        uint256 amount1,
        uint256 reserve,
        uint256 missing
    ); // shows exactly how liquidation amounts were divided
93: event WithdrawReserves(uint256 amount, address receiver);
94: event SetTransformer(address transformer, bool active);
95: event SetLimits(
        uint256 minLoanSize,
        uint256 globalLendLimit,
        uint256 globalDebtLimit,
        uint256 dailyLendIncreaseLimitMin,
        uint256 dailyDebtIncreaseLimitMin
    );
102: event SetReserveFactor(uint32 reserveFactorX32);
103: event SetReserveProtectionFactor(uint32 reserveProtectionFactorX32);
104: event SetTokenConfig(address token, uint32 collateralFactorX32, uint32 collateralValueLimitFactorX32);
106: event SetEmergencyAdmin(address emergencyAdmin);
```
[68](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L68) | [70](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L70) | [71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L71) | [73](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L73) | [75](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L75) | [78](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L78) | [79](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L79) | [80](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L80) | [93](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L93) | [94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L94) | [95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L95) | [102](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L102) | [103](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L103) | [104](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L104) | [106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L106)

```solidity
File: src/V3Oracle.sol

30: event TokenConfigUpdated(address indexed token, TokenConfig config);
31: event OracleModeUpdated(address indexed token, Mode mode);
32: event SetMaxPoolPriceDifference(uint16 maxPoolPriceDifference);
33: event SetEmergencyAdmin(address emergencyAdmin);
```
[30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L30) | [31](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L31) | [32](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L32) | [33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L33)

```solidity
File: src/InterestRateModel.sol

18: event SetValues(
        uint256 baseRatePerYearX96, uint256 multiplierPerYearX96, uint256 jumpMultiplierPerYearX96, uint256 kinkX96
    );
```
[18](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L18)

```solidity
File: src/automators/AutoExit.sol

11: event Executed(
        uint256 indexed tokenId,
        address account,
        bool isSwap,
        uint256 amountReturned0,
        uint256 amountReturned1,
        address token0,
        address token1
    );
20: event PositionConfigured(
        uint256 indexed tokenId,
        bool isActive,
        bool token0Swap,
        bool token1Swap,
        int24 token0TriggerTick,
        int24 token1TriggerTick,
        uint64 token0SlippageX64,
        uint64 token1SlippageX64,
        bool onlyFees,
        uint64 maxRewardX64
    );
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L11) | [20](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L20)

```solidity
File: src/automators/Automator.sol

27: event OperatorChanged(address newOperator, bool active);
28: event VaultChanged(address newVault, bool active);
30: event WithdrawerChanged(address newWithdrawer);
31: event TWAPConfigChanged(uint32 TWAPSeconds, uint16 maxTWAPTickDifference);
```
[27](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L27) | [28](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L28) | [30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L30) | [31](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L31)

```solidity
File: src/transformers/AutoCompound.sol

18: event AutoCompounded(
        address account,
        uint256 tokenId,
        uint256 amountAdded0,
        uint256 amountAdded1,
        uint256 reward0,
        uint256 reward1,
        address token0,
        address token1
    );
30: event RewardUpdated(address account, uint64 totalRewardX64);
33: event BalanceAdded(uint256 tokenId, address token, uint256 amount);
34: event BalanceRemoved(uint256 tokenId, address token, uint256 amount);
35: event BalanceWithdrawn(uint256 tokenId, address token, address to, uint256 amount);
```
[18](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L18) | [30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L30) | [33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L33) | [34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L34) | [35](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L35)

```solidity
File: src/transformers/AutoRange.sol

13: event PositionConfigured(
        uint256 indexed tokenId,
        int32 lowerTickLimit,
        int32 upperTickLimit,
        int32 lowerTickDelta,
        int32 upperTickDelta,
        uint64 token0SlippageX64,
        uint64 token1SlippageX64,
        bool onlyFees,
        uint64 maxRewardX64
    );
```
[13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L13)

```solidity
File: src/transformers/V3Utils.sol

22: event CompoundFees(uint256 indexed tokenId, uint128 liquidity, uint256 amount0, uint256 amount1);
23: event ChangeRange(uint256 indexed tokenId, uint256 newTokenId);
24: event WithdrawAndCollectAndSwap(uint256 indexed tokenId, address token, uint256 amount);
25: event SwapAndMint(uint256 indexed tokenId, uint128 liquidity, uint256 amount0, uint256 amount1);
26: event SwapAndIncreaseLiquidity(uint256 indexed tokenId, uint128 liquidity, uint256 amount0, uint256 amount1);
```
[22](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L22) | [23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L23) | [24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L24) | [25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L25) | [26](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L26)

```solidity
File: src/utils/Swapper.sol

18: event Swap(address indexed tokenIn, address indexed tokenOut, uint256 amountIn, uint256 amountOut);
```
[18](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L18)
</details>

### [N-39] Consider Using `safePermit()` Instead of `permit()`

The use of the `permit()` function can be risky as observed in the Anyswap hack where the function didn't really exist, but the fallback function didn't revert the transaction. In particular, tokens like WETH, BNB, and HEX exhibit a 'phantom permit'—they accept any call to `permit()` without reverting, posing a security risk.

To mitigate this risk, consider using `safePermit()` which ensures that the `permit` function call actually goes through as intended.

For more details, see [Phantom Functions and the Billion Dollar No-op](https://media.dedaub.com/phantom-functions-and-the-billion-dollar-no-op-c56f062ae49f#ef54).

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

423: nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);
```
[423](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L423)

```solidity
File: src/transformers/V3Utils.sol

106: nonfungiblePositionManager.permit(address(this), tokenId, instructions.deadline, v, r, s);
```
[106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L106)
</details>

### [N-40] Consider Adding Emergency-Stop Functionality

Smart contracts that hold significant value, interact with external contracts, or have complex logic should include an emergency-stop mechanism for added security. This allows pausing certain contract functionalities in case of emergencies, mitigating potential damages.

This contract seems to lack such a mechanism. Implementing an emergency stop can enhance contract security and reliability.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

1: No emergency stop pattern found
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1)
</details>

### [N-41] NatSpec: Public State variable declarations should have descriptions

State variables should ideally be accompanied by NatSpec comments to describe their purpose and usage. 
This aids developers in understanding the function and purpose of each variable, especially in large and complex contracts.
Consider adding `@dev` or `@notice` descriptions to your state variables.

<details>
<summary><i>55 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

36: uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%
38: uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
39: uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%
41: uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%
43: uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%
44: uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%
115: mapping(address => TokenConfig) public tokenConfigs;
118: uint32 public reserveFactorX32 = 0;
121: uint32 public reserveProtectionFactorX32 = MIN_RESERVE_PROTECTION_FACTOR_X32;
124: uint256 public debtSharesTotal = 0;
127: uint256 public lastExchangeRateUpdate = 0;
128: uint256 public lastDebtExchangeRateX96 = Q96;
129: uint256 public lastLendExchangeRateX96 = Q96;
131: uint256 public globalDebtLimit = 0;
132: uint256 public globalLendLimit = 0;
135: uint256 public minLoanSize = 0;
138: uint256 public dailyLendIncreaseLimitMin = 0;
139: uint256 public dailyLendIncreaseLimitLeft = 0;
140: uint256 public dailyLendIncreaseLimitLastReset = 0;
143: uint256 public dailyDebtIncreaseLimitMin = 0;
144: uint256 public dailyDebtIncreaseLimitLeft = 0;
145: uint256 public dailyDebtIncreaseLimitLastReset = 0;
154: mapping(uint256 => Loan) public loans; // tokenID -> loan mapping
163: mapping(address => bool) public transformerAllowList; // contracts allowed to transform positions (selected audited contracts e.g. V3Utils)
164: mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; // owners permissions for other addresses to call transform on owners behalf (e.g. AutoRange contract)
167: address public emergencyAdmin;
```
[36](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L36) | [38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L38) | [39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L39) | [41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L41) | [43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L43) | [44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L44) | [115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L115) | [118](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L118) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L121) | [124](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L124) | [127](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L127) | [128](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L128) | [129](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L129) | [131](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L131) | [132](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L132) | [135](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L135) | [138](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L138) | [139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L139) | [140](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L140) | [143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L143) | [144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L144) | [145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L145) | [154](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L154) | [163](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L163) | [164](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L164) | [167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L167)

```solidity
File: src/V3Oracle.sol

25: uint16 public constant MIN_PRICE_DIFFERENCE = 200; //2%
56: mapping(address => TokenConfig) public feedConfigs;
58: address public immutable factory;
59: INonfungiblePositionManager public immutable nonfungiblePositionManager;
62: address public immutable referenceToken;
63: uint8 public immutable referenceTokenDecimals;
65: uint16 public maxPoolPriceDifference = MIN_PRICE_DIFFERENCE; // max price difference between oracle derived price and pool price x10000
68: address public immutable chainlinkReferenceToken;
71: address public emergencyAdmin;
```
[25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L25) | [56](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L56) | [58](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L58) | [59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L59) | [62](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L62) | [63](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L63) | [65](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L65) | [68](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L68) | [71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L71)

```solidity
File: src/InterestRateModel.sol

13: uint256 public constant YEAR_SECS = 31557600; // taking into account leap years
15: uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10; // 10%
16: uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%
23: uint256 public multiplierPerSecondX96;
24: uint256 public baseRatePerSecondX96;
25: uint256 public jumpMultiplierPerSecondX96;
26: uint256 public kinkX96;
```
[13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L13) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L15) | [16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L16) | [23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L23) | [24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L24) | [25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L25) | [26](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L26)

```solidity
File: src/automators/AutoExit.sol

60: mapping(uint256 => PositionConfig) public positionConfigs;
```
[60](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L60)

```solidity
File: src/automators/Automator.sol

23: uint32 public constant MIN_TWAP_SECONDS = 60; // 1 minute
24: uint32 public constant MAX_TWAP_TICK_DIFFERENCE = 200; // 2%
34: mapping(address => bool) public operators;
35: mapping(address => bool) public vaults;
37: address public withdrawer;
38: uint32 public TWAPSeconds;
39: uint16 public maxTWAPTickDifference;
```
[23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L23) | [24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L24) | [34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L34) | [35](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L35) | [37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L37) | [38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L38) | [39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L39)

```solidity
File: src/transformers/AutoCompound.sol

45: mapping(uint256 => mapping(address => uint256)) public positionBalances;
47: uint64 public constant MAX_REWARD_X64 = uint64(Q64 / 50); // 2%
48: uint64 public totalRewardX64 = MAX_REWARD_X64; // 2%
```
[45](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L45) | [47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L47) | [48](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L48)

```solidity
File: src/transformers/AutoRange.sol

50: mapping(uint256 => PositionConfig) public positionConfigs;
```
[50](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L50)

```solidity
File: src/utils/Swapper.sol

23: address public immutable factory;
```
[23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L23)
</details>

### [N-42] Consider adding a block/deny-list

While adding a block or deny-list may increase the level of centralization in the contract, it provides an additional layer of security by preventing hackers from using stolen tokens or carrying out other malicious activities.

Although it's a trade-off, a block or deny-list can help improve the overall security posture of the contract.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/utils/FlashloanLiquidator.sol

11: contract FlashloanLiquidator is Swapper, IUniswapV3FlashCallback {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L11)
</details>

### [N-43] Non-uppercase/Constant-case Naming for `immutable` Variables

For better readability and adherence to common naming conventions, variable names declared as immutable should be written in all uppercase letters.

<details>
<summary><i>18 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

47: INonfungiblePositionManager public immutable nonfungiblePositionManager;
50: IUniswapV3Factory public immutable factory;
53: IInterestRateModel public immutable interestRateModel;
56: IV3Oracle public immutable oracle;
59: IPermit2 public immutable permit2;
62: address public immutable override asset;
65: uint8 private immutable assetDecimals;
```
[47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L47) | [50](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L50) | [53](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L53) | [56](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L56) | [59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L59) | [62](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L62) | [65](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L65)

```solidity
File: src/V3Oracle.sol

58: address public immutable factory;
59: INonfungiblePositionManager public immutable nonfungiblePositionManager;
62: address public immutable referenceToken;
63: uint8 public immutable referenceTokenDecimals;
68: address public immutable chainlinkReferenceToken;
```
[58](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L58) | [59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L59) | [62](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L62) | [63](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L63) | [68](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L68)

```solidity
File: src/transformers/V3Utils.sol

19: IPermit2 public immutable permit2;
```
[19](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L19)

```solidity
File: src/utils/Swapper.sol

21: IWETH9 public immutable weth;
23: address public immutable factory;
26: INonfungiblePositionManager public immutable nonfungiblePositionManager;
29: address public immutable zeroxRouter;
32: address public immutable universalRouter;
```
[21](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L21) | [23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L23) | [26](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L26) | [29](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L29) | [32](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L32)
</details>

### [N-44] Not using the named return variables anywhere in the function is confusing

Declaring a named return variable but returning a different value within the function is an inconsistent use of named return variables.
This practice can lead to confusion and misinterpretation of the function's intended behavior, as it contradicts the purpose of declaring named return variables, which is to enhance readability and reduce complexity in the code.

This inconsistency might signal an error in the function logic where the declared return variable is not being used as intended.
It is recommended to revisit the function's logic to ensure that the named return variables are being utilized correctly, or to adjust the return statements to reflect the actual values being returned, fostering better clarity and coherence in the code.

<details>
<summary><i>5 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit - `return tokenOwner[tokenId];` statement in functions but `owner` are declared
258: function ownerOf(uint256 tokenId) external view override returns (address owner) {
/// @audit - `return _convertToShares(assets, lendExchangeRateX96, Math.Rounding.Down);` statement in functions but `shares` are declared
289: function convertToShares(uint256 assets) external view override returns (uint256 shares) {
/// @audit - `return _convertToAssets(shares, lendExchangeRateX96, Math.Rounding.Down);` statement in functions but `assets` are declared
295: function convertToAssets(uint256 shares) external view override returns (uint256 assets) {
/// @audit - `return tokenId;` statement in functions but `newTokenId` are declared
497: function transform(uint256 tokenId, address transformer, bytes calldata data)
        external
        override
        returns (uint256 newTokenId)
    {
```
[258](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L258) | [289](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L289) | [295](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L295) | [497](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L497)

```solidity
File: src/transformers/V3Utils.sol

/// @audit - `return execute(tokenId, instructions);` statement in functions but `newTokenId` are declared
98: function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)
        public
        returns (uint256 newTokenId)
    {
```
[98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L98)
</details>

### [N-45] Function Names Not in mixedCase

Function names should use mixedCase for better readability and consistency with Solidity style guidelines. 
Examples of good practice include: getBalance, transfer, verifyOwner, addMember, changeOwner. 
[More information in Documentation](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#function-names)

<details>
<summary><i>5 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Oracle.sol

346: function _getTWAPPriceX96(TokenConfig memory feedConfig) internal view returns (uint256 poolTWAPPriceX96) {
```
[346](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L346)

```solidity
File: src/automators/Automator.sol

87: function setTWAPConfig(uint16 _maxTWAPTickDifference, uint32 _TWAPSeconds) public onlyOwner {
123: function withdrawETH(address to) external {
166: function _hasMaxTWAPTickDifference(IUniswapV3Pool pool, uint32 twapPeriod, int24 currentTick, uint16 maxDifference)
180: function _getTWAPTick(IUniswapV3Pool pool, uint32 twapPeriod) internal view returns (int24, bool) {
```
[87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L87) | [123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L123) | [166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L166) | [180](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L180)
</details>

### [N-46] Insufficient Comments in Complex Functions

Complex functions spanning multiple lines should have more comments to better explain the purpose of each logic step.
Proper commenting can greatly improve the readability and maintainability of the codebase. Consider adding explicit comments
to provide insights into the function's operation.

<details>
<summary><i>15 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit function with 33 lines has only 4 comment lines
550: function borrow(uint256 tokenId, uint256 assets) external override {
/// @audit function with 52 lines has only 5 comment lines
685: function liquidate(LiquidateParams calldata params) external override returns (uint256 amount0, uint256 amount1) {
/// @audit function with 42 lines has only 5 comment lines
953: function _repay(uint256 tokenId, uint256 amount, bool isShare, bytes memory permitData) internal {
```
[550](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L550) | [685](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L685) | [953](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L953)

```solidity
File: src/V3Oracle.sol

/// @audit function with 40 lines has only 0 comment lines
272: function _getReferenceTokenPriceX96(address token, uint256 cachedChainlinkReferencePriceX96)
        internal
        view
        returns (uint256 priceX96, uint256 chainlinkReferencePriceX96)
    {
```
[272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L272)

```solidity
File: src/automators/AutoExit.sol

/// @audit function with 83 lines has only 11 comment lines
100: function execute(ExecuteParams calldata params) external {
```
[100](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L100)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit function with 64 lines has only 13 comment lines
101: function execute(ExecuteParams calldata params) external nonReentrant {
```
[101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L101)

```solidity
File: src/transformers/AutoRange.sol

/// @audit function with 119 lines has only 18 comment lines
111: function execute(ExecuteParams calldata params) external {
```
[111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L111)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit function with 46 lines has only 1 comment lines
40: function leverageUp(LeverageUpParams calldata params) external {
/// @audit function with 43 lines has only 1 comment lines
123: function leverageDown(LeverageDownParams calldata params) external {
```
[40](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L40) | [123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L123)

```solidity
File: src/transformers/V3Utils.sol

/// @audit function with 227 lines has only 4 comment lines
115: function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {
/// @audit function with 33 lines has only 6 comment lines
597: function _prepareAddPermit2(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther,
        IPermit2.PermitBatchTransferFrom memory permit,
        bytes memory signature
    ) internal {
/// @audit function with 36 lines has only 2 comment lines
653: function _prepareAdd(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther
    ) internal returns (uint256 needed0, uint256 needed1, uint256 neededOther) {
/// @audit function with 33 lines has only 0 comment lines
735: function _swapAndIncrease(SwapAndIncreaseLiquidityParams memory params, IERC20 token0, IERC20 token1, bool unwrap)
        internal
        returns (uint128 liquidity, uint256 added0, uint256 added1)
    {
/// @audit function with 51 lines has only 1 comment lines
779: function _swapAndPrepareAmounts(SwapAndMintParams memory params, bool unwrap)
        internal
        returns (uint256 total0, uint256 total1)
    {
```
[115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L115) | [597](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L597) | [653](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L653) | [735](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L735) | [779](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L779)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit function with 32 lines has only 4 comment lines
66: function uniswapV3FlashCallback(uint256 fee0, uint256 fee1, bytes calldata callbackData) external {
```
[66](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L66)
</details>

### [N-47] Common functions should be refactored to a common base contract

The codebase contains several functions with the same implementations across multiple files.
To enhance maintainability and reduce potential errors, consider refactoring these common functions into a shared base contract.
This practice promotes code reuse and easier future upgrades.

<details>
<summary><i>8 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

289: function convertToShares(uint256 assets) external view override returns (uint256 shares) {
        (, uint256 lendExchangeRateX96) = _calculateGlobalInterest();
        return _convertToShares(assets, lendExchangeRateX96, Math.Rounding.Down);
    }
334: function previewDeposit(uint256 assets) public view override returns (uint256) {
        (, uint256 lendExchangeRateX96) = _calculateGlobalInterest();
        return _convertToShares(assets, lendExchangeRateX96, Math.Rounding.Down);
    }
295: function convertToAssets(uint256 shares) external view override returns (uint256 assets) {
        (, uint256 lendExchangeRateX96) = _calculateGlobalInterest();
        return _convertToAssets(shares, lendExchangeRateX96, Math.Rounding.Down);
    }
352: function previewRedeem(uint256 shares) public view override returns (uint256) {
        (, uint256 lendExchangeRateX96) = _calculateGlobalInterest();
        return _convertToAssets(shares, lendExchangeRateX96, Math.Rounding.Down);
    }
870: function setEmergencyAdmin(address admin) external onlyOwner {
        emergencyAdmin = admin;
        emit SetEmergencyAdmin(admin);
    }
```
[289](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L289) | [334](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L334) | [295](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L295) | [352](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L352) | [870](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L870)

```solidity
File: src/V3Oracle.sol

265: function setEmergencyAdmin(address admin) external onlyOwner {
        emergencyAdmin = admin;
        emit SetEmergencyAdmin(admin);
    }
```
[265](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L265)

```solidity
File: src/automators/Automator.sol

218: function _transferToken(address to, IERC20 token, uint256 amount, bool unwrap) internal {
        if (address(weth) == address(token) && unwrap) {
            weth.withdraw(amount);
            (bool sent,) = to.call{value: amount}("");
            if (!sent) {
                revert EtherSendFailed();
            }
        } else {
            SafeERC20.safeTransfer(token, to, amount);
        }
    }
```
[218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L218)

```solidity
File: src/transformers/V3Utils.sol

864: function _transferToken(address to, IERC20 token, uint256 amount, bool unwrap) internal {
        if (address(weth) == address(token) && unwrap) {
            weth.withdraw(amount);
            (bool sent,) = to.call{value: amount}("");
            if (!sent) {
                revert EtherSendFailed();
            }
        } else {
            SafeERC20.safeTransfer(token, to, amount);
        }
    }
```
[864](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L864)
</details>

### [N-48] NatSpec: Non-public state variable declarations should use `@dev` tags

Non-public state variables in smart contracts often have specialized purposes that may not be immediately clear to developers who did not write the original code.
Adding comments to explain the role and functionality of these variables can greatly aid in code readability and maintainability.
This is especially beneficial for future code reviews and audits.

<details>
<summary><i>11 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

33: uint256 private constant Q32 = 2 ** 32;
34: uint256 private constant Q96 = 2 ** 96;
157: mapping(address => uint256[]) private ownedTokens; // Mapping from owner address to list of owned token IDs
158: mapping(uint256 => uint256) private ownedTokensIndex; // Mapping from token ID to index of the owner tokens list (for removal without loop)
159: mapping(uint256 => address) private tokenOwner; // Mapping from token ID to owner
161: uint256 private transformedTokenId = 0; // transient storage (when available in dencun)
```
[33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L33) | [34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L34) | [157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L157) | [158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L158) | [159](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L159) | [161](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L161)

```solidity
File: src/V3Oracle.sol

27: uint256 private constant Q96 = 2 ** 96;
28: uint256 private constant Q128 = 2 ** 128;
```
[27](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L27) | [28](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L28)

```solidity
File: src/InterestRateModel.sol

12: uint256 private constant Q96 = 2 ** 96;
```
[12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L12)

```solidity
File: src/automators/Automator.sol

20: uint256 internal constant Q64 = 2 ** 64;
21: uint256 internal constant Q96 = 2 ** 96;
```
[20](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L20) | [21](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L21)
</details>

### [N-49] `constant`s should be defined rather than using magic numbers

Magic numbers are hardcoded numerical values used directly in the code, making it harder to read and maintain.
Consider using constants instead of magic numbers.

<details>
<summary><i>8 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Oracle.sol

/// @audit 10000
144: ? (priceX96 - verifyPriceX96) * 10000 / priceX96
/// @audit 10000
145: : (verifyPriceX96 - priceX96) * 10000 / verifyPriceX96;
```
[144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L144) | [145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L145)

```solidity
File: src/transformers/AutoRange.sol

/// @audit 10000
301: if (fee == 10000) {
/// @audit 200
302: return 200;
/// @audit 3000
303: } else if (fee == 3000) {
/// @audit 60
304: return 60;
/// @audit 500
305: } else if (fee == 500) {
/// @audit 10
306: return 10;
```
[301](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L301) | [302](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L302) | [303](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L303) | [304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L304) | [305](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L305) | [306](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L306)
</details>

### [N-50] Consider moving `msg.sender` checks to a common authorization `modifier`

Functions that are only allowed to be called by a specific actor should use a modifier to check if the caller is the specified actor (e.g., owner, specific role, etc.).
Using `require` to check `msg.sender` in the function body is less efficient and less clear.

Consider refactoring these `require` statements into a modifier for better readability, organization, and gas efficiency.

<details>
<summary><i>24 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

419: if (msg.sender != owner) {
435: if (msg.sender != address(nonfungiblePositionManager) || from == address(this)) {
484: if (tokenOwner[tokenId] != msg.sender) {
515: if (loanOwner != msg.sender && !transformApprovals[loanOwner][tokenId][msg.sender]) {
561: if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {
620: if (owner != msg.sender) {
814: if (msg.sender != emergencyAdmin && msg.sender != owner()) {
935: if (msg.sender != owner) {
```
[419](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L419) | [435](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L435) | [484](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L484) | [515](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L515) | [561](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L561) | [620](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L620) | [814](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L814) | [935](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L935)

```solidity
File: src/V3Oracle.sol

250: if (msg.sender != emergencyAdmin && msg.sender != owner()) {
```
[250](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L250)

```solidity
File: src/automators/AutoExit.sol

101: if (!operators[msg.sender]) {
220: if (owner != msg.sender) {
```
[101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L101) | [220](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L220)

```solidity
File: src/automators/Automator.sol

105: if (msg.sender != withdrawer) {
124: if (msg.sender != withdrawer) {
232: if (vaults[msg.sender]) {
244: if (owner != msg.sender) {
```
[105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L105) | [124](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L124) | [232](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L232) | [244](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L244)

```solidity
File: src/transformers/AutoCompound.sol

88: if (!operators[msg.sender] || !vaults[vault]) {
102: if (!operators[msg.sender] && !vaults[msg.sender]) {
205: if (owner != msg.sender) {
228: if (msg.sender != withdrawer) {
```
[88](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L88) | [102](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L102) | [205](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L205) | [228](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L228)

```solidity
File: src/transformers/AutoRange.sol

98: if (!operators[msg.sender] || !vaults[vault]) {
112: if (!operators[msg.sender] && !vaults[msg.sender]) {
```
[98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L98) | [112](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L112)

```solidity
File: src/transformers/V3Utils.sol

102: if (nonfungiblePositionManager.ownerOf(tokenId) != msg.sender) {
362: if (msg.sender != address(nonfungiblePositionManager)) {
```
[102](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L102) | [362](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L362)

```solidity
File: src/utils/Swapper.sol

161: if (address(_getPool(tokenIn, tokenOut, fee)) != msg.sender) {
```
[161](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L161)
</details>

### [N-51] NatSpec: Contract declarations should have descriptions

NatSpec descriptions are crucial for self-documenting smart contracts. They provide vital information 
about the contract's purpose and behavior.

Specifically, the `@dev` or `@notice` tags are quintessential 
for detailed explanations about the contract. 

Ensure these descriptions are present directly above the contract definition braces. 
This positioning allows the compiler to correctly identify and associate the descriptions with the contract.

[Learn More about Proper NatSpec Formatting](https://docs.soliditylang.org/en/develop/natspec-format.html)

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/automators/Automator.sol

18: abstract contract Automator is Swapper, Ownable {
```
[18](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L18)

```solidity
File: src/utils/Swapper.sol

17: abstract contract Swapper is IUniswapV3SwapCallback, IErrors {
```
[17](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L17)
</details>

### [N-52] NatSpec: Contract declarations should have `@author` tag

In the world of decentralized code, giving credit is key. NatSpec's `@author` tag acknowledges the minds behind the code.
It appears this Solidity contract omits the `@author` directive in its NatSpec annotations.
Properly attributing code to its contributors not only recognizes effort but also aids in establishing trust and credibility.
[Dive Deeper into NatSpec Guidelines](https://docs.soliditylang.org/en/develop/natspec-format.html)

<details>
<summary><i>9 issue instances in 9 files:</i></summary>

```solidity
File: src/V3Vault.sol

30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {
```
[30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30)

```solidity
File: src/V3Oracle.sol

24: contract V3Oracle is IV3Oracle, Ownable, IErrors {
```
[24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L24)

```solidity
File: src/InterestRateModel.sol

11: contract InterestRateModel is Ownable, IInterestRateModel, IErrors {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L11)

```solidity
File: src/automators/AutoExit.sol

10: contract AutoExit is Automator {
```
[10](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L10)

```solidity
File: src/transformers/AutoCompound.sol

16: contract AutoCompound is Automator, Multicall, ReentrancyGuard {
```
[16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L16)

```solidity
File: src/transformers/AutoRange.sol

11: contract AutoRange is Automator {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L11)

```solidity
File: src/transformers/LeverageTransformer.sol

12: contract LeverageTransformer is Swapper {
```
[12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L12)

```solidity
File: src/transformers/V3Utils.sol

15: contract V3Utils is Swapper, IERC721Receiver {
```
[15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L15)

```solidity
File: src/utils/FlashloanLiquidator.sol

11: contract FlashloanLiquidator is Swapper, IUniswapV3FlashCallback {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L11)
</details>

### [N-53] Missing NatSpec Descriptions for Event Declarations

Event declarations should have accompanying NatSpec comments with `@dev` or `@notice` tag to describe their purpose and the meaning of emitted parameters. 
These comments provide clarity for developers, reviewers, and users of the contract.
[More information in Documentation](https://docs.soliditylang.org/en/latest/natspec-format.html)

<details>
<summary><i>36 issue instances in 9 files:</i></summary>

```solidity
File: src/V3Vault.sol

68: event ApprovedTransform(uint256 indexed tokenId, address owner, address target, bool isActive);
70: event Add(uint256 indexed tokenId, address owner, uint256 oldTokenId); // when a token is added replacing another token - oldTokenId > 0
71: event Remove(uint256 indexed tokenId, address recipient);
73: event ExchangeRateUpdate(uint256 debtExchangeRateX96, uint256 lendExchangeRateX96);
75: event WithdrawCollateral(
        uint256 indexed tokenId, address owner, address recipient, uint128 liquidity, uint256 amount0, uint256 amount1
    );
78: event Borrow(uint256 indexed tokenId, address owner, uint256 assets, uint256 shares);
79: event Repay(uint256 indexed tokenId, address repayer, address owner, uint256 assets, uint256 shares);
80: event Liquidate(
        uint256 indexed tokenId,
        address liquidator,
        address owner,
        uint256 value,
        uint256 cost,
        uint256 amount0,
        uint256 amount1,
        uint256 reserve,
        uint256 missing
    ); // shows exactly how liquidation amounts were divided
93: event WithdrawReserves(uint256 amount, address receiver);
94: event SetTransformer(address transformer, bool active);
95: event SetLimits(
        uint256 minLoanSize,
        uint256 globalLendLimit,
        uint256 globalDebtLimit,
        uint256 dailyLendIncreaseLimitMin,
        uint256 dailyDebtIncreaseLimitMin
    );
102: event SetReserveFactor(uint32 reserveFactorX32);
103: event SetReserveProtectionFactor(uint32 reserveProtectionFactorX32);
104: event SetTokenConfig(address token, uint32 collateralFactorX32, uint32 collateralValueLimitFactorX32);
106: event SetEmergencyAdmin(address emergencyAdmin);
```
[68](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L68) | [70](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L70) | [71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L71) | [73](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L73) | [75](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L75) | [78](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L78) | [79](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L79) | [80](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L80) | [93](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L93) | [94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L94) | [95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L95) | [102](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L102) | [103](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L103) | [104](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L104) | [106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L106)

```solidity
File: src/V3Oracle.sol

30: event TokenConfigUpdated(address indexed token, TokenConfig config);
31: event OracleModeUpdated(address indexed token, Mode mode);
32: event SetMaxPoolPriceDifference(uint16 maxPoolPriceDifference);
33: event SetEmergencyAdmin(address emergencyAdmin);
```
[30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L30) | [31](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L31) | [32](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L32) | [33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L33)

```solidity
File: src/InterestRateModel.sol

18: event SetValues(
        uint256 baseRatePerYearX96, uint256 multiplierPerYearX96, uint256 jumpMultiplierPerYearX96, uint256 kinkX96
    );
```
[18](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L18)

```solidity
File: src/automators/AutoExit.sol

20: event PositionConfigured(
        uint256 indexed tokenId,
        bool isActive,
        bool token0Swap,
        bool token1Swap,
        int24 token0TriggerTick,
        int24 token1TriggerTick,
        uint64 token0SlippageX64,
        uint64 token1SlippageX64,
        bool onlyFees,
        uint64 maxRewardX64
    );
```
[20](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L20)

```solidity
File: src/automators/Automator.sol

27: event OperatorChanged(address newOperator, bool active);
28: event VaultChanged(address newVault, bool active);
30: event WithdrawerChanged(address newWithdrawer);
31: event TWAPConfigChanged(uint32 TWAPSeconds, uint16 maxTWAPTickDifference);
```
[27](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L27) | [28](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L28) | [30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L30) | [31](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L31)

```solidity
File: src/transformers/AutoCompound.sol

30: event RewardUpdated(address account, uint64 totalRewardX64);
33: event BalanceAdded(uint256 tokenId, address token, uint256 amount);
34: event BalanceRemoved(uint256 tokenId, address token, uint256 amount);
35: event BalanceWithdrawn(uint256 tokenId, address token, address to, uint256 amount);
```
[30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L30) | [33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L33) | [34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L34) | [35](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L35)

```solidity
File: src/transformers/AutoRange.sol

13: event PositionConfigured(
        uint256 indexed tokenId,
        int32 lowerTickLimit,
        int32 upperTickLimit,
        int32 lowerTickDelta,
        int32 upperTickDelta,
        uint64 token0SlippageX64,
        uint64 token1SlippageX64,
        bool onlyFees,
        uint64 maxRewardX64
    );
```
[13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L13)

```solidity
File: src/transformers/V3Utils.sol

22: event CompoundFees(uint256 indexed tokenId, uint128 liquidity, uint256 amount0, uint256 amount1);
23: event ChangeRange(uint256 indexed tokenId, uint256 newTokenId);
24: event WithdrawAndCollectAndSwap(uint256 indexed tokenId, address token, uint256 amount);
25: event SwapAndMint(uint256 indexed tokenId, uint128 liquidity, uint256 amount0, uint256 amount1);
26: event SwapAndIncreaseLiquidity(uint256 indexed tokenId, uint128 liquidity, uint256 amount0, uint256 amount1);
```
[22](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L22) | [23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L23) | [24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L24) | [25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L25) | [26](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L26)

```solidity
File: src/utils/Swapper.sol

18: event Swap(address indexed tokenIn, address indexed tokenOut, uint256 amountIn, uint256 amountOut);
```
[18](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L18)
</details>

### [N-54] Invalid NatSpec comment style

NatSpec comments in Solidity are meant to be recognized by tools for a variety of purposes such as documentation generation.
The correct style is to use `///` for single-line comments and `/* ... */` for multi-line comments.
Incorrect styles can cause tools to not recognize the comments as intended.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/transformers/V3Utils.sol

18: // @notice Permit2 contract
```
[18](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L18)
</details>

### [N-55] Consider defining system-wide constants in a single file

System-wide constants should be declared in a single file for better maintainability and readability.
This contract seems to contain constants which could potentially be system-wide and could be better managed if they were centralized in a single location.

<details>
<summary><i>20 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

33: uint256 private constant Q32 = 2 ** 32;
34: uint256 private constant Q96 = 2 ** 96;
36: uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%
38: uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
39: uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%
41: uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%
43: uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%
44: uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%
```
[33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L33) | [34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L34) | [36](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L36) | [38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L38) | [39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L39) | [41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L41) | [43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L43) | [44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L44)

```solidity
File: src/V3Oracle.sol

25: uint16 public constant MIN_PRICE_DIFFERENCE = 200; //2%
27: uint256 private constant Q96 = 2 ** 96;
28: uint256 private constant Q128 = 2 ** 128;
```
[25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L25) | [27](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L27) | [28](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L28)

```solidity
File: src/InterestRateModel.sol

12: uint256 private constant Q96 = 2 ** 96;
13: uint256 public constant YEAR_SECS = 31557600; // taking into account leap years
15: uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10; // 10%
16: uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%
```
[12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L12) | [13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L13) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L15) | [16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L16)

```solidity
File: src/automators/Automator.sol

20: uint256 internal constant Q64 = 2 ** 64;
21: uint256 internal constant Q96 = 2 ** 96;
23: uint32 public constant MIN_TWAP_SECONDS = 60; // 1 minute
24: uint32 public constant MAX_TWAP_TICK_DIFFERENCE = 200; // 2%
```
[20](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L20) | [21](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L21) | [23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L23) | [24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L24)

```solidity
File: src/transformers/AutoCompound.sol

47: uint64 public constant MAX_REWARD_X64 = uint64(Q64 / 50); // 2%
```
[47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L47)
</details>

### [N-56] Add inline comments for unnamed variables

Having unnamed variables in function definitions can be confusing and decrease the code readability. 
Adding inline comments to explain the purpose of unnamed variables could make the code easier to understand and maintain.

For example, convert function declarations like `function foo(address x, address)` to `function foo(address x, address /* y */)` to indicate that the unnamed variable could have been named 'y'.

<details>
<summary><i>4 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit - `address`
301: function maxDeposit(address) external view override returns (uint256) {
/// @audit - `address`
312: function maxMint(address) external view override returns (uint256) {
/// @audit - `address`
429: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
    {
```
[301](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L301) | [312](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L312) | [429](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L429)

```solidity
File: src/transformers/V3Utils.sol

/// @audit - `address`
356: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
    {
```
[356](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L356)
</details>

### [N-57] Consider making contracts `Upgradeable`

Contract uses a non-upgradeable design.
Transitioning to an upgradeable contract structure is more aligned with contemporary smart contract practices.
This approach not only enhances flexibility but also allows for continuous improvement and adaptation, ensuring the contract stays relevant and robust in an ever-evolving ecosystem.

<details>
<summary><i>11 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit - Contract `V3Vault` is not upgradeable
30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {
```
[30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30)

```solidity
File: src/V3Oracle.sol

/// @audit - Contract `V3Oracle` is not upgradeable
24: contract V3Oracle is IV3Oracle, Ownable, IErrors {
```
[24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L24)

```solidity
File: src/InterestRateModel.sol

/// @audit - Contract `InterestRateModel` is not upgradeable
11: contract InterestRateModel is Ownable, IInterestRateModel, IErrors {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L11)

```solidity
File: src/automators/AutoExit.sol

/// @audit - Contract `AutoExit` is not upgradeable
10: contract AutoExit is Automator {
```
[10](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L10)

```solidity
File: src/automators/Automator.sol

/// @audit - Contract `Automator` is not upgradeable
18: abstract contract Automator is Swapper, Ownable {
```
[18](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L18)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit - Contract `AutoCompound` is not upgradeable
16: contract AutoCompound is Automator, Multicall, ReentrancyGuard {
```
[16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L16)

```solidity
File: src/transformers/AutoRange.sol

/// @audit - Contract `AutoRange` is not upgradeable
11: contract AutoRange is Automator {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L11)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit - Contract `LeverageTransformer` is not upgradeable
12: contract LeverageTransformer is Swapper {
```
[12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L12)

```solidity
File: src/transformers/V3Utils.sol

/// @audit - Contract `V3Utils` is not upgradeable
15: contract V3Utils is Swapper, IERC721Receiver {
```
[15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L15)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit - Contract `FlashloanLiquidator` is not upgradeable
11: contract FlashloanLiquidator is Swapper, IUniswapV3FlashCallback {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L11)

```solidity
File: src/utils/Swapper.sol

/// @audit - Contract `Swapper` is not upgradeable
17: abstract contract Swapper is IUniswapV3SwapCallback, IErrors {
```
[17](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L17)
</details>

### [N-58] Events that mark critical parameter changes should contain both the old and the new value

When emitting events that signify critical changes in parameters, it's important to include both the old and new values. 

This aids in auditability, providing more complete information about the state change. It's especially necessary when the new value isn't required to be different from the old one, as this prevents ambiguity in event logs.

<details>
<summary><i>3 issue instances in 3 files:</i></summary>

```solidity
File: src/V3Vault.sol

849: emit SetReserveProtectionFactor(_reserveProtectionFactorX32);
```
[849](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L849)

```solidity
File: src/V3Oracle.sol

190: emit SetMaxPoolPriceDifference(_maxPoolPriceDifference);
```
[190](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L190)

```solidity
File: src/automators/Automator.sol

60: emit WithdrawerChanged(_withdrawer);
```
[60](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L60)
</details>

### [N-59] Style guide: Non-`external`/`public` variable names should begin with an underscore

The naming convention for non-public (private and internal) variables in Solidity recommends the use of a leading underscore.

Since `constants` can be public, to avoid confusion, they should also be prefixed with an underscore.

This practice clearly differentiates between public/external and non-public variables, enhancing code clarity and reducing the likelihood of misinterpretation or errors.
Following this convention improves code readability and maintainability.

<details>
<summary><i>12 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

33: uint256 private constant Q32 = 2 ** 32;
34: uint256 private constant Q96 = 2 ** 96;
65: uint8 private immutable assetDecimals;
157: mapping(address => uint256[]) private ownedTokens; // Mapping from owner address to list of owned token IDs
158: mapping(uint256 => uint256) private ownedTokensIndex; // Mapping from token ID to index of the owner tokens list (for removal without loop)
159: mapping(uint256 => address) private tokenOwner; // Mapping from token ID to owner
161: uint256 private transformedTokenId = 0; // transient storage (when available in dencun)
```
[33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L33) | [34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L34) | [65](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L65) | [157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L157) | [158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L158) | [159](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L159) | [161](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L161)

```solidity
File: src/V3Oracle.sol

27: uint256 private constant Q96 = 2 ** 96;
28: uint256 private constant Q128 = 2 ** 128;
```
[27](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L27) | [28](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L28)

```solidity
File: src/InterestRateModel.sol

12: uint256 private constant Q96 = 2 ** 96;
```
[12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L12)

```solidity
File: src/automators/Automator.sol

20: uint256 internal constant Q64 = 2 ** 64;
21: uint256 internal constant Q96 = 2 ** 96;
```
[20](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L20) | [21](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L21)
</details>

### [N-60] Style guide: Contract does not follow the Solidity style guide's suggested layout ordering

Adhering to a recommended order in Solidity contracts enhances code readability and maintenance.
[More information in Documentation](https://docs.soliditylang.org/en/latest/style-guide.html#order-of-layout)
It's recommended to use the following order:
1. Type declarations
2. State variables
3. Events
4. Errors
5. Modifiers
6. Functions

<details>
<summary><i>24 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit `type` declared after `event`
109: struct TokenConfig {
        uint32 collateralFactorX32; // how much this token is valued as collateral
        uint32 collateralValueLimitFactorX32; // how much asset equivalent may be lent out given this collateral
        uint192 totalDebtShares; // how much debt shares are theoretically backed by this collateral
    }
/// @audit `type` declared after `state variable`
150: struct Loan {
        uint256 debtShares;
    }
/// @audit `type` declared after `function`
666: struct LiquidateState {
        uint256 newDebtExchangeRateX96;
        uint256 newLendExchangeRateX96;
        uint256 debt;
        bool isHealthy;
        uint256 liquidationValue;
        uint256 liquidatorCost;
        uint256 reserveCost;
        uint256 missing;
        uint256 fullValue;
        uint256 collateralValue;
        uint256 feeValue;
    }
```
[109](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L109) | [150](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L150) | [666](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L666)

```solidity
File: src/V3Oracle.sol

/// @audit `type` declared after `event`
34: enum Mode {
        NOT_SET,
        CHAINLINK_TWAP_VERIFY, // using chainlink for price and TWAP to verify
        TWAP_CHAINLINK_VERIFY, // using TWAP for price and chainlink to verify
        CHAINLINK, // using only chainlink directly
        TWAP // using TWAP directly
    }
/// @audit `type` declared after `function`
375: struct PositionState {
        uint256 tokenId;
        address token0;
        address token1;
        uint24 fee;
        int24 tickLower;
        int24 tickUpper;
        uint128 liquidity;
        uint256 feeGrowthInside0LastX128;
        uint256 feeGrowthInside1LastX128;
        uint128 tokensOwed0;
        uint128 tokensOwed1;
        IUniswapV3Pool pool;
        uint160 sqrtPriceX96;
        int24 tick;
        uint160 sqrtPriceX96Lower;
        uint160 sqrtPriceX96Upper;
    }
```
[34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L34) | [375](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L375)

```solidity
File: src/InterestRateModel.sol

/// @audit `state variable` declared after `event`
23: uint256 public multiplierPerSecondX96;
```
[23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L23)

```solidity
File: src/automators/AutoExit.sol

/// @audit `type` declared after `constructor`
44: struct PositionConfig {
        bool isActive; // if position is active
        // should swap token to other token when triggered
        bool token0Swap;
        bool token1Swap;
        // when should action be triggered (when this tick is reached - allow execute)
        int24 token0TriggerTick; // when tick is below this one
        int24 token1TriggerTick; // when tick is equal or above this one
        // max price difference from current pool price for swap / Q64
        uint64 token0SlippageX64; // when token 0 is swapped to token 1
        uint64 token1SlippageX64; // when token 1 is swapped to token 0
        bool onlyFees; // if only fees maybe used for protocol reward
        uint64 maxRewardX64; // max allowed reward percentage of fees or full position
    }
/// @audit `type` declared after `state variable`
63: struct ExecuteParams {
        uint256 tokenId; // tokenid to process
        bytes swapData; // if its a swap order - must include swap data
        uint128 liquidity; // liquidity the calculations are based on
        uint256 amountRemoveMin0; // min amount to be removed from liquidity
        uint256 amountRemoveMin1; // min amount to be removed from liquidity
        uint256 deadline; // for uniswap operations - operator promises fair value
        uint64 rewardX64; // which reward will be used for protocol, can be max configured amount (considering onlyFees)
    }
```
[44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L44) | [63](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L63)

```solidity
File: src/automators/Automator.sol

/// @audit `state variable` declared after `event`
34: mapping(address => bool) public operators;
```
[34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L34)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit `state variable` declared after `constructor`
45: mapping(uint256 => mapping(address => uint256)) public positionBalances;
/// @audit `type` declared after `state variable`
51: struct ExecuteParams {
        // tokenid to autocompound
        uint256 tokenId;
        // swap direction - calculated off-chain
        bool swap0To1;
        // swap amount - calculated off-chain - if this is set to 0 no swap happens
        uint256 amountIn;
    }
```
[45](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L45) | [51](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L51)

```solidity
File: src/transformers/AutoRange.sol

/// @audit `type` declared after `constructor`
37: struct PositionConfig {
        // needs more than int24 because it can be [-type(uint24).max,type(uint24).max]
        int32 lowerTickLimit; // if negative also in-range positions may be adjusted / if 0 out of range positions may be adjusted
        int32 upperTickLimit; // if negative also in-range positions may be adjusted / if 0 out of range positions may be adjusted
        int32 lowerTickDelta; // this amount is added to current tick (floored to tickspacing) to define lowerTick of new position
        int32 upperTickDelta; // this amount is added to current tick (floored to tickspacing) to define upperTick of new position
        uint64 token0SlippageX64; // max price difference from current pool price for swap / Q64 for token0
        uint64 token1SlippageX64; // max price difference from current pool price for swap / Q64 for token1
        bool onlyFees; // if only fees maybe used for protocol reward
        uint64 maxRewardX64; // max allowed reward percentage of fees or full position
    }
/// @audit `type` declared after `state variable`
53: struct ExecuteParams {
        uint256 tokenId;
        bool swap0To1;
        uint256 amountIn; // if this is set to 0 no swap happens
        bytes swapData;
        uint128 liquidity; // liquidity the calculations are based on
        uint256 amountRemoveMin0; // min amount to be removed from liquidity
        uint256 amountRemoveMin1; // min amount to be removed from liquidity
        uint256 deadline; // for uniswap operations - operator promises fair value
        uint64 rewardX64; // which reward will be used for protocol, can be max configured amount (considering onlyFees)
    }
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L37) | [53](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L53)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit `type` declared after `constructor`
16: struct LeverageUpParams {
        // which token to leverage
        uint256 tokenId;
        // how much to borrow
        uint256 borrowAmount;
        // how much of borrowed lend token should be swapped to token0
        uint256 amountIn0;
        uint256 amountOut0Min;
        bytes swapData0; // encoded data from 0x api call (address,bytes) - allowanceTarget,data
        // how much of borrowed lend token should be swapped to token1
        uint256 amountIn1;
        uint256 amountOut1Min;
        bytes swapData1; // encoded data from 0x api call (address,bytes) - allowanceTarget,data
        // for adding liquidity slippage
        uint256 amountAddMin0;
        uint256 amountAddMin1;
        // recipient for leftover tokens
        address recipient;
        // for all uniswap deadlineable functions
        uint256 deadline;
    }
/// @audit `type` declared after `function`
97: struct LeverageDownParams {
        // which token to leverage
        uint256 tokenId;
        // for removing - remove liquidity amount
        uint128 liquidity;
        uint256 amountRemoveMin0;
        uint256 amountRemoveMin1;
        // collect fee amount (if type(uint128).max - ALL)
        uint128 feeAmount0;
        uint128 feeAmount1;
        // how much of token0 should be swapped to lend token
        uint256 amountIn0;
        uint256 amountOut0Min;
        bytes swapData0; // encoded data from 0x api call (address,bytes) - allowanceTarget,data
        // how much of token1 should be swapped to lend token
        uint256 amountIn1;
        uint256 amountOut1Min;
        bytes swapData1; // encoded data from 0x api call (address,bytes) - allowanceTarget,data
        // recipient for leftover tokens
        address recipient;
        // for all uniswap deadlineable functions
        uint256 deadline;
    }
```
[16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L16) | [97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L97)

```solidity
File: src/transformers/V3Utils.sol

/// @audit `type` declared after `constructor`
41: enum WhatToDo {
        CHANGE_RANGE,
        WITHDRAW_AND_COLLECT_AND_SWAP,
        COMPOUND_FEES
    }
/// @audit `type` declared after `function`
382: struct SwapParams {
        IERC20 tokenIn;
        IERC20 tokenOut;
        uint256 amountIn;
        uint256 minAmountOut;
        address recipient; // recipient of tokenOut and leftover tokenIn (if any leftover)
        bytes swapData;
        bool unwrap; // if tokenIn or tokenOut is WETH - unwrap
        bytes permitData; // if permit2 signatures are used - set this
    }
/// @audit `type` declared after `function`
432: struct SwapAndMintParams {
        IERC20 token0;
        IERC20 token1;
        uint24 fee;
        int24 tickLower;
        int24 tickUpper;
        // how much is provided of token0 and token1
        uint256 amount0;
        uint256 amount1;
        address recipient; // recipient of leftover tokens
        address recipientNFT; // recipient of nft
        uint256 deadline;
        // source token for swaps (maybe either address(0), token0, token1 or another token)
        // if swapSourceToken is another token than token0 or token1 -> amountIn0 + amountIn1 of swapSourceToken are expected to be available
        IERC20 swapSourceToken;
        // if swapSourceToken needs to be swapped to token0 - set values
        uint256 amountIn0;
        uint256 amountOut0Min;
        bytes swapData0;
        // if swapSourceToken needs to be swapped to token1 - set values
        uint256 amountIn1;
        uint256 amountOut1Min;
        bytes swapData1;
        // min amount to be added after swap
        uint256 amountAddMin0;
        uint256 amountAddMin1;
        // data to be sent along newly created NFT when transfered to recipientNFT (sent to IERC721Receiver callback)
        bytes returnData;
        // if permit2 signatures are used - set this
        bytes permitData;
    }
/// @audit `type` declared after `function`
504: struct SwapAndIncreaseLiquidityParams {
        uint256 tokenId;
        // how much is provided of token0 and token1
        uint256 amount0;
        uint256 amount1;
        address recipient; // recipient of leftover tokens
        uint256 deadline;
        // source token for swaps (maybe either address(0), token0, token1 or another token)
        // if swapSourceToken is another token than token0 or token1 -> amountIn0 + amountIn1 of swapSourceToken are expected to be available
        IERC20 swapSourceToken;
        // if swapSourceToken needs to be swapped to token0 - set values
        uint256 amountIn0;
        uint256 amountOut0Min;
        bytes swapData0;
        // if swapSourceToken needs to be swapped to token1 - set values
        uint256 amountIn1;
        uint256 amountOut1Min;
        bytes swapData1;
        // min amount to be added after swap
        uint256 amountAddMin0;
        uint256 amountAddMin1;
        // if permit2 signatures are used - set this
        bytes permitData;
    }
/// @audit `type` declared after `function`
587: struct PrepareAddPermit2State {
        uint256 needed0;
        uint256 needed1;
        uint256 neededOther;
        uint256 i;
        uint256 balanceBefore0;
        uint256 balanceBefore1;
        uint256 balanceBeforeOther;
    }
```
[41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L41) | [382](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L382) | [432](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L432) | [504](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L504) | [587](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L587)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit `type` declared after `constructor`
27: struct LiquidateParams {
        uint256 tokenId; // loan to liquidate
        uint256 debtShares; // debt shares calculation is based on
        IVault vault; // vault where the loan is
        IUniswapV3Pool flashLoanPool; // pool which is used for flashloan - may not be used in the swaps below
        uint256 amount0In; // how much of token0 to swap to asset (0 if no swap should be done)
        bytes swapData0; // swap data for token0 swap
        uint256 amount1In; // how much of token1 to swap to asset (0 if no swap should be done)
        bytes swapData1; // swap data for token1 swap
        uint256 minReward; // min reward amount (works as a global slippage control for complete operation)
    }
```
[27](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L27)

```solidity
File: src/utils/Swapper.sol

/// @audit `state variable` declared after `event`
21: IWETH9 public immutable weth;
/// @audit `type` declared after `constructor`
50: struct ZeroxRouterData {
        address allowanceTarget;
        bytes data;
    }
/// @audit `type` declared after `function`
119: struct PoolSwapParams {
        IUniswapV3Pool pool;
        IERC20 token0;
        IERC20 token1;
        uint24 fee;
        bool swap0For1;
        uint256 amountIn;
        uint256 amountOutMin;
    }
```
[21](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L21) | [50](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L50) | [119](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L119)
</details>

### [N-61] Using Low-Level Call for Transfers

Directly using low-level calls for Ether transfers can introduce vulnerabilities and obscure the intent of your transfers.
Adopt modern Solidity best practices by switching to recognized libraries like `SafeTransferLib.safeTransferETH` or `Address.sendValue`.
This ensures safer transactions, enhances code clarity, and aligns with the standards of the Solidity community.

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: src/automators/Automator.sol

130: (bool sent,) = to.call{value: balance}("");
221: (bool sent,) = to.call{value: amount}("");
```
[130](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L130) | [221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L221)

```solidity
File: src/transformers/V3Utils.sol

867: (bool sent,) = to.call{value: amount}("");
```
[867](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L867)
</details>

### [N-62] Consider bounding input array length

The functions in question operate on arrays without established boundaries, executing function calls for each of their entries.
If these arrays become excessively long, a function might revert due to gas constraints.
To enhance user experience, consider incorporating a `require()` statement that enforces a sensible maximum array length.
This approach can avoid unnecessary computational work and ensure smoother transactions.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/automators/Automator.sol

/// @audit `count` equal to `tokens.length` and it not bounded
111: for (; i < count; ++i) {
```
[111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L111)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit `count` equal to `tokens.length` and it not bounded
233: for (; i < count; ++i) {
```
[233](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L233)
</details>

### [N-63] NatSpec: Function declarations should have `@notice` tag

In Solidity, the `@notice` tag in NatSpec comments is used to provide important explanations to end users about what a function does. 
It appears that this contract's function declarations are missing `@notice` tags in their NatSpec annotations.

The absence of `@notice` tags reduces the contract's transparency and could lead to misunderstandings about a function's purpose and behavior.
Note that the Solidity compiler treats comments beginning with `///` or `/**` as `@notice` tags if one wasn't explicitly provided.
[Learn More About NatSpec Guidelines](https://docs.soliditylang.org/en/develop/natspec-format.html)

<details>
<summary><i>17 issue instances in 9 files:</i></summary>

```solidity
File: src/V3Vault.sol

169: constructor(
        string memory name,
        string memory symbol,
        address _asset,
        INonfungiblePositionManager _nonfungiblePositionManager,
        IInterestRateModel _interestRateModel,
        IV3Oracle _oracle,
        IPermit2 _permit2
    ) ERC20(name, symbol) {
384: function deposit(uint256 assets, address receiver, bytes calldata permitData) external override returns (uint256) {
390: function mint(uint256 shares, address receiver, bytes calldata permitData) external override returns (uint256) {
609: function decreaseLiquidityAndCollect(DecreaseLiquidityAndCollectParams calldata params)
        external
        override
        returns (uint256 amount0, uint256 amount1)
    {
```
[169](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L169) | [384](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L384) | [390](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L390) | [609](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L609)

```solidity
File: src/V3Oracle.sol

74: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _referenceToken,
        address _chainlinkReferenceToken
    ) {
```
[74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L74)

```solidity
File: src/automators/AutoExit.sol

33: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
218: function configToken(uint256 tokenId, PositionConfig calldata config) external {
```
[33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L33) | [218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L218)

```solidity
File: src/automators/Automator.sol

41: constructor(
        INonfungiblePositionManager npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Swapper(npm, _zeroxRouter, _universalRouter) {
```
[41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L41)

```solidity
File: src/transformers/AutoCompound.sol

37: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, address(0), address(0)) {}
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L37)

```solidity
File: src/transformers/AutoRange.sol

25: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
276: function configToken(uint256 tokenId, address vault, PositionConfig calldata config) external {
```
[25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L25) | [276](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L276)

```solidity
File: src/transformers/LeverageTransformer.sol

13: constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)
        Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter)
    {}
40: function leverageUp(LeverageUpParams calldata params) external {
123: function leverageDown(LeverageDownParams calldata params) external {
```
[13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L13) | [40](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L40) | [123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L123)

```solidity
File: src/utils/FlashloanLiquidator.sol

24: constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)
        Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter)
    {}
67: function uniswapV3FlashCallback(uint256 fee0, uint256 fee1, bytes calldata callbackData) external {
```
[24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L24) | [67](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L67)

```solidity
File: src/utils/Swapper.sol

156: function uniswapV3SwapCallback(int256 amount0Delta, int256 amount1Delta, bytes calldata data) external override {
```
[156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L156)
</details>

### [N-64] Constants in comparisons should appear on the left side

Placing constants on the left side of comparison statements can help prevent accidental assignments and improve code readability.
In languages like C, placing constants on the left can protect against unintended assignments that would be treated as true conditions, leading to bugs.
Although Solidity does not have this specific issue, using the same practice can still be beneficial for code readability and consistency.

Consider placing constants on the left side of comparison operators like `==`, `!=`, `<`, `>`, `<=`, and `>=`."

<details>
<summary><i>70 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

443: if (data.length > 0) {
712: if (state.reserveCost > 0) {
717: if (params.permitData.length > 0) {
778: if (amount > 0) {
893: if (permitData.length > 0) {
977: if (assets > 0) {
978: if (permitData.length > 0) {
1064: if (liquidity > 0) {
1186: if (lastRateUpdate > 0) {
```
[443](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L443) | [712](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L712) | [717](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L717) | [778](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L778) | [893](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L893) | [977](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L977) | [978](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L978) | [1064](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1064) | [1186](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1186)

```solidity
File: src/V3Oracle.sol

362: if (twapSeconds == 0) {
431: if (state.liquidity > 0) {
```
[362](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L362) | [431](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L431)

```solidity
File: src/InterestRateModel.sol

47: if (debt == 0) {
```
[47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L47)

```solidity
File: src/automators/AutoExit.sol

124: if (state.liquidity == 0) {
149: if (params.swapData.length == 0) {
199: if (state.amount0 > 0) {
202: if (state.amount1 > 0) {
```
[124](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L124) | [149](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L149) | [199](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L199) | [202](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L202)

```solidity
File: src/automators/Automator.sol

113: if (balance > 0) {
129: if (balance > 0) {
200: if (liquidity > 0) {
```
[113](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L113) | [129](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L129) | [200](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L200)

```solidity
File: src/transformers/AutoCompound.sol

123: if (state.amount0 > 0 || state.amount1 > 0) {
127: if (amountIn > 0) {
133: if (tSecs > 0) {
140: if (amountIn > 0) {
160: if (state.maxAddAmount0 > 0 || state.maxAddAmount1 > 0) {
212: if (balance0 > 0) {
216: if (balance1 > 0) {
279: if (allowance0 == 0) {
283: if (allowance1 == 0) {
```
[123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L123) | [127](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L127) | [133](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L133) | [140](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L140) | [160](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L160) | [212](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L212) | [216](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L216) | [279](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L279) | [283](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L283)

```solidity
File: src/transformers/AutoRange.sol

243: if (state.amount0 - state.amountAdded0 > 0) {
246: if (state.amount1 - state.amountAdded1 > 0) {
301: if (fee == 10000) {
303: } else if (fee == 3000) {
305: } else if (fee == 500) {
309: if (spacing <= 0) {
```
[243](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L243) | [246](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L246) | [301](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L301) | [303](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L303) | [305](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L305) | [309](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L309)

```solidity
File: src/transformers/LeverageTransformer.sol

52: if (params.amountIn0 > 0) {
64: if (params.amountIn1 > 0) {
146: if (params.amountIn0 > 0 && token != token0) {
155: if (params.amountIn1 > 0 && token != token1) {
169: if (amount0 > 0 && token != token0) {
172: if (amount1 > 0 && token != token1) {
```
[52](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L52) | [64](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L64) | [146](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L146) | [155](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L155) | [169](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L169) | [172](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L172)

```solidity
File: src/transformers/V3Utils.sol

120: if (instructions.liquidity != 0) {
342: if (targetAmount != 0 && instructions.targetToken != address(0)) {
402: if (params.permitData.length > 0) {
420: if (amountOut != 0) {
426: if (leftOver != 0) {
476: if (params.permitData.length > 0) {
539: if (params.permitData.length > 0) {
577: if (needed0 > 0) {
580: if (needed1 > 0) {
583: if (neededOther > 0) {
617: if (state.needed0 > 0) {
621: if (state.needed1 > 0) {
625: if (state.neededOther > 0) {
634: if (state.needed0 > 0) {
639: if (state.needed1 > 0) {
644: if (state.neededOther > 0) {
666: if (msg.value != 0) {
822: if (leftOver != 0) {
830: if (total0 != 0) {
834: if (total1 != 0) {
855: if (left0 != 0) {
858: if (left1 != 0) {
884: if (liquidity != 0) {
```
[120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L120) | [342](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L342) | [402](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L402) | [420](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L420) | [426](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L426) | [476](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L476) | [539](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L539) | [577](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L577) | [580](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L580) | [583](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L583) | [617](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L617) | [621](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L621) | [625](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L625) | [634](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L634) | [639](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L639) | [644](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L644) | [666](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L666) | [822](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L822) | [830](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L830) | [834](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L834) | [855](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L855) | [858](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L858) | [884](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L884)

```solidity
File: src/utils/FlashloanLiquidator.sol

43: if (liquidationCost == 0) {
90: if (balance > 0) {
96: if (balance > 0) {
105: if (balance > 0) {
```
[43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L43) | [90](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L90) | [96](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L96) | [105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L105)

```solidity
File: src/utils/Swapper.sol

77: if (params.amountIn != 0 && params.swapData.length != 0 && address(params.tokenOut) != address(0)) {
133: if (params.amountIn > 0) {
157: require(amount0Delta > 0 || amount1Delta > 0); // swaps entirely within 0-liquidity regions are not supported
```
[77](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L77) | [133](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L133) | [157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L157)
</details>

### [N-65] NatSpec: Contract declarations should have `@notice` tag

The `@notice` tag in NatSpec annotations serves to provide information about the contract's functionality that is visible to end-users.
Including `@notice` comments helps to improve the contract's transparency and ease of understanding, contributing to the overall trust and credibility of the code.
[NatSpec Guidelines](https://docs.soliditylang.org/en/develop/natspec-format.html)

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/utils/FlashloanLiquidator.sol

11: contract FlashloanLiquidator is Swapper, IUniswapV3FlashCallback {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L11)
</details>

### [N-66] Large numeric literals should use underscores for readability

Large numeric literals are often hard to read and prone to mistakes.
To improve readability and reduce the likelihood of errors, it is recommended to separate the digits of large numeric literals using underscores.
For example, instead of '1000000', use '1_000_000'.

<details>
<summary><i>5 issue instances in 3 files:</i></summary>

```solidity
File: src/V3Oracle.sol

144: ? (priceX96 - verifyPriceX96) * 10000 / priceX96
145: : (verifyPriceX96 - priceX96) * 10000 / verifyPriceX96;
```
[144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L144) | [145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L145)

```solidity
File: src/InterestRateModel.sol

13: uint256 public constant YEAR_SECS = 31557600; // taking into account leap years
```
[13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L13)

```solidity
File: src/transformers/AutoRange.sol

301: if (fee == 10000) {
303: } else if (fee == 3000) {
```
[301](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L301) | [303](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L303)
</details>

### [N-67] Named Imports of Parent Contracts Are Missing

It's important to have named imports for parent contracts to ensure code readability and maintainability.
Missing named imports can make it difficult to understand the code hierarchy and can lead to issues in the future.

<details>
<summary><i>22 issue instances in 9 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit Missing named import for parent contract: `ERC20`
30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {
/// @audit Missing named import for parent contract: `Multicall`
30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {
/// @audit Missing named import for parent contract: `Ownable`
30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {
/// @audit Missing named import for parent contract: `IVault`
30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {
/// @audit Missing named import for parent contract: `IERC721Receiver`
30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {
/// @audit Missing named import for parent contract: `IErrors`
30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {
```
[30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30) | [30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30) | [30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30) | [30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30) | [30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30) | [30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30)

```solidity
File: src/V3Oracle.sol

/// @audit Missing named import for parent contract: `IV3Oracle`
24: contract V3Oracle is IV3Oracle, Ownable, IErrors {
/// @audit Missing named import for parent contract: `Ownable`
24: contract V3Oracle is IV3Oracle, Ownable, IErrors {
/// @audit Missing named import for parent contract: `IErrors`
24: contract V3Oracle is IV3Oracle, Ownable, IErrors {
```
[24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L24) | [24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L24) | [24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L24)

```solidity
File: src/InterestRateModel.sol

/// @audit Missing named import for parent contract: `Ownable`
11: contract InterestRateModel is Ownable, IInterestRateModel, IErrors {
/// @audit Missing named import for parent contract: `IInterestRateModel`
11: contract InterestRateModel is Ownable, IInterestRateModel, IErrors {
/// @audit Missing named import for parent contract: `IErrors`
11: contract InterestRateModel is Ownable, IInterestRateModel, IErrors {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L11) | [11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L11) | [11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L11)

```solidity
File: src/automators/AutoExit.sol

/// @audit Missing named import for parent contract: `Automator`
10: contract AutoExit is Automator {
```
[10](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L10)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit Missing named import for parent contract: `Automator`
16: contract AutoCompound is Automator, Multicall, ReentrancyGuard {
/// @audit Missing named import for parent contract: `Multicall`
16: contract AutoCompound is Automator, Multicall, ReentrancyGuard {
/// @audit Missing named import for parent contract: `ReentrancyGuard`
16: contract AutoCompound is Automator, Multicall, ReentrancyGuard {
```
[16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L16) | [16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L16) | [16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L16)

```solidity
File: src/transformers/AutoRange.sol

/// @audit Missing named import for parent contract: `Automator`
11: contract AutoRange is Automator {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L11)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit Missing named import for parent contract: `Swapper`
12: contract LeverageTransformer is Swapper {
```
[12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L12)

```solidity
File: src/transformers/V3Utils.sol

/// @audit Missing named import for parent contract: `Swapper`
15: contract V3Utils is Swapper, IERC721Receiver {
/// @audit Missing named import for parent contract: `IERC721Receiver`
15: contract V3Utils is Swapper, IERC721Receiver {
```
[15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L15) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L15)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit Missing named import for parent contract: `Swapper`
11: contract FlashloanLiquidator is Swapper, IUniswapV3FlashCallback {
/// @audit Missing named import for parent contract: `IUniswapV3FlashCallback`
11: contract FlashloanLiquidator is Swapper, IUniswapV3FlashCallback {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L11) | [11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L11)
</details>

### [N-68] Long functions should be refactored into multiple, smaller, functions

Functions that span many lines can be hard to understand and maintain.
It is often beneficial to refactor long functions into multiple smaller functions.
This improves readability, makes testing easier, and can even lead to gas optimization if it eliminates the need for variables that would otherwise have to be stored in memory.

<details>
<summary><i>15 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

 /// @audit 33 lines (excluding comments)
550: function borrow(uint256 tokenId, uint256 assets) external override {
 /// @audit 52 lines (excluding comments)
685: function liquidate(LiquidateParams calldata params) external override returns (uint256 amount0, uint256 amount1) {
 /// @audit 42 lines (excluding comments)
953: function _repay(uint256 tokenId, uint256 amount, bool isShare, bytes memory permitData) internal {
```
[550](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L550) | [685](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L685) | [953](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L953)

```solidity
File: src/V3Oracle.sol

 /// @audit 40 lines (excluding comments)
272: function _getReferenceTokenPriceX96(address token, uint256 cachedChainlinkReferencePriceX96)
        internal
        view
        returns (uint256 priceX96, uint256 chainlinkReferencePriceX96)
    {
```
[272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L272)

```solidity
File: src/automators/AutoExit.sol

 /// @audit 83 lines (excluding comments)
100: function execute(ExecuteParams calldata params) external {
```
[100](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L100)

```solidity
File: src/transformers/AutoCompound.sol

 /// @audit 64 lines (excluding comments)
101: function execute(ExecuteParams calldata params) external nonReentrant {
```
[101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L101)

```solidity
File: src/transformers/AutoRange.sol

 /// @audit 119 lines (excluding comments)
111: function execute(ExecuteParams calldata params) external {
```
[111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L111)

```solidity
File: src/transformers/LeverageTransformer.sol

 /// @audit 46 lines (excluding comments)
40: function leverageUp(LeverageUpParams calldata params) external {
 /// @audit 43 lines (excluding comments)
123: function leverageDown(LeverageDownParams calldata params) external {
```
[40](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L40) | [123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L123)

```solidity
File: src/transformers/V3Utils.sol

 /// @audit 227 lines (excluding comments)
115: function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {
 /// @audit 33 lines (excluding comments)
597: function _prepareAddPermit2(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther,
        IPermit2.PermitBatchTransferFrom memory permit,
        bytes memory signature
    ) internal {
 /// @audit 36 lines (excluding comments)
653: function _prepareAdd(
        IERC20 token0,
        IERC20 token1,
        IERC20 otherToken,
        uint256 amount0,
        uint256 amount1,
        uint256 amountOther
    ) internal returns (uint256 needed0, uint256 needed1, uint256 neededOther) {
 /// @audit 33 lines (excluding comments)
735: function _swapAndIncrease(SwapAndIncreaseLiquidityParams memory params, IERC20 token0, IERC20 token1, bool unwrap)
        internal
        returns (uint128 liquidity, uint256 added0, uint256 added1)
    {
 /// @audit 51 lines (excluding comments)
779: function _swapAndPrepareAmounts(SwapAndMintParams memory params, bool unwrap)
        internal
        returns (uint256 total0, uint256 total1)
    {
```
[115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L115) | [597](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L597) | [653](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L653) | [735](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L735) | [779](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L779)

```solidity
File: src/utils/FlashloanLiquidator.sol

 /// @audit 32 lines (excluding comments)
66: function uniswapV3FlashCallback(uint256 fee0, uint256 fee1, bytes calldata callbackData) external {
```
[66](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L66)
</details>

### [N-69] NatSpec: Contract declarations should have `@dev` tags

NatSpec comments are a critical part of Solidity's documentation system, designed to help developers and others understand the behavior and purpose of a contract.
The `@dev` tag, in particular, provides context and insight into the contract's development considerations.
A missing `@dev` comment can lead to misunderstandings about the contract, making it harder for others to contribute to or use the contract effectively.
Therefore, it's highly recommended to include `@dev` comments in the documentation to enhance code readability and maintainability.
[Refer to NatSpec Documentation](https://docs.soliditylang.org/en/develop/natspec-format.html)

<details>
<summary><i>9 issue instances in 9 files:</i></summary>

```solidity
File: src/V3Vault.sol

30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {
```
[30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30)

```solidity
File: src/V3Oracle.sol

24: contract V3Oracle is IV3Oracle, Ownable, IErrors {
```
[24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L24)

```solidity
File: src/InterestRateModel.sol

11: contract InterestRateModel is Ownable, IInterestRateModel, IErrors {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L11)

```solidity
File: src/automators/AutoExit.sol

10: contract AutoExit is Automator {
```
[10](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L10)

```solidity
File: src/transformers/AutoCompound.sol

16: contract AutoCompound is Automator, Multicall, ReentrancyGuard {
```
[16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L16)

```solidity
File: src/transformers/AutoRange.sol

11: contract AutoRange is Automator {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L11)

```solidity
File: src/transformers/LeverageTransformer.sol

12: contract LeverageTransformer is Swapper {
```
[12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L12)

```solidity
File: src/transformers/V3Utils.sol

15: contract V3Utils is Swapper, IERC721Receiver {
```
[15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L15)

```solidity
File: src/utils/FlashloanLiquidator.sol

11: contract FlashloanLiquidator is Swapper, IUniswapV3FlashCallback {
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L11)
</details>

### [N-70] `public` functions not called by the contract should be declared `external` instead

Contracts are allowed to override their parents' functions and change the visibility from `external` to `public`.
If a `public` function is not called internally within the contract, it should be declared as `external` to save gas.

<details>
<summary><i>7 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

334: function previewDeposit(uint256 assets) public view override returns (uint256) {
340: function previewMint(uint256 shares) public view override returns (uint256) {
346: function previewWithdraw(uint256 assets) public view override returns (uint256) {
352: function previewRedeem(uint256 shares) public view override returns (uint256) {
```
[334](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L334) | [340](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L340) | [346](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L346) | [352](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L352)

```solidity
File: src/InterestRateModel.sol

58: function getRatesPerSecondX96(uint256 cash, uint256 debt)
        public
        view
        override
        returns (uint256 borrowRateX96, uint256 supplyRateX96)
    {
```
[58](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L58)

```solidity
File: src/automators/Automator.sol

79: function setVault(address _vault, bool _active) public onlyOwner {
```
[79](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L79)

```solidity
File: src/transformers/V3Utils.sol

98: function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)
        public
        returns (uint256 newTokenId)
    {
```
[98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L98)
</details>

### [N-71] Large multiples of ten should use scientific notation

Large multiples of ten should use scientific notation (e.g., 1e4) instead of decimal literals (e.g., 10000)
for better code readability.

<details>
<summary><i>4 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Oracle.sol

/// @audit `10000` should be written as `1e4`
144: ? (priceX96 - verifyPriceX96) * 10000 / priceX96
/// @audit `10000` should be written as `1e4`
145: : (verifyPriceX96 - priceX96) * 10000 / verifyPriceX96;
```
[144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L144) | [145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L145)

```solidity
File: src/transformers/AutoRange.sol

/// @audit `10000` should be written as `1e4`
301: if (fee == 10000) {
/// @audit `3000` should be written as `3e3`
303: } else if (fee == 3000) {
```
[301](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L301) | [303](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L303)
</details>

### [N-72] Complex casting

Complex casting in Solidity contracts can introduce both readability issues and potential for overflows. 
Whenever multiple casts are found, consider whether the complexity is necessary.
If so, it is strongly recommended to add inline comments to explain why these casts are needed and to assure that no overflows are introduced.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Oracle.sol

369: int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)));
```
[369](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L369)

```solidity
File: src/automators/Automator.sol

187: return (int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapPeriod))), true);
```
[187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L187)
</details>

### [N-73] Equal `block.timestamp` Cases Not Handled

Solidity code that checks if `block.timestamp` is greater than a certain variable but fails to handle the case when `block.timestamp` is equal to the variable may lead to unintended behaviors and potential vulnerabilities.

To ensure correct and secure function execution, it's recommended to include checks for cases where `block.timestamp` equals the compared variable.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

1155: if (block.timestamp > lastExchangeRateUpdate) {
```
[1155](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1155)

```solidity
File: src/V3Oracle.sol

338: if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0) {
```
[338](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L338)
</details>

### [N-74] `else`-block not required

In Solidity, if an `if` block contains a `return` statement, subsequent `else` blocks become unnecessary.
This is because the `return` statement halts the execution of the function at that point, making any `else` conditions redundant.
Therefore, omitting `else` after such `if` blocks can lead to cleaner and more readable code without any change in the functionality.

<details>
<summary><i>6 issue instances in 3 files:</i></summary>

```solidity
File: src/V3Vault.sol

304: if (value >= globalLendLimit) {
            return 0;
        } else {
            return globalLendLimit - value;
        }
315: if (value >= globalLendLimit) {
            return 0;
        } else {
            return _convertToShares(globalLendLimit - value, lendExchangeRateX96, Math.Rounding.Down);
        }
574: if (assets > dailyDebtIncreaseLimitLeft) {
            revert DailyDebtIncreaseLimit();
        } else {
            dailyDebtIncreaseLimitLeft -= assets;
        }
910: if (assets > dailyLendIncreaseLimitLeft) {
            revert DailyLendIncreaseLimit();
        } else {
            dailyLendIncreaseLimitLeft -= assets;
        }
```
[304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L304) | [315](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L315) | [574](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L574) | [910](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L910)

```solidity
File: src/automators/Automator.sol

172: if (twapOk) {
            return twapTick - currentTick >= -int16(maxDifference) && twapTick - currentTick <= int16(maxDifference);
        } else {
            return false;
        }
```
[172](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L172)

```solidity
File: src/transformers/AutoRange.sol

301: if (fee == 10000) {
            return 200;
        } else if (fee == 3000) {
            return 60;
        } else if (fee == 500) {
```
[301](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L301)
</details>

### [N-75] Polymorphic functions make security audits more time-consuming and error-prone

While function overriding allows for functions with the same name to coexist, it's advisable to avoid this practice for the sake of readability and maintainability. 

Having multiple functions with the same name, even with different parameters or in inherited contracts, can cause confusion and increase the chance of errors during development, testing, and debugging.
Using distinct and descriptive function names not only clarifies the purpose and behavior of each function but also helps prevent unintended function calls or incorrect overriding.

<details>
<summary><i>6 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

360: function deposit(uint256 assets, address receiver) external override returns (uint256) {
384: function deposit(uint256 assets, address receiver, bytes calldata permitData) external override returns (uint256) {
366: function mint(uint256 shares, address receiver) external override returns (uint256) {
390: function mint(uint256 shares, address receiver, bytes calldata permitData) external override returns (uint256) {
652: function repay(uint256 tokenId, uint256 amount, bool isShare) external override {
661: function repay(uint256 tokenId, uint256 amount, bool isShare, bytes calldata permitData) external override {
```
[360](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L360) | [384](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L384) | [366](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L366) | [390](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L390) | [652](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L652) | [661](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L661)
</details>

### [N-76] Style guide: Function ordering does not follow the Solidity style guide

Ordering helps readers identify which functions they can call and to find the constructor and fallback definitions easier.
But there are contracts in the project that do not comply with this.
Functions should be grouped according to their visibility and ordered:
- constructor 
- receive function (if exists)
- fallback function (if exists)
- external
- public
- internal
- private.

<details>
<summary><i>18 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit `public` function `totalAssets()` declared before `external` function `convertToShares()`
284: function totalAssets() public view override returns (uint256) {
289: function convertToShares(uint256 assets) external view override returns (uint256 shares) {
/// @audit `public` function `previewRedeem()` declared before `external` function `deposit()`
352: function previewRedeem(uint256 shares) public view override returns (uint256) {
360: function deposit(uint256 assets, address receiver) external override returns (uint256) {
```
[284](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L284) | [289](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L289) | [352](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L352) | [360](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L360)

```solidity
File: src/V3Oracle.sol

/// @audit `internal` function `_requireMaxDifference()` declared before `public` function `getPositionBreakdown()`
138: function _requireMaxDifference(uint256 priceX96, uint256 verifyPriceX96, uint256 maxDifferenceX10000)
        internal
        pure
    {
162: function getPositionBreakdown(uint256 tokenId)
        public
        view
        override
        returns (
            address token0,
            address token1,
            uint24 fee,
            uint128 liquidity,
            uint256 amount0,
            uint256 amount1,
            uint128 fees0,
            uint128 fees1
        )
    {
/// @audit `public` function `getPositionBreakdown()` declared before `external` function `setMaxPoolPriceDifference()`
162: function getPositionBreakdown(uint256 tokenId)
        public
        view
        override
        returns (
            address token0,
            address token1,
            uint24 fee,
            uint128 liquidity,
            uint256 amount0,
            uint256 amount1,
            uint128 fees0,
            uint128 fees1
        )
    {
185: function setMaxPoolPriceDifference(uint16 _maxPoolPriceDifference) external onlyOwner {
```
[138](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L138) | [162](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L162) | [162](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L162) | [185](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L185)

```solidity
File: src/automators/Automator.sol

/// @audit `public` function `setTWAPConfig()` declared before `external` function `withdrawBalances()`
87: function setTWAPConfig(uint16 _maxTWAPTickDifference, uint32 _TWAPSeconds) public onlyOwner {
104: function withdrawBalances(address[] calldata tokens, address to) external virtual {
/// @audit `function` declared before `receive`
229: function _validateOwner(uint256 tokenId, address vault) internal returns (address owner) {
251: receive() external payable {
```
[87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L87) | [104](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L104) | [229](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L229) | [251](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L251)

```solidity
File: src/transformers/V3Utils.sol

/// @audit `public` function `execute()` declared before `external` function `onERC721Received()`
115: function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {
356: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
    {
/// @audit `function` declared before `receive`
892: function _collectFees(uint256 tokenId, IERC20 token0, IERC20 token1, uint128 collectAmount0, uint128 collectAmount1)
        internal
        returns (uint256 amount0, uint256 amount1)
    {
914: receive() external payable {
```
[115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L115) | [356](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L356) | [892](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L892) | [914](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L914)

```solidity
File: src/utils/Swapper.sol

/// @audit `internal` function `_poolSwap()` declared before `external` function `uniswapV3SwapCallback()`
132: function _poolSwap(PoolSwapParams memory params) internal returns (uint256 amountInDelta, uint256 amountOutDelta) {
156: function uniswapV3SwapCallback(int256 amount0Delta, int256 amount1Delta, bytes calldata data) external override {
```
[132](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L132) | [156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L156)
</details>

### [N-77] Style guide: Lines are too long

It is generally recommended that lines in the source code should not exceed 80-120 characters.
Multiline output parameters and return statements should follow the same style recommended for wrapping long lines found in the Maximum Line Length section.

<details>
<summary><i>50 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

28: /// @notice The vault manages ONE ERC20 (eg. USDC) asset for lending / borrowing, but collateral positions can be composed of any 2 tokens configured each with a collateralFactor > 0
70: event Add(uint256 indexed tokenId, address owner, uint256 oldTokenId); // when a token is added replacing another token - oldTokenId > 0
158: mapping(uint256 => uint256) private ownedTokensIndex; // Mapping from token ID to index of the owner tokens list (for removal without loop)
163: mapping(address => bool) public transformerAllowList; // contracts allowed to transform positions (selected audited contracts e.g. V3Utils)
164: mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; // owners permissions for other addresses to call transform on owners behalf (e.g. AutoRange contract)
230: /// @return liquidationValue If position is liquidatable - the value of the (partial) position which the liquidator recieves - otherwise 0
427: /// @notice Whenever a token is recieved it either creates a new loan, or modifies an existing one when in transform mode.
492: /// @notice Method which allows a contract to transform a loan by changing it (and only at the end checking collateral)
496: /// @return newTokenId Final token ID (may be different than input token ID when the position was replaced by transformation)
604: /// @dev Decreases the liquidity of a given position and collects the resultant assets (and possibly additional fees)
605: /// This function is not allowed during transformation (if a transformer wants to decreaseLiquidity he can call the methods directly on the NonfungiblePositionManager)
606: /// @param params Struct containing various parameters for the operation. Includes tokenId, liquidity amount, minimum asset amounts, and deadline.
614: // this method is not allowed during transform - can be called directly on nftmanager if needed from transform contract
636: params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
714: _handleReserveLiquidation(state.reserveCost, state.newDebtExchangeRateX96, state.newLendExchangeRateX96);
769: _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up) * reserveProtectionFactorX32 / Q32;
842: /// @notice sets reserve protection factor - percentage of globalLendAmount which can't be withdrawn by owner (onlyOwner)
855: /// @param collateralValueLimitFactorX32 how much of it maybe used as collateral measured as percentage of total lent assets mutiplied by Q32
1089: //  if position is not valuable enough - missing part is covered by reserves - if not enough reserves - collectively by other borrowers
1096: // if position has less than enough value - liquidation cost maybe less - rest is payed by protocol or lenders collectively
1204: // updates collateral token configs - and check if limit is not surpassed (check is only done on increasing debt shares)
```
[28](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L28) | [70](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L70) | [158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L158) | [163](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L163) | [164](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L164) | [230](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L230) | [427](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L427) | [492](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L492) | [496](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L496) | [604](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L604) | [605](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L605) | [606](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L606) | [614](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L614) | [636](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L636) | [714](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L714) | [769](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L769) | [842](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L842) | [855](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L855) | [1089](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1089) | [1096](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1096) | [1204](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1204)

```solidity
File: src/V3Oracle.sol

65: uint16 public maxPoolPriceDifference = MIN_PRICE_DIFFERENCE; // max price difference between oracle derived price and pool price x10000
152: /// @notice Gets breakdown of a uniswap v3 position (tokens and fee tier, liquidity, current liquidity amounts, uncollected fees)
368: (int56[] memory tickCumulatives,) = pool.observe(secondsAgos); // pool observe may fail when there is not enough history available (only use pool with enough history!)
```
[65](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L65) | [152](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L152) | [368](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L368)

```solidity
File: src/automators/AutoExit.sol

7: /// @notice Lets a v3 position to be automatically removed (limit order) or swapped to the opposite token (stop loss order) when it reaches a certain tick.
184: // when swap and !onlyFees - protocol reward is removed only from target token (to incentivize optimal swap done by operator)
```
[7](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L7) | [184](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L184)

```solidity
File: src/transformers/AutoRange.sol

39: int32 lowerTickLimit; // if negative also in-range positions may be adjusted / if 0 out of range positions may be adjusted
40: int32 upperTickLimit; // if negative also in-range positions may be adjusted / if 0 out of range positions may be adjusted
41: int32 lowerTickDelta; // this amount is added to current tick (floored to tickspacing) to define lowerTick of new position
42: int32 upperTickDelta; // this amount is added to current tick (floored to tickspacing) to define upperTick of new position
191: state.amount0 = params.swap0To1 ? state.amount0 - state.amountInDelta : state.amount0 + state.amountOutDelta;
192: state.amount1 = params.swap0To1 ? state.amount1 + state.amountOutDelta : state.amount1 - state.amountInDelta;
```
[39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L39) | [40](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L40) | [41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L41) | [42](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L42) | [191](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L191) | [192](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L192)

```solidity
File: src/transformers/LeverageTransformer.sol

139: params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
```
[139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L139)

```solidity
File: src/transformers/V3Utils.sol

47: /// @notice Complete description of what should be executed on provided NFT - different fields are used depending on specified WhatToDo
66: // collect fee amount for COMPOUND_FEES / CHANGE_RANGE / WITHDRAW_AND_COLLECT_AND_SWAP (if uint256(128).max - ALL)
73: // remove liquidity amount for COMPOUND_FEES (in this case should be probably 0) / CHANGE_RANGE / WITHDRAW_AND_COLLECT_AND_SWAP
109: // NOTE: previous operator can not be reset as operator set by permit can not change operator - so this operator will stay until reset
317: _transferToken(instructions.recipient, IERC20(token0), amount0 - amountInDelta, instructions.unwrap);
334: _transferToken(instructions.recipient, IERC20(token1), amount1 - amountInDelta, instructions.unwrap);
354: /// @notice ERC721 callback function. Called on safeTransferFrom and does manipulation as configured in encoded Instructions parameter.
355: /// At the end the NFT (and any newly minted NFT) is returned to sender. The leftover tokens are sent to instructions.recipient.
395: /// If tokenIn is wrapped native token - both the token or the wrapped token can be sent (the sum of both must be equal to amountIn)
445: // if swapSourceToken is another token than token0 or token1 -> amountIn0 + amountIn1 of swapSourceToken are expected to be available
464: /// @notice Does 1 or 2 swaps from swapSourceToken to token0 and token1 and adds as much as possible liquidity to a newly minted position.
512: // if swapSourceToken is another token than token0 or token1 -> amountIn0 + amountIn1 of swapSourceToken are expected to be available
529: /// @notice Does 1 or 2 swaps from swapSourceToken to token0 and token1 and adds as much as possible liquidity to any existing position (no need to be position owner).
725: // mint is done to address(this) because it is not a safemint and safeTransferFrom needs to be done manually afterwards
```
[47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L47) | [66](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L66) | [73](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L73) | [109](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L109) | [317](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L317) | [334](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L334) | [354](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L354) | [355](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L355) | [395](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L395) | [445](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L445) | [464](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L464) | [512](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L512) | [529](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L529) | [725](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L725)

```solidity
File: src/utils/FlashloanLiquidator.sol

64: params.flashLoanPool.flash(address(this), isAsset0 ? liquidationCost : 0, !isAsset0 ? liquidationCost : 0, data);
68: // no origin check is needed - because the contract doesn't hold any funds - there is no benefit in calling uniswapV3FlashCallback() from another context
```
[64](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L64) | [68](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L68)

```solidity
File: src/utils/Swapper.sol

172: return IUniswapV3Pool(PoolAddress.computeAddress(address(factory), PoolAddress.getPoolKey(tokenA, tokenB, fee)));
```
[172](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L172)
</details>

### [N-78] Numeric Values Related to Time Lacking Units

For enhanced readability and comprehensibility, numeric values related to time in your Solidity code should employ time units like seconds, minutes, hours, days, or weeks.

Please note that:
- 1 == 1 seconds
- 1 minutes == 60 seconds
- 1 hours == 60 minutes
- 1 days == 24 hours
- 1 weeks == 7 days

More about Time Uints in [Solidity Documentation](https://docs.soliditylang.org/en/latest/units-and-global-variables.html#time-units).

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/automators/Automator.sol

23: uint32 public constant MIN_TWAP_SECONDS = 60; // 1 minute
```
[23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L23)
</details>

### [N-79] Style guide: Extraneous whitespace

See the [whitespace](https://docs.soliditylang.org/en/v0.8.24/style-guide.html#whitespace-in-expressions) section of the Solidity Style Guide

<details>
<summary><i>28 issue instances in 6 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit `More than one space around an assignment or other operator to align with another`
551: bool isTransformMode =
            transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];
/// @audit `More than one space around an assignment or other operator to align with another`
702: (state.isHealthy, state.fullValue, state.collateralValue, state.feeValue) =
            _checkLoanIsHealthy(params.tokenId, state.debt);
/// @audit `More than one space around an assignment or other operator to align with another`
708: (state.liquidationValue, state.liquidatorCost, state.reserveCost) =
            _calculateLiquidation(state.debt, state.fullValue, state.collateralValue);
/// @audit `More than one space around an assignment or other operator to align with another`
713: state.missing =
                _handleReserveLiquidation(state.reserveCost, state.newDebtExchangeRateX96, state.newLendExchangeRateX96);
/// @audit `More than one space around an assignment or other operator to align with another`
718: (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
                abi.decode(params.permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
/// @audit `More than one space around an assignment or other operator to align with another`
734: (amount0, amount1) =
            _sendPositionValue(params.tokenId, state.liquidationValue, state.fullValue, state.feeValue, msg.sender);
/// @audit `More than one space around an assignment or other operator to align with another`
768: uint256 protected =
            _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up) * reserveProtectionFactorX32 / Q32;
/// @audit `More than one space around an assignment or other operator to align with another`
894: (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
                abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
/// @audit `More than one space around an assignment or other operator to align with another`
979: (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
                    abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
/// @audit `More than one space around an assignment or other operator to align with another`
1106: uint256 penaltyFractionX96 =
                (Q96 - ((fullValue - maxPenaltyValue) * Q96 / (startLiquidationValue - maxPenaltyValue)));
/// @audit `More than one space around an assignment or other operator to align with another`
1252: dailyLendIncreaseLimitLeft =
                dailyLendIncreaseLimitMin > lendIncreaseLimit ? dailyLendIncreaseLimitMin : lendIncreaseLimit;
/// @audit `More than one space around an assignment or other operator to align with another`
1264: dailyDebtIncreaseLimitLeft =
                dailyDebtIncreaseLimitMin > debtIncreaseLimit ? dailyDebtIncreaseLimitMin : debtIncreaseLimit;
```
[551](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L551) | [702](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L702) | [708](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L708) | [713](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L713) | [718](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L718) | [734](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L734) | [768](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L768) | [894](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L894) | [979](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L979) | [1106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1106) | [1252](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1252) | [1264](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1264)

```solidity
File: src/V3Oracle.sol

/// @audit `Immediately before a comma`
397: ,
/// @audit `Immediately before a comma`
398: ,
/// @audit `More than one space around an assignment or other operator to align with another`
101: (address token0, address token1, uint24 fee,, uint256 amount0, uint256 amount1, uint256 fees0, uint256 fees1) =
            getPositionBreakdown(tokenId);
/// @audit `More than one space around an assignment or other operator to align with another`
106: (price0X96, cachedChainlinkReferencePriceX96) =
            _getReferenceTokenPriceX96(token0, cachedChainlinkReferencePriceX96);
/// @audit `More than one space around an assignment or other operator to align with another`
108: (price1X96, cachedChainlinkReferencePriceX96) =
            _getReferenceTokenPriceX96(token1, cachedChainlinkReferencePriceX96);
```
[397](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L397) | [398](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L398) | [101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L101) | [106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L106) | [108](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L108)

```solidity
File: src/automators/AutoExit.sol

/// @audit `More than one space around an assignment or other operator to align with another`
120: (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
            nonfungiblePositionManager.positions(params.tokenId);
```
[120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L120)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit `More than one space around an assignment or other operator to align with another`
115: (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper,,,,,) =
            nonfungiblePositionManager.positions(params.tokenId);
/// @audit `More than one space around an assignment or other operator to align with another`
147: state.amount0 =
                        params.swap0To1 ? state.amount0 - state.amountInDelta : state.amount0 + state.amountOutDelta;
/// @audit `More than one space around an assignment or other operator to align with another`
149: state.amount1 =
                        params.swap0To1 ? state.amount1 + state.amountOutDelta : state.amount1 - state.amountInDelta;
```
[115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L115) | [147](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L147) | [149](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L149)

```solidity
File: src/transformers/AutoRange.sol

/// @audit `More than one space around an assignment or other operator to align with another`
130: (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
            nonfungiblePositionManager.positions(params.tokenId);
```
[130](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L130)

```solidity
File: src/transformers/V3Utils.sol

/// @audit `More than one space around an assignment or other operator to align with another`
403: (ISignatureTransfer.PermitBatchTransferFrom memory pbtf, bytes memory signature) =
                abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));
/// @audit `More than one space around an assignment or other operator to align with another`
477: (ISignatureTransfer.PermitBatchTransferFrom memory pbtf, bytes memory signature) =
                abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));
/// @audit `More than one space around an assignment or other operator to align with another`
540: (ISignatureTransfer.PermitBatchTransferFrom memory pbtf, bytes memory signature) =
                abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));
/// @audit `More than one space around an assignment or other operator to align with another`
574: (uint256 needed0, uint256 needed1, uint256 neededOther) =
            _prepareAdd(token0, token1, otherToken, amount0, amount1, amountOther);
/// @audit `More than one space around an assignment or other operator to align with another`
610: (state.needed0, state.needed1, state.neededOther) =
            _prepareAdd(token0, token1, otherToken, amount0, amount1, amountOther);
/// @audit `More than one space around an assignment or other operator to align with another`
613: ISignatureTransfer.SignatureTransferDetails[] memory transferDetails =
            new ISignatureTransfer.SignatureTransferDetails[](permit.permitted.length);
```
[403](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L403) | [477](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L477) | [540](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L540) | [574](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L574) | [610](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L610) | [613](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L613)
</details>

### [N-80] Avoid the use of sensitive terms

Inclusive language plays a critical role in fostering an environment where everyone belongs.
Please use alternative terms as suggested below:
master -> source
slave -> replica
blacklist -> blocklist
whitelist -> allowlist

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

494: /// @param transformer The address of a whitelisted transformer contract
```
[494](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L494)
</details>

### [N-81] Unused import

The contract contains import statements for libraries or other contracts that are not utilized within the code.
Excessive or unused imports can clutter the codebase, leading to inefficiency and potential confusion.
Consider removing any imports that are not essential to the contract's functionality.

<details>
<summary><i>12 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit - IUniswapV3Pool imported but not used
5: import "v3-core/interfaces/IUniswapV3Pool.sol";
/// @audit - TickMath imported but not used
6: import "v3-core/libraries/TickMath.sol";
/// @audit - FixedPoint128 imported but not used
7: import "v3-core/libraries/FixedPoint128.sol";
/// @audit - LiquidityAmounts imported but not used
9: import "v3-periphery/libraries/LiquidityAmounts.sol";
```
[5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L5) | [6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L6) | [7](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L7) | [9](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L9)

```solidity
File: src/V3Oracle.sol

/// @audit - IUniswapV3Factory imported but not used
4: import "v3-core/interfaces/IUniswapV3Factory.sol";
```
[4](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L4)

```solidity
File: src/automators/Automator.sol

/// @audit - SafeCast imported but not used
6: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
/// @audit - IUniswapV3Factory imported but not used
8: import "v3-core/interfaces/IUniswapV3Factory.sol";
/// @audit - IUniswapV3Pool imported but not used
9: import "v3-core/interfaces/IUniswapV3Pool.sol";
/// @audit - TickMath imported but not used
10: import "v3-core/libraries/TickMath.sol";
/// @audit - FullMath imported but not used
11: import "v3-core/libraries/FullMath.sol";
/// @audit - IWETH9 imported but not used
15: import "../../lib/IWETH9.sol";
```
[6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L6) | [8](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L8) | [9](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L9) | [10](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L10) | [11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L11) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L15)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit - SafeMath imported but not used
6: import "@openzeppelin/contracts/utils/math/SafeMath.sol";
```
[6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L6)
</details>

### [N-82] `if`-statement can be converted to a ternary

The ternary operator provides a shorthand way to write if / else statements.
It can improve readability and reduce the number of lines of code.
Traditional `if / else` statements, particularly those spanning only a one lines, could potentially be refactored using the ternary operator.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Oracle.sol

349: if (feedConfig.isToken0) {
            poolTWAPPriceX96 = priceX96;
        } else {
            poolTWAPPriceX96 = Q96 * Q96 / priceX96;
        }
```
[349](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L349)

```solidity
File: src/automators/Automator.sol

157: if (swap0For1) {
            amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), priceX96, Q96 * Q64);
        } else {
            amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), Q96, priceX96 * Q64);
        }
```
[157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L157)
</details>

### [N-83] Consider using named mappings

As of Solidity version 0.8.18, it is possible to use named mappings to clarify the purpose of each mapping in the code. 
It is recommended to use this feature for better code readability and maintainability.

More information: [Solidity 0.8.18 Release Announcement](https://blog.soliditylang.org/2023/02/01/solidity-0.8.18-release-announcement/)

<details>
<summary><i>13 issue instances in 6 files:</i></summary>

```solidity
File: src/V3Vault.sol

115: mapping(address => TokenConfig) public tokenConfigs;
154: mapping(uint256 => Loan) public loans; // tokenID -> loan mapping
157: mapping(address => uint256[]) private ownedTokens; // Mapping from owner address to list of owned token IDs
158: mapping(uint256 => uint256) private ownedTokensIndex; // Mapping from token ID to index of the owner tokens list (for removal without loop)
159: mapping(uint256 => address) private tokenOwner; // Mapping from token ID to owner
163: mapping(address => bool) public transformerAllowList; // contracts allowed to transform positions (selected audited contracts e.g. V3Utils)
164: mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; // owners permissions for other addresses to call transform on owners behalf (e.g. AutoRange contract)
```
[115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L115) | [154](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L154) | [157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L157) | [158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L158) | [159](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L159) | [163](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L163) | [164](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L164)

```solidity
File: src/V3Oracle.sol

56: mapping(address => TokenConfig) public feedConfigs;
```
[56](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L56)

```solidity
File: src/automators/AutoExit.sol

60: mapping(uint256 => PositionConfig) public positionConfigs;
```
[60](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L60)

```solidity
File: src/automators/Automator.sol

34: mapping(address => bool) public operators;
35: mapping(address => bool) public vaults;
```
[34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L34) | [35](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L35)

```solidity
File: src/transformers/AutoCompound.sol

45: mapping(uint256 => mapping(address => uint256)) public positionBalances;
```
[45](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L45)

```solidity
File: src/transformers/AutoRange.sol

50: mapping(uint256 => PositionConfig) public positionConfigs;
```
[50](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L50)
</details>

### [N-84] Use of `override` is unnecessary

In Solidity version 0.8.8 and later, the use of the `override` keyword becomes superfluous when a function is overriding solely from an interface and the function isn't present in multiple base contracts.
Previously, the `override` keyword was required as an explicit indication to the compiler. However, this is no longer the case, and the extraneous use of the keyword can make the code less clean and more verbose.

Solidity documentation on [Function Overriding](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding).

<details>
<summary><i>40 issue instances in 6 files:</i></summary>

```solidity
File: src/V3Vault.sol

195: function vaultInfo()
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
219: function lendInfo(address account) external view override returns (uint256 amount) {
231: function loanInfo(uint256 tokenId)
        external
        view
        override
        returns (
            uint256 debt,
            uint256 fullValue,
            uint256 collateralValue,
            uint256 liquidationCost,
            uint256 liquidationValue
        )
    {
258: function ownerOf(uint256 tokenId) external view override returns (address owner) {
264: function loanCount(address owner) external view override returns (uint256) {
271: function loanAtIndex(address owner, uint256 index) external view override returns (uint256) {
277: function decimals() public view override(IERC20Metadata, ERC20) returns (uint8) {
284: function totalAssets() public view override returns (uint256) {
289: function convertToShares(uint256 assets) external view override returns (uint256 shares) {
295: function convertToAssets(uint256 shares) external view override returns (uint256 assets) {
301: function maxDeposit(address) external view override returns (uint256) {
312: function maxMint(address) external view override returns (uint256) {
323: function maxWithdraw(address owner) external view override returns (uint256) {
329: function maxRedeem(address owner) external view override returns (uint256) {
334: function previewDeposit(uint256 assets) public view override returns (uint256) {
340: function previewMint(uint256 shares) public view override returns (uint256) {
346: function previewWithdraw(uint256 assets) public view override returns (uint256) {
352: function previewRedeem(uint256 shares) public view override returns (uint256) {
360: function deposit(uint256 assets, address receiver) external override returns (uint256) {
366: function mint(uint256 shares, address receiver) external override returns (uint256) {
372: function withdraw(uint256 assets, address receiver, address owner) external override returns (uint256) {
378: function redeem(uint256 shares, address receiver, address owner) external override returns (uint256) {
384: function deposit(uint256 assets, address receiver, bytes calldata permitData) external override returns (uint256) {
390: function mint(uint256 shares, address receiver, bytes calldata permitData) external override returns (uint256) {
400: function create(uint256 tokenId, address recipient) external override {
410: function createWithPermit(
        uint256 tokenId,
        address owner,
        address recipient,
        uint256 deadline,
        uint8 v,
        bytes32 r,
        bytes32 s
    ) external override {
429: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
    {
483: function approveTransform(uint256 tokenId, address target, bool isActive) external override {
497: function transform(uint256 tokenId, address transformer, bytes calldata data)
        external
        override
        returns (uint256 newTokenId)
    {
550: function borrow(uint256 tokenId, uint256 assets) external override {
609: function decreaseLiquidityAndCollect(DecreaseLiquidityAndCollectParams calldata params)
        external
        override
        returns (uint256 amount0, uint256 amount1)
    {
652: function repay(uint256 tokenId, uint256 amount, bool isShare) external override {
661: function repay(uint256 tokenId, uint256 amount, bool isShare, bytes calldata permitData) external override {
685: function liquidate(LiquidateParams calldata params) external override returns (uint256 amount0, uint256 amount1) {
```
[195](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L195) | [219](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L219) | [231](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L231) | [258](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L258) | [264](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L264) | [271](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L271) | [277](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L277) | [284](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L284) | [289](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L289) | [295](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L295) | [301](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L301) | [312](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L312) | [323](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L323) | [329](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L329) | [334](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L334) | [340](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L340) | [346](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L346) | [352](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L352) | [360](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L360) | [366](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L366) | [372](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L372) | [378](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L378) | [384](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L384) | [390](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L390) | [400](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L400) | [410](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L410) | [429](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L429) | [483](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L483) | [497](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L497) | [550](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L550) | [609](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L609) | [652](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L652) | [661](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L661) | [685](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L685)

```solidity
File: src/V3Oracle.sol

95: function getValue(uint256 tokenId, address token)
        external
        view
        override
        returns (uint256 value, uint256 feeValue, uint256 price0X96, uint256 price1X96)
    {
162: function getPositionBreakdown(uint256 tokenId)
        public
        view
        override
        returns (
            address token0,
            address token1,
            uint24 fee,
            uint128 liquidity,
            uint256 amount0,
            uint256 amount1,
            uint128 fees0,
            uint128 fees1
        )
    {
```
[95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L95) | [162](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L162)

```solidity
File: src/InterestRateModel.sol

58: function getRatesPerSecondX96(uint256 cash, uint256 debt)
        public
        view
        override
        returns (uint256 borrowRateX96, uint256 supplyRateX96)
    {
```
[58](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L58)

```solidity
File: src/transformers/AutoCompound.sol

227: function withdrawBalances(address[] calldata tokens, address to) external override nonReentrant {
```
[227](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L227)

```solidity
File: src/transformers/V3Utils.sol

356: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
    {
```
[356](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L356)

```solidity
File: src/utils/Swapper.sol

156: function uniswapV3SwapCallback(int256 amount0Delta, int256 amount1Delta, bytes calldata data) external override {
```
[156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L156)
</details>

### [N-85] Setters should prevent re-setting of the same value

Setter functions should include a condition to check if the new value being assigned is different from the current value. This practice prevents redundant state changes and the emission of unnecessary events, ensuring that changes only occur when actual updates to the values are made.

This not only helps to maintain the integrity of the contract's state but also keeps the event logs cleaner and more meaningful by avoiding the recording of identical consecutive values. Such an approach can improve the clarity and efficiency of debugging and data tracking processes.

<details>
<summary><i>25 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit Missing `active` check before state change
796: transformerAllowList[transformer] = active;
/// @audit Missing `_minLoanSize` check before state change
817: minLoanSize = _minLoanSize;
/// @audit Missing `_globalLendLimit` check before state change
819: globalLendLimit = _globalLendLimit;
/// @audit Missing `_globalDebtLimit` check before state change
820: globalDebtLimit = _globalDebtLimit;
/// @audit Missing `_dailyLendIncreaseLimitMin` check before state change
821: dailyLendIncreaseLimitMin = _dailyLendIncreaseLimitMin;
/// @audit Missing `_dailyDebtIncreaseLimitMin` check before state change
822: dailyDebtIncreaseLimitMin = _dailyDebtIncreaseLimitMin;
/// @audit Missing `_reserveFactorX32` check before state change
838: reserveFactorX32 = _reserveFactorX32;
/// @audit Missing `_reserveProtectionFactorX32` check before state change
848: reserveProtectionFactorX32 = _reserveProtectionFactorX32;
/// @audit Missing `admin` check before state change
871: emergencyAdmin = admin;
/// @audit Missing `lendExchangeRateX96` check before state change
1225: uint256 lentAssets = _convertToAssets(totalSupply(), lendExchangeRateX96, Math.Rounding.Up);
/// @audit Missing `debtExchangeRateX96` check before state change
1229: && _convertToAssets(tokenConfigs[token0].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
                            > lentAssets * collateralValueLimitFactorX32 / Q32
                ) {
                    revert CollateralValueLimit();
/// @audit Missing `debtExchangeRateX96` check before state change
1237: && _convertToAssets(tokenConfigs[token1].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
                            > lentAssets * collateralValueLimitFactorX32 / Q32
                ) {
                    revert CollateralValueLimit();
```
[796](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L796) | [817](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L817) | [819](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L819) | [820](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L820) | [821](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L821) | [822](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L822) | [838](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L838) | [848](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L848) | [871](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L871) | [1225](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1225) | [1229](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1229) | [1237](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1237)

```solidity
File: src/V3Oracle.sol

/// @audit Missing `_maxPoolPriceDifference` check before state change
189: maxPoolPriceDifference = _maxPoolPriceDifference;
/// @audit Missing `admin` check before state change
266: emergencyAdmin = admin;
```
[189](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L189) | [266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L266)

```solidity
File: src/InterestRateModel.sol

/// @audit Missing `baseRatePerYearX96` check before state change
94: baseRatePerSecondX96 = baseRatePerYearX96 / YEAR_SECS;
/// @audit Missing `multiplierPerYearX96` check before state change
96: multiplierPerSecondX96 = multiplierPerYearX96 / YEAR_SECS;
/// @audit Missing `jumpMultiplierPerYearX96` check before state change
97: jumpMultiplierPerSecondX96 = jumpMultiplierPerYearX96 / YEAR_SECS;
/// @audit Missing `_kinkX96` check before state change
98: kinkX96 = _kinkX96;
```
[94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L94) | [96](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L96) | [97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L97) | [98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L98)

```solidity
File: src/automators/Automator.sol

/// @audit Missing `_withdrawer` check before state change
61: withdrawer = _withdrawer;
/// @audit Missing `_active` check before state change
71: operators[_operator] = _active;
/// @audit Missing `_active` check before state change
81: vaults[_vault] = _active;
/// @audit Missing `_TWAPSeconds` check before state change
95: TWAPSeconds = _TWAPSeconds;
/// @audit Missing `_maxTWAPTickDifference` check before state change
96: maxTWAPTickDifference = _maxTWAPTickDifference;
```
[61](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L61) | [71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L71) | [81](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L81) | [95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L95) | [96](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L96)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit Missing `_totalRewardX64` check before state change
245: totalRewardX64 = _totalRewardX64;
/// @audit Missing `amount` check before state change
257: positionBalances[tokenId][token] = amount;
```
[245](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L245) | [257](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L257)
</details>

### [N-86] Use Unchecked for Divisions on Constant or Immutable Values

Unsigned divisions on constant or immutable values do not result in overflow.
Therefore, these operations can be marked as unchecked, optimizing gas usage without compromising safety.

For instance, if `a` is an unsigned integer and `b` is a constant or immutable, a / b can be safely rewritten as: unchecked { a / b }

<details>
<summary><i>20 issue instances in 3 files:</i></summary>

```solidity
File: src/V3Vault.sol

769: _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up) * reserveProtectionFactorX32 / Q32;
1100: uint256 maxPenaltyValue = debt * (Q32 + MAX_LIQUIDATION_PENALTY_X32) / Q32;
1109: + (MAX_LIQUIDATION_PENALTY_X32 - MIN_LIQUIDATION_PENALTY_X32) * penaltyFractionX96 / Q96;
1111: liquidationValue = debt * (Q32 + penaltyX32) / Q32;
1116: uint256 penaltyValue = fullValue * (Q32 - MAX_LIQUIDATION_PENALTY_X32) / Q32;
1188: + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;
1190: + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;
1230: > lentAssets * collateralValueLimitFactorX32 / Q32
1238: > lentAssets * collateralValueLimitFactorX32 / Q32
```
[769](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L769) | [1100](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1100) | [1109](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1109) | [1111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1111) | [1116](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1116) | [1188](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1188) | [1190](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1190) | [1230](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1230) | [1238](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1238)

```solidity
File: src/V3Oracle.sol

120: value = (price0X96 * (amount0 + fees0) / Q96 + price1X96 * (amount1 + fees1) / Q96) * Q96 / priceTokenX96;
120: value = (price0X96 * (amount0 + fees0) / Q96 + price1X96 * (amount1 + fees1) / Q96) * Q96 / priceTokenX96;
121: feeValue = (price0X96 * fees0 / Q96 + price1X96 * fees1 / Q96) * Q96 / priceTokenX96;
121: feeValue = (price0X96 * fees0 / Q96 + price1X96 * fees1 / Q96) * Q96 / priceTokenX96;
```
[120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L120) | [120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L120) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L121) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L121)

```solidity
File: src/InterestRateModel.sol

67: borrowRateX96 = (utilizationRateX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
69: uint256 normalRateX96 = (kinkX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
71: borrowRateX96 = (excessUtilX96 * jumpMultiplierPerSecondX96 / Q96) + normalRateX96;
74: supplyRateX96 = utilizationRateX96 * borrowRateX96 / Q96;
95: baseRatePerSecondX96 = baseRatePerYearX96 / YEAR_SECS;
96: multiplierPerSecondX96 = multiplierPerYearX96 / YEAR_SECS;
97: jumpMultiplierPerSecondX96 = jumpMultiplierPerYearX96 / YEAR_SECS;
```
[67](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L67) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L69) | [71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L71) | [74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L74) | [95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L95) | [96](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L96) | [97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L97)
</details>

### [N-87] Contracts should have full test coverage

It's recommended to have full test coverage for all contracts.
While 100% code coverage does not guarantee absence of bugs, it can catch simple bugs and reduce regressions during code modifications.
Moreover, to achieve full coverage, authors often have to refactor their code into more modular components, each testable separately.
This leads to lower interdependencies, and results in code that is easier to understand and audit.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: app/2024-03-revert-lend

1: All files
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/app/2024-03-revert-lend#L1)
</details>

### [N-88] Large or complicated code bases should implement invariant tests

Large or complex code bases should include invariant fuzzing tests, such as those provided by Echidna.
These tests require the identification of invariants that should not be violated under any circumstances, with the fuzzer testing various inputs and function calls to ensure these invariants always hold.
This is especially important for code with a lot of inline-assembly, complicated math, or complex interactions between contracts. Despite having 100% code coverage, bugs can still occur due to the order of operations a user performs.
Extensive and well-written invariant tests can significantly reduce this testing gap.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: app/2024-03-revert-lend

1: All files
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/app/2024-03-revert-lend#L1)
</details>

### [N-89] Implement Formal Verification Proofs to Improve Security

Formal verification offers a mathematical proof confirming that your code operates as intended and is devoid of edge cases 
that may lead to unintended behavior. By leveraging this rigorous audit technique, you not only enhance the robustness 
of your code but also strengthen the trust of stakeholders in the safety of your contract.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: app/2024-03-revert-lend

1: All files
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/app/2024-03-revert-lend#L1)
</details>

