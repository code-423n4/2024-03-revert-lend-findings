## Gas Findings

|    | Issue | Instances | Total Gas Saved |
|----|-------|:---------:|:---------:|
| [G-01] | Optimize Storage Layout in Structs | 5 | 100000 |
| [G-02] | Optimize Storage with Byte Truncation for Time Related State Variables | 1 | 20000 |
| [G-03] | Contract storage can use fewer slots by changing the order of state variables | 1 | 20000 |
| [G-04] | Optimize Storage Layout in Structs by Truncating Time Related Fields | 8 | 160000 |
| [G-05] | `do`-`while` is cheaper than `for`-loops when the initial check can be skipped | 2 | 510 |
| [G-06] | Use `assembly` for Efficient Event Emission | 49 | 18620 |
| [G-07] | Use custom errors rather than `require()/assert()/revert(with msg)` with string to save gas | 3 | 150 |
| [G-08] | Enable IR-based code generation | 11 | - |
| [G-09] | Avoid Explicit Initialization to Zero for Non-Constant/Non-Immutable State Variables | 13 | 37700 |
| [G-10] | Assembly: Check `msg.sender` using xor and the scratch space | 23 | 483 |
| [G-11] | Assembly: Use scratch space for building calldata | 10 | 5060 |
| [G-12] | Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct` | 9 | - |
| [G-13] | Assigning `state` variables directly with struct constructors wastes gas | 2 | 142 |
| [G-14] | Assembly: Use scratch space when building emitted events with two data arguments | 35 | 525 |
| [G-15] | Stack variable is only used once | 41 | 123 |
| [G-16] | `abi.encodePacked `is more gas efficient than `abi.encode` | 4 | 800 |
| [G-17] | Consider Using `selfbalance()` Over `address(this).balance` | 1 | - |
| [G-18] | Use `assembly` to write mutable storage values | 50 | 550 |
| [G-19] | Using `delete` on a `uint/int` variable is cheaper than assigning it to `0` | 5 | 40 |
| [G-20] | Use `revert()` to gain maximum gas savings | 105 | 5250 |
| [G-21] | `x.a = x.a + b` always cheaper than `x.a += b` for Structs | 14 | 70 |
| [G-22] | Using `constants` instead of `enum` can save gas | 2 | 0 |
| [G-23] | Create variable outside the loop | 2 | 40 |
| [G-24] | Counting down when iterating, saves gas | 2 | 18 |
| [G-25] | Using `> 0` costs more gas than `!= 0` when used on a `uint` in a `require()` statement | 1 | 6 |
| [G-26] | `>=` costs less gas than `>` | 56 | 336 |
| [G-27] | Consider pre-calculating the address of `address(this)` to save gas | 58 | 0 |
| [G-28] | Use `unchecked` for Non-Loop Increment/Decrement Operations | 3 | 90 |
| [G-29] | Using `this` to access functions results in an external call, wasting gas | 1 | 100 |
| [G-30] | Constructors can be marked `payable` | 11 | 264 |
| [G-31] | Split `revert` checks to save gas | 13 | - |
| [G-32] | Multiple accesses of a mapping/array should use a local variable cache | 30 | 4200 |
| [G-33] | Reduce gas usage by moving to Solidity 0.8.19 or later | 11 | - |
| [G-34] | Reduce deployment costs by tweaking contracts' metadata | 11 | 116600 |
| [G-35] | Use Pre-Increment/Decrement (++i/--i) to Save Gas | 3 | 15 |
| [G-36] | Nesting `if`-statements is cheaper than using `&&` | 18 | 108 |
| [G-37] | Use `storage` instead of `memory` for state structs/arrays | 3 | 6300 |
| [G-38] | Optimize by Using Assembly for Low-Level Calls' Return Data | 5 | 795 |
| [G-39] | Avoid transferring amounts of zero in order to save gas | 10 | 1000 |
| [G-40] | `>=` costs less gas than `>` | 71 | 213 |
| [G-41] | Cache Function Calls for Efficiency | 20 | - |
| [G-42] | Unutilized Named Return Variables Waste Gas Without Optimizer | 8 | - |
| [G-43] | Use `unchecked` for Math Operations if they already checked | 21 | 1785 |
| [G-44] | Using `private` rather than `public`, saves gas | 66 | 1452000 |
| [G-45] | Refactor duplicated require()/revert() checks to save gas | 10 | - |
| [G-46] | Use Assembly for Efficient Memory Management in Multiple External Calls | 13 | 36000 |
| [G-47] | Optimize `require/revert` Statements with Assembly | 3 | 1200 |
| [G-48] | Simple checks for zero `uint` can be done using `assembly` to save gas | 21 | 84 |
| [G-49] | Consider using solady's `FixedPointMathLib` | 143 | - |
| [G-50] | Avoid Zero to Non-Zero Storage Writes Where Possible | 28 | 685100 |
| [G-51] | Consider Packing Small `uint` When it's Possible | 4 | 83200 |
| [G-52] | Consider Using `calldata` Instead of `memory` for Function Parameters | 1 | 300 |
| [G-53] | Use `unchecked` for division which do not divide by -X sonce they can't overflow | 70 | 1400 |
| [G-54] | Use solady library where possible to save gas | 21 | 21000 |
| [G-55] | Avoid Inverting `if`-`else` Conditions | 1 | 3 |
| [G-56] | Use `uint256(1)`/`uint256(2)` instead of `true`/`false` to save gas for changes | 4 | 68000 |
| [G-57] | Use Bit Shifting for Multiplication by Powers of Two | 2 | 40 |
| [G-58] | Avoid contract existence checks by using low-level calls | 181 | 18100 |
| [G-59] | Mark Functions That Revert For Normal Users As `payable` | 15 | 315 |
| [G-60] | Prefer `private` over `public` for Constants to Save Gas | 13 | 39000 |
| [G-61] | `<x> += <y>` costs more gas than `<x> = <x> + <y>` for state variables | 7 | 791 |
| [G-62] | Using `bool`s for storage incurs overhead | 4 | 400 |
| [G-63] | Optimize Gas by Using Only Named Returns | 31 | 1364 |
| [G-64] | Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead | 86 | 516 |
| [G-65] | Unlimited gas consumption risk due to external call recipients | 3 | - |
| [G-66] | Use assembly to check for `address(0)` | 6 | 348 |
| [G-67] | `internal`/`private` functions only called once can be inlined to save gas | 18 | 360 |
| [G-68] | Consider using OZ EnumerateSet in place of nested mappings | 2 | 2000 |
| [G-69] | Declare `immutable` as `private` to save gas | 17 | 51000 |
| [G-70] | State variables should be cached in stack rather than re-reading them from storage | 17 | 2425 |
| [G-71] | Optimize names to save gas | 11 | 220 |
| [G-72] | Avoid updating storage when the value hasn't changed | 22 | 20000 |
| [G-73] | Optimize External Calls with Assembly for Memory Efficiency | 31 | 6820 |

Total: 1603 instances of 73 issues with 2993879 gas saved

## Gas Findings Details

### [G-01] Optimize Storage Layout in Structs

The field ordering within the following structs isn't optimized for efficient storage in the Ethereum Virtual Machine (EVM). By appropriately rearranging the fields within these structs, you can achieve improved gas efficiency during interactions with these structs. 

In the context of EVM, a well-structured and optimized struct can save a substantial amount of gas. For instance, packing the struct into fewer storage slots could avoid an extra SSTORE operation (costing 20000 gas) during the first setting of the struct. Subsequent read and write operations also experience reduced gas consumption due to optimized struct layout.

Please consider rearranging the fields in the identified structs to capitalize on these potential gas savings and improve overall contract performance.

<details>
<summary><i>5 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Oracle.sol

/// @audit - Struct used 6 storage slots, but can be packed to 4 storage slots.
//	struct TokenConfig {
//	    Mode mode;
//	    IUniswapV3Pool pool;
//	    AggregatorV3Interface feed;
//	    uint32 twapSeconds;
//	    uint32 maxFeedAge;
//	    uint16 maxDifference;
//	    uint8 tokenDecimals;
//	    uint8 feedDecimals;
//	    bool isToken0;
//	}
43: struct TokenConfig {
        AggregatorV3Interface feed; // chainlink feed
        uint32 maxFeedAge;
        uint8 feedDecimals;
        uint8 tokenDecimals;
        IUniswapV3Pool pool; // reference pool
        bool isToken0;
        uint32 twapSeconds;
        Mode mode;
        uint16 maxDifference; // max price difference x10000
    }
```
[43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L43)

```solidity
File: src/automators/AutoExit.sol

/// @audit - Struct used 7 storage slots, but can be packed to 6 storage slots.
//	struct ExecuteParams {
//	    uint256 deadline;
//	    uint256 amountRemoveMin1;
//	    uint256 amountRemoveMin0;
//	    bytes swapData;
//	    uint256 tokenId;
//	    uint128 liquidity;
//	    uint64 rewardX64;
//	}
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
[63](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L63)

```solidity
File: src/transformers/AutoRange.sol

/// @audit - Struct used 9 storage slots, but can be packed to 7 storage slots.
//	struct ExecuteParams {
//	    uint256 deadline;
//	    uint256 amountRemoveMin1;
//	    uint256 amountRemoveMin0;
//	    bytes swapData;
//	    uint256 amountIn;
//	    uint256 tokenId;
//	    uint128 liquidity;
//	    uint64 rewardX64;
//	    bool swap0To1;
//	}
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
[53](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L53)

```solidity
File: src/transformers/V3Utils.sol

/// @audit - Struct used 8 storage slots, but can be packed to 7 storage slots.
//	struct SwapParams {
//	    bytes permitData;
//	    bytes swapData;
//	    uint256 minAmountOut;
//	    uint256 amountIn;
//	    IERC20 tokenOut;
//	    IERC20 tokenIn;
//	    address recipient;
//	    bool unwrap;
//	}
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
/// @audit - Struct used 19 storage slots, but can be packed to 18 storage slots.
//	struct SwapAndMintParams {
//	    bytes permitData;
//	    bytes returnData;
//	    uint256 amountAddMin1;
//	    uint256 amountAddMin0;
//	    bytes swapData1;
//	    uint256 amountOut1Min;
//	    uint256 amountIn1;
//	    bytes swapData0;
//	    uint256 amountOut0Min;
//	    uint256 amountIn0;
//	    IERC20 swapSourceToken;
//	    uint256 deadline;
//	    uint256 amount1;
//	    uint256 amount0;
//	    IERC20 token1;
//	    IERC20 token0;
//	    address recipientNFT;
//	    int24 tickUpper;
//	    int24 tickLower;
//	    uint24 fee;
//	    address recipient;
//	}
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
```
[382](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L382) | [432](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L432)
</details>

### [G-02] Optimize Storage with Byte Truncation for Time Related State Variables

Certain state variables, particularly timestamps, can be safely stored using `uint32`. 
By optimizing these variables, contracts can utilize storage more efficiently.
This not only results in a reduction in the initial gas costs (due to fewer Gsset operations) but also provides savings in subsequent read and write operations.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit - State variables after packing use 22 storage slots, but can be packed to 17 storage slots.
//	mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals;
//	mapping(address => bool) public transformerAllowList;
//	uint256 private transformedTokenId = 0;
//	mapping(uint256 => address) private tokenOwner;
//	mapping(uint256 => uint256) private ownedTokensIndex;
//	mapping(address => uint256[]) private ownedTokens;
//	mapping(uint256 => Loan) public loans;
//	uint256 public dailyDebtIncreaseLimitLastReset = 0;
//	uint256 public dailyDebtIncreaseLimitLeft = 0;
//	uint256 public dailyDebtIncreaseLimitMin = 0;
//	uint256 public minLoanSize = 0;
//	uint256 public globalDebtLimit = 0;
//	uint256 public lastDebtExchangeRateX96 = Q96;
//	uint256 public debtSharesTotal = 0;
//	mapping(address => TokenConfig) public tokenConfigs;
//	address public emergencyAdmin;
//	uint32 public dailyLendIncreaseLimitLastReset = 0;
//	uint32 public dailyLendIncreaseLimitLeft = 0;
//	uint32 public dailyLendIncreaseLimitMin = 0;
//	uint32 public globalLendLimit = 0;
//	uint32 public lastLendExchangeRateX96 = Q96;
//	uint32 public lastExchangeRateUpdate = 0;
//	uint32 public reserveProtectionFactorX32 = MIN_RESERVE_PROTECTION_FACTOR_X32;
//	uint32 public reserveFactorX32 = 0;

30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
```
[30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30)
</details>

### [G-03] Contract storage can use fewer slots by changing the order of state variables

The reduction of slots can reduce the gas consumption of each storage read/write operation.
If variables occupying the same slot are written within the same transaction, avoids a separate Gsset (20000 gas).
Reads of the variables can also be cheaper.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit - State variables use 23 storage slots, but can be packed to 22 storage slots.
//	mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals
//	mapping(address => bool) public transformerAllowList
//	uint256 private transformedTokenId = 0
//	mapping(uint256 => address) private tokenOwner
//	mapping(uint256 => uint256) private ownedTokensIndex
//	mapping(address => uint256[]) private ownedTokens
//	mapping(uint256 => Loan) public loans
//	uint256 public dailyDebtIncreaseLimitLastReset = 0
//	uint256 public dailyDebtIncreaseLimitLeft = 0
//	uint256 public dailyDebtIncreaseLimitMin = 0
//	uint256 public dailyLendIncreaseLimitLastReset = 0
//	uint256 public dailyLendIncreaseLimitLeft = 0
//	uint256 public dailyLendIncreaseLimitMin = 0
//	uint256 public minLoanSize = 0
//	uint256 public globalLendLimit = 0
//	uint256 public globalDebtLimit = 0
//	uint256 public lastLendExchangeRateX96 = Q96
//	uint256 public lastDebtExchangeRateX96 = Q96
//	uint256 public lastExchangeRateUpdate = 0
//	uint256 public debtSharesTotal = 0
//	mapping(address => TokenConfig) public tokenConfigs
//	address public emergencyAdmin
//	uint32 public reserveProtectionFactorX32 = MIN_RESERVE_PROTECTION_FACTOR_X32
//	uint32 public reserveFactorX32 = 0

30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
```
[30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L30)
</details>

### [G-04] Optimize Storage Layout in Structs by Truncating Time Related Fields

The field ordering within the following structs isn't optimized for efficient storage in the Ethereum Virtual Machine (EVM). By appropriately rearranging the fields within these structs, you can achieve improved gas efficiency during interactions with these structs. 

In the context of EVM, a well-structured and optimized struct can save a substantial amount of gas. For instance, packing the struct into fewer storage slots could avoid an extra SSTORE operation (costing 20000 gas) during the first setting of the struct. Subsequent read and write operations also experience reduced gas consumption due to optimized struct layout.

Please consider rearranging the fields in the identified structs to capitalize on these potential gas savings and improve overall contract performance.

<details>
<summary><i>8 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit - Packed struct used 11 storage slots, but can be packed to 10 storage slots.
//	struct LiquidateState {
//	    uint256 feeValue;
//	    uint256 collateralValue;
//	    uint256 fullValue;
//	    uint256 missing;
//	    uint256 reserveCost;
//	    uint256 liquidatorCost;
//	    uint256 liquidationValue;
//	    uint256 debt;
//	    uint256 newDebtExchangeRateX96;
//	    uint32 newLendExchangeRateX96;
//	    bool isHealthy;
//	}
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
[666](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L666)

```solidity
File: src/automators/AutoExit.sol

/// @audit - Packed struct used 6 storage slots, but can be packed to 5 storage slots.
//	struct ExecuteParams {
//	    uint256 amountRemoveMin1;
//	    uint256 amountRemoveMin0;
//	    bytes swapData;
//	    uint256 tokenId;
//	    uint128 liquidity;
//	    uint64 rewardX64;
//	    uint32 deadline;
//	}
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
[63](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L63)

```solidity
File: src/transformers/AutoRange.sol

/// @audit - Packed struct used 7 storage slots, but can be packed to 6 storage slots.
//	struct ExecuteParams {
//	    uint256 amountRemoveMin1;
//	    uint256 amountRemoveMin0;
//	    bytes swapData;
//	    uint256 amountIn;
//	    uint256 tokenId;
//	    uint128 liquidity;
//	    uint64 rewardX64;
//	    uint32 deadline;
//	    bool swap0To1;
//	}
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
[53](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L53)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit - Packed struct used 12 storage slots, but can be packed to 11 storage slots.
//	struct LeverageUpParams {
//	    uint256 amountAddMin1;
//	    uint256 amountAddMin0;
//	    bytes swapData1;
//	    uint256 amountOut1Min;
//	    uint256 amountIn1;
//	    bytes swapData0;
//	    uint256 amountOut0Min;
//	    uint256 amountIn0;
//	    uint256 borrowAmount;
//	    uint256 tokenId;
//	    address recipient;
//	    uint32 deadline;
//	}
17: struct LeverageUpParams {
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
/// @audit - Packed struct used 13 storage slots, but can be packed to 12 storage slots.
//	struct LeverageDownParams {
//	    bytes swapData1;
//	    uint256 amountOut1Min;
//	    uint256 amountIn1;
//	    bytes swapData0;
//	    uint256 amountOut0Min;
//	    uint256 amountIn0;
//	    uint256 amountRemoveMin1;
//	    uint256 amountRemoveMin0;
//	    uint256 tokenId;
//	    address recipient;
//	    uint32 deadline;
//	    uint128 feeAmount1;
//	    uint128 feeAmount0;
//	    uint128 liquidity;
//	}
98: struct LeverageDownParams {
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
[17](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L17) | [98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L98)

```solidity
File: src/transformers/V3Utils.sol

/// @audit - Packed struct used 19 storage slots, but can be packed to 18 storage slots.
//	struct Instructions {
//	    bytes swapAndMintReturnData;
//	    bytes returnData;
//	    uint256 amountAddMin1;
//	    uint256 amountAddMin0;
//	    bytes swapData1;
//	    uint256 amountOut1Min;
//	    uint256 amountIn1;
//	    bytes swapData0;
//	    uint256 amountOut0Min;
//	    uint256 amountIn0;
//	    uint256 amountRemoveMin1;
//	    uint256 amountRemoveMin0;
//	    WhatToDo whatToDo;
//	    address recipientNFT;
//	    uint32 deadline;
//	    int24 tickUpper;
//	    int24 tickLower;
//	    bool unwrap;
//	    address recipient;
//	    uint24 fee;
//	    address targetToken;
//	    uint128 liquidity;
//	    uint128 feeAmount1;
//	    uint128 feeAmount0;
//	}
48: struct Instructions {
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
        uint256 deadline;
        // left over tokens will be sent to this address
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
/// @audit - Packed struct used 18 storage slots, but can be packed to 17 storage slots.
//	struct SwapAndMintParams {
//	    bytes permitData;
//	    bytes returnData;
//	    uint256 amountAddMin1;
//	    uint256 amountAddMin0;
//	    bytes swapData1;
//	    uint256 amountOut1Min;
//	    uint256 amountIn1;
//	    bytes swapData0;
//	    uint256 amountOut0Min;
//	    uint256 amountIn0;
//	    IERC20 swapSourceToken;
//	    uint256 amount1;
//	    uint256 amount0;
//	    IERC20 token1;
//	    IERC20 token0;
//	    address recipientNFT;
//	    uint32 deadline;
//	    int24 tickUpper;
//	    int24 tickLower;
//	    address recipient;
//	    uint24 fee;
//	}
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
/// @audit - Packed struct used 15 storage slots, but can be packed to 14 storage slots.
//	struct SwapAndIncreaseLiquidityParams {
//	    bytes permitData;
//	    uint256 amountAddMin1;
//	    uint256 amountAddMin0;
//	    bytes swapData1;
//	    uint256 amountOut1Min;
//	    uint256 amountIn1;
//	    bytes swapData0;
//	    uint256 amountOut0Min;
//	    uint256 amountIn0;
//	    IERC20 swapSourceToken;
//	    uint256 amount1;
//	    uint256 amount0;
//	    uint256 tokenId;
//	    address recipient;
//	    uint32 deadline;
//	}
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
```
[48](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L48) | [432](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L432) | [504](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L504)
</details>

### [G-05] `do`-`while` is cheaper than `for`-loops when the initial check can be skipped

Using `do-while` loops instead of `for` loops can be more gas-efficient. 
Even if you add an `if` condition to account for the case where the loop doesn't execute at all, a `do-while` loop can still be cheaper in terms of gas.

Example:
```solidity
/// 774 gas cost
function forLoop() public pure {
    for (uint256 i; i < 10;) {
        unchecked {
            ++i;
        }
    }
}
/// 519 gas cost
function doWhileLoop() public pure {
    uint256 i;
    do {
        unchecked {
            ++i;
        }
    } while (i < 10);
}
```

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/automators/Automator.sol

111: for (; i < count; ++i)
```
[111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L111)

```solidity
File: src/transformers/AutoCompound.sol

233: for (; i < count; ++i)
```
[233](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L233)
</details>

### [G-06] Use `assembly` for Efficient Event Emission

To efficiently emit events, consider utilizing assembly by making use of scratch space and the free memory pointer.
This approach can potentially avoid the costs associated with memory expansion.

However, it's crucial to cache and restore the free memory pointer for safe optimization.
Good examples of such practices can be found in well-optimized [Solady's codebases](https://github.com/Vectorized/solady/blob/main/src/tokens/ERC1155.sol#L167).
Please review your code and consider the potential gas savings of this approach.

<details>
<summary><i>49 issue instances in 9 files:</i></summary>

```solidity
File: src/V3Vault.sol

449: emit Add(tokenId, owner, 0)
464: emit Add(tokenId, owner, oldTokenId)
489: emit ApprovedTransform(tokenId, msg.sender, target, isActive)
601: emit Borrow(tokenId, owner, assets, shares)
645: emit WithdrawCollateral(params.tokenId, owner, params.recipient, params.liquidity, amount0, amount1)
746: emit Liquidate(
            params.tokenId,
            msg.sender,
            owner,
            state.fullValue,
            state.liquidatorCost,
            amount0,
            amount1,
            state.reserveCost,
            state.missing
        )
782: emit WithdrawReserves(amount, receiver)
798: emit SetTransformer(transformer, active)
830: emit SetLimits(
            _minLoanSize, _globalLendLimit, _globalDebtLimit, _dailyLendIncreaseLimitMin, _dailyDebtIncreaseLimitMin
        )
839: emit SetReserveFactor(_reserveFactorX32)
849: emit SetReserveProtectionFactor(_reserveProtectionFactorX32)
865: emit SetTokenConfig(token, collateralFactorX32, collateralValueLimitFactorX32)
872: emit SetEmergencyAdmin(admin)
916: emit Deposit(msg.sender, receiver, assets, shares)
951: emit Withdraw(msg.sender, receiver, owner, assets, shares)
1013: emit Repay(tokenId, msg.sender, owner, assets, shares)
1084: emit Remove(tokenId, owner)
1139: emit ExchangeRateUpdate(newDebtExchangeRateX96, newLendExchangeRateX96)
1160: emit ExchangeRateUpdate(newDebtExchangeRateX96, newLendExchangeRateX96)
```
[449](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L449) | [464](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L464) | [489](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L489) | [601](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L601) | [645](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L645) | [746](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L746) | [782](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L782) | [798](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L798) | [830](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L830) | [839](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L839) | [849](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L849) | [865](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L865) | [872](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L872) | [916](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L916) | [951](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L951) | [1013](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1013) | [1084](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1084) | [1139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1139) | [1160](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1160)

```solidity
File: src/V3Oracle.sol

190: emit SetMaxPoolPriceDifference(_maxPoolPriceDifference)
242: emit TokenConfigUpdated(token, config)
243: emit OracleModeUpdated(token, mode)
260: emit OracleModeUpdated(token, mode)
267: emit SetEmergencyAdmin(admin)
```
[190](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L190) | [242](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L242) | [243](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L243) | [260](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L260) | [267](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L267)

```solidity
File: src/InterestRateModel.sol

100: emit SetValues(baseRatePerYearX96, multiplierPerYearX96, jumpMultiplierPerYearX96, _kinkX96)
```
[100](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L100)

```solidity
File: src/automators/AutoExit.sol

208: emit PositionConfigured(params.tokenId, false, false, false, 0, 0, 0, 0, false, 0)
211: emit Executed(
            params.tokenId, msg.sender, state.isSwap, state.amount0, state.amount1, state.token0, state.token1
        )
232: emit PositionConfigured(
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
        )
```
[208](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L208) | [211](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L211) | [232](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L232)

```solidity
File: src/automators/Automator.sol

60: emit WithdrawerChanged(_withdrawer)
70: emit OperatorChanged(_operator, _active)
80: emit VaultChanged(_vault, _active)
94: emit TWAPConfigChanged(_TWAPSeconds, _maxTWAPTickDifference)
```
[60](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L60) | [70](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L70) | [80](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L80) | [94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L94)

```solidity
File: src/transformers/AutoCompound.sol

183: emit AutoCompounded(
            msg.sender,
            params.tokenId,
            state.compounded0,
            state.compounded1,
            state.amount0Fees,
            state.amount1Fees,
            state.token0,
            state.token1
        )
246: emit RewardUpdated(msg.sender, _totalRewardX64)
251: emit BalanceAdded(tokenId, token, amount)
259: emit BalanceAdded(tokenId, token, amount - currentBalance)
261: emit BalanceRemoved(tokenId, token, currentBalance - amount)
271: emit BalanceRemoved(tokenId, token, amount)
273: emit BalanceWithdrawn(tokenId, token, to, amount)
```
[183](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L183) | [246](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L246) | [251](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L251) | [259](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L259) | [261](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L261) | [271](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L271) | [273](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L273)

```solidity
File: src/transformers/AutoRange.sol

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
            )
266: emit PositionConfigured(params.tokenId, 0, 0, 0, 0, 0, 0, false, 0)
268: emit RangeChanged(params.tokenId, state.newTokenId)
286: emit PositionConfigured(
            tokenId,
            config.lowerTickLimit,
            config.upperTickLimit,
            config.lowerTickDelta,
            config.upperTickDelta,
            config.token0SlippageX64,
            config.token1SlippageX64,
            config.onlyFees,
            config.maxRewardX64
        )
```
[252](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L252) | [266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L266) | [268](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L268) | [286](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L286)

```solidity
File: src/transformers/V3Utils.sol

218: emit CompoundFees(tokenId, liquidity, amount0, amount1)
303: emit ChangeRange(tokenId, newTokenId)
348: emit WithdrawAndCollectAndSwap(tokenId, instructions.targetToken, targetAmount)
729: emit SwapAndMint(tokenId, liquidity, added0, added1)
773: emit SwapAndIncreaseLiquidity(params.tokenId, liquidity, added0, added1)
```
[218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L218) | [303](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L303) | [348](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L348) | [729](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L729) | [773](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L773)

```solidity
File: src/utils/Swapper.sol

116: emit Swap(address(params.tokenIn), address(params.tokenOut), amountInDelta, amountOutDelta)
```
[116](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L116)
</details>

### [G-07] Use custom errors rather than `require()/assert()/revert(with msg)` with string to save gas

Custom errors are available from solidity version 0.8.4.
Custom errors save [~50](https://gist.github.com/IllIllI000/ad1bd0d29a0101b25e57c293b4b0c746) gas each time they're hit by [avoiding having to allocate and store the revert string](https://soliditylang.org/blog/2021/04/21/custom-errors/#errors-in-depth).
Alse Custom error are cheaper than `assert()`.
```solidity
    revert CustomError(); // 157 gas
    assert(false); // 164 gas
    revert("Custom Error"); // 406 gas
    require(false, "Custom Error"); // 421 gas
```


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

### [G-08] Enable IR-based code generation

The `--via-ir` command line option activates the IR-based code generator in Solidity, which is designed to enable powerful optimization passes that can span across functions. The end result may be a contract that requires less gas to execute its functions.

We recommend you enable this feature, run tests, and benchmark the gas usage of your contract to evaluate if it leads to any tangible gas savings. Experimenting with this feature could lead to a more gas-efficient contract.

[Solidity Documentation](https://docs.soliditylang.org/en/v0.8.20/ir-breaking-changes.html#solidity-ir-based-codegen-changes).

<details>
<summary><i>11 issue instances in 1 files:</i></summary>

```solidity

File: src/V3Vault.sol
File: src/V3Oracle.sol
File: src/InterestRateModel.sol
File: src/automators/AutoExit.sol
File: src/automators/Automator.sol
File: src/transformers/AutoCompound.sol
File: src/transformers/AutoRange.sol
File: src/transformers/LeverageTransformer.sol
File: src/transformers/V3Utils.sol
File: src/utils/FlashloanLiquidator.sol
File: src/utils/Swapper.sol
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1) | [1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L1) | [1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L1) | [1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L1) | [1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L1) | [1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L1) | [1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L1) | [1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L1) | [1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L1) | [1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L1) | [1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L1)
</details>

### [G-09] Avoid Explicit Initialization to Zero for Non-Constant/Non-Immutable State Variables

Explicitly initializing non-constant/non-immutable state variables to zero is not efficient from a gas perspective. 
Letting Solidity use the default zero for uninitialized storage variables avoids a Gsreset, which costs 2900 gas, during deployment.
Consider removing these unnecessary initializations to optimize gas usage.
```solidity
    uint256 public foo = 0; // tx 69107 gas | exec 14669 gas
    uint256 public foo;     // tx 66854 gas | exec 12464 gas
``` 

<details>
<summary><i>13 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

118: uint32 public reserveFactorX32 = 0
124: uint256 public debtSharesTotal = 0
127: uint256 public lastExchangeRateUpdate = 0
131: uint256 public globalDebtLimit = 0
132: uint256 public globalLendLimit = 0
135: uint256 public minLoanSize = 0
138: uint256 public dailyLendIncreaseLimitMin = 0
139: uint256 public dailyLendIncreaseLimitLeft = 0
140: uint256 public dailyLendIncreaseLimitLastReset = 0
143: uint256 public dailyDebtIncreaseLimitMin = 0
144: uint256 public dailyDebtIncreaseLimitLeft = 0
145: uint256 public dailyDebtIncreaseLimitLastReset = 0
161: uint256 private transformedTokenId = 0
```
[118](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L118) | [124](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L124) | [127](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L127) | [131](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L131) | [132](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L132) | [135](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L135) | [138](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L138) | [139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L139) | [140](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L140) | [143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L143) | [144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L144) | [145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L145) | [161](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L161)
</details>

### [G-10] Assembly: Check `msg.sender` using xor and the scratch space

See [this](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender) prior finding for details on the conversion

<details>
<summary><i>23 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

419: if (msg.sender != owner) {
435: if (msg.sender != address(nonfungiblePositionManager) || from == address(this)) {
484: if (tokenOwner[tokenId] != msg.sender) {
515: if (loanOwner != msg.sender && !transformApprovals[loanOwner][tokenId][msg.sender]) {
561: if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {
561: if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {
621: if (owner != msg.sender) {
814: if (msg.sender != emergencyAdmin && msg.sender != owner()) {
814: if (msg.sender != emergencyAdmin && msg.sender != owner()) {
935: if (msg.sender != owner) {
```
[419](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L419) | [435](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L435) | [484](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L484) | [515](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L515) | [561](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L561) | [561](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L561) | [621](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L621) | [814](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L814) | [814](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L814) | [935](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L935)

```solidity
File: src/V3Oracle.sol

250: if (msg.sender != emergencyAdmin && msg.sender != owner()) {
250: if (msg.sender != emergencyAdmin && msg.sender != owner()) {
```
[250](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L250) | [250](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L250)

```solidity
File: src/automators/AutoExit.sol

220: if (owner != msg.sender) {
```
[220](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L220)

```solidity
File: src/automators/Automator.sol

105: if (msg.sender != withdrawer) {
124: if (msg.sender != withdrawer) {
245: if (owner != msg.sender) {
252: if (msg.sender != address(weth)) {
```
[105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L105) | [124](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L124) | [245](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L245) | [252](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L252)

```solidity
File: src/transformers/AutoCompound.sol

205: if (owner != msg.sender) {
228: if (msg.sender != withdrawer) {
```
[205](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L205) | [228](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L228)

```solidity
File: src/transformers/V3Utils.sol

102: if (nonfungiblePositionManager.ownerOf(tokenId) != msg.sender) {
362: if (msg.sender != address(nonfungiblePositionManager)) {
915: if (msg.sender != address(weth)) {
```
[102](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L102) | [362](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L362) | [915](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L915)

```solidity
File: src/utils/Swapper.sol

161: if (address(_getPool(tokenIn, tokenOut, fee)) != msg.sender) {
```
[161](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L161)
</details>

### [G-11] Assembly: Use scratch space for building calldata

If an external call's calldata can fit into two or fewer words, use the scratch space to build the calldata, rather than allowing Solidity to do a memory expansion.

<details>
<summary><i>10 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

1049: (,,, liquidity,,, fees0, fees1) = oracle.getPositionBreakdown(tokenId)
1275: (fullValue, feeValue,,) = oracle.getValue(tokenId, address(asset))
```
[1049](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1049) | [1275](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1275)

```solidity
File: src/automators/AutoExit.sol

120: (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
            nonfungiblePositionManager.positions(params.tokenId)
```
[120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L120)

```solidity
File: src/automators/Automator.sol

148: (sqrtPriceX96, currentTick,,,,,) = pool.slot0()
```
[148](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L148)

```solidity
File: src/transformers/AutoCompound.sol

115: (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper,,,,,) =
            nonfungiblePositionManager.positions(params.tokenId)
129: (state.sqrtPriceX96, state.tick,,,,,) = pool.slot0()
163: (, state.compounded0, state.compounded1) = nonfungiblePositionManager.increaseLiquidity(
                    INonfungiblePositionManager.IncreaseLiquidityParams(
                        params.tokenId, state.maxAddAmount0, state.maxAddAmount1, 0, 0, block.timestamp
                    )
                )
209: (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(tokenId)
```
[115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L115) | [129](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L129) | [163](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L163) | [209](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L209)

```solidity
File: src/transformers/AutoRange.sol

130: (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
            nonfungiblePositionManager.positions(params.tokenId)
217: (state.newTokenId,, state.amountAdded0, state.amountAdded1) = nonfungiblePositionManager.mint(mintParams)
```
[130](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L130) | [217](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L217)
</details>

### [G-12] Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`

Combining multiple address/ID mappings into a single mapping to a struct can lead to gas savings.
By refactoring multiple mappings into a singular mapping with a struct, you can save on storage slots, which in turn can reduce the gas cost in certain operations.
Prioritize this refactor if optimizing gas is a primary concern for your contract's operations.

<details>
<summary><i>9 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

154: mapping(uint256 => Loan) public loans
158: mapping(uint256 => uint256) private ownedTokensIndex
159: mapping(uint256 => address) private tokenOwner
115: mapping(address => TokenConfig) public tokenConfigs
157: mapping(address => uint256[]) private ownedTokens
163: mapping(address => bool) public transformerAllowList
164: mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals
```
[154](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L154) | [158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L158) | [159](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L159) | [115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L115) | [157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L157) | [163](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L163) | [164](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L164)

```solidity
File: src/automators/Automator.sol

34: mapping(address => bool) public operators
35: mapping(address => bool) public vaults
```
[34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L34) | [35](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L35)
</details>

### [G-13] Assigning `state` variables directly with struct constructors wastes gas

Utilizing named struct constructors for `state`(only state) variable assignments can lead to inefficient gas usage.
When a struct is initialized with named arguments, the Solidity compiler must first organize these fields in memory, which consumes additional gas.
To optimize gas usage, it is recommended to assign struct fields directly in storage using dot notation.
```solidity
    // stateStruct = TestStruct(20, 20); // 4633 gas
    // stateStruct = TestStruct({ var1: 20, var2: 20 }); // 4633 gas
    // stateStruct.var1 = 20;
    // stateStruct.var2 = 20; // 4562 gas
```

<details>
<summary><i>2 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

446: loans[tokenId] = Loan(0)
461: loans[tokenId] = Loan(loans[oldTokenId].debtShares)
```
[446](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L446) | [461](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L461)
</details>

### [G-14] Assembly: Use scratch space when building emitted events with two data arguments

Using the scratch space for more than one, but at most two words worth of data (non-indexed arguments) will save gas over needing Solidity's abi memory expansion used for emitting normally.

<details>
<summary><i>35 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

449: emit Add(tokenId, owner, 0)
464: emit Add(tokenId, owner, oldTokenId)
489: emit ApprovedTransform(tokenId, msg.sender, target, isActive)
601: emit Borrow(tokenId, owner, assets, shares)
645: emit WithdrawCollateral(params.tokenId, owner, params.recipient, params.liquidity, amount0, amount1)
746: emit Liquidate(
            params.tokenId,
            msg.sender,
            owner,
            state.fullValue,
            state.liquidatorCost,
            amount0,
            amount1,
            state.reserveCost,
            state.missing
        )
782: emit WithdrawReserves(amount, receiver)
798: emit SetTransformer(transformer, active)
830: emit SetLimits(
            _minLoanSize, _globalLendLimit, _globalDebtLimit, _dailyLendIncreaseLimitMin, _dailyDebtIncreaseLimitMin
        )
865: emit SetTokenConfig(token, collateralFactorX32, collateralValueLimitFactorX32)
1013: emit Repay(tokenId, msg.sender, owner, assets, shares)
1139: emit ExchangeRateUpdate(newDebtExchangeRateX96, newLendExchangeRateX96)
1160: emit ExchangeRateUpdate(newDebtExchangeRateX96, newLendExchangeRateX96)
```
[449](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L449) | [464](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L464) | [489](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L489) | [601](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L601) | [645](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L645) | [746](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L746) | [782](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L782) | [798](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L798) | [830](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L830) | [865](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L865) | [1013](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1013) | [1139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1139) | [1160](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1160)

```solidity
File: src/InterestRateModel.sol

100: emit SetValues(baseRatePerYearX96, multiplierPerYearX96, jumpMultiplierPerYearX96, _kinkX96)
```
[100](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L100)

```solidity
File: src/automators/AutoExit.sol

208: emit PositionConfigured(params.tokenId, false, false, false, 0, 0, 0, 0, false, 0)
211: emit Executed(
            params.tokenId, msg.sender, state.isSwap, state.amount0, state.amount1, state.token0, state.token1
        )
232: emit PositionConfigured(
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
        )
```
[208](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L208) | [211](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L211) | [232](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L232)

```solidity
File: src/automators/Automator.sol

70: emit OperatorChanged(_operator, _active)
80: emit VaultChanged(_vault, _active)
94: emit TWAPConfigChanged(_TWAPSeconds, _maxTWAPTickDifference)
```
[70](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L70) | [80](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L80) | [94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L94)

```solidity
File: src/transformers/AutoCompound.sol

183: emit AutoCompounded(
            msg.sender,
            params.tokenId,
            state.compounded0,
            state.compounded1,
            state.amount0Fees,
            state.amount1Fees,
            state.token0,
            state.token1
        )
246: emit RewardUpdated(msg.sender, _totalRewardX64)
251: emit BalanceAdded(tokenId, token, amount)
259: emit BalanceAdded(tokenId, token, amount - currentBalance)
261: emit BalanceRemoved(tokenId, token, currentBalance - amount)
271: emit BalanceRemoved(tokenId, token, amount)
273: emit BalanceWithdrawn(tokenId, token, to, amount)
```
[183](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L183) | [246](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L246) | [251](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L251) | [259](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L259) | [261](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L261) | [271](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L271) | [273](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L273)

```solidity
File: src/transformers/AutoRange.sol

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
            )
266: emit PositionConfigured(params.tokenId, 0, 0, 0, 0, 0, 0, false, 0)
286: emit PositionConfigured(
            tokenId,
            config.lowerTickLimit,
            config.upperTickLimit,
            config.lowerTickDelta,
            config.upperTickDelta,
            config.token0SlippageX64,
            config.token1SlippageX64,
            config.onlyFees,
            config.maxRewardX64
        )
```
[252](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L252) | [266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L266) | [286](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L286)

```solidity
File: src/transformers/V3Utils.sol

218: emit CompoundFees(tokenId, liquidity, amount0, amount1)
348: emit WithdrawAndCollectAndSwap(tokenId, instructions.targetToken, targetAmount)
729: emit SwapAndMint(tokenId, liquidity, added0, added1)
773: emit SwapAndIncreaseLiquidity(params.tokenId, liquidity, added0, added1)
```
[218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L218) | [348](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L348) | [729](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L729) | [773](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L773)

```solidity
File: src/utils/Swapper.sol

116: emit Swap(address(params.tokenIn), address(params.tokenOut), amountInDelta, amountOutDelta)
```
[116](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L116)
</details>

### [G-15] Stack variable is only used once

If the variable is only accessed once, it's cheaper to use the assigned value directly that one time, and save the 3 gas the extra stack assignment would spend

<details>
<summary><i>41 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit - `owner` variable
531: address owner = nonfungiblePositionManager.ownerOf(tokenId)
/// @audit - `debt` variable
539: uint256 debt = _convertToAssets(loans[tokenId].debtShares, newDebtExchangeRateX96, Math.Rounding.Up)
/// @audit - `collectParams` variable
633: INonfungiblePositionManager.CollectParams memory collectParams = INonfungiblePositionManager.CollectParams(
            params.tokenId,
            params.recipient,
            params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
            params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)
        )
/// @audit - `debt` variable
642: uint256 debt = _convertToAssets(loans[params.tokenId].debtShares, newDebtExchangeRateX96, Math.Rounding.Up)
/// @audit - `available` variable
772: uint256 available = balance > unprotected ? unprotected : balance
/// @audit - `startLiquidationValue` variable
1105: uint256 startLiquidationValue = debt * fullValue / collateralValue
/// @audit - `penaltyFractionX96` variable
1106: uint256 penaltyFractionX96 =
                (Q96 - ((fullValue - maxPenaltyValue) * Q96 / (startLiquidationValue - maxPenaltyValue)))
/// @audit - `penaltyX32` variable
1108: uint256 penaltyX32 = MIN_LIQUIDATION_PENALTY_X32
                + (MAX_LIQUIDATION_PENALTY_X32 - MIN_LIQUIDATION_PENALTY_X32) * penaltyFractionX96 / Q96
/// @audit - `debt` variable
1177: uint256 debt = _convertToAssets(debtSharesTotal, oldDebtExchangeRateX96, Math.Rounding.Up)
/// @audit - `collateralFactorX32` variable
1276: uint256 collateralFactorX32 = _calculateTokenCollateralFactorX32(tokenId)
```
[531](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L531) | [539](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L539) | [633](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L633) | [642](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L642) | [772](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L772) | [1105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1105) | [1106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1106) | [1108](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1108) | [1177](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1177) | [1276](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1276)

```solidity
File: src/V3Oracle.sol

/// @audit - `derivedPoolPriceX96` variable
129: uint256 derivedPoolPriceX96 = price0X96 * Q96 / price1X96
/// @audit - `pool` variable
134: IUniswapV3Pool pool = _getPool(token0, token1, fee)
/// @audit - `priceX96` variable
135: uint256 priceX96 = _getReferencePoolPriceX96(pool, 0)
/// @audit - `differenceX10000` variable
143: uint256 differenceX10000 = priceX96 > verifyPriceX96
            ? (priceX96 - verifyPriceX96) * 10000 / priceX96
            : (verifyPriceX96 - priceX96) * 10000 / verifyPriceX96
/// @audit - `isToken0` variable
230: bool isToken0 = token0 == token
/// @audit - `usesChainlink` variable
289: bool usesChainlink = (
            feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY
                || feedConfig.mode == Mode.CHAINLINK
        )
/// @audit - `usesTWAP` variable
293: bool usesTWAP = (
            feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY
                || feedConfig.mode == Mode.TWAP
        )
/// @audit - `tick` variable
369: int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)))
```
[129](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L129) | [134](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L134) | [135](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L135) | [143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L143) | [230](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L230) | [289](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L289) | [293](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L293) | [369](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L369)

```solidity
File: src/InterestRateModel.sol

/// @audit - `normalRateX96` variable
69: uint256 normalRateX96 = (kinkX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96
/// @audit - `excessUtilX96` variable
70: uint256 excessUtilX96 = utilizationRateX96 - kinkX96
```
[69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L69) | [70](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L70)

```solidity
File: src/automators/AutoExit.sol

/// @audit - `owner` variable
219: address owner = nonfungiblePositionManager.ownerOf(tokenId)
```
[219](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L219)

```solidity
File: src/automators/Automator.sol

/// @audit - `count` variable
110: uint256 count = tokens.length
```
[110](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L110)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit - `count` variable
232: uint256 count = tokens.length
/// @audit - `allowance0` variable
278: uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager))
/// @audit - `allowance1` variable
282: uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager))
```
[232](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L232) | [278](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L278) | [282](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L282)

```solidity
File: src/transformers/AutoRange.sol

/// @audit - `mintParams` variable
198: INonfungiblePositionManager.MintParams memory mintParams = INonfungiblePositionManager.MintParams(
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
[198](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L198)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit - `increaseLiquidityParams` variable
80: INonfungiblePositionManager.IncreaseLiquidityParams memory increaseLiquidityParams = INonfungiblePositionManager
            .IncreaseLiquidityParams(
            params.tokenId, amount0, amount1, params.amountAddMin0, params.amountAddMin1, params.deadline
        )
/// @audit - `decreaseLiquidityParams` variable
130: INonfungiblePositionManager.DecreaseLiquidityParams memory decreaseLiquidityParams = INonfungiblePositionManager
            .DecreaseLiquidityParams(
            params.tokenId, params.liquidity, params.amountRemoveMin0, params.amountRemoveMin1, params.deadline
        )
/// @audit - `collectParams` variable
136: INonfungiblePositionManager.CollectParams memory collectParams = INonfungiblePositionManager.CollectParams(
            params.tokenId,
            address(this),
            params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
            params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)
        )
```
[80](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L80) | [130](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L130) | [136](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L136)

```solidity
File: src/transformers/V3Utils.sol

/// @audit - `mintParams` variable
711: INonfungiblePositionManager.MintParams memory mintParams = INonfungiblePositionManager.MintParams(
            address(params.token0),
            address(params.token1),
            params.fee,
            params.tickLower,
            params.tickUpper,
            total0,
            total1,
            params.amountAddMin0,
            params.amountAddMin1,
            address(this), // is sent to real recipient aftwards
            params.deadline
        )
/// @audit - `increaseLiquidityParams` variable
766: INonfungiblePositionManager.IncreaseLiquidityParams memory increaseLiquidityParams = INonfungiblePositionManager
            .IncreaseLiquidityParams(
            params.tokenId, total0, total1, params.amountAddMin0, params.amountAddMin1, params.deadline
        )
/// @audit - `balanceBefore0` variable
896: uint256 balanceBefore0 = token0.balanceOf(address(this))
/// @audit - `balanceBefore1` variable
897: uint256 balanceBefore1 = token1.balanceOf(address(this))
/// @audit - `balanceAfter0` variable
901: uint256 balanceAfter0 = token0.balanceOf(address(this))
/// @audit - `balanceAfter1` variable
902: uint256 balanceAfter1 = token1.balanceOf(address(this))
```
[711](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L711) | [766](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L766) | [896](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L896) | [897](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L897) | [901](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L901) | [902](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L902)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit - `data` variable
51: bytes memory data = abi.encode(
            FlashCallbackData(
                params.tokenId,
                params.debtShares,
                liquidationCost,
                params.vault,
                IERC20(asset),
                RouterSwapParams(IERC20(token0), IERC20(asset), params.amount0In, 0, params.swapData0),
                RouterSwapParams(IERC20(token1), IERC20(asset), params.amount1In, 0, params.swapData1),
                msg.sender,
                params.minReward
            )
        )
```
[51](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L51)

```solidity
File: src/utils/Swapper.sol

/// @audit - `balanceInBefore` variable
78: uint256 balanceInBefore = params.tokenIn.balanceOf(address(this))
/// @audit - `balanceOutBefore` variable
79: uint256 balanceOutBefore = params.tokenOut.balanceOf(address(this))
/// @audit - `balanceInAfter` variable
104: uint256 balanceInAfter = params.tokenIn.balanceOf(address(this))
/// @audit - `balanceOutAfter` variable
105: uint256 balanceOutAfter = params.tokenOut.balanceOf(address(this))
/// @audit - `amountToPay` variable
166: uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta)
```
[78](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L78) | [79](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L79) | [104](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L104) | [105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L105) | [166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L166)
</details>

### [G-16] `abi.encodePacked `is more gas efficient than `abi.encode`

`abi.encode()` pads all elementary types to 32 bytes, whereas `abi.encodePacked()` will only use the minimal required memory to encode the data.
```solidity
    function testPacking() public pure returns (bytes memory) {
        // return abi.encode("string"); // 1120 gas
        // return abi.encodePacked("string"); // 913 gas
    }
```

<details>
<summary><i>4 issue instances in 3 files:</i></summary>

```solidity
File: src/V3Vault.sol

401: abi.encode(recipient)
424: abi.encode(recipient)
```
[401](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L401) | [424](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L424)

```solidity
File: src/utils/FlashloanLiquidator.sol

51: abi.encode(
            FlashCallbackData(
                params.tokenId,
                params.debtShares,
                liquidationCost,
                params.vault,
                IERC20(asset),
                RouterSwapParams(IERC20(token0), IERC20(asset), params.amount0In, 0, params.swapData0),
                RouterSwapParams(IERC20(token1), IERC20(asset), params.amount1In, 0, params.swapData1),
                msg.sender,
                params.minReward
            )
        )
```
[51](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L51)

```solidity
File: src/utils/Swapper.sol

139: abi.encode(
                    params.swap0For1 ? params.token0 : params.token1,
                    params.swap0For1 ? params.token1 : params.token0,
                    params.fee
                )
```
[139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L139)
</details>

### [G-17] Consider Using `selfbalance()` Over `address(this).balance`

The `selfbalance()` function from Yul can be more gas-efficient than using `address(this).balance` in certain scenarios.
Although the Solidity compiler is sometimes optimized enough to handle this, manually switching to `selfbalance()` could yield gas savings.

Note: Always thoroughly test both approaches to confirm the actual gas savings.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/automators/Automator.sol

128: address(this).balance
```
[128](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L128)
</details>

### [G-18] Use `assembly` to write mutable storage values

Writing to storage using `assembly` is more gas efficient.
```solidity
    function writeStorage() external {
        // storageNumber = 10; // 2358 gas
        // assembly {
        //     sstore(storageNumber.slot, 10) // 2350 gas
        // }
        // storageAddr = 0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc3; // 2411 gas
        // assembly {
        //     sstore(storageAddr.slot, 0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc3) // 2350 gas
        // }
    }
```

<details>
<summary><i>50 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

446: loans[tokenId] = Loan(0)
458: transformedTokenId = tokenId
461: loans[tokenId] = Loan(loans[oldTokenId].debtShares)
487: transformApprovals[msg.sender][tokenId][target] = isActive
508: transformedTokenId = tokenId
542: transformedTokenId = 0
797: transformerAllowList[transformer] = active
818: minLoanSize = _minLoanSize
819: globalLendLimit = _globalLendLimit
820: globalDebtLimit = _globalDebtLimit
821: dailyLendIncreaseLimitMin = _dailyLendIncreaseLimitMin
822: dailyDebtIncreaseLimitMin = _dailyDebtIncreaseLimitMin
838: reserveFactorX32 = _reserveFactorX32
848: reserveProtectionFactorX32 = _reserveProtectionFactorX32
863: tokenConfigs[token].collateralFactorX32 = collateralFactorX32
864: tokenConfigs[token].collateralValueLimitFactorX32 = collateralValueLimitFactorX32
871: emergencyAdmin = admin
1138: lastLendExchangeRateX96 = newLendExchangeRateX96
1157: lastDebtExchangeRateX96 = newDebtExchangeRateX96
1158: lastLendExchangeRateX96 = newLendExchangeRateX96
1159: lastExchangeRateUpdate = block.timestamp
1181: supplyRateX96 = supplyRateX96.mulDiv(Q32 - reserveFactorX32, Q32)
1252: dailyLendIncreaseLimitLeft =
                dailyLendIncreaseLimitMin > lendIncreaseLimit ? dailyLendIncreaseLimitMin : lendIncreaseLimit
1254: dailyLendIncreaseLimitLastReset = time
1264: dailyDebtIncreaseLimitLeft =
                dailyDebtIncreaseLimitMin > debtIncreaseLimit ? dailyDebtIncreaseLimitMin : debtIncreaseLimit
1266: dailyDebtIncreaseLimitLastReset = time
1298: ownedTokensIndex[tokenId] = ownedTokens[to].length
1300: tokenOwner[tokenId] = to
1308: ownedTokens[from][tokenIndex] = lastTokenId
1309: ownedTokensIndex[lastTokenId] = tokenIndex
```
[446](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L446) | [458](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L458) | [461](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L461) | [487](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L487) | [508](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L508) | [542](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L542) | [797](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L797) | [818](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L818) | [819](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L819) | [820](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L820) | [821](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L821) | [822](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L822) | [838](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L838) | [848](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L848) | [863](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L863) | [864](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L864) | [871](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L871) | [1138](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1138) | [1157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1157) | [1158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1158) | [1159](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1159) | [1181](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1181) | [1252](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1252) | [1254](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1254) | [1264](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1264) | [1266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1266) | [1298](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1298) | [1300](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1300) | [1308](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1308) | [1309](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1309)

```solidity
File: src/V3Oracle.sol

189: maxPoolPriceDifference = _maxPoolPriceDifference
240: feedConfigs[token] = config
259: feedConfigs[token].mode = mode
266: emergencyAdmin = admin
```
[189](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L189) | [240](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L240) | [259](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L259) | [266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L266)

```solidity
File: src/InterestRateModel.sol

95: baseRatePerSecondX96 = baseRatePerYearX96 / YEAR_SECS
96: multiplierPerSecondX96 = multiplierPerYearX96 / YEAR_SECS
97: jumpMultiplierPerSecondX96 = jumpMultiplierPerYearX96 / YEAR_SECS
98: kinkX96 = _kinkX96
```
[95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L95) | [96](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L96) | [97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L97) | [98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L98)

```solidity
File: src/automators/AutoExit.sol

230: positionConfigs[tokenId] = config
```
[230](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L230)

```solidity
File: src/automators/Automator.sol

61: withdrawer = _withdrawer
71: operators[_operator] = _active
81: vaults[_vault] = _active
95: TWAPSeconds = _TWAPSeconds
96: maxTWAPTickDifference = _maxTWAPTickDifference
```
[61](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L61) | [71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L71) | [81](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L81) | [95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L95) | [96](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L96)

```solidity
File: src/transformers/AutoCompound.sol

245: totalRewardX64 = _totalRewardX64
250: positionBalances[tokenId][token] = positionBalances[tokenId][token] + amount
257: positionBalances[tokenId][token] = amount
270: positionBalances[tokenId][token] = positionBalances[tokenId][token] - amount
```
[245](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L245) | [250](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L250) | [257](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L257) | [270](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L270)

```solidity
File: src/transformers/AutoRange.sol

251: positionConfigs[state.newTokenId] = config
284: positionConfigs[tokenId] = config
```
[251](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L251) | [284](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L284)
</details>

### [G-19] Using `delete` on a `uint/int` variable is cheaper than assigning it to `0`

```solidity
function test() external {
    delete foo; // 5148 gas
    foo = 0; // 5156 gas
}
```

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

### [G-20] Use `revert()` to gain maximum gas savings

If you dont need Error messages, or you want gain maximum gas savings - `revert()` is a cheapest way to revert transaction in terms of gas.
```solidity
    revert(); // 117 gas 
    require(false); // 132 gas
    revert CustomError(); // 157 gas
    assert(false); // 164 gas
    revert("Custom Error"); // 406 gas
    require(false, "Custom Error"); // 421 gas
```


<details>
<summary><i>105 issue instances in 10 files:</i></summary>

```solidity
File: src/V3Vault.sol

420: revert Unauthorized()
436: revert WrongContract()
485: revert Unauthorized()
503: revert TransformNotAllowed()
506: revert Reentrancy()
516: revert Unauthorized()
524: revert TransformFailed()
533: revert Unauthorized()
562: revert Unauthorized()
572: revert GlobalDebtLimit()
575: revert DailyDebtIncreaseLimit()
587: revert MinLoanSize()
616: revert TransformNotAllowed()
622: revert Unauthorized()
688: revert TransformNotAllowed()
697: revert DebtChanged()
705: revert NotLiquidatable()
738: revert SlippageError()
775: revert InsufficientLiquidity()
794: revert InvalidConfig()
815: revert Unauthorized()
846: revert InvalidConfig()
861: revert CollateralFactorExceedsMax()
907: revert GlobalLendLimit()
911: revert DailyLendIncreaseLimit()
941: revert InsufficientLiquidity()
974: revert RepayExceedsDebt()
1009: revert MinLoanSize()
1200: revert CollateralFail()
1232: revert CollateralValueLimit()
1240: revert CollateralValueLimit()
```
[420](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L420) | [436](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L436) | [485](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L485) | [503](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L503) | [506](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L506) | [516](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L516) | [524](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L524) | [533](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L533) | [562](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L562) | [572](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L572) | [575](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L575) | [587](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L587) | [616](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L616) | [622](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L622) | [688](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L688) | [697](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L697) | [705](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L705) | [738](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L738) | [775](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L775) | [794](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L794) | [815](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L815) | [846](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L846) | [861](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L861) | [907](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L907) | [911](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L911) | [941](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L941) | [974](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L974) | [1009](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1009) | [1200](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1200) | [1232](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1232) | [1240](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1240)

```solidity
File: src/V3Oracle.sol

148: revert PriceDifferenceExceeded()
187: revert InvalidConfig()
212: revert InvalidConfig()
222: revert InvalidConfig()
228: revert InvalidPool()
251: revert Unauthorized()
256: revert InvalidConfig()
284: revert NotConfigured()
339: revert ChainlinkPriceError()
```
[148](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L148) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L187) | [212](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L212) | [222](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L222) | [228](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L228) | [251](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L251) | [256](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L256) | [284](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L284) | [339](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L339)

```solidity
File: src/InterestRateModel.sol

92: revert InvalidConfig()
```
[92](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L92)

```solidity
File: src/automators/AutoExit.sol

102: revert Unauthorized()
109: revert NotConfigured()
116: revert ExceedsMaxReward()
125: revert NoLiquidity()
128: revert LiquidityChanged()
136: revert NotReady()
150: revert MissingSwapData()
221: revert Unauthorized()
226: revert InvalidConfig()
```
[102](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L102) | [109](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L109) | [116](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L116) | [125](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L125) | [128](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L128) | [136](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L136) | [150](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L150) | [221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L221) | [226](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L226)

```solidity
File: src/automators/Automator.sol

89: revert InvalidConfig()
92: revert InvalidConfig()
106: revert Unauthorized()
125: revert Unauthorized()
132: revert EtherSendFailed()
152: revert TWAPCheckFailed()
223: revert EtherSendFailed()
233: revert Unauthorized()
238: revert Unauthorized()
246: revert Unauthorized()
253: revert NotWETH()
```
[89](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L89) | [92](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L92) | [106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L106) | [125](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L125) | [132](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L132) | [152](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L152) | [223](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L223) | [233](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L233) | [238](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L238) | [246](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L246) | [253](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L253)

```solidity
File: src/transformers/AutoCompound.sol

244: require(_totalRewardX64 <= totalRewardX64, ">totalRewardX64")
269: require(amount <= balance, "amount>balance")
89: revert Unauthorized()
103: revert Unauthorized()
206: revert Unauthorized()
229: revert Unauthorized()
```
[244](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L244) | [269](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L269) | [89](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L89) | [103](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L103) | [206](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L206) | [229](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L229)

```solidity
File: src/transformers/AutoRange.sol

99: revert Unauthorized()
113: revert Unauthorized()
119: revert NotConfigured()
126: revert ExceedsMaxReward()
134: revert LiquidityChanged()
150: revert SwapAmountTooLarge()
178: revert SameRange()
270: revert NotReady()
281: revert InvalidConfig()
310: revert NotSupportedFeeTier()
```
[99](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L99) | [113](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L113) | [119](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L119) | [126](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L126) | [134](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L134) | [150](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L150) | [178](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L178) | [270](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L270) | [281](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L281) | [310](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L310)

```solidity
File: src/transformers/V3Utils.sol

103: revert Unauthorized()
143: revert AmountError()
350: revert NotSupportedWhatToDo()
363: revert WrongContract()
368: revert SelfSend()
399: revert SameToken()
473: revert SameToken()
636: revert TransferError()
641: revert TransferError()
646: revert TransferError()
672: revert TooMuchEtherSent()
677: revert TooMuchEtherSent()
682: revert TooMuchEtherSent()
685: revert NoEtherToken()
785: revert AmountError()
796: revert AmountError()
869: revert EtherSendFailed()
906: revert CollectError()
909: revert CollectError()
916: revert NotWETH()
```
[103](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L103) | [143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L143) | [350](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L350) | [363](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L363) | [368](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L368) | [399](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L399) | [473](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L473) | [636](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L636) | [641](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L641) | [646](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L646) | [672](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L672) | [677](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L677) | [682](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L682) | [685](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L685) | [785](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L785) | [796](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L796) | [869](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L869) | [906](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L906) | [909](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L909) | [916](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L916)

```solidity
File: src/utils/FlashloanLiquidator.sol

44: revert NotLiquidatable()
103: revert NotEnoughReward()
```
[44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L44) | [103](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L103)

```solidity
File: src/utils/Swapper.sol

157: require(amount0Delta > 0 || amount1Delta > 0)
91: revert SwapFailed()
101: revert WrongContract()
112: revert SlippageError()
150: revert SlippageError()
162: revert Unauthorized()
```
[157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L157) | [91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L91) | [101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L101) | [112](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L112) | [150](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L150) | [162](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L162)
</details>

### [G-21] `x.a = x.a + b` always cheaper than `x.a += b` for Structs

Using direct assignment operations (e.g., `x.a = x.a + b`) is more gas-efficient compared to compound assignment operations (e.g., `x.a += b`).
Examples:
```solidity
    // direct write to storage   -> 5337 gas
    // struct storage pointer    -> 5341 gas
    // memory struct             -> 4628 gas
    // memory function param     -> 1109 gas
    x.a += b;

    // direct write to storage   -> 5330 gas
    // struct storage pointer    -> 5334 gas
    // memory struct             -> 4625 gas
    // memory function param     -> 1106 gas
    x.a = struct.a + b;
```


<details>
<summary><i>14 issue instances in 3 files:</i></summary>

```solidity
File: src/V3Vault.sol

1217: tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares)
1218: tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares)
1220: tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares)
1221: tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares)
```
[1217](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1217) | [1218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1218) | [1220](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1220) | [1221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1221)

```solidity
File: src/automators/AutoExit.sol

155: state.amount0 -= state.feeAmount0 * params.rewardX64 / Q64
156: state.amount1 -= state.feeAmount1 * params.rewardX64 / Q64
187: state.amount0 -= state.amount0 * params.rewardX64 / Q64
189: state.amount1 -= state.amount1 * params.rewardX64 / Q64
194: state.amount0 -= (config.onlyFees ? state.feeAmount0 : state.amount0) * params.rewardX64 / Q64
195: state.amount1 -= (config.onlyFees ? state.feeAmount1 : state.amount1) * params.rewardX64 / Q64
```
[155](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L155) | [156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L156) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L187) | [189](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L189) | [194](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L194) | [195](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L195)

```solidity
File: src/transformers/AutoRange.sol

145: state.amount0 -= state.protocolReward0
146: state.amount1 -= state.protocolReward1
238: state.amount0 -= state.protocolReward0
239: state.amount1 -= state.protocolReward1
```
[145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L145) | [146](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L146) | [238](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L238) | [239](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L239)
</details>

### [G-22] Using `constants` instead of `enum` can save gas

`Enum` is expensive and it is [more efficient to use constants](https://www.codehawks.com/finding/clm84992q02j9w9ruebun36d9) instead.
An illustrative example of this approach can be found in the [ReentrancyGuard.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/181d518609a9f006fcb97af63e6952e603cf100e/contracts/utils/ReentrancyGuard.sol#L34-L35)

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Oracle.sol

35: enum Mode {
        NOT_SET,
        CHAINLINK_TWAP_VERIFY, // using chainlink for price and TWAP to verify
        TWAP_CHAINLINK_VERIFY, // using TWAP for price and chainlink to verify
        CHAINLINK, // using only chainlink directly
        TWAP // using TWAP directly
    }
```
[35](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L35)

```solidity
File: src/transformers/V3Utils.sol

41: enum WhatToDo {
        CHANGE_RANGE,
        WITHDRAW_AND_COLLECT_AND_SWAP,
        COMPOUND_FEES
    }
```
[41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L41)
</details>

### [G-23] Create variable outside the loop

Creating variables inside the loop consum more gas compared to declaring them outside and just reaffecting values to them inside the loop.
```solidity
    // uint256 outsideVar = anyValue;
    for (uint256 i = 0; i < 10; i++) {
        // outsideVar = value;     // 1984 gas
        uint256 insideVar = value; // 2012 gas 
    }
```

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/automators/Automator.sol

112: uint256 balance = IERC20(tokens[i]).balanceOf(address(this))
```
[112](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L112)

```solidity
File: src/transformers/AutoCompound.sol

234: uint256 balance = positionBalances[0][tokens[i]]
```
[234](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L234)
</details>

### [G-24] Counting down when iterating, saves gas

Counting down saves 6 gas per loop, since checks for zero are more efficient than checks against any other value.

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

### [G-25] Using `> 0` costs more gas than `!= 0` when used on a `uint` in a `require()` statement

This change saves 6 gas per instance. The optimization works until solidity version 0.8.13 where there is a regression in gas costs.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/utils/Swapper.sol

157: require(amount0Delta > 0 || amount1Delta > 0)
```
[157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L157)
</details>

### [G-26] `>=` costs less gas than `>`

The compiler uses opcodes GT and ISZERO for solidity code that uses >, but only requires LT for >=, which saves 3 gas. If < is being used, the condition can be inverted.
In cases where a for-loop is being used, one can count down rather than up, in order to use the optimal operator.

<details>
<summary><i>56 issue instances in 10 files:</i></summary>

```solidity
File: src/V3Vault.sol

443: if (data.length > 0) {
505: if (transformedTokenId > 0) {
552: transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];
615: if (transformedTokenId > 0) {
687: if (transformedTokenId > 0) {
712: if (state.reserveCost > 0) {
717: if (params.permitData.length > 0) {
778: if (amount > 0) {
893: if (permitData.length > 0) {
977: if (assets > 0) {
978: if (permitData.length > 0) {
1064: if (liquidity > 0) {
1186: if (lastRateUpdate > 0) {
```
[443](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L443) | [505](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L505) | [552](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L552) | [615](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L615) | [687](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L687) | [712](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L712) | [717](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L717) | [778](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L778) | [893](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L893) | [977](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L977) | [978](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L978) | [1064](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1064) | [1186](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1186)

```solidity
File: src/V3Oracle.sol

431: if (state.liquidity > 0) {
```
[431](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L431)

```solidity
File: src/automators/AutoExit.sol

199: if (state.amount0 > 0) {
202: if (state.amount1 > 0) {
```
[199](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L199) | [202](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L202)

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
123: if (state.amount0 > 0 || state.amount1 > 0) {
127: if (amountIn > 0) {
133: if (tSecs > 0) {
140: if (amountIn > 0) {
160: if (state.maxAddAmount0 > 0 || state.maxAddAmount1 > 0) {
160: if (state.maxAddAmount0 > 0 || state.maxAddAmount1 > 0) {
212: if (balance0 > 0) {
216: if (balance1 > 0) {
```
[123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L123) | [123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L123) | [127](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L127) | [133](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L133) | [140](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L140) | [160](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L160) | [160](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L160) | [212](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L212) | [216](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L216)

```solidity
File: src/transformers/AutoRange.sol

243: if (state.amount0 - state.amountAdded0 > 0) {
246: if (state.amount1 - state.amountAdded1 > 0) {
```
[243](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L243) | [246](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L246)

```solidity
File: src/transformers/LeverageTransformer.sol

52: if (params.amountIn0 > 0) {
64: if (params.amountIn1 > 0) {
93: if (token != token0 && token != token1 && amount > 0) {
146: if (params.amountIn0 > 0 && token != token0) {
155: if (params.amountIn1 > 0 && token != token1) {
169: if (amount0 > 0 && token != token0) {
172: if (amount1 > 0 && token != token1) {
```
[52](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L52) | [64](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L64) | [93](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L93) | [146](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L146) | [155](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L155) | [169](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L169) | [172](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L172)

```solidity
File: src/transformers/V3Utils.sol

402: if (params.permitData.length > 0) {
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
```
[402](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L402) | [476](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L476) | [539](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L539) | [577](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L577) | [580](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L580) | [583](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L583) | [617](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L617) | [621](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L621) | [625](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L625) | [634](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L634) | [639](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L639) | [644](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L644)

```solidity
File: src/utils/FlashloanLiquidator.sol

90: if (balance > 0) {
96: if (balance > 0) {
105: if (balance > 0) {
```
[90](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L90) | [96](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L96) | [105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L105)

```solidity
File: src/utils/Swapper.sol

133: if (params.amountIn > 0) {
157: require(amount0Delta > 0 || amount1Delta > 0); // swaps entirely within 0-liquidity regions are not supported
157: require(amount0Delta > 0 || amount1Delta > 0); // swaps entirely within 0-liquidity regions are not supported
166: uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta);
```
[133](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L133) | [157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L157) | [157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L157) | [166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L166)
</details>

### [G-27] Consider pre-calculating the address of `address(this)` to save gas

Use foundry's script.sol or solady's LibRlp.sol to save the value in a constant, which will avoid having to spend gas to push the value on the stack every time it's used.

<details>
<summary><i>58 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

285: return IERC20(asset).balanceOf(address(this));
401: nonfungiblePositionManager.safeTransferFrom(msg.sender, address(this), tokenId, abi.encode(recipient));
423: nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);
424: nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));
435: if (msg.sender != address(nonfungiblePositionManager) || from == address(this)) {
532: if (owner != address(this)) {
561: if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {
722: ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost),
728: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);
791: transformer == address(0) || transformer == address(this) || transformer == asset
897: permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
901: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
982: permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
986: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
1083: nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId);
```
[285](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L285) | [401](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L401) | [423](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L423) | [424](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L424) | [435](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L435) | [532](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L532) | [561](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L561) | [722](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L722) | [728](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L728) | [791](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L791) | [897](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L897) | [901](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L901) | [982](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L982) | [986](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L986) | [1083](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1083)

```solidity
File: src/automators/Automator.sol

112: uint256 balance = IERC20(tokens[i]).balanceOf(address(this));
128: uint256 balance = address(this).balance;
209: INonfungiblePositionManager.CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max)
```
[112](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L112) | [128](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L128) | [209](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L209)

```solidity
File: src/transformers/AutoCompound.sol

92: params.tokenId, address(this), abi.encodeWithSelector(AutoCompound.execute.selector, params)
110: params.tokenId, address(this), type(uint128).max, type(uint128).max
278: uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager));
282: uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager));
```
[92](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L92) | [110](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L110) | [278](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L278) | [282](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L282)

```solidity
File: src/transformers/AutoRange.sol

102: params.tokenId, address(this), abi.encodeWithSelector(AutoRange.execute.selector, params)
208: address(this), // is sent to real recipient aftwards
232: nonfungiblePositionManager.safeTransferFrom(address(this), state.owner, state.newTokenId);
```
[102](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L102) | [208](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L208) | [232](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L232)

```solidity
File: src/transformers/LeverageTransformer.sol

138: address(this),
```
[138](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L138)

```solidity
File: src/transformers/V3Utils.sol

106: nonfungiblePositionManager.permit(address(this), tokenId, instructions.deadline, v, r, s);
367: if (from == address(this)) {
376: nonfungiblePositionManager.safeTransferFrom(address(this), from, tokenId, instructions.returnData);
578: SafeERC20.safeTransferFrom(token0, msg.sender, address(this), needed0);
581: SafeERC20.safeTransferFrom(token1, msg.sender, address(this), needed1);
584: SafeERC20.safeTransferFrom(otherToken, msg.sender, address(this), neededOther);
618: state.balanceBefore0 = token0.balanceOf(address(this));
619: transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed0);
622: state.balanceBefore1 = token1.balanceOf(address(this));
623: transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed1);
626: state.balanceBeforeOther = otherToken.balanceOf(address(this));
627: transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.neededOther);
635: if (token0.balanceOf(address(this)) - state.balanceBefore0 != state.needed0) {
640: if (token1.balanceOf(address(this)) - state.balanceBefore1 != state.needed1) {
645: if (otherToken.balanceOf(address(this)) - state.balanceBeforeOther != state.neededOther) {
721: address(this), // is sent to real recipient aftwards
727: nonfungiblePositionManager.safeTransferFrom(address(this), params.recipientNFT, tokenId, params.returnData);
896: uint256 balanceBefore0 = token0.balanceOf(address(this));
897: uint256 balanceBefore1 = token1.balanceOf(address(this));
899: INonfungiblePositionManager.CollectParams(tokenId, address(this), collectAmount0, collectAmount1)
901: uint256 balanceAfter0 = token0.balanceOf(address(this));
902: uint256 balanceAfter1 = token1.balanceOf(address(this));
```
[106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L106) | [367](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L367) | [376](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L376) | [578](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L578) | [581](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L581) | [584](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L584) | [618](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L618) | [619](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L619) | [622](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L622) | [623](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L623) | [626](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L626) | [627](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L627) | [635](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L635) | [640](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L640) | [645](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L645) | [721](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L721) | [727](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L727) | [896](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L896) | [897](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L897) | [899](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L899) | [901](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L901) | [902](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L902)

```solidity
File: src/utils/FlashloanLiquidator.sol

64: params.flashLoanPool.flash(address(this), isAsset0 ? liquidationCost : 0, !isAsset0 ? liquidationCost : 0, data);
75: data.tokenId, data.debtShares, data.swap0.amountIn, data.swap1.amountIn, address(this), ""
89: uint256 balance = data.swap0.tokenIn.balanceOf(address(this));
95: uint256 balance = data.swap1.tokenIn.balanceOf(address(this));
101: uint256 balance = data.asset.balanceOf(address(this));
```
[64](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L64) | [75](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L75) | [89](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L89) | [95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L95) | [101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L101)

```solidity
File: src/utils/Swapper.sol

78: uint256 balanceInBefore = params.tokenIn.balanceOf(address(this));
79: uint256 balanceOutBefore = params.tokenOut.balanceOf(address(this));
104: uint256 balanceInAfter = params.tokenIn.balanceOf(address(this));
105: uint256 balanceOutAfter = params.tokenOut.balanceOf(address(this));
135: address(this),
```
[78](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L78) | [79](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L79) | [104](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L104) | [105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L105) | [135](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L135)
</details>

### [G-28] Use `unchecked` for Non-Loop Increment/Decrement Operations

Disclaimer: `You should be sure that underflow is not possible `
Using `unchecked` increments can save gas by bypassing the built-in overflow checks.
This can save 30-40 gas per iteration.
It is recommended to use unchecked increments when overflow is not possible.

<details>
<summary><i>3 issue instances in 1 files:</i></summary>

```solidity
File: src/transformers/V3Utils.sol

619: state.i++
623: state.i++
627: state.i++
```
[619](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L619) | [623](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L623) | [627](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L627)
</details>

### [G-29] Using `this` to access functions results in an external call, wasting gas

Using `this.<fn>()` to call an external function from within the contract unnecessarily wastes gas. This is because calling an external function requires a gas overhead of 100 gas.

Instead, you can reduce the gas cost by making the function public and calling it directly without `this`. The Ethereum Virtual Machine (EVM) does not require additional gas for calling public functions internally.

Always aim for efficient gas usage when writing Solidity contracts to optimize for cost and performance.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/automators/Automator.sol

128: uint256 balance = address(this).balance;
```
[128](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L128)
</details>

### [G-30] Constructors can be marked `payable`

Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided.

A constructor can safely be marked as `payable`, since only the deployer would be able to pass funds, and the project itself would not pass any funds. 
T
his could save an average of about 21 gas per call, in addition to the extra deployment cost.

<details>
<summary><i>11 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

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

74: constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _referenceToken,
        address _chainlinkReferenceToken
    ) {
```
[74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L74)

```solidity
File: src/InterestRateModel.sol

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

32: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
```
[32](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L32)

```solidity
File: src/automators/Automator.sol

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
File: src/transformers/AutoCompound.sol

36: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, address(0), address(0)) {}
```
[36](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L36)

```solidity
File: src/transformers/AutoRange.sol

24: constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
```
[24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L24)

```solidity
File: src/transformers/LeverageTransformer.sol

13: constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)
        Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter)
    {}
```
[13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L13)

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
File: src/utils/FlashloanLiquidator.sol

23: constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)
        Swapper(_nonfungiblePositionManager, _zeroxRouter, _universalRouter)
    {}
```
[23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L23)

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

### [G-31] Split `revert` checks to save gas

Using boolean operators in a single `if() revert` statement can consume more gas than necessary.
Consider splitting these statements to save gas.

<details>
<summary><i>13 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

435: if (msg.sender != address(nonfungiblePositionManager) || from == address(this)) {
            revert WrongContract();
502: if (tokenId == 0 || !transformerAllowList[transformer]) {
            revert TransformNotAllowed();
736: if (amount0 < params.amount0Min || amount1 < params.amount1Min) {
            revert SlippageError();
790: if (
            transformer == address(0) || transformer == address(this) || transformer == asset
                || transformer == address(nonfungiblePositionManager)
        ) {
            revert InvalidConfig();
```
[435](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L435) | [502](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L502) | [736](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L736) | [790](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L790)

```solidity
File: src/V3Oracle.sol

227: if (!(token0 == token && token1 == referenceToken || token0 == referenceToken && token1 == token)) {
                revert InvalidPool();
338: if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0) {
            revert ChainlinkPriceError();
```
[227](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L227) | [338](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L338)

```solidity
File: src/InterestRateModel.sol

88: if (
            baseRatePerYearX96 > MAX_BASE_RATE_X96 || multiplierPerYearX96 > MAX_MULTIPLIER_X96
                || jumpMultiplierPerYearX96 > MAX_MULTIPLIER_X96
        ) {
            revert InvalidConfig();
```
[88](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L88)

```solidity
File: src/automators/AutoExit.sol

111: if (
            config.onlyFees && params.rewardX64 > config.maxRewardX64
                || !config.onlyFees && params.rewardX64 > config.maxRewardX64
        ) {
            revert ExceedsMaxReward();
```
[111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L111)

```solidity
File: src/transformers/AutoCompound.sol

88: if (!operators[msg.sender] || !vaults[vault]) {
            revert Unauthorized();
```
[88](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L88)

```solidity
File: src/transformers/AutoRange.sol

98: if (!operators[msg.sender] || !vaults[vault]) {
            revert Unauthorized();
121: if (
            config.onlyFees && params.rewardX64 > config.maxRewardX64
                || !config.onlyFees && params.rewardX64 > config.maxRewardX64
        ) {
            revert ExceedsMaxReward();
148: if (params.swap0To1 && params.amountIn > state.amount0 || !params.swap0To1 && params.amountIn > state.amount1) {
            revert SwapAmountTooLarge();
```
[98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L98) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L121) | [148](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L148)

```solidity
File: src/transformers/V3Utils.sol

142: if (amount0 < instructions.amountIn0 || amount1 < instructions.amountIn1) {
            revert AmountError();
```
[142](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L142)
</details>

### [G-32] Multiple accesses of a mapping/array should use a local variable cache

Leveraging a local variable to cache these values when accessed more than once can yield a gas saving of approximately 42 units per access.
This reduction is attributed to eliminating the need for recalculating the key's keccak256 hash (which costs Gkeccak256 - 30 gas) and the associated stack operations.
For arrays, this also prevents the overhead of re-computing offsets in memory or calldata.

<details>
<summary><i>30 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit `tokenOwner[tokenId]` is used 2 times
561: if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {
595: address owner = tokenOwner[tokenId];
/// @audit `tokenConfigs[token]` is used 2 times
863: tokenConfigs[token].collateralFactorX32 = collateralFactorX32;
864: tokenConfigs[token].collateralValueLimitFactorX32 = collateralValueLimitFactorX32;
/// @audit `tokenConfigs[token0]` is used 4 times
1217: tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1220: tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
1226: uint256 collateralValueLimitFactorX32 = tokenConfigs[token0].collateralValueLimitFactorX32;
1229: && _convertToAssets(tokenConfigs[token0].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
/// @audit `tokenConfigs[token1]` is used 4 times
1218: tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1221: tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
1234: collateralValueLimitFactorX32 = tokenConfigs[token1].collateralValueLimitFactorX32;
1237: && _convertToAssets(tokenConfigs[token1].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
/// @audit `ownedTokens[to]` is used 2 times
1298: ownedTokensIndex[tokenId] = ownedTokens[to].length;
1299: ownedTokens[to].push(tokenId);
/// @audit `ownedTokens[from]` is used 4 times
1304: uint256 lastTokenIndex = ownedTokens[from].length - 1;
1307: uint256 lastTokenId = ownedTokens[from][lastTokenIndex];
1308: ownedTokens[from][tokenIndex] = lastTokenId;
1311: ownedTokens[from].pop();
/// @audit `ownedTokensIndex[tokenId]` is used 2 times
1305: uint256 tokenIndex = ownedTokensIndex[tokenId];
1312: // Note that ownedTokensIndex[tokenId] is not deleted. There is no need to delete it - gas optimization
```
[561](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L561) | [595](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L595) | [863](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L863) | [864](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L864) | [1217](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1217) | [1220](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1220) | [1226](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1226) | [1229](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1229) | [1218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1218) | [1221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1221) | [1234](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1234) | [1237](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1237) | [1298](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1298) | [1299](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1299) | [1304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1304) | [1307](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1307) | [1308](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1308) | [1311](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1311) | [1305](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1305) | [1312](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1312)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit `positionBalances[params.tokenId]` is used 2 times
119: state.amount0 = state.amount0 + positionBalances[params.tokenId][state.token0];
120: state.amount1 = state.amount1 + positionBalances[params.tokenId][state.token1];
/// @audit `positionBalances[tokenId]` is used 2 times
211: uint256 balance0 = positionBalances[tokenId][token0];
215: uint256 balance1 = positionBalances[tokenId][token1];
/// @audit `positionBalances[tokenId]` is used 2 times
250: positionBalances[tokenId][token] = positionBalances[tokenId][token] + amount;
250: positionBalances[tokenId][token] = positionBalances[tokenId][token] + amount;
/// @audit `positionBalances[tokenId]` is used 2 times
255: uint256 currentBalance = positionBalances[tokenId][token];
257: positionBalances[tokenId][token] = amount;
/// @audit `positionBalances[tokenId]` is used 2 times
270: positionBalances[tokenId][token] = positionBalances[tokenId][token] - amount;
270: positionBalances[tokenId][token] = positionBalances[tokenId][token] - amount;
```
[119](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L119) | [120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L120) | [211](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L211) | [215](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L215) | [250](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L250) | [250](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L250) | [255](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L255) | [257](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L257) | [270](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L270) | [270](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L270)
</details>

### [G-33] Reduce gas usage by moving to Solidity 0.8.19 or later

See [this](https://soliditylang.org/blog/2023/02/22/solidity-0.8.19-release-announcement/#preventing-dead-code-in-runtime-bytecode) link for the full details. Additionally, every new release has new optimizations, which will save gas.

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

### [G-34] Reduce deployment costs by tweaking contracts' metadata

The Solidity compiler appends 53 bytes of metadata to the smart contract code which translates to an extra 10,600 gas (200 per bytecode) + the calldata cost (16 gas per non-zero bytes, 4 gas per zero-byte).
This translates to up to 848 additional gas in calldata cost.
One way to reduce this cost is by optimizing the IPFS hash that gets appended to the smart contract code.

Why is this important?
- The metadata adds an extra 53 bytes, resulting in an additional 10,600 gas cost for deployment.
- It also incurs up to 848 additional gas in calldata cost.

Options to Reduce Gas:
1. Use the `--no-cbor-metadata` compiler option to exclude metadata, but this might affect contract verification.
2. Mine for code comments that lead to an IPFS hash with more zeros, reducing calldata costs.

<details>
<summary><i>11 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1)

```solidity
File: src/V3Oracle.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L1)

```solidity
File: src/InterestRateModel.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L1)

```solidity
File: src/automators/AutoExit.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L1)

```solidity
File: src/automators/Automator.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L1)

```solidity
File: src/transformers/AutoCompound.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L1)

```solidity
File: src/transformers/AutoRange.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L1)

```solidity
File: src/transformers/LeverageTransformer.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L1)

```solidity
File: src/transformers/V3Utils.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L1)

```solidity
File: src/utils/FlashloanLiquidator.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L1)

```solidity
File: src/utils/Swapper.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L1)
</details>

### [G-35] Use Pre-Increment/Decrement (++i/--i) to Save Gas

Using pre-increment (++i) or pre-decrement (--i) operators is more gas-efficient compared to their post counterparts (i++ or i--).
This is because pre-increment/decrement operators avoid the need for an additional temporary variable that stores the original value of the iterator.
This subtle difference results in saving of around 5 gas units per operation, which can accumulate to substantial savings in gas costs in contracts with frequent increment/decrement operations.

<details>
<summary><i>3 issue instances in 1 files:</i></summary>

```solidity
File: src/transformers/V3Utils.sol

619: transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed0);
623: transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed1);
627: transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.neededOther);
```
[619](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L619) | [623](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L623) | [627](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L627)
</details>

### [G-36] Nesting `if`-statements is cheaper than using `&&`

Optimization of condition checks in your smart contract is a crucial aspect in ensuring gas efficiency. Specifically, substituting multiple `&&` checks with nested `if` statements can lead to substantial gas savings.

When evaluating multiple conditions within a single `if` statement using the `&&` operator, each condition will consume gas even if a preceding condition fails. However, if these checks are broken down into nested `if` statements, execution halts as soon as a condition fails, saving the gas that would have been consumed by subsequent checks.

This practice is especially beneficial in scenarios where the `if` statement isn't followed by an `else` statement. The reason being, when an `else` statement is present, all conditions must be checked regardless to determine the correct branch of execution.

By reworking your code to utilize nested `if` statements, you can optimize gas usage, reduce execution cost, and enhance your contract's performance.

<details>
<summary><i>18 issue instances in 9 files:</i></summary>

```solidity
File: src/V3Vault.sol

515: if (loanOwner != msg.sender && !transformApprovals[loanOwner][tokenId][msg.sender]) {
561: if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {
814: if (msg.sender != emergencyAdmin && msg.sender != owner()) {
```
[515](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L515) | [561](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L561) | [814](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L814)

```solidity
File: src/V3Oracle.sol

227: if (!(token0 == token && token1 == referenceToken || token0 == referenceToken && token1 == token)) {
250: if (msg.sender != emergencyAdmin && msg.sender != owner()) {
```
[227](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L227) | [250](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L250)

```solidity
File: src/automators/AutoExit.sol

135: if (config.token0TriggerTick <= state.tick && state.tick < config.token1TriggerTick) {
```
[135](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L135)

```solidity
File: src/automators/Automator.sol

219: if (address(weth) == address(token) && unwrap) {
```
[219](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L219)

```solidity
File: src/transformers/AutoCompound.sol

102: if (!operators[msg.sender] && !vaults[msg.sender]) {
```
[102](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L102)

```solidity
File: src/transformers/AutoRange.sol

112: if (!operators[msg.sender] && !vaults[msg.sender]) {
149: if (params.swap0To1 && params.amountIn > state.amount0 || !params.swap0To1 && params.amountIn > state.amount1) {
```
[112](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L112) | [149](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L149)

```solidity
File: src/transformers/LeverageTransformer.sol

93: if (token != token0 && token != token1 && amount > 0) {
146: if (params.amountIn0 > 0 && token != token0) {
155: if (params.amountIn1 > 0 && token != token1) {
169: if (amount0 > 0 && token != token0) {
172: if (amount1 > 0 && token != token1) {
```
[93](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L93) | [146](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L146) | [155](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L155) | [169](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L169) | [172](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L172)

```solidity
File: src/transformers/V3Utils.sol

342: if (targetAmount != 0 && instructions.targetToken != address(0)) {
865: if (address(weth) == address(token) && unwrap) {
```
[342](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L342) | [865](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L865)

```solidity
File: src/utils/Swapper.sol

77: if (params.amountIn != 0 && params.swapData.length != 0 && address(params.tokenOut) != address(0)) {
```
[77](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L77)
</details>

### [G-37] Use `storage` instead of `memory` for state structs/arrays

When fetching data from storage, assigning it to a memory variable causes all fields of the struct/array to be read from storage, incurring a Gcoldsload (2100 gas) for each field.
Reading fields from the new memory variable incurs an additional MLOAD rather than a cheap stack read.

Instead, declare variables with the storage keyword and cache any fields that need to be re-read in stack variables.
This approach is more cost-efficient, only incurring the Gcoldsload for fields actually read.

The only time it makes sense to read the whole struct/array into a memory variable is if the full struct/array is being returned by the function, passed to a function that requires memory, or read from another memory array/struct.

<details>
<summary><i>3 issue instances in 3 files:</i></summary>

```solidity
File: src/V3Oracle.sol

177: PositionState memory state = _initializeState(tokenId);
```
[177](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L177)

```solidity
File: src/automators/AutoExit.sol

106: PositionConfig memory config = positionConfigs[params.tokenId];
```
[106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L106)

```solidity
File: src/transformers/AutoRange.sol

116: PositionConfig memory config = positionConfigs[params.tokenId];
```
[116](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L116)
</details>

### [G-38] Optimize by Using Assembly for Low-Level Calls' Return Data

Even second return value from a low-level call is not assigned, it is still copied to memory, leading to additional gas costs.
By employing assembly, you can bypass this memory copying, achieving a 159 gas saving.

<details>
<summary><i>5 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

522: (bool success,) = transformer.call(data);
```
[522](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L522)

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

```solidity
File: src/utils/Swapper.sol

89: (bool success,) = zeroxRouter.call(data.data);
```
[89](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L89)
</details>

### [G-39] Avoid transferring amounts of zero in order to save gas

Performing token or Ether transfers with a zero amount may result in unnecessary gas consumption. 
The absence of a zero-amount check before a transfer or send operation can lead to wasted gas, as the state of the contract remains the same even if the amount is zero. 
Adding a conditional check for zero amounts can prevent these costly, unnecessary operations, thereby optimizing the contract's gas usage.

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

### [G-40] `>=` costs less gas than `>`

The Solidity compiler requires fewer opcodes when the `>=` operator is used in place of the `>` operator. 
Specifically, the compiler uses GT and ISZERO opcodes for `>` but only requires LT for `>=`, saving 3 gas. 
Thus, wherever applicable, it's recommended to use `>=` instead of `>` to enhance gas efficiency in your code. Same applies for `<=` and `<`.

<details>
<summary><i>71 issue instances in 11 files:</i></summary>

```solidity
File: src/V3Vault.sol

571: if (debtSharesTotal > _convertToShares(globalDebtLimit, newDebtExchangeRateX96, Math.Rounding.Down)) {
574: if (assets > dailyDebtIncreaseLimitLeft) {
586: if (debt < minLoanSize) {
737: if (amount0 < params.amount0Min || amount1 < params.amount1Min) {
737: if (amount0 < params.amount0Min || amount1 < params.amount1Min) {
771: uint256 unprotected = reserves > protected ? reserves - protected : 0;
772: uint256 available = balance > unprotected ? unprotected : balance;
774: if (amount > available) {
845: if (_reserveProtectionFactorX32 < MIN_RESERVE_PROTECTION_FACTOR_X32) {
860: if (collateralFactorX32 > MAX_COLLATERAL_FACTOR_X32) {
906: if (totalSupply() > globalLendLimit) {
910: if (assets > dailyLendIncreaseLimitLeft) {
940: if (available < assets) {
973: if (shares > currentShares) {
1008: if (_convertToAssets(loanDebtShares, newDebtExchangeRateX96, Math.Rounding.Up) < minLoanSize) {
1027: reserves = balance + debt > lent ? balance + debt - lent : 0;
1028: available = balance > reserves ? balance - reserves : 0;
1052: if (liquidationValue < feeValue) {
1131: if (reserveCost > reserves) {
1155: if (block.timestamp > lastExchangeRateUpdate) {
1216: if (oldShares > newShares) {
1228: collateralValueLimitFactorX32 < type(uint32).max
1229: && _convertToAssets(tokenConfigs[token0].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
                            > lentAssets * collateralValueLimitFactorX32 / Q32
1236: collateralValueLimitFactorX32 < type(uint32).max
1237: && _convertToAssets(tokenConfigs[token1].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
                            > lentAssets * collateralValueLimitFactorX32 / Q32
1249: if (force || time > dailyLendIncreaseLimitLastReset) {
1253: dailyLendIncreaseLimitMin > lendIncreaseLimit ? dailyLendIncreaseLimitMin : lendIncreaseLimit;
1261: if (force || time > dailyDebtIncreaseLimitLastReset) {
1265: dailyDebtIncreaseLimitMin > debtIncreaseLimit ? dailyDebtIncreaseLimitMin : debtIncreaseLimit;
```
[571](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L571) | [574](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L574) | [586](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L586) | [737](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L737) | [737](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L737) | [771](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L771) | [772](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L772) | [774](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L774) | [845](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L845) | [860](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L860) | [906](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L906) | [910](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L910) | [940](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L940) | [973](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L973) | [1008](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1008) | [1027](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1027) | [1028](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1028) | [1052](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1052) | [1131](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1131) | [1155](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1155) | [1216](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1216) | [1228](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1228) | [1229](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1229) | [1236](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1236) | [1237](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1237) | [1249](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1249) | [1253](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1253) | [1261](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1261) | [1265](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1265)

```solidity
File: src/V3Oracle.sol

143: uint256 differenceX10000 = priceX96 > verifyPriceX96
186: if (_maxPoolPriceDifference < MIN_PRICE_DIFFERENCE) {
221: if (maxDifference < MIN_PRICE_DIFFERENCE) {
338: if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0) {
485: if (tickCurrent < tickLower) {
488: } else if (tickCurrent < tickUpper) {
```
[143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L143) | [186](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L186) | [221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L221) | [338](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L338) | [485](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L485) | [488](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L488)

```solidity
File: src/InterestRateModel.sol

89: baseRatePerYearX96 > MAX_BASE_RATE_X96 || multiplierPerYearX96 > MAX_MULTIPLIER_X96
89: baseRatePerYearX96 > MAX_BASE_RATE_X96 || multiplierPerYearX96 > MAX_MULTIPLIER_X96
90: || jumpMultiplierPerYearX96 > MAX_MULTIPLIER_X96
```
[89](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L89) | [89](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L89) | [90](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L90)

```solidity
File: src/automators/AutoExit.sol

113: config.onlyFees && params.rewardX64 > config.maxRewardX64
114: || !config.onlyFees && params.rewardX64 > config.maxRewardX64
135: if (config.token0TriggerTick <= state.tick && state.tick < config.token1TriggerTick) {
```
[113](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L113) | [114](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L114) | [135](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L135)

```solidity
File: src/automators/Automator.sol

88: if (_TWAPSeconds < MIN_TWAP_SECONDS) {
91: if (_maxTWAPTickDifference > MAX_TWAP_TICK_DIFFERENCE) {
111: for (; i < count; ++i) {
```
[88](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L88) | [91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L91) | [111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L111)

```solidity
File: src/transformers/AutoCompound.sol

233: for (; i < count; ++i) {
244: require(_totalRewardX64 <= totalRewardX64, ">totalRewardX64");
258: if (amount > currentBalance) {
269: require(amount <= balance, "amount>balance");
```
[233](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L233) | [244](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L244) | [258](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L258) | [269](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L269)

```solidity
File: src/transformers/AutoRange.sol

123: config.onlyFees && params.rewardX64 > config.maxRewardX64
124: || !config.onlyFees && params.rewardX64 > config.maxRewardX64
149: if (params.swap0To1 && params.amountIn > state.amount0 || !params.swap0To1 && params.amountIn > state.amount1) {
149: if (params.swap0To1 && params.amountIn > state.amount0 || !params.swap0To1 && params.amountIn > state.amount1) {
167: state.currentTick < state.tickLower - config.lowerTickLimit
280: if (config.lowerTickDelta > config.upperTickDelta) {
```
[123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L123) | [124](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L124) | [149](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L149) | [149](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L149) | [167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L167) | [280](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L280)

```solidity
File: src/transformers/LeverageTransformer.sol

87: if (amount0 > added0) {
90: if (amount1 > added1) {
```
[87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L87) | [90](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L90)

```solidity
File: src/transformers/V3Utils.sol

142: if (amount0 < instructions.amountIn0 || amount1 < instructions.amountIn1) {
142: if (amount0 < instructions.amountIn0 || amount1 < instructions.amountIn1) {
316: if (amountInDelta < amount0) {
333: if (amountInDelta < amount1) {
671: if (amountAdded0 > amount0) {
676: if (amountAdded1 > amount1) {
681: if (amountAddedOther > amountOther) {
690: if (amount0 > amountAdded0) {
693: if (amount1 > amountAdded1) {
697: amountOther > amountAddedOther && address(otherToken) != address(0) && token0 != otherToken
784: if (params.amount0 < params.amountIn1) {
795: if (params.amount1 < params.amountIn0) {
```
[142](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L142) | [142](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L142) | [316](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L316) | [333](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L333) | [671](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L671) | [676](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L676) | [681](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L681) | [690](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L690) | [693](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L693) | [697](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L697) | [784](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L784) | [795](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L795)

```solidity
File: src/utils/FlashloanLiquidator.sol

102: if (balance < data.minReward) {
```
[102](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L102)

```solidity
File: src/utils/Swapper.sol

111: if (amountOutDelta < params.amountOutMin) {
149: if (amountOutDelta < params.amountOutMin) {
```
[111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L111) | [149](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L149)
</details>

### [G-41] Cache Function Calls for Efficiency

Function calls, especially external function calls, can be quite expensive in terms of gas. 
If you need to retrieve the same data more than once in a function, it is more efficient to call 
the function once, store the result in a local variable, and then use that variable later in the 
code instead of making the function call again.

<details>
<summary><i>20 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

1217: tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1218: tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1220: tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
1221: tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
```
[1217](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1217) | [1218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1218) | [1220](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1220) | [1221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1221)

```solidity
File: src/transformers/V3Utils.sol

618: state.balanceBefore0 = token0.balanceOf(address(this));
635: if (token0.balanceOf(address(this)) - state.balanceBefore0 != state.needed0) {
622: state.balanceBefore1 = token1.balanceOf(address(this));
640: if (token1.balanceOf(address(this)) - state.balanceBefore1 != state.needed1) {
626: state.balanceBeforeOther = otherToken.balanceOf(address(this));
645: if (otherToken.balanceOf(address(this)) - state.balanceBeforeOther != state.neededOther) {
896: uint256 balanceBefore0 = token0.balanceOf(address(this));
901: uint256 balanceAfter0 = token0.balanceOf(address(this));
897: uint256 balanceBefore1 = token1.balanceOf(address(this));
902: uint256 balanceAfter1 = token1.balanceOf(address(this));
```
[618](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L618) | [635](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L635) | [622](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L622) | [640](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L640) | [626](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L626) | [645](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L645) | [896](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L896) | [901](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L901) | [897](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L897) | [902](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L902)

```solidity
File: src/utils/FlashloanLiquidator.sol

89: uint256 balance = data.swap0.tokenIn.balanceOf(address(this));
95: uint256 balance = data.swap1.tokenIn.balanceOf(address(this));
```
[89](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L89) | [95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L95)

```solidity
File: src/utils/Swapper.sol

78: uint256 balanceInBefore = params.tokenIn.balanceOf(address(this));
104: uint256 balanceInAfter = params.tokenIn.balanceOf(address(this));
79: uint256 balanceOutBefore = params.tokenOut.balanceOf(address(this));
105: uint256 balanceOutAfter = params.tokenOut.balanceOf(address(this));
```
[78](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L78) | [104](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L104) | [79](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L79) | [105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L105)
</details>

### [G-42] Unutilized Named Return Variables Waste Gas Without Optimizer

Utilizing named return variables without assignment or explicit return in functions can lead to unnecessary gas costs without an active optimizer.
To enhance gas efficiency, you might consider opting for unnamed return variables, especially when they aren't explicitly used or returned.
Keeping the current configuration without an active optimizer can result in extra gas costs associated with superfluous stack variables.

<details>
<summary><i>8 issue instances in 3 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit - Redundant `return tokenOwner[tokenId];` statement in functions with named return variables
258: function ownerOf(uint256 tokenId) external view override returns (address owner) {
/// @audit - Redundant `return _convertToShares(assets, lendExchangeRateX96, Math.Rounding.Down);` statement in functions with named return variables
289: function convertToShares(uint256 assets) external view override returns (uint256 shares) {
/// @audit - Redundant `return _convertToAssets(shares, lendExchangeRateX96, Math.Rounding.Down);` statement in functions with named return variables
295: function convertToAssets(uint256 shares) external view override returns (uint256 assets) {
/// @audit - Redundant `return tokenId;` statement in functions with named return variables
497: function transform(uint256 tokenId, address transformer, bytes calldata data)
        external
        override
        returns (uint256 newTokenId)
    {
```
[258](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L258) | [289](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L289) | [295](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L295) | [497](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L497)

```solidity
File: src/V3Oracle.sol

/// @audit - Redundant `return (Q96, chainlinkReferencePriceX96);` statement in functions with named return variables
272: function _getReferenceTokenPriceX96(address token, uint256 cachedChainlinkReferencePriceX96)
        internal
        view
        returns (uint256 priceX96, uint256 chainlinkReferencePriceX96)
    {
```
[272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L272)

```solidity
File: src/transformers/V3Utils.sol

/// @audit - Redundant `return execute(tokenId, instructions);` statement in functions with named return variables
98: function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)
        public
        returns (uint256 newTokenId)
    {
397: function swap(SwapParams calldata params) external payable returns (uint256 amountOut) {
779: function _swapAndPrepareAmounts(SwapAndMintParams memory params, bool unwrap)
        internal
        returns (uint256 total0, uint256 total1)
    {
```
[98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L98) | [397](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L397) | [779](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L779)
</details>

### [G-43] Use `unchecked` for Math Operations if they already checked

Some subtraction operations in the contract have implicit checks that prevent underflow. 
To optimize gas, consider wrapping such operations in an `unchecked` block. 
Always review the logic thoroughly before making changes to ensure the safety of operations.

<details>
<summary><i>21 issue instances in 6 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit - mathematical operation `globalLendLimit - value` checked above in line:
/// 304: if (value >= globalLendLimit) {
307: return globalLendLimit - value;
/// @audit - mathematical operation `globalLendLimit - value` checked above in line:
/// 315: if (value >= globalLendLimit) {
318: return _convertToShares(globalLendLimit - value, lendExchangeRateX96, Math.Rounding.Down);
/// @audit - mathematical operation `liquidationValue - feeValue` checked above in line:
/// 1052: if (liquidationValue < feeValue) {
1060: liquidity = uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue));
/// @audit - mathematical operation `fullValue - maxPenaltyValue` checked above in line:
/// 1103: if (fullValue >= maxPenaltyValue) {
1107: (Q96 - ((fullValue - maxPenaltyValue) * Q96 / (startLiquidationValue - maxPenaltyValue)));
/// @audit - mathematical operation `reserveCost - reserves` checked above in line:
/// 1131: if (reserveCost > reserves) {
1132: missing = reserveCost - reserves;
/// @audit - mathematical operation `oldShares - newShares` checked above in line:
/// 1216: if (oldShares > newShares) {
1217: tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
/// @audit - mathematical operation `oldShares - newShares` checked above in line:
/// 1216: if (oldShares > newShares) {
1218: tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
/// @audit - mathematical operation `newShares - oldShares` checked above in line:
/// 1216: if (oldShares > newShares) {
1220: tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
/// @audit - mathematical operation `newShares - oldShares` checked above in line:
/// 1216: if (oldShares > newShares) {
1221: tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
```
[307](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L307) | [318](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L318) | [1060](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1060) | [1107](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1107) | [1132](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1132) | [1217](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1217) | [1218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1218) | [1220](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1220) | [1221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1221)

```solidity
File: src/InterestRateModel.sol

/// @audit - mathematical operation `utilizationRateX96 - kinkX96` checked above in line:
/// 66: if (utilizationRateX96 <= kinkX96) {
70: uint256 excessUtilX96 = utilizationRateX96 - kinkX96;
```
[70](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L70)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit - mathematical operation `amount - currentBalance` checked above in line:
/// 258: if (amount > currentBalance) {
259: emit BalanceAdded(tokenId, token, amount - currentBalance);
/// @audit - mathematical operation `currentBalance - amount` checked above in line:
/// 258: if (amount > currentBalance) {
261: emit BalanceRemoved(tokenId, token, currentBalance - amount);
```
[259](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L259) | [261](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L261)

```solidity
File: src/transformers/AutoRange.sol

/// @audit - mathematical operation `baseTick + config.lowerTickDelta` checked above in line:
/// 174: if (
                baseTick + config.lowerTickDelta == state.tickLower
                    && baseTick + config.upperTickDelta == state.tickUpper
            ) {
202: SafeCast.toInt24(baseTick + config.lowerTickDelta), // reverts if out of valid range
/// @audit - mathematical operation `baseTick + config.upperTickDelta` checked above in line:
/// 174: if (
                baseTick + config.lowerTickDelta == state.tickLower
                    && baseTick + config.upperTickDelta == state.tickUpper
            ) {
203: SafeCast.toInt24(baseTick + config.upperTickDelta), // reverts if out of valid range
```
[202](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L202) | [203](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L203)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit - mathematical operation `amount0 - added0` checked above in line:
/// 87: if (amount0 > added0) {
88: SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0 - added0);
/// @audit - mathematical operation `amount1 - added1` checked above in line:
/// 90: if (amount1 > added1) {
91: SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1 - added1);
```
[88](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L88) | [91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L91)

```solidity
File: src/transformers/V3Utils.sol

/// @audit - mathematical operation `amount0 - amountInDelta` checked above in line:
/// 316: if (amountInDelta < amount0) {
317: _transferToken(instructions.recipient, IERC20(token0), amount0 - amountInDelta, instructions.unwrap);
/// @audit - mathematical operation `amount1 - amountInDelta` checked above in line:
/// 333: if (amountInDelta < amount1) {
334: _transferToken(instructions.recipient, IERC20(token1), amount1 - amountInDelta, instructions.unwrap);
/// @audit - mathematical operation `amount0 - amountAdded0` checked above in line:
/// 671: if (amountAdded0 > amount0) {
691: needed0 = amount0 - amountAdded0;
/// @audit - mathematical operation `amount1 - amountAdded1` checked above in line:
/// 676: if (amountAdded1 > amount1) {
694: needed1 = amount1 - amountAdded1;
/// @audit - mathematical operation `amountOther - amountAddedOther` checked above in line:
/// 681: if (amountAddedOther > amountOther) {
700: neededOther = amountOther - amountAddedOther;
```
[317](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L317) | [334](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L334) | [691](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L691) | [694](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L694) | [700](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L700)
</details>

### [G-44] Using `private` rather than `public`, saves gas

Public storage variables increase the contract's size due to the implicit generation of public getter functions. 
This makes the contract larger and could increase deployment and interaction costs.

If you do not require other contracts to read these variables, consider making them `private`. 

Example:
```solidity
/// 145426 gas to deploy
contract PublicState {
    address public first;
    address public second;
}
/// 77126 gas to deploy
contract PrivateState {
    address private first;
    address private second;
}
```

<details>
<summary><i>66 issue instances in 9 files:</i></summary>

```solidity
File: src/V3Vault.sol

36: uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%
38: uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
39: uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%
41: uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%
43: uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%
44: uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%
47: INonfungiblePositionManager public immutable nonfungiblePositionManager;
50: IUniswapV3Factory public immutable factory;
53: IInterestRateModel public immutable interestRateModel;
56: IV3Oracle public immutable oracle;
59: IPermit2 public immutable permit2;
62: address public immutable override asset;
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
[36](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L36) | [38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L38) | [39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L39) | [41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L41) | [43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L43) | [44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L44) | [47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L47) | [50](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L50) | [53](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L53) | [56](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L56) | [59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L59) | [62](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L62) | [115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L115) | [118](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L118) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L121) | [124](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L124) | [127](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L127) | [128](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L128) | [129](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L129) | [131](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L131) | [132](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L132) | [135](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L135) | [138](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L138) | [139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L139) | [140](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L140) | [143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L143) | [144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L144) | [145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L145) | [154](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L154) | [163](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L163) | [164](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L164) | [167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L167)

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

### [G-45] Refactor duplicated require()/revert() checks to save gas

Duplicate require()/revert() checks can be refactored into a modifier or function, saving deployment costs.

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

### [G-46] Use Assembly for Efficient Memory Management in Multiple External Calls

When making multiple external calls in a Solidity contract, it may be more efficient to use inline assembly to reuse the memory space allocated for function arguments and return data.
This can prevent unnecessary memory expansion and reduce gas costs.

Example:
```solidity
contract Solidity {
    // cost: 7262
    function call(address calledAddress) external pure returns(uint256) {
        Called called = Called(calledAddress);
        uint256 res1 = called.add(1, 2);
        uint256 res2 = called.add(3, 4);

        uint256 res = res1 + res2;
        return res;
    }
}

contract Assembly {
    // cost: 5281
    function call(address calledAddress) external view returns(uint256) {
        assembly {
            // check that calledAddress has code deployed to it
            if iszero(extcodesize(calledAddress)) {
                revert(0x00, 0x00)
            }

            // first call
            mstore(0x00, hex"771602f7")
            mstore(0x04, 0x01)
            mstore(0x24, 0x02)
            let success := staticcall(gas(), calledAddress, 0x00, 0x44, 0x60, 0x20)
            if iszero(success) {
                revert(0x00, 0x00)
            }
            let res1 := mload(0x60)

            // second call
            mstore(0x04, 0x03)
            mstore(0x24, 0x4)
            success := staticcall(gas(), calledAddress, 0x00, 0x44, 0x60, 0x20)
            if iszero(success) {
                revert(0x00, 0x00)
            }
            let res2 := mload(0x60)

            // add results
            let res := add(res1, res2)

            // return data
            mstore(0x60, res)
            return(0x60, 0x20)
        }
    }
}
```

<details>
<summary><i>13 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit function `createWithPermit()` has multiple external calls
423: nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);
424: nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));
/// @audit function `transform()` has multiple external calls
520: nonfungiblePositionManager.approve(transformer, tokenId);
531: address owner = nonfungiblePositionManager.ownerOf(tokenId);
537: nonfungiblePositionManager.approve(address(0), tokenId);
/// @audit function `decreaseLiquidityAndCollect()` has multiple external calls
627: (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(
            INonfungiblePositionManager.DecreaseLiquidityParams(
                params.tokenId, params.liquidity, params.amount0Min, params.amount1Min, params.deadline
            )
        );
640: (amount0, amount1) = nonfungiblePositionManager.collect(collectParams);
/// @audit function `_sendPositionValue()` has multiple external calls
1045: (,,,,,,, liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);
1049: (,,, liquidity,,, fees0, fees1) = oracle.getPositionBreakdown(tokenId);
1065: nonfungiblePositionManager.decreaseLiquidity(
                INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp)
            );
1070: (amount0, amount1) = nonfungiblePositionManager.collect(
            INonfungiblePositionManager.CollectParams(tokenId, recipient, fees0, fees1)
        );
```
[423](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L423) | [424](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L424) | [520](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L520) | [531](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L531) | [537](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L537) | [627](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L627) | [640](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L640) | [1045](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1045) | [1049](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1049) | [1065](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1065) | [1070](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1070)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit function `_checkApprovals()` has multiple external calls
278: uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager));
282: uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager));
```
[278](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L278) | [282](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L282)
</details>

### [G-47] Optimize `require/revert` Statements with Assembly

Using inline assembly for revert statements in Solidity can offer gas optimizations.
The typical `require` or `revert` statements in Solidity perform additional memory operations and type checks which can be avoided by using low-level assembly code.

In certain contracts, particularly those that might revert often or are otherwise sensitive to gas costs, using assembly to handle reversion can offer meaningful savings.
These savings primarily come from avoiding memory expansion costs and extra type checks that the Solidity compiler performs.

Example:
```solidity
/// calling restrictedAction(2) with a non-owner address: 24042
function restrictedAction(uint256 num)  external {
    require(owner == msg.sender, "caller is not owner");
    specialNumber = num;
}

// calling restrictedAction(2) with a non-owner address: 23734
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
```

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: src/transformers/AutoCompound.sol

244: require(_totalRewardX64 <= totalRewardX64, ">totalRewardX64");
269: require(amount <= balance, "amount>balance");
```
[244](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L244) | [269](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L269)

```solidity
File: src/utils/Swapper.sol

157: require(amount0Delta > 0 || amount1Delta > 0); // swaps entirely within 0-liquidity regions are not supported
```
[157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L157)
</details>

### [G-48] Simple checks for zero `uint` can be done using `assembly` to save gas

The usage of inline `assembly` to check if variable is the `zero` can save gas compared to traditional `require` or `if` statement checks.
```solidity
    // gas 396 gas | 399 gas
    assembly {
        if iszero(value) { // use iszero(iszero(value)) for != add 3 gas
            revert(0, 0)
        }
    }
    require(value != 0); // 401 gas
    require(value == 0); // 401 gas

<details>
<summary><i>21 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

441: if (transformedTokenId == 0) {
502: if (tokenId == 0 || !transformerAllowList[transformer]) {
            revert TransformNotAllowed();
```
[441](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L441) | [502](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L502)

```solidity
File: src/V3Oracle.sol

362: if (twapSeconds == 0) {
            (sqrtPriceX96,,,,,,) = pool.slot0();
```
[362](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L362)

```solidity
File: src/InterestRateModel.sol

47: if (debt == 0) {
```
[47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L47)

```solidity
File: src/automators/AutoExit.sol

124: if (state.liquidity == 0) {
            revert NoLiquidity();
149: if (params.swapData.length == 0) {
                revert MissingSwapData();
```
[124](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L124) | [149](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L149)

```solidity
File: src/transformers/AutoCompound.sol

279: if (allowance0 == 0) {
            SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max);
283: if (allowance1 == 0) {
            SafeERC20.safeApprove(IERC20(token1), address(nonfungiblePositionManager), type(uint256).max);
```
[279](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L279) | [283](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L283)

```solidity
File: src/transformers/V3Utils.sol

120: if (instructions.liquidity != 0) {
            (amount0, amount1) = _decreaseLiquidity(
                tokenId,
                instructions.liquidity,
                instructions.deadline,
                instructions.amountRemoveMin0,
                instructions.amountRemoveMin1
            );
342: if (targetAmount != 0 && instructions.targetToken != address(0)) {
                _transferToken(
                    instructions.recipient, IERC20(instructions.targetToken), targetAmount, instructions.unwrap
                );
420: if (amountOut != 0) {
            _transferToken(params.recipient, params.tokenOut, amountOut, params.unwrap);
426: if (leftOver != 0) {
            _transferToken(params.recipient, params.tokenIn, leftOver, params.unwrap);
666: if (msg.value != 0) {
            weth.deposit{value: msg.value}();
822: if (leftOver != 0) {
                _transferToken(params.recipient, params.swapSourceToken, leftOver, unwrap);
830: if (total0 != 0) {
            SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), 0);
834: if (total1 != 0) {
            SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), 0);
855: if (left0 != 0) {
            _transferToken(to, token0, left0, unwrap);
858: if (left1 != 0) {
            _transferToken(to, token1, left1, unwrap);
884: if (liquidity != 0) {
            (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(
                INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, token0Min, token1Min, deadline)
            );
```
[120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L120) | [342](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L342) | [420](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L420) | [426](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L426) | [666](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L666) | [822](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L822) | [830](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L830) | [834](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L834) | [855](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L855) | [858](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L858) | [884](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L884)

```solidity
File: src/utils/FlashloanLiquidator.sol

43: if (liquidationCost == 0) {
            revert NotLiquidatable();
```
[43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L43)

```solidity
File: src/utils/Swapper.sol

77: if (params.amountIn != 0 && params.swapData.length != 0 && address(params.tokenOut) != address(0)) {
            uint256 balanceInBefore = params.tokenIn.balanceOf(address(this));
```
[77](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L77)
</details>

### [G-49] Consider using solady's `FixedPointMathLib`

Utilizing gas-optimized math functions from libraries like [Solady](https://github.com/Vectorized/solady/blob/main/src/utils/FixedPointMathLib.sol) can lead to more efficient smart contracts.
This is particularly beneficial in contracts where these operations are frequently used.

<details>
<summary><i>143 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

36: uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%
38: uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
39: uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%
769: _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up) * reserveProtectionFactorX32 / Q32;
1054: fees0 = uint128(liquidationValue * fees0 / feeValue);
1055: fees1 = uint128(liquidationValue * fees1 / feeValue);
1060: liquidity = uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue));
1100: uint256 maxPenaltyValue = debt * (Q32 + MAX_LIQUIDATION_PENALTY_X32) / Q32;
1105: uint256 startLiquidationValue = debt * fullValue / collateralValue;
1107: (Q96 - ((fullValue - maxPenaltyValue) * Q96 / (startLiquidationValue - maxPenaltyValue)));
1109: + (MAX_LIQUIDATION_PENALTY_X32 - MIN_LIQUIDATION_PENALTY_X32) * penaltyFractionX96 / Q96;
1111: liquidationValue = debt * (Q32 + penaltyX32) / Q32;
1116: uint256 penaltyValue = fullValue * (Q32 - MAX_LIQUIDATION_PENALTY_X32) / Q32;
1137: newLendExchangeRateX96 = (totalLent - missing) * newLendExchangeRateX96 / totalLent;
1188: + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;
1188: + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;
1190: + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;
1190: + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;
1230: > lentAssets * collateralValueLimitFactorX32 / Q32
1238: > lentAssets * collateralValueLimitFactorX32 / Q32
1250: uint256 lendIncreaseLimit = _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up)
                * (Q32 + MAX_DAILY_LEND_INCREASE_X32) / Q32;
1262: uint256 debtIncreaseLimit = _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up)
                * (Q32 + MAX_DAILY_DEBT_INCREASE_X32) / Q32;
36: uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%
38: uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
39: uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%
41: uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%
43: uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%
44: uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%
769: _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up) * reserveProtectionFactorX32 / Q32;
1054: fees0 = uint128(liquidationValue * fees0 / feeValue);
1055: fees1 = uint128(liquidationValue * fees1 / feeValue);
1060: liquidity = uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue));
1100: uint256 maxPenaltyValue = debt * (Q32 + MAX_LIQUIDATION_PENALTY_X32) / Q32;
1105: uint256 startLiquidationValue = debt * fullValue / collateralValue;
1107: (Q96 - ((fullValue - maxPenaltyValue) * Q96 / (startLiquidationValue - maxPenaltyValue)));
1109: + (MAX_LIQUIDATION_PENALTY_X32 - MIN_LIQUIDATION_PENALTY_X32) * penaltyFractionX96 / Q96;
1111: liquidationValue = debt * (Q32 + penaltyX32) / Q32;
1116: uint256 penaltyValue = fullValue * (Q32 - MAX_LIQUIDATION_PENALTY_X32) / Q32;
1137: newLendExchangeRateX96 = (totalLent - missing) * newLendExchangeRateX96 / totalLent;
1188: + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;
1190: + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;
1230: > lentAssets * collateralValueLimitFactorX32 / Q32
1238: > lentAssets * collateralValueLimitFactorX32 / Q32
1248: uint256 time = block.timestamp / 1 days;
1260: uint256 time = block.timestamp / 1 days;
33: uint256 private constant Q32 = 2 ** 32;
34: uint256 private constant Q96 = 2 ** 96;
```
[36](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L36) | [38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L38) | [39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L39) | [769](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L769) | [1054](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1054) | [1055](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1055) | [1060](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1060) | [1100](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1100) | [1105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1105) | [1107](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1107) | [1109](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1109) | [1111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1111) | [1116](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1116) | [1137](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1137) | [1188](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1188) | [1188](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1188) | [1190](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1190) | [1190](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1190) | [1230](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1230) | [1238](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1238) | [1250](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1250) | [1262](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1262) | [36](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L36) | [38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L38) | [39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L39) | [41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L41) | [43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L43) | [44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L44) | [769](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L769) | [1054](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1054) | [1055](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1055) | [1060](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1060) | [1100](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1100) | [1105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1105) | [1107](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1107) | [1109](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1109) | [1111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1111) | [1116](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1116) | [1137](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1137) | [1188](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1188) | [1190](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1190) | [1230](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1230) | [1238](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1238) | [1248](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1248) | [1260](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1260) | [33](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L33) | [34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L34)

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
342: return uint256(answer) * Q96 / (10 ** feedConfig.feedDecimals);
353: poolTWAPPriceX96 = Q96 * Q96 / priceX96;
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
27: uint256 private constant Q96 = 2 ** 96;
28: uint256 private constant Q128 = 2 ** 128;
304: chainlinkPriceX96 = (10 ** referenceTokenDecimals) * chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96
305: / (10 ** feedConfig.tokenDecimals);
342: return uint256(answer) * Q96 / (10 ** feedConfig.feedDecimals);
```
[120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L120) | [120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L120) | [120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L120) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L121) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L121) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L121) | [122](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L122) | [123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L123) | [129](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L129) | [144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L144) | [145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L145) | [304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L304) | [304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L304) | [342](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L342) | [353](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L353) | [120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L120) | [120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L120) | [120](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L120) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L121) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L121) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L121) | [122](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L122) | [123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L123) | [129](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L129) | [144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L144) | [145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L145) | [304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L304) | [304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L304) | [342](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L342) | [353](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L353) | [369](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L369) | [27](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L27) | [28](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L28) | [304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L304) | [305](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L305) | [342](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L342)

```solidity
File: src/InterestRateModel.sol

16: uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%
50: return debt * Q96 / (cash + debt);
67: borrowRateX96 = (utilizationRateX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
69: uint256 normalRateX96 = (kinkX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
71: borrowRateX96 = (excessUtilX96 * jumpMultiplierPerSecondX96 / Q96) + normalRateX96;
74: supplyRateX96 = utilizationRateX96 * borrowRateX96 / Q96;
15: uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10; // 10%
50: return debt * Q96 / (cash + debt);
67: borrowRateX96 = (utilizationRateX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
69: uint256 normalRateX96 = (kinkX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
71: borrowRateX96 = (excessUtilX96 * jumpMultiplierPerSecondX96 / Q96) + normalRateX96;
74: supplyRateX96 = utilizationRateX96 * borrowRateX96 / Q96;
95: baseRatePerSecondX96 = baseRatePerYearX96 / YEAR_SECS;
96: multiplierPerSecondX96 = multiplierPerYearX96 / YEAR_SECS;
97: jumpMultiplierPerSecondX96 = jumpMultiplierPerYearX96 / YEAR_SECS;
12: uint256 private constant Q96 = 2 ** 96;
```
[16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L16) | [50](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L50) | [67](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L67) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L69) | [71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L71) | [74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L74) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L15) | [50](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L50) | [67](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L67) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L69) | [71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L71) | [74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L74) | [95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L95) | [96](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L96) | [97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L97) | [12](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L12)

```solidity
File: src/automators/AutoExit.sol

155: state.amount0 -= state.feeAmount0 * params.rewardX64 / Q64;
156: state.amount1 -= state.feeAmount1 * params.rewardX64 / Q64;
187: state.amount0 -= state.amount0 * params.rewardX64 / Q64;
189: state.amount1 -= state.amount1 * params.rewardX64 / Q64;
194: state.amount0 -= (config.onlyFees ? state.feeAmount0 : state.amount0) * params.rewardX64 / Q64;
195: state.amount1 -= (config.onlyFees ? state.feeAmount1 : state.amount1) * params.rewardX64 / Q64;
155: state.amount0 -= state.feeAmount0 * params.rewardX64 / Q64;
156: state.amount1 -= state.feeAmount1 * params.rewardX64 / Q64;
187: state.amount0 -= state.amount0 * params.rewardX64 / Q64;
189: state.amount1 -= state.amount1 * params.rewardX64 / Q64;
194: state.amount0 -= (config.onlyFees ? state.feeAmount0 : state.amount0) * params.rewardX64 / Q64;
195: state.amount1 -= (config.onlyFees ? state.feeAmount1 : state.amount1) * params.rewardX64 / Q64;
```
[155](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L155) | [156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L156) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L187) | [189](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L189) | [194](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L194) | [195](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L195) | [155](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L155) | [156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L156) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L187) | [189](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L189) | [194](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L194) | [195](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L195)

```solidity
File: src/automators/Automator.sol

158: amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), priceX96, Q96 * Q64);
158: amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), priceX96, Q96 * Q64);
160: amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), Q96, priceX96 * Q64);
160: amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), Q96, priceX96 * Q64);
187: return (int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapPeriod))), true);
20: uint256 internal constant Q64 = 2 ** 64;
21: uint256 internal constant Q96 = 2 ** 96;
```
[158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L158) | [158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L158) | [160](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L160) | [160](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L160) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L187) | [20](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L20) | [21](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L21)

```solidity
File: src/transformers/AutoCompound.sol

156: state.maxAddAmount0 = state.amount0 * Q64 / (rewardX64 + Q64);
157: state.maxAddAmount1 = state.amount1 * Q64 / (rewardX64 + Q64);
170: state.amount0Fees = state.compounded0 * rewardX64 / Q64;
171: state.amount1Fees = state.compounded1 * rewardX64 / Q64;
47: uint64 public constant MAX_REWARD_X64 = uint64(Q64 / 50); // 2%
156: state.maxAddAmount0 = state.amount0 * Q64 / (rewardX64 + Q64);
157: state.maxAddAmount1 = state.amount1 * Q64 / (rewardX64 + Q64);
170: state.amount0Fees = state.compounded0 * rewardX64 / Q64;
171: state.amount1Fees = state.compounded1 * rewardX64 / Q64;
```
[156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L156) | [157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L157) | [170](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L170) | [171](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L171) | [47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L47) | [156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L156) | [157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L157) | [170](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L170) | [171](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L171)

```solidity
File: src/transformers/AutoRange.sol

143: state.protocolReward0 = state.feeAmount0 * params.rewardX64 / Q64;
144: state.protocolReward1 = state.feeAmount1 * params.rewardX64 / Q64;
195: state.maxAddAmount0 = config.onlyFees ? state.amount0 : state.amount0 * Q64 / (params.rewardX64 + Q64);
196: state.maxAddAmount1 = config.onlyFees ? state.amount1 : state.amount1 * Q64 / (params.rewardX64 + Q64);
236: state.protocolReward0 = state.amountAdded0 * params.rewardX64 / Q64;
237: state.protocolReward1 = state.amountAdded1 * params.rewardX64 / Q64;
39: int32 lowerTickLimit; // if negative also in-range positions may be adjusted / if 0 out of range positions may be adjusted
40: int32 upperTickLimit; // if negative also in-range positions may be adjusted / if 0 out of range positions may be adjusted
43: uint64 token0SlippageX64; // max price difference from current pool price for swap / Q64 for token0
44: uint64 token1SlippageX64; // max price difference from current pool price for swap / Q64 for token1
143: state.protocolReward0 = state.feeAmount0 * params.rewardX64 / Q64;
144: state.protocolReward1 = state.feeAmount1 * params.rewardX64 / Q64;
195: state.maxAddAmount0 = config.onlyFees ? state.amount0 : state.amount0 * Q64 / (params.rewardX64 + Q64);
196: state.maxAddAmount1 = config.onlyFees ? state.amount1 : state.amount1 * Q64 / (params.rewardX64 + Q64);
236: state.protocolReward0 = state.amountAdded0 * params.rewardX64 / Q64;
237: state.protocolReward1 = state.amountAdded1 * params.rewardX64 / Q64;
```
[143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L143) | [144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L144) | [195](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L195) | [196](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L196) | [236](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L236) | [237](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L237) | [39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L39) | [40](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L40) | [43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L43) | [44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L44) | [143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L143) | [144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L144) | [195](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L195) | [196](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L196) | [236](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L236) | [237](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L237)
</details>

### [G-50] Avoid Zero to Non-Zero Storage Writes Where Possible

Changing a storage variable from zero to non-zero costs 22,100 gas in total. (20,000 gas for a zero to non-zero write and 2,100 for a cold storage access)
Consider using non-zero architecture to avoid high gas costs for zero to non-zero storage writes.

Example:

```solidity
- uint256 public counter = 0;  // rewrite this costs more
+ uint256 public counter = 1;  // rewrite this costs less
```

<details>
<summary><i>28 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

458: transformedTokenId = tokenId;
508: transformedTokenId = tokenId;
577: dailyDebtIncreaseLimitLeft -= assets;
731: debtSharesTotal -= debtShares;
818: minLoanSize = _minLoanSize;
819: globalLendLimit = _globalLendLimit;
820: globalDebtLimit = _globalDebtLimit;
821: dailyLendIncreaseLimitMin = _dailyLendIncreaseLimitMin;
822: dailyDebtIncreaseLimitMin = _dailyDebtIncreaseLimitMin;
838: reserveFactorX32 = _reserveFactorX32;
848: reserveProtectionFactorX32 = _reserveProtectionFactorX32;
913: dailyLendIncreaseLimitLeft -= assets;
992: debtSharesTotal -= shares;
1138: lastLendExchangeRateX96 = newLendExchangeRateX96;
1157: lastDebtExchangeRateX96 = newDebtExchangeRateX96;
1158: lastLendExchangeRateX96 = newLendExchangeRateX96;
1159: lastExchangeRateUpdate = block.timestamp;
1252: dailyLendIncreaseLimitLeft =
                dailyLendIncreaseLimitMin > lendIncreaseLimit ? dailyLendIncreaseLimitMin : lendIncreaseLimit;
1254: dailyLendIncreaseLimitLastReset = time;
1264: dailyDebtIncreaseLimitLeft =
                dailyDebtIncreaseLimitMin > debtIncreaseLimit ? dailyDebtIncreaseLimitMin : debtIncreaseLimit;
1266: dailyDebtIncreaseLimitLastReset = time;
1298: ownedTokensIndex[tokenId] = ownedTokens[to].length;
1308: ownedTokens[from][tokenIndex] = lastTokenId;
1309: ownedTokensIndex[lastTokenId] = tokenIndex;
```
[458](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L458) | [508](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L508) | [577](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L577) | [731](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L731) | [818](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L818) | [819](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L819) | [820](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L820) | [821](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L821) | [822](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L822) | [838](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L838) | [848](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L848) | [913](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L913) | [992](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L992) | [1138](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1138) | [1157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1157) | [1158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1158) | [1159](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1159) | [1252](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1252) | [1254](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1254) | [1264](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1264) | [1266](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1266) | [1298](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1298) | [1308](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1308) | [1309](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1309)

```solidity
File: src/V3Oracle.sol

189: maxPoolPriceDifference = _maxPoolPriceDifference;
```
[189](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L189)

```solidity
File: src/automators/Automator.sol

95: TWAPSeconds = _TWAPSeconds;
96: maxTWAPTickDifference = _maxTWAPTickDifference;
```
[95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L95) | [96](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L96)

```solidity
File: src/transformers/AutoCompound.sol

245: totalRewardX64 = _totalRewardX64;
```
[245](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L245)
</details>

### [G-51] Consider Packing Small `uint` When it's Possible

Packing `uint` variables into the same storage slot can help in reducing gas costs.
This is particularly useful when storing or reading multiple smaller uints (e.g., uint80) in a single transaction.
Consider using bit manipulation to pack these variables.

If you pack two `uint` variables into a single `uint` storage slot, you'd perform only one SLOAD operation (800 gas) instead of two (1,600 gas) when you read them.
This saves 800 gas for each read operation involving the two variables.

Similarly, when you need to update both variables, a single SSTORE operation would cost you 20,000 gas instead of 40,000 gas, saving you another 20,000 gas. 

Example:
```Solidity
uint160 packedVariables;

function packVariables(uint80 x, uint80 y) external {
    packedVariables = uint160(x) << 80 | uint160(y);
}
```

<details>
<summary><i>4 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

118: uint32 public reserveFactorX32 = 0;
121: uint32 public reserveProtectionFactorX32 = MIN_RESERVE_PROTECTION_FACTOR_X32;
```
[118](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L118) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L121)

```solidity
File: src/automators/Automator.sol

39: uint16 public maxTWAPTickDifference;
38: uint32 public TWAPSeconds;
```
[39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L39) | [38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L38)
</details>

### [G-52] Consider Using `calldata` Instead of `memory` for Function Parameters

When function parameters are not being modified within the function, it can be more gas efficient 
to use `calldata` instead of `memory`. The Ethereum Virtual Machine (EVM) does not need to copy 
parameters marked with `calldata` from `calldata` to `memory`, saving gas. This is particularly effective 
for larger arrays and structs.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/transformers/V3Utils.sol

/// @audit `instructions` not modified within function
115: function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {
```
[115](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L115)
</details>

### [G-53] Use `unchecked` for division which do not divide by -X sonce they can't overflow

Solidity introduced the `unchecked` block in version 0.8.0 as a measure to provide control over arithmetic operations. 
Any operation inside this block will not trigger the built-in overflow and underflow checks, thus saving gas costs. 
Since a division operation between two `uint`s (unsigned integers) can never result in an overflow or underflow, it's an ideal candidate for the use of `unchecked {}` block.
This practice enables optimal gas usage without risking any arithmetic anomalies.

<details>
<summary><i>70 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

36: uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%
38: uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
39: uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%
41: uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%
43: uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%
44: uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%
769: _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up) * reserveProtectionFactorX32 / Q32;
1054: fees0 = uint128(liquidationValue * fees0 / feeValue);
1055: fees1 = uint128(liquidationValue * fees1 / feeValue);
1060: liquidity = uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue));
1100: uint256 maxPenaltyValue = debt * (Q32 + MAX_LIQUIDATION_PENALTY_X32) / Q32;
1105: uint256 startLiquidationValue = debt * fullValue / collateralValue;
1107: (Q96 - ((fullValue - maxPenaltyValue) * Q96 / (startLiquidationValue - maxPenaltyValue)));
1109: + (MAX_LIQUIDATION_PENALTY_X32 - MIN_LIQUIDATION_PENALTY_X32) * penaltyFractionX96 / Q96;
1111: liquidationValue = debt * (Q32 + penaltyX32) / Q32;
1116: uint256 penaltyValue = fullValue * (Q32 - MAX_LIQUIDATION_PENALTY_X32) / Q32;
1137: newLendExchangeRateX96 = (totalLent - missing) * newLendExchangeRateX96 / totalLent;
1188: + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;
1190: + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;
1230: > lentAssets * collateralValueLimitFactorX32 / Q32
1238: > lentAssets * collateralValueLimitFactorX32 / Q32
1248: uint256 time = block.timestamp / 1 days;
1260: uint256 time = block.timestamp / 1 days;
```
[36](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L36) | [38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L38) | [39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L39) | [41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L41) | [43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L43) | [44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L44) | [769](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L769) | [1054](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1054) | [1055](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1055) | [1060](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1060) | [1100](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1100) | [1105](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1105) | [1107](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1107) | [1109](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1109) | [1111](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1111) | [1116](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1116) | [1137](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1137) | [1188](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1188) | [1190](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1190) | [1230](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1230) | [1238](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1238) | [1248](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1248) | [1260](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1260)

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

15: uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10; // 10%
50: return debt * Q96 / (cash + debt);
67: borrowRateX96 = (utilizationRateX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
69: uint256 normalRateX96 = (kinkX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
71: borrowRateX96 = (excessUtilX96 * jumpMultiplierPerSecondX96 / Q96) + normalRateX96;
74: supplyRateX96 = utilizationRateX96 * borrowRateX96 / Q96;
95: baseRatePerSecondX96 = baseRatePerYearX96 / YEAR_SECS;
96: multiplierPerSecondX96 = multiplierPerYearX96 / YEAR_SECS;
97: jumpMultiplierPerSecondX96 = jumpMultiplierPerYearX96 / YEAR_SECS;
```
[15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L15) | [50](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L50) | [67](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L67) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L69) | [71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L71) | [74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L74) | [95](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L95) | [96](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L96) | [97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L97)

```solidity
File: src/automators/AutoExit.sol

155: state.amount0 -= state.feeAmount0 * params.rewardX64 / Q64;
156: state.amount1 -= state.feeAmount1 * params.rewardX64 / Q64;
187: state.amount0 -= state.amount0 * params.rewardX64 / Q64;
189: state.amount1 -= state.amount1 * params.rewardX64 / Q64;
194: state.amount0 -= (config.onlyFees ? state.feeAmount0 : state.amount0) * params.rewardX64 / Q64;
195: state.amount1 -= (config.onlyFees ? state.feeAmount1 : state.amount1) * params.rewardX64 / Q64;
```
[155](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L155) | [156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L156) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L187) | [189](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L189) | [194](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L194) | [195](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L195)

```solidity
File: src/automators/Automator.sol

187: return (int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapPeriod))), true);
```
[187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L187)

```solidity
File: src/transformers/AutoCompound.sol

47: uint64 public constant MAX_REWARD_X64 = uint64(Q64 / 50); // 2%
156: state.maxAddAmount0 = state.amount0 * Q64 / (rewardX64 + Q64);
157: state.maxAddAmount1 = state.amount1 * Q64 / (rewardX64 + Q64);
170: state.amount0Fees = state.compounded0 * rewardX64 / Q64;
171: state.amount1Fees = state.compounded1 * rewardX64 / Q64;
```
[47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L47) | [156](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L156) | [157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L157) | [170](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L170) | [171](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L171)

```solidity
File: src/transformers/AutoRange.sol

39: int32 lowerTickLimit; // if negative also in-range positions may be adjusted / if 0 out of range positions may be adjusted
40: int32 upperTickLimit; // if negative also in-range positions may be adjusted / if 0 out of range positions may be adjusted
43: uint64 token0SlippageX64; // max price difference from current pool price for swap / Q64 for token0
44: uint64 token1SlippageX64; // max price difference from current pool price for swap / Q64 for token1
143: state.protocolReward0 = state.feeAmount0 * params.rewardX64 / Q64;
144: state.protocolReward1 = state.feeAmount1 * params.rewardX64 / Q64;
195: state.maxAddAmount0 = config.onlyFees ? state.amount0 : state.amount0 * Q64 / (params.rewardX64 + Q64);
196: state.maxAddAmount1 = config.onlyFees ? state.amount1 : state.amount1 * Q64 / (params.rewardX64 + Q64);
236: state.protocolReward0 = state.amountAdded0 * params.rewardX64 / Q64;
237: state.protocolReward1 = state.amountAdded1 * params.rewardX64 / Q64;
```
[39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L39) | [40](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L40) | [43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L43) | [44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L44) | [143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L143) | [144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L144) | [195](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L195) | [196](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L196) | [236](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L236) | [237](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L237)
</details>

### [G-54] Use solady library where possible to save gas

The following OpenZeppelin imports have a Solady equivalent, as such they can be used to save GAS as Solady modules have been specifically designed to be as GAS efficient as possible.

<details>
<summary><i>21 issue instances in 8 files:</i></summary>

```solidity
File: src/V3Vault.sol

11: import "@openzeppelin/contracts/utils/math/Math.sol";
13: import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
14: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
15: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
16: import "@openzeppelin/contracts/access/Ownable.sol";
17: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
18: import "@openzeppelin/contracts/utils/Multicall.sol";
```
[11](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L11) | [13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L13) | [14](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L14) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L15) | [16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L16) | [17](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L17) | [18](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L18)

```solidity
File: src/V3Oracle.sol

13: import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";
15: import "@openzeppelin/contracts/access/Ownable.sol";
```
[13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L13) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L15)

```solidity
File: src/InterestRateModel.sol

3: import "@openzeppelin/contracts/access/Ownable.sol";
```
[3](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L3)

```solidity
File: src/automators/Automator.sol

3: import "@openzeppelin/contracts/access/Ownable.sol";
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
6: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
```
[3](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L3) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L5) | [6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L6)

```solidity
File: src/transformers/AutoCompound.sol

3: import "@openzeppelin/contracts/security/ReentrancyGuard.sol";
5: import "@openzeppelin/contracts/utils/Multicall.sol";
6: import "@openzeppelin/contracts/utils/math/SafeMath.sol";
```
[3](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L3) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L5) | [6](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L6)

```solidity
File: src/transformers/LeverageTransformer.sol

3: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[3](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L3) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L5)

```solidity
File: src/transformers/V3Utils.sol

3: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
5: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
```
[3](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L3) | [5](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L5)

```solidity
File: src/utils/Swapper.sol

3: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[3](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L3)
</details>

### [G-55] Avoid Inverting `if`-`else` Conditions

Inverting the condition of an `if`-`else`-statement results in extra gas consumption.
Consider simplifying the condition to reduce gas costs.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: src/automators/AutoExit.sol

185: if (!config.onlyFees) {
                if (state.isAbove) {
                    state.amount0 -= state.amount0 * params.rewardX64 / Q64;
                } else {
                    state.amount1 -= state.amount1 * params.rewardX64 / Q64;
                }
```
[185](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L185)
</details>

### [G-56] Use `uint256(1)`/`uint256(2)` instead of `true`/`false` to save gas for changes

Boolean variables in Solidity are more expensive than `uint256` or any type that takes up a full word, due to additional gas costs associated with write operations.
When using boolean variables, each write operation emits an extra SLOAD to read the slot's contents, replace the bits taken up by the boolean, and then write back.
This process cannot be disabled and leads to extra gas consumption.

By using `uint256(1)` and `uint256(2)` for representing true and false states, you can avoid a `Gwarmaccess` (100 gas) cost and also avoid a `Gsset` (20000 gas) cost when changing from `false` to `true`, after having been `true` in the past.
This approach helps in optimizing gas usage, making your contract more cost-effective.

[Usage in OpenZeppelin ReentrancyGuard.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/58f635312aa21f947cae5f8578638a85aa2519f5/contracts/security/ReentrancyGuard.sol#L23-L27)

<details>
<summary><i>4 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

163: mapping(address => bool) public transformerAllowList; // contracts allowed to transform positions (selected audited contracts e.g. V3Utils)
164: mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; // owners permissions for other addresses to call transform on owners behalf (e.g. AutoRange contract)
```
[163](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L163) | [164](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L164)

```solidity
File: src/automators/Automator.sol

34: mapping(address => bool) public operators;
35: mapping(address => bool) public vaults;
```
[34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L34) | [35](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L35)
</details>

### [G-57] Use Bit Shifting for Multiplication by Powers of Two

When multiplying by powers of two (e.g., 2, 4, 8), it is more efficient to use bit shifting.

`<x> * 2` can be replaced with `<x> << 1`, as both operations are equivalent.
However, the multiplication approach may incur additional gas overhead due to potential jumps to and from a compiler utility function that introduces checks.

This overhead can be minimized by using bit shifting when multiplying by powers of two.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

38: uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
```
[38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L38)

```solidity
File: src/InterestRateModel.sol

16: uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%
```
[16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L16)
</details>

### [G-58] Avoid contract existence checks by using low-level calls

Before version 0.8.10, the Solidity compiler would insert extra code, such as EXTCODESIZE (costing 100 gas), to check the existence of a contract for external function calls.
Newer versions, starting from 0.8.10, no longer insert these checks if the external call has a return value.
You can achieve similar behavior in earlier Solidity versions by using low-level calls like `call`.
This low-level call don't check for contract existence, saving gas costs.

<details>
<summary><i>181 issue instances in 10 files:</i></summary>

```solidity
File: src/V3Vault.sol

179: assetDecimals = IERC20Metadata(_asset).decimals();
181: factory = IUniswapV3Factory(_nonfungiblePositionManager.factory());
401: nonfungiblePositionManager.safeTransferFrom(msg.sender, address(this), tokenId, abi.encode(recipient));
423: nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);
424: nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));
520: nonfungiblePositionManager.approve(transformer, tokenId);
531: address owner = nonfungiblePositionManager.ownerOf(tokenId);
537: nonfungiblePositionManager.approve(address(0), tokenId);
599: SafeERC20.safeTransfer(IERC20(asset), isTransformMode ? msg.sender : owner, assets);
627: (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(
628: INonfungiblePositionManager.DecreaseLiquidityParams(
633: INonfungiblePositionManager.CollectParams memory collectParams = INonfungiblePositionManager.CollectParams(
640: (amount0, amount1) = nonfungiblePositionManager.collect(collectParams);
720: permit2.permitTransferFrom(
722: ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost),
728: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);
779: SafeERC20.safeTransfer(IERC20(asset), receiver, amount);
896: permit2.permitTransferFrom(
897: permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
901: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
946: SafeERC20.safeTransfer(IERC20(asset), receiver, assets);
981: permit2.permitTransferFrom(
982: permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
986: SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
1045: (,,,,,,, liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);
1049: (,,, liquidity,,, fees0, fees1) = oracle.getPositionBreakdown(tokenId);
1065: nonfungiblePositionManager.decreaseLiquidity(
1066: INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp)
1070: (amount0, amount1) = nonfungiblePositionManager.collect(
1071: INonfungiblePositionManager.CollectParams(tokenId, recipient, fees0, fees1)
1083: nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId);
1144: (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(tokenId);
1179: (uint256 borrowRateX96, uint256 supplyRateX96) = interestRateModel.getRatesPerSecondX96(available, debt);
1213: (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(tokenId);
1275: (fullValue, feeValue,,) = oracle.getValue(tokenId, address(asset));
```
[179](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L179) | [181](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L181) | [401](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L401) | [423](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L423) | [424](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L424) | [520](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L520) | [531](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L531) | [537](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L537) | [599](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L599) | [627](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L627) | [628](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L628) | [633](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L633) | [640](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L640) | [720](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L720) | [722](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L722) | [728](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L728) | [779](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L779) | [896](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L896) | [897](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L897) | [901](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L901) | [946](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L946) | [981](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L981) | [982](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L982) | [986](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L986) | [1045](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1045) | [1049](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1049) | [1065](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1065) | [1066](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1066) | [1070](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1070) | [1071](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1071) | [1083](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1083) | [1144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1144) | [1179](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1179) | [1213](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1213) | [1275](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1275)

```solidity
File: src/V3Oracle.sol

80: factory = _nonfungiblePositionManager.factory();
82: referenceTokenDecimals = IERC20Metadata(_referenceToken).decimals();
215: uint8 feedDecimals = feed.decimals();
216: uint8 tokenDecimals = IERC20Metadata(token).decimals();
225: address token0 = pool.token0();
226: address token1 = pool.token1();
337: (, int256 answer,, uint256 updatedAt,) = feedConfig.feed.latestRoundData();
363: (sqrtPriceX96,,,,,,) = pool.slot0();
368: (int56[] memory tickCumulatives,) = pool.observe(secondsAgos); // pool observe may fail when there is not enough history available (only use pool with enough history!)
370: sqrtPriceX96 = TickMath.getSqrtRatioAtTick(tick);
409: ) = nonfungiblePositionManager.positions(tokenId);
422: (state.sqrtPriceX96, state.tick,,,,,) = state.pool.slot0();
432: state.sqrtPriceX96Lower = TickMath.getSqrtRatioAtTick(state.tickLower);
433: state.sqrtPriceX96Upper = TickMath.getSqrtRatioAtTick(state.tickUpper);
434: (amount0, amount1) = LiquidityAmounts.getAmountsForLiquidity(
455: position.pool.feeGrowthGlobal0X128(),
456: position.pool.feeGrowthGlobal1X128()
480: (,, uint256 lowerFeeGrowthOutside0X128, uint256 lowerFeeGrowthOutside1X128,,,,) = pool.ticks(tickLower);
481: (,, uint256 upperFeeGrowthOutside0X128, uint256 upperFeeGrowthOutside1X128,,,,) = pool.ticks(tickUpper);
500: return IUniswapV3Pool(PoolAddress.computeAddress(factory, PoolAddress.getPoolKey(tokenA, tokenB, fee)));
```
[80](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L80) | [82](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L82) | [215](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L215) | [216](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L216) | [225](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L225) | [226](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L226) | [337](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L337) | [363](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L363) | [368](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L368) | [370](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L370) | [409](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L409) | [422](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L422) | [432](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L432) | [433](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L433) | [434](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L434) | [455](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L455) | [456](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L456) | [480](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L480) | [481](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L481) | [500](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L500)

```solidity
File: src/automators/AutoExit.sol

121: nonfungiblePositionManager.positions(params.tokenId);
132: (, state.tick,,,,,) = state.pool.slot0();
172: Swapper.RouterSwapParams(
198: state.owner = nonfungiblePositionManager.ownerOf(params.tokenId);
219: address owner = nonfungiblePositionManager.ownerOf(tokenId);
```
[121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L121) | [132](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L132) | [172](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L172) | [198](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L198) | [219](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L219)

```solidity
File: src/automators/Automator.sol

148: (sqrtPriceX96, currentTick,,,,,) = pool.slot0();
186: try pool.observe(secondsAgos) returns (int56[] memory tickCumulatives, uint160[] memory) {
202: (feeAmount0, feeAmount1) = nonfungiblePositionManager.decreaseLiquidity(
203: INonfungiblePositionManager.DecreaseLiquidityParams(
208: (amount0, amount1) = nonfungiblePositionManager.collect(
209: INonfungiblePositionManager.CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max)
220: weth.withdraw(amount);
226: SafeERC20.safeTransfer(token, to, amount);
240: owner = IVault(vault).ownerOf(tokenId);
242: owner = nonfungiblePositionManager.ownerOf(tokenId);
```
[148](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L148) | [186](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L186) | [202](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L202) | [203](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L203) | [208](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L208) | [209](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L209) | [220](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L220) | [226](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L226) | [240](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L240) | [242](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L242)

```solidity
File: src/transformers/AutoCompound.sol

91: IVault(vault).transform(
108: (state.amount0, state.amount1) = nonfungiblePositionManager.collect(
109: INonfungiblePositionManager.CollectParams(
116: nonfungiblePositionManager.positions(params.tokenId);
129: (state.sqrtPriceX96, state.tick,,,,,) = pool.slot0();
143: Swapper.PoolSwapParams(
163: (, state.compounded0, state.compounded1) = nonfungiblePositionManager.increaseLiquidity(
164: INonfungiblePositionManager.IncreaseLiquidityParams(
201: address owner = nonfungiblePositionManager.ownerOf(tokenId);
203: owner = IVault(owner).ownerOf(tokenId);
209: (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(tokenId);
272: SafeERC20.safeTransfer(IERC20(token), to, amount);
278: uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager));
280: SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max);
282: uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager));
284: SafeERC20.safeApprove(IERC20(token1), address(nonfungiblePositionManager), type(uint256).max);
```
[91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L91) | [108](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L108) | [109](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L109) | [116](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L116) | [129](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L129) | [143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L143) | [163](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L163) | [164](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L164) | [201](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L201) | [203](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L203) | [209](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L209) | [272](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L272) | [278](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L278) | [280](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L280) | [282](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L282) | [284](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L284)

```solidity
File: src/transformers/AutoRange.sol

101: IVault(vault).transform(
131: nonfungiblePositionManager.positions(params.tokenId);
182: Swapper.RouterSwapParams(
198: INonfungiblePositionManager.MintParams memory mintParams = INonfungiblePositionManager.MintParams(
202: SafeCast.toInt24(baseTick + config.lowerTickDelta), // reverts if out of valid range
203: SafeCast.toInt24(baseTick + config.upperTickDelta), // reverts if out of valid range
213: SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), state.maxAddAmount0);
214: SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), state.maxAddAmount1);
217: (state.newTokenId,, state.amountAdded0, state.amountAdded1) = nonfungiblePositionManager.mint(mintParams);
220: SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), 0);
221: SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), 0);
223: state.owner = nonfungiblePositionManager.ownerOf(params.tokenId);
228: state.realOwner = IVault(state.owner).ownerOf(params.tokenId);
232: nonfungiblePositionManager.safeTransferFrom(address(this), state.owner, state.newTokenId);
308: int24 spacing = IUniswapV3Factory(factory).feeAmountTickSpacing(fee);
```
[101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L101) | [131](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L131) | [182](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L182) | [198](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L198) | [202](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L202) | [203](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L203) | [213](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L213) | [214](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L214) | [217](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L217) | [220](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L220) | [221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L221) | [223](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L223) | [228](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L228) | [232](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L232) | [308](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L308)

```solidity
File: src/transformers/LeverageTransformer.sol

43: address token = IVault(msg.sender).asset();
45: IVault(msg.sender).borrow(params.tokenId, amount);
47: (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(params.tokenId);
54: Swapper.RouterSwapParams(
66: Swapper.RouterSwapParams(
77: SafeERC20.safeIncreaseAllowance(IERC20(token0), address(nonfungiblePositionManager), amount0);
78: SafeERC20.safeIncreaseAllowance(IERC20(token1), address(nonfungiblePositionManager), amount1);
81: .IncreaseLiquidityParams(
84: (, uint256 added0, uint256 added1) = nonfungiblePositionManager.increaseLiquidity(increaseLiquidityParams);
88: SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0 - added0);
91: SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1 - added1);
94: SafeERC20.safeTransfer(IERC20(token), params.recipient, amount);
124: address token = IVault(msg.sender).asset();
125: (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(params.tokenId);
131: .DecreaseLiquidityParams(
134: (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(decreaseLiquidityParams);
136: INonfungiblePositionManager.CollectParams memory collectParams = INonfungiblePositionManager.CollectParams(
142: (amount0, amount1) = nonfungiblePositionManager.collect(collectParams);
148: Swapper.RouterSwapParams(
157: Swapper.RouterSwapParams(
165: SafeERC20.safeApprove(IERC20(token), msg.sender, amount);
166: IVault(msg.sender).repay(params.tokenId, amount, false);
170: SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0);
173: SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1);
```
[43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L43) | [45](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L45) | [47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L47) | [54](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L54) | [66](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L66) | [77](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L77) | [78](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L78) | [81](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L81) | [84](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L84) | [88](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L88) | [91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L91) | [94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L94) | [124](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L124) | [125](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L125) | [131](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L131) | [134](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L134) | [136](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L136) | [142](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L142) | [148](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L148) | [157](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L157) | [165](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L165) | [166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L166) | [170](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L170) | [173](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L173)

```solidity
File: src/transformers/V3Utils.sol

102: if (nonfungiblePositionManager.ownerOf(tokenId) != msg.sender) {
106: nonfungiblePositionManager.permit(address(this), tokenId, instructions.deadline, v, r, s);
116: (,, address token0, address token1,,,, uint128 liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);
308: Swapper.RouterSwapParams(
325: Swapper.RouterSwapParams(
376: nonfungiblePositionManager.safeTransferFrom(address(this), from, tokenId, instructions.returnData);
414: Swapper.RouterSwapParams(
537: (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(params.tokenId);
578: SafeERC20.safeTransferFrom(token0, msg.sender, address(this), needed0);
581: SafeERC20.safeTransferFrom(token1, msg.sender, address(this), needed1);
584: SafeERC20.safeTransferFrom(otherToken, msg.sender, address(this), neededOther);
619: transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed0);
623: transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed1);
627: transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.neededOther);
631: permit2.permitTransferFrom(permit, transferDetails, msg.sender, signature);
711: INonfungiblePositionManager.MintParams memory mintParams = INonfungiblePositionManager.MintParams(
726: (tokenId, liquidity, added0, added1) = nonfungiblePositionManager.mint(mintParams);
727: nonfungiblePositionManager.safeTransferFrom(address(this), params.recipientNFT, tokenId, params.returnData);
767: .IncreaseLiquidityParams(
771: (liquidity, added0, added1) = nonfungiblePositionManager.increaseLiquidity(increaseLiquidityParams);
788: Swapper.RouterSwapParams(
799: Swapper.RouterSwapParams(
807: Swapper.RouterSwapParams(
812: Swapper.RouterSwapParams(
831: SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), 0);
832: SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), total0);
835: SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), 0);
836: SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), total1);
866: weth.withdraw(amount);
872: SafeERC20.safeTransfer(token, to, amount);
885: (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(
886: INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, token0Min, token1Min, deadline)
898: (amount0, amount1) = nonfungiblePositionManager.collect(
899: INonfungiblePositionManager.CollectParams(tokenId, address(this), collectAmount0, collectAmount1)
```
[102](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L102) | [106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L106) | [116](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L116) | [308](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L308) | [325](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L325) | [376](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L376) | [414](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L414) | [537](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L537) | [578](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L578) | [581](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L581) | [584](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L584) | [619](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L619) | [623](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L623) | [627](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L627) | [631](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L631) | [711](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L711) | [726](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L726) | [727](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L727) | [767](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L767) | [771](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L771) | [788](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L788) | [799](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L799) | [807](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L807) | [812](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L812) | [831](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L831) | [832](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L832) | [835](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L835) | [836](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L836) | [866](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L866) | [872](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L872) | [885](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L885) | [886](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L886) | [898](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L898) | [899](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L899)

```solidity
File: src/utils/FlashloanLiquidator.sol

42: (,,, uint256 liquidationCost,) = params.vault.loanInfo(params.tokenId);
47: (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(params.tokenId);
48: address asset = params.vault.asset();
50: bool isAsset0 = params.flashLoanPool.token0() == asset;
64: params.flashLoanPool.flash(address(this), isAsset0 ? liquidationCost : 0, !isAsset0 ? liquidationCost : 0, data);
72: SafeERC20.safeApprove(data.asset, address(data.vault), data.liquidationCost);
73: data.vault.liquidate(
74: IVault.LiquidateParams(
78: SafeERC20.safeApprove(data.asset, address(data.vault), 0);
85: SafeERC20.safeTransfer(data.asset, msg.sender, data.liquidationCost + (fee0 + fee1));
91: SafeERC20.safeTransfer(data.swap0.tokenIn, data.liquidator, balance);
97: SafeERC20.safeTransfer(data.swap1.tokenIn, data.liquidator, balance);
106: SafeERC20.safeTransfer(data.asset, data.liquidator, balance);
```
[42](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L42) | [47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L47) | [48](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L48) | [50](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L50) | [64](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L64) | [72](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L72) | [73](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L73) | [74](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L74) | [78](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L78) | [85](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L85) | [91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L91) | [97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L97) | [106](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L106)

```solidity
File: src/utils/Swapper.sol

42: weth = IWETH9(_nonfungiblePositionManager.WETH9());
43: factory = _nonfungiblePositionManager.factory();
87: SafeERC20.safeApprove(params.tokenIn, data.allowanceTarget, params.amountIn);
94: SafeERC20.safeApprove(params.tokenIn, data.allowanceTarget, 0);
98: SafeERC20.safeTransfer(params.tokenIn, universalRouter, params.amountIn);
99: IUniversalRouter(universalRouter).execute(data.commands, data.inputs, data.deadline);
134: (int256 amount0Delta, int256 amount1Delta) = params.pool.swap(
167: SafeERC20.safeTransfer(IERC20(tokenIn), msg.sender, amountToPay);
172: return IUniswapV3Pool(PoolAddress.computeAddress(address(factory), PoolAddress.getPoolKey(tokenA, tokenB, fee)));
```
[42](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L42) | [43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L43) | [87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L87) | [94](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L94) | [98](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L98) | [99](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L99) | [134](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L134) | [167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L167) | [172](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L172)
</details>

### [G-59] Mark Functions That Revert For Normal Users As `payable`

Functions guaranteed to revert when called by normal users can be marked `payable`.
If a function modifier such as onlyOwner is used, the function will revert if a normal user tries to pay the function.
Marking the function as payable will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided.

The extra opcodes avoided are CALLVALUE(2),DUP1(3),ISZERO(3),PUSH2(3),JUMPI(10),PUSH1(3),DUP1(3),REVERT(0),JUMPDEST(1),POP(2), which costs an average of about 21 gas per call to the function, in addition to the extra deployment cost.

<details>
<summary><i>15 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

765: function withdrawReserves(uint256 amount, address receiver) external onlyOwner {
788: function setTransformer(address transformer, bool active) external onlyOwner {
837: function setReserveFactor(uint32 _reserveFactorX32) external onlyOwner {
844: function setReserveProtectionFactor(uint32 _reserveProtectionFactorX32) external onlyOwner {
856: function setTokenConfig(address token, uint32 collateralFactorX32, uint32 collateralValueLimitFactorX32)
        external
        onlyOwner
    {
870: function setEmergencyAdmin(address admin) external onlyOwner {
```
[765](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L765) | [788](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L788) | [837](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L837) | [844](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L844) | [856](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L856) | [870](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L870)

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
265: function setEmergencyAdmin(address admin) external onlyOwner {
```
[185](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L185) | [201](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L201) | [265](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L265)

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

### [G-60] Prefer `private` over `public` for Constants to Save Gas

Using `private` instead of `public` for constants can save gas.

The compiler doesn't need to create non-payable getter functions for deployment calldata, store the bytes of the value outside of where it's used, or add another entry to the method ID table, saving 3406-3606 gas in deployment.

If needed, the values can be read from the verified contract source code, or a single getter function that returns a tuple of the values of all currently public constants can be implemented.

<details>
<summary><i>13 issue instances in 5 files:</i></summary>

```solidity
File: src/V3Vault.sol

36: uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%
38: uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
39: uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%
41: uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%
43: uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%
44: uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%
```
[36](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L36) | [38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L38) | [39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L39) | [41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L41) | [43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L43) | [44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L44)

```solidity
File: src/V3Oracle.sol

25: uint16 public constant MIN_PRICE_DIFFERENCE = 200; //2%
```
[25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L25)

```solidity
File: src/InterestRateModel.sol

13: uint256 public constant YEAR_SECS = 31557600; // taking into account leap years
15: uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10; // 10%
16: uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%
```
[13](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L13) | [15](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L15) | [16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L16)

```solidity
File: src/automators/Automator.sol

23: uint32 public constant MIN_TWAP_SECONDS = 60; // 1 minute
24: uint32 public constant MAX_TWAP_TICK_DIFFERENCE = 200; // 2%
```
[23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L23) | [24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L24)

```solidity
File: src/transformers/AutoCompound.sol

47: uint64 public constant MAX_REWARD_X64 = uint64(Q64 / 50); // 2%
```
[47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L47)
</details>

### [G-61] `<x> += <y>` costs more gas than `<x> = <x> + <y>` for state variables

Using the addition operator instead of plus-equals saves gas.
Replace `<x> += <y>` or `<x> -= <y>` with `<x> = <x> + <y>` or `<x> = <x> - <y>`.

<details>
<summary><i>7 issue instances in 1 files:</i></summary>

```solidity
File: src/V3Vault.sol

569: debtSharesTotal += shares;
577: dailyDebtIncreaseLimitLeft -= assets;
731: debtSharesTotal -= debtShares;
913: dailyLendIncreaseLimitLeft -= assets;
949: dailyLendIncreaseLimitLeft += assets;
992: debtSharesTotal -= shares;
995: dailyDebtIncreaseLimitLeft += assets;
```
[569](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L569) | [577](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L577) | [731](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L731) | [913](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L913) | [949](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L949) | [992](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L992) | [995](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L995)
</details>

### [G-62] Using `bool`s for storage incurs overhead

Utilizing booleans for storage is less gas-efficient compared to using types that consume a full word like uint256.
Every write operation on a boolean necessitates an extra SLOAD operation to read the slot's current value, modify the boolean bits, and then write back.
This additional step is the compiler's measure against contract upgrades and pointer aliasing.

To enhance gas efficiency, consider using `uint256(0)` for false and `uint256(1)` for true, bypassing the extra Gwarmaccess (100 gas) incurred by the SLOAD.

<details>
<summary><i>4 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

163: mapping(address => bool) public transformerAllowList; // contracts allowed to transform positions (selected audited contracts e.g. V3Utils)
164: mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; // owners permissions for other addresses to call transform on owners behalf (e.g. AutoRange contract)
```
[163](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L163) | [164](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L164)

```solidity
File: src/automators/Automator.sol

34: mapping(address => bool) public operators;
35: mapping(address => bool) public vaults;
```
[34](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L34) | [35](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L35)
</details>

### [G-63] Optimize Gas by Using Only Named Returns

The Solidity compiler can generate more efficient bytecode when using named returns.
It's recommended to replace anonymous returns with named returns for potential gas savings.

Example:
```solidity
/// 985 gas cost
function add(uint256 x, uint256 y) public pure returns (uint256) {
    return x + y;
}
/// 941 gas cost
function addNamed(uint256 x, uint256 y) public pure returns (uint256 res) {
    res = x + y;
}
```

<details>
<summary><i>31 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

264: function loanCount(address owner) external view override returns (uint256) {
271: function loanAtIndex(address owner, uint256 index) external view override returns (uint256) {
277: function decimals() public view override(IERC20Metadata, ERC20) returns (uint8) {
284: function totalAssets() public view override returns (uint256) {
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
429: function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
        external
        override
        returns (bytes4)
    {
1142: function _calculateTokenCollateralFactorX32(uint256 tokenId) internal view returns (uint32) {
1280: function _convertToShares(uint256 amount, uint256 exchangeRateX96, Math.Rounding rounding)
        internal
        pure
        returns (uint256)
    {
1288: function _convertToAssets(uint256 shares, uint256 exchangeRateX96, Math.Rounding rounding)
        internal
        pure
        returns (uint256)
    {
```
[264](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L264) | [271](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L271) | [277](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L277) | [284](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L284) | [301](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L301) | [312](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L312) | [323](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L323) | [329](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L329) | [334](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L334) | [340](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L340) | [346](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L346) | [352](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L352) | [360](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L360) | [366](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L366) | [372](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L372) | [378](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L378) | [384](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L384) | [390](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L390) | [429](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L429) | [1142](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1142) | [1280](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1280) | [1288](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1288)

```solidity
File: src/V3Oracle.sol

329: function _getChainlinkPriceX96(address token) internal view returns (uint256) {
359: function _getReferencePoolPriceX96(IUniswapV3Pool pool, uint32 twapSeconds) internal view returns (uint256) {
499: function _getPool(address tokenA, address tokenB, uint24 fee) internal view returns (IUniswapV3Pool) {
```
[329](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L329) | [359](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L359) | [499](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L499)

```solidity
File: src/InterestRateModel.sol

46: function getUtilizationRateX96(uint256 cash, uint256 debt) public pure returns (uint256) {
```
[46](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L46)

```solidity
File: src/automators/Automator.sol

166: function _hasMaxTWAPTickDifference(IUniswapV3Pool pool, uint32 twapPeriod, int24 currentTick, uint16 maxDifference)
        internal
        view
        returns (bool)
    {
180: function _getTWAPTick(IUniswapV3Pool pool, uint32 twapPeriod) internal view returns (int24, bool) {
```
[166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L166) | [180](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L180)

```solidity
File: src/transformers/AutoRange.sol

300: function _getTickSpacing(uint24 fee) internal view returns (int24) {
```
[300](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L300)

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

171: function _getPool(address tokenA, address tokenB, uint24 fee) internal view returns (IUniswapV3Pool) {
```
[171](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L171)
</details>

### [G-64] Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead

Usage of uints/ints smaller than 32 bytes (256 bits) incurs overhead. The Ethereum Virtual Machine (EVM) operates on 32 bytes at a time. Therefore, if an element is smaller than 32 bytes, the EVM must use more operations to reduce the size of the element from 32 bytes to the desired size. 

Operations involving smaller size uints/ints cost extra gas due to the compiler having to clear the higher bits of the memory word before operating on the small size integer. This also includes the associated stack operations of doing so. 

It's recommended to use larger sizes and downcast where needed to optimize for gas efficiency.

<details>
<summary><i>86 issue instances in 9 files:</i></summary>

```solidity
File: src/V3Vault.sol

36: uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%
38: uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
39: uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%
41: uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%
43: uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%
44: uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%
65: uint8 private immutable assetDecimals;
102: event SetReserveFactor(uint32 reserveFactorX32);
103: event SetReserveProtectionFactor(uint32 reserveProtectionFactorX32);
104: event SetTokenConfig(address token, uint32 collateralFactorX32, uint32 collateralValueLimitFactorX32);
118: uint32 public reserveFactorX32 = 0;
121: uint32 public reserveProtectionFactorX32 = MIN_RESERVE_PROTECTION_FACTOR_X32;
277: function decimals() public view override(IERC20Metadata, ERC20) returns (uint8) {
636: params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
            params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)
        );
837: function setReserveFactor(uint32 _reserveFactorX32) external onlyOwner {
844: function setReserveProtectionFactor(uint32 _reserveProtectionFactorX32) external onlyOwner {
856: function setTokenConfig(address token, uint32 collateralFactorX32, uint32 collateralValueLimitFactorX32)
        external
        onlyOwner
    {
1039: uint128 liquidity;
1040: uint128 fees0;
1041: uint128 fees1;
1046: fees0 = type(uint128).max;
1047: fees1 = type(uint128).max;
1054: fees0 = uint128(liquidationValue * fees0 / feeValue);
1055: fees1 = uint128(liquidationValue * fees1 / feeValue);
1058: fees0 = type(uint128).max;
1059: fees1 = type(uint128).max;
1060: liquidity = uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue));
1145: uint32 factor0X32 = tokenConfigs[token0].collateralFactorX32;
1146: uint32 factor1X32 = tokenConfigs[token1].collateralFactorX32;
1228: collateralValueLimitFactorX32 < type(uint32).max
                        && _convertToAssets(tokenConfigs[token0].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
                            > lentAssets * collateralValueLimitFactorX32 / Q32
                ) {
1236: collateralValueLimitFactorX32 < type(uint32).max
                        && _convertToAssets(tokenConfigs[token1].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
                            > lentAssets * collateralValueLimitFactorX32 / Q32
                ) {
```
[36](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L36) | [38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L38) | [39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L39) | [41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L41) | [43](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L43) | [44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L44) | [65](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L65) | [102](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L102) | [103](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L103) | [104](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L104) | [118](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L118) | [121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L121) | [277](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L277) | [636](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L636) | [837](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L837) | [844](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L844) | [856](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L856) | [1039](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1039) | [1040](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1040) | [1041](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1041) | [1046](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1046) | [1047](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1047) | [1054](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1054) | [1055](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1055) | [1058](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1058) | [1059](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1059) | [1060](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1060) | [1145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1145) | [1146](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1146) | [1228](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1228) | [1236](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1236)

```solidity
File: src/V3Oracle.sol

25: uint16 public constant MIN_PRICE_DIFFERENCE = 200; //2%
32: event SetMaxPoolPriceDifference(uint16 maxPoolPriceDifference);
63: uint8 public immutable referenceTokenDecimals;
65: uint16 public maxPoolPriceDifference = MIN_PRICE_DIFFERENCE; // max price difference between oracle derived price and pool price x10000
101: (address token0, address token1, uint24 fee,, uint256 amount0, uint256 amount1, uint256 fees0, uint256 fees1) =
            getPositionBreakdown(tokenId);
133: function _checkPoolPrice(address token0, address token1, uint24 fee, uint256 derivedPoolPriceX96) internal view {
185: function setMaxPoolPriceDifference(uint16 _maxPoolPriceDifference) external onlyOwner {
204: uint32 maxFeedAge,
        IUniswapV3Pool pool,
        uint32 twapSeconds,
        Mode mode,
        uint16 maxDifference
    ) external onlyOwner {
215: uint8 feedDecimals = feed.decimals();
216: uint8 tokenDecimals = IERC20Metadata(token).decimals();
359: function _getReferencePoolPriceX96(IUniswapV3Pool pool, uint32 twapSeconds) internal view returns (uint256) {
365: uint32[] memory secondsAgos = new uint32[](2);
368: (int56[] memory tickCumulatives,) = pool.observe(secondsAgos); // pool observe may fail when there is not enough history available (only use pool with enough history!)
369: int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)));
401: uint24 fee,
            int24 tickLower,
            int24 tickUpper,
            uint128 liquidity,
            uint256 feeGrowthInside0LastX128,
            uint256 feeGrowthInside1LastX128,
            uint128 tokensOwed0,
            uint128 tokensOwed1
        ) = nonfungiblePositionManager.positions(tokenId);
445: function _getUncollectedFees(PositionState memory position, int24 tick)
        internal
        view
        returns (uint128 fees0, uint128 fees1)
    {
467: fees0 = uint128(FullMath.mulDiv(feeGrowth0, position.liquidity, Q128));
468: fees1 = uint128(FullMath.mulDiv(feeGrowth1, position.liquidity, Q128));
474: int24 tickLower,
        int24 tickUpper,
        int24 tickCurrent,
        uint256 feeGrowthGlobal0X128,
        uint256 feeGrowthGlobal1X128
    ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {
499: function _getPool(address tokenA, address tokenB, uint24 fee) internal view returns (IUniswapV3Pool) {
```
[25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L25) | [32](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L32) | [63](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L63) | [65](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L65) | [101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L101) | [133](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L133) | [185](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L185) | [204](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L204) | [215](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L215) | [216](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L216) | [359](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L359) | [365](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L365) | [368](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L368) | [369](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L369) | [401](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L401) | [445](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L445) | [467](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L467) | [468](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L468) | [474](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L474) | [499](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L499)

```solidity
File: src/automators/AutoExit.sol

37: uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
```
[37](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L37)

```solidity
File: src/automators/Automator.sol

23: uint32 public constant MIN_TWAP_SECONDS = 60; // 1 minute
24: uint32 public constant MAX_TWAP_TICK_DIFFERENCE = 200; // 2%
31: event TWAPConfigChanged(uint32 TWAPSeconds, uint16 maxTWAPTickDifference);
38: uint32 public TWAPSeconds;
39: uint16 public maxTWAPTickDifference;
45: uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Swapper(npm, _zeroxRouter, _universalRouter) {
87: function setTWAPConfig(uint16 _maxTWAPTickDifference, uint32 _TWAPSeconds) public onlyOwner {
166: function _hasMaxTWAPTickDifference(IUniswapV3Pool pool, uint32 twapPeriod, int24 currentTick, uint16 maxDifference)
        internal
        view
        returns (bool)
    {
171: (int24 twapTick, bool twapOk) = _getTWAPTick(pool, twapPeriod);
173: return twapTick - currentTick >= -int16(maxDifference) && twapTick - currentTick <= int16(maxDifference);
180: function _getTWAPTick(IUniswapV3Pool pool, uint32 twapPeriod) internal view returns (int24, bool) {
181: uint32[] memory secondsAgos = new uint32[](2);
186: try pool.observe(secondsAgos) returns (int56[] memory tickCumulatives, uint160[] memory) {
187: return (int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapPeriod))), true);
209: INonfungiblePositionManager.CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max)
        );
```
[23](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L23) | [24](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L24) | [31](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L31) | [38](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L38) | [39](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L39) | [45](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L45) | [87](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L87) | [166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L166) | [171](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L171) | [173](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L173) | [180](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L180) | [181](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L181) | [186](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L186) | [187](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L187) | [209](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L209)

```solidity
File: src/transformers/AutoCompound.sol

30: event RewardUpdated(address account, uint64 totalRewardX64);
41: uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, address(0), address(0)) {}
47: uint64 public constant MAX_REWARD_X64 = uint64(Q64 / 50); // 2%
48: uint64 public totalRewardX64 = MAX_REWARD_X64; // 2%
110: params.tokenId, address(this), type(uint128).max, type(uint128).max
            )
        );
132: uint32 tSecs = TWAPSeconds;
243: function setReward(uint64 _totalRewardX64) external onlyOwner {
```
[30](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L30) | [41](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L41) | [47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L47) | [48](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L48) | [110](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L110) | [132](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L132) | [243](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L243)

```solidity
File: src/transformers/AutoRange.sol

29: uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
170: int24 tickSpacing = _getTickSpacing(state.fee);
171: int24 baseTick = state.currentTick - (((state.currentTick % tickSpacing) + tickSpacing) % tickSpacing);
300: function _getTickSpacing(uint24 fee) internal view returns (int24) {
308: int24 spacing = IUniswapV3Factory(factory).feeAmountTickSpacing(fee);
```
[29](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L29) | [170](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L170) | [171](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L171) | [300](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L300) | [308](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L308)

```solidity
File: src/transformers/LeverageTransformer.sol

139: params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
            params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)
        );
```
[139](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L139)

```solidity
File: src/transformers/V3Utils.sol

116: (,, address token0, address token1,,,, uint128 liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);
133: instructions.feeAmount0 == type(uint128).max
                ? type(uint128).max
                : (amount0 + instructions.feeAmount0).toUint128(),
            instructions.feeAmount1 == type(uint128).max
                ? type(uint128).max
                : (amount1 + instructions.feeAmount1).toUint128()
        );
535: returns (uint128 liquidity, uint256 amount0, uint256 amount1)
    {
737: returns (uint128 liquidity, uint256 added0, uint256 added1)
    {
```
[116](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L116) | [133](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L133) | [535](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L535) | [737](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L737)

```solidity
File: src/utils/Swapper.sol

160: (address tokenIn, address tokenOut, uint24 fee) = abi.decode(data, (address, address, uint24));
171: function _getPool(address tokenA, address tokenB, uint24 fee) internal view returns (IUniswapV3Pool) {
```
[160](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L160) | [171](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L171)
</details>

### [G-65] Unlimited gas consumption risk due to external call recipients

When calling an external function without specifying a gas limit , the called contract may consume all the remaining gas, causing the tx to be reverted.
To mitigate this, it is recommended to explicitly set a gas limit when making low level external calls.

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

### [G-66] Use assembly to check for `address(0)`

The usage of inline assembly to check if variable is the zero can save gas compared to traditional `require` or `if` statement checks. 

The assembly check uses the `extcodesize` operation which is generally cheaper in terms of gas.

[More information can be found here.](https://medium.com/@kalexotsu/solidity-assembly-checking-if-an-address-is-0-efficiently-d2bfe071331)

<details>
<summary><i>6 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

790: if (
            transformer == address(0) || transformer == address(this) || transformer == asset
                || transformer == address(nonfungiblePositionManager)
        ) {
            revert InvalidConfig();
```
[790](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L790)

```solidity
File: src/automators/Automator.sol

236: if (vault != address(0)) {
            if (!vaults[vault]) {
                revert Unauthorized();
```
[236](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L236)

```solidity
File: src/transformers/V3Utils.sol

342: if (targetAmount != 0 && instructions.targetToken != address(0)) {
                _transferToken(
                    instructions.recipient, IERC20(instructions.targetToken), targetAmount, instructions.unwrap
                );
696: if (
            amountOther > amountAddedOther && address(otherToken) != address(0) && token0 != otherToken
                && token1 != otherToken
        ) {
805: } else if (address(params.swapSourceToken) != address(0)) {
            (uint256 amountInDelta0, uint256 amountOutDelta0) = _routerSwap(
                Swapper.RouterSwapParams(
                    params.swapSourceToken, params.token0, params.amountIn0, params.amountOut0Min, params.swapData0
                )
            );
```
[342](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L342) | [696](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L696) | [805](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L805)

```solidity
File: src/utils/Swapper.sol

77: if (params.amountIn != 0 && params.swapData.length != 0 && address(params.tokenOut) != address(0)) {
            uint256 balanceInBefore = params.tokenIn.balanceOf(address(this));
```
[77](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L77)
</details>

### [G-67] `internal`/`private` functions only called once can be inlined to save gas

`internal` functions that are only called once should be inlined to save gas. 
Not inlining such functions costs an extra 20 to 40 gas due to the additional `JUMP` instructions and stack operations required for function calls.

<details>
<summary><i>18 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit function `_sendPositionValue()` called only once
1032: function _sendPositionValue(
        uint256 tokenId,
        uint256 liquidationValue,
        uint256 fullValue,
        uint256 feeValue,
        address recipient
    ) internal returns (uint256 amount0, uint256 amount1) {
/// @audit function `_handleReserveLiquidation()` called only once
1123: function _handleReserveLiquidation(
        uint256 reserveCost,
        uint256 newDebtExchangeRateX96,
        uint256 newLendExchangeRateX96
    ) internal returns (uint256 missing) {
/// @audit function `_calculateTokenCollateralFactorX32()` called only once
1143: function _calculateTokenCollateralFactorX32(uint256 tokenId) internal view returns (uint32) {
/// @audit function `_removeTokenFromOwner()` called only once
1303: function _removeTokenFromOwner(address from, uint256 tokenId) internal {
```
[1032](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1032) | [1123](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1123) | [1143](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1143) | [1303](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1303)

```solidity
File: src/V3Oracle.sol

/// @audit function `_checkPoolPrice()` called only once
133: function _checkPoolPrice(address token0, address token1, uint24 fee, uint256 derivedPoolPriceX96) internal view {
/// @audit function `_getTWAPPriceX96()` called only once
346: function _getTWAPPriceX96(TokenConfig memory feedConfig) internal view returns (uint256 poolTWAPPriceX96) {
/// @audit function `_initializeState()` called only once
395: function _initializeState(uint256 tokenId) internal view returns (PositionState memory state) {
/// @audit function `_getAmounts()` called only once
426: function _getAmounts(PositionState memory state)
        internal
        view
        returns (uint256 amount0, uint256 amount1, uint128 fees0, uint128 fees1)
    {
/// @audit function `_getUncollectedFees()` called only once
445: function _getUncollectedFees(PositionState memory position, int24 tick)
        internal
        view
        returns (uint128 fees0, uint128 fees1)
    {
/// @audit function `_getFeeGrowthInside()` called only once
472: function _getFeeGrowthInside(
        IUniswapV3Pool pool,
        int24 tickLower,
        int24 tickUpper,
        int24 tickCurrent,
        uint256 feeGrowthGlobal0X128,
        uint256 feeGrowthGlobal1X128
    ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {
```
[133](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L133) | [346](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L346) | [395](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L395) | [426](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L426) | [445](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L445) | [472](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L472)

```solidity
File: src/automators/Automator.sol

/// @audit function `_hasMaxTWAPTickDifference()` called only once
166: function _hasMaxTWAPTickDifference(IUniswapV3Pool pool, uint32 twapPeriod, int24 currentTick, uint16 maxDifference)
        internal
        view
        returns (bool)
    {
/// @audit function `_getTWAPTick()` called only once
180: function _getTWAPTick(IUniswapV3Pool pool, uint32 twapPeriod) internal view returns (int24, bool) {
/// @audit function `_transferToken()` called only once
218: function _transferToken(address to, IERC20 token, uint256 amount, bool unwrap) internal {
```
[166](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L166) | [180](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L180) | [218](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L218)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit function `_checkApprovals()` called only once
276: function _checkApprovals(address token0, address token1) internal {
```
[276](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L276)

```solidity
File: src/transformers/AutoRange.sol

/// @audit function `_getTickSpacing()` called only once
300: function _getTickSpacing(uint24 fee) internal view returns (int24) {
```
[300](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L300)

```solidity
File: src/transformers/V3Utils.sol

/// @audit function `_decreaseLiquidity()` called only once
877: function _decreaseLiquidity(
        uint256 tokenId,
        uint128 liquidity,
        uint256 deadline,
        uint256 token0Min,
        uint256 token1Min
    ) internal returns (uint256 amount0, uint256 amount1) {
/// @audit function `_collectFees()` called only once
892: function _collectFees(uint256 tokenId, IERC20 token0, IERC20 token1, uint128 collectAmount0, uint128 collectAmount1)
        internal
        returns (uint256 amount0, uint256 amount1)
    {
```
[877](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L877) | [892](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L892)

```solidity
File: src/utils/Swapper.sol

/// @audit function `_getPool()` called only once
171: function _getPool(address tokenA, address tokenB, uint24 fee) internal view returns (IUniswapV3Pool) {
```
[171](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L171)
</details>

### [G-68] Consider using OZ EnumerateSet in place of nested mappings

Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).

A possible optimization involves manually concatenating the keys followed by a single hash operation and an sstore. However, this technique introduces the risk of storage collision, especially when there are other nested hash maps in the contract that use the same key types. Because Solidity is unaware of the number and structure of nested hash maps in a contract, it follows a conservative approach in computing the storage slot to avoid possible collisions.

OpenZeppelin's EnumerableSet provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

164: mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; // owners permissions for other addresses to call transform on owners behalf (e.g. AutoRange contract)
```
[164](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L164)

```solidity
File: src/transformers/AutoCompound.sol

44: mapping(uint256 => mapping(address => uint256)) public positionBalances;
```
[44](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L44)
</details>

### [G-69] Declare `immutable` as `private` to save gas

Using `private` instead of `public` for immutables saves gas.

The compiler doesn't need to create non-payable getter functions for deployment calldata, store the bytes of the value outside of where it's used, or add another entry to the method ID table, saving 3406-3606 gas in deployment.

<details>
<summary><i>17 issue instances in 4 files:</i></summary>

```solidity
File: src/V3Vault.sol

47: INonfungiblePositionManager public immutable nonfungiblePositionManager;
50: IUniswapV3Factory public immutable factory;
53: IInterestRateModel public immutable interestRateModel;
56: IV3Oracle public immutable oracle;
59: IPermit2 public immutable permit2;
62: address public immutable override asset;
```
[47](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L47) | [50](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L50) | [53](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L53) | [56](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L56) | [59](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L59) | [62](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L62)

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

### [G-70] State variables should be cached in stack rather than re-reading them from storage

Caching state variables in local variables can optimize gas usage, as accessing the stack is cheaper than accessing storage.

The instances below point to the second+ access of a state variable within a function.

<details>
<summary><i>17 issue instances in 2 files:</i></summary>

```solidity
File: src/V3Vault.sol

/// @audit function maxDeposit() uses state variable `globalLendLimit` 2 times
304: if (value >= globalLendLimit) {
307: return globalLendLimit - value;
/// @audit function maxMint() uses state variable `globalLendLimit` 2 times
304: if (value >= globalLendLimit) {
318: return _convertToShares(globalLendLimit - value, lendExchangeRateX96, Math.Rounding.Down);
/// @audit function transform() uses state variable `transformedTokenId` 2 times
505: if (transformedTokenId > 0) {
528: tokenId = transformedTokenId;
/// @audit function _resetDailyLendIncreaseLimit() uses state variable `dailyLendIncreaseLimitMin` 2 times
1253: dailyLendIncreaseLimitMin > lendIncreaseLimit ? dailyLendIncreaseLimitMin : lendIncreaseLimit;
1253: dailyLendIncreaseLimitMin > lendIncreaseLimit ? dailyLendIncreaseLimitMin : lendIncreaseLimit;
/// @audit function _resetDailyDebtIncreaseLimit() uses state variable `dailyDebtIncreaseLimitMin` 2 times
1265: dailyDebtIncreaseLimitMin > debtIncreaseLimit ? dailyDebtIncreaseLimitMin : debtIncreaseLimit;
1265: dailyDebtIncreaseLimitMin > debtIncreaseLimit ? dailyDebtIncreaseLimitMin : debtIncreaseLimit;
```
[304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L304) | [307](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L307) | [304](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L304) | [318](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L318) | [505](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L505) | [528](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L528) | [1253](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1253) | [1253](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1253) | [1265](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1265) | [1265](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1265)

```solidity
File: src/InterestRateModel.sol

/// @audit function getRatesPerSecondX96() uses state variable `multiplierPerSecondX96` 2 times
67: borrowRateX96 = (utilizationRateX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
69: uint256 normalRateX96 = (kinkX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
/// @audit function getRatesPerSecondX96() uses state variable `baseRatePerSecondX96` 2 times
67: borrowRateX96 = (utilizationRateX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
69: uint256 normalRateX96 = (kinkX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
/// @audit function getRatesPerSecondX96() uses state variable `kinkX96` 3 times
66: if (utilizationRateX96 <= kinkX96) {
69: uint256 normalRateX96 = (kinkX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;
70: uint256 excessUtilX96 = utilizationRateX96 - kinkX96;
```
[67](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L67) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L69) | [67](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L67) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L69) | [66](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L66) | [69](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L69) | [70](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L70)
</details>

### [G-71] Optimize names to save gas

Function names for public and external methods, as well as public state variable names, can be optimized to achieve gas savings.
By renaming functions to generate method IDs with two leading zero bytes, you can save 128 gas during contract deployment.
Further, renaming functions for lower method IDs can conserve 22 gas per call for each sorted position shifted.

Optimizing function names for gas efficiency can result in significant savings, especially for frequently called functions or heavily deployed contracts. 
Reference: [Solidity Gas Optimizations - Function Name](https://blog.emn178.cc/en/post/solidity-gas-optimization-function-name/)

<details>
<summary><i>11 issue instances in 11 files:</i></summary>

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
File: src/automators/Automator.sol

18: abstract contract Automator is Swapper, Ownable {
```
[18](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L18)

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

```solidity
File: src/utils/Swapper.sol

17: abstract contract Swapper is IUniswapV3SwapCallback, IErrors {
```
[17](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L17)
</details>

### [G-72] Avoid updating storage when the value hasn't changed

A check regarding whether the current value and the new value are the same should be added.
This helps prevent unnecessary state changes and events in case the new value is the same as the current value.

<details>
<summary><i>22 issue instances in 5 files:</i></summary>

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
```
[796](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L796) | [817](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L817) | [819](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L819) | [820](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L820) | [821](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L821) | [822](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L822) | [838](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L838) | [848](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L848) | [871](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L871)

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

### [G-73] Optimize External Calls with Assembly for Memory Efficiency

Using interfaces to make external contract calls in Solidity is convenient but can be inefficient in terms of memory utilization.
Each such call involves creating a new memory location to store the data being passed, thus incurring memory expansion costs. 

Inline assembly allows for optimized memory usage by re-using already allocated memory spaces or using the scratch space for smaller datasets.
This can result in notable gas savings, especially for contracts that make frequent external calls.

Additionally, using inline assembly enables important safety checks like verifying if the target address has code deployed to it using `extcodesize(addr)` before making the call, mitigating risks associated with contract interactions.

<details>
<summary><i>31 issue instances in 7 files:</i></summary>

```solidity
File: src/V3Vault.sol

285: return IERC20(asset).balanceOf(address(this));
401: nonfungiblePositionManager.safeTransferFrom(msg.sender, address(this), tokenId, abi.encode(recipient));
423: nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);
424: nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));
520: nonfungiblePositionManager.approve(transformer, tokenId);
531: address owner = nonfungiblePositionManager.ownerOf(tokenId);
537: nonfungiblePositionManager.approve(address(0), tokenId);
627: (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(
            INonfungiblePositionManager.DecreaseLiquidityParams(
                params.tokenId, params.liquidity, params.amount0Min, params.amount1Min, params.deadline
            )
        );
640: (amount0, amount1) = nonfungiblePositionManager.collect(collectParams);
720: permit2.permitTransferFrom(
                permit,
                ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost),
                msg.sender,
                signature
            );
896: permit2.permitTransferFrom(
                permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
            );
981: permit2.permitTransferFrom(
                    permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
                );
1045: (,,,,,,, liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);
1049: (,,, liquidity,,, fees0, fees1) = oracle.getPositionBreakdown(tokenId);
1065: nonfungiblePositionManager.decreaseLiquidity(
                INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp)
            );
1070: (amount0, amount1) = nonfungiblePositionManager.collect(
            INonfungiblePositionManager.CollectParams(tokenId, recipient, fees0, fees1)
        );
1083: nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId);
1144: (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(tokenId);
1179: (uint256 borrowRateX96, uint256 supplyRateX96) = interestRateModel.getRatesPerSecondX96(available, debt);
1213: (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(tokenId);
1275: (fullValue, feeValue,,) = oracle.getValue(tokenId, address(asset));
```
[285](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L285) | [401](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L401) | [423](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L423) | [424](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L424) | [520](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L520) | [531](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L531) | [537](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L537) | [627](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L627) | [640](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L640) | [720](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L720) | [896](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L896) | [981](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L981) | [1045](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1045) | [1049](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1049) | [1065](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1065) | [1070](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1070) | [1083](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1083) | [1144](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1144) | [1179](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1179) | [1213](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1213) | [1275](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1275)

```solidity
File: src/V3Oracle.sol

409: ) = nonfungiblePositionManager.positions(tokenId);
```
[409](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L409)

```solidity
File: src/automators/Automator.sol

240: owner = IVault(vault).ownerOf(tokenId);
```
[240](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L240)

```solidity
File: src/transformers/AutoCompound.sol

91: IVault(vault).transform(
            params.tokenId, address(this), abi.encodeWithSelector(AutoCompound.execute.selector, params)
        );
203: owner = IVault(owner).ownerOf(tokenId);
278: uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager));
282: uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager));
```
[91](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L91) | [203](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L203) | [278](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L278) | [282](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L282)

```solidity
File: src/transformers/AutoRange.sol

101: IVault(vault).transform(
            params.tokenId, address(this), abi.encodeWithSelector(AutoRange.execute.selector, params)
        );
308: int24 spacing = IUniswapV3Factory(factory).feeAmountTickSpacing(fee);
```
[101](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L101) | [308](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L308)

```solidity
File: src/transformers/V3Utils.sol

631: permit2.permitTransferFrom(permit, transferDetails, msg.sender, signature);
```
[631](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L631)

```solidity
File: src/utils/Swapper.sol

99: IUniversalRouter(universalRouter).execute(data.commands, data.inputs, data.deadline);
```
[99](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L99)
</details>

