## Summary

### Gas Optimization

no |Issue |Instances||
|-|:-|:-:|:-:|
| [G-01] | Pre-increments and pre-decrements are cheaper than post-increments and post-decrements |  |3|--| 
| [G-02] | Can make the variable outside the loop to save gas |  |2|--| 
| [G-03] |Before transfer of  some functions, we should check some variables for possible gas save |  |13|--| 
| [G-04] |Do not calculate constants |  |17|--| 
| [G-05] |TERNARY UNNECESSARY |  |7|--| 
| [G-06] |Empty blocks should be removed or emit something |  |3|--| 
| [G-07] | Using storage instead of memory for structs/arrays saves gas |  |14|--| 
| [G-08] |ith assembly, .call (bool success)  transfer can be done gas-optimized |  |2|--| 
| [G-09] |Use constants instead of type(uintx).max |  |7|--| 
| [G-10] |Use hardcode address instead address(this) |  |9|--| 




## Gas Optimizations  

## [G-1] Pre-increments and pre-decrements are cheaper than post-increments and post-decrements
       
```solidity
file:/src/transformers/V3Utils.sol
 619           transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed0);
 623            transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed1);
 627            transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.neededOther);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/V3Utils.sol#L619




## [G-2] Can make the variable outside the loop to save gas

Consider making the stack variables before the loop which gonna save gas

2 instances here collection and collectionScore

```solidity
File:/src/automators/Automator.sol
112            uint256 balance = IERC20(tokens[i]).balanceOf(address(this));

```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/automators/Automator.sol#L112

```solidity
file:/src/transformers/AutoCompound.sol
 234           uint256 balance = positionBalances[0][tokens[i]];

  https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoCompound.sol#L234
```


## [G-3] Before transfer of  some functions, we should check some variables for possible gas save

Before transfer, we should check for amount being 0 so the function doesn't run when its not gonna do anything:
 

```solidity
file:/src/V3Vault.sol
401       nonfungiblePositionManager.safeTransferFrom(msg.sender, address(this), tokenId, abi.encode(recipient));
424        nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));
599        SafeERC20.safeTransfer(IERC20(asset), isTransformMode ? msg.sender : owner, assets);
720            permit2.permitTransferFrom(
                permit,
                ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost),
                msg.sender,
                signature
            );
728            SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);
779            SafeERC20.safeTransfer(IERC20(asset), receiver, amount);
896            permit2.permitTransferFrom(
                permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
            );
901            SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
946        SafeERC20.safeTransfer(IERC20(asset), receiver, assets);
1083        nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId);


```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L401

```solidity
272       SafeERC20.safeTransfer(IERC20(token), to, amount);
```

https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoCompound.sol#L272

```solidity
file: /src/utils/Swapper.sol
167        SafeERC20.safeTransfer(IERC20(tokenIn), msg.sender, amountToPay);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/utils/Swapper.sol#L167

## [G-4] Do not calculate constants
Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.

*There are 17 instance(s) of this issue:*



```solidity
file:/src/V3Vault.sol
33    uint256 private constant Q32 = 2 ** 32;
34    uint256 private constant Q96 = 2 ** 96;

36    uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%

38    uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
39    uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%

41    uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%

43    uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%
44    uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L33-L44


```solidity
file:/src/V3Oracle.sol

27    uint256 private constant Q96 = 2 ** 96;
28   uint256 private constant Q128 = 2 ** 128;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Oracle.sol#L27-L28


```solidity
file:/src/InterestRateModel.sol
12    uint256 private constant Q96 = 2 ** 96;
13   uint256 public constant YEAR_SECS = 31557600; // taking into account leap years


15    uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10; // 10%
16    uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%


```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/InterestRateModel.sol#L12-L17

```solidity
file:/src/automators/Automator.sol
20    uint256 internal constant Q64 = 2 ** 64;
21    uint256 internal constant Q96 = 2 ** 96;


23    uint32 public constant MIN_TWAP_SECONDS = 60; // 1 minute
24    uint32 public constant MAX_TWAP_TICK_DIFFERENCE = 200; // 2%
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/automators/Automator.sol#L20-L24
## [G-5]TERNARY UNNECESSARY

```solidity
file:/src/V3Vault.sol
599        SafeERC20.safeTransfer(IERC20(asset), isTransformMode ? msg.sender : owner, assets);
1147        return factor0X32 > factor1X32 ? factor1X32 : factor0X32;
1253                dailyLendIncreaseLimitMin > lendIncreaseLimit ? dailyLendIncreaseLimitMin : lendIncreaseLimit;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L599

```solidity
file:/src/transformers/LeverageTransformer.sol
49        uint256 amount0 = token == token0 ? amount : 0;
50       uint256 amount1 = token == token1 ? amount : 0;
144        uint256 amount = token == token0 ? amount0 : (token == token1 ? amount1 : 0);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/LeverageTransformer.sol#L49-L50
```solidity
file:/src/utils/Swapper.sol
166        uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/utils/Swapper.sol#L166

## [G-6] Empty blocks should be removed or emit something

The gas cost of an empty constructor block in Solidity is typically in the range of 200-500 gas units. 

The code should be refactored such that they no longer exist, or the block should do something useful, such as emitting an event or reverting.
If the contract is meant to be extended, the contract should be abstract and the function signatures be added without any default implementation.

If the block is an empty if-statement block to avoid doing subsequent checks in the else-if/else conditions, the else-if/else conditions should be 
nested under the negation of the if-statement, because they involve different classes of checks, which may lead to the introduction of errors when 
the code is later modified (if( x ) {}else if(y){ . . . }else{ . . . } => if ( !x) {if(y) { . . . }else{ . . .}}) . 
Empty receive()/fallback() payable functions that are not used, can be removed to save deployment gas.


```solidity
file:
41    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/automators/AutoExit.sol#L41
```solidity
file:
43    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, address(0), address(0)) {}
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoCompound.sol#L43
```solidity
file:
33    ) Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoRange.sol#L33

## [G-7] Using storage instead of memory for structs/arrays saves gas

When fetching data from a storage location, assigning the data to a memory variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (2100 gas) for each field of the struct/array. If the fields are read from the new memory variable, they incur an additional MLOAD rather than a cheap stack read. Instead of declearing the variable with the memory keyword, declaring the variable with the storage keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incuring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a memory variable, is if the full struct/array is being returned by the function, is being passed to a function that requires memory, or if the array/struct is being read from another memory array/struct

```solidity
file:/src/V3Oracle.sol
177        PositionState memory state = _initializeState(tokenId);
365            uint32[] memory secondsAgos = new uint32[](2);
368            (int56[] memory tickCumulatives,) = pool.observe(secondsAgos);

https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Oracle.sol#L177
```solidity
file:/src/automators/AutoExit.sol
105        ExecuteState memory state;
106        PositionConfig memory config = positionConfigs[params.tokenId];
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/automators/AutoExit.sol#L105-L106
```solidity
file:/src/automators/Automator.sol#L181
181        uint32[] memory secondsAgos = new uint32[](2);
186        try pool.observe(secondsAgos) returns (int56[] memory tickCumulatives, uint160[] memory) {
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/automators/Automator.sol#L181
```solidity
file:/src/transformers/AutoCompound.sol
105        ExecuteState memory state;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoCompound.sol#L105

```solidity
file:/src/transformers/AutoRange.so
115        ExecuteState memory state;
116        PositionConfig memory config = positionConfigs[params.tokenId];

```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoRange.sol#L115-L116
```solidity
file:/src/transformers/V3Utils.sol
371        Instructions memory instructions = abi.decode(data, (Instructions));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/V3Utils.sol#L371

```solidity
file:
70        FlashCallbackData memory data = abi.decode(callbackData, (FlashCallbackData));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/utils/FlashloanLiquidator.sol#L70

## [G-8]  With assembly, .call (bool success)  transfer can be done gas-optimized

return data (bool success,) has to be stored due to EVM architecture, but in a usage like below, ‘out’ and ‘outsize’ values are given (0,0), 
this storage disappears and gas optimization is provided.
https://code4rena.com/reports/2023-01-biconomy#g-01-with-assembly-call-bool-success-transfer-can-be-done-gas-optimized

Did you know that the normal "(bool success, bytes memory returnData) = http://target.call()" automatically copies the return data to memory even if you omit the returnData variable? If a relayer executes transactions with such calls it can lead to a gas-griefing attack.

```solidity
file:src/V3Vault.sol
 522       (bool success,) = transformer.call(data);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L522-L522
```solidity
file:/src/utils/Swapper.sol
89                (bool success,) = zeroxRouter.call(data.data);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/utils/Swapper.sol#L89

## [G-9] Use constants instead of type(uintx).max

type(uint120).max or type(uint128).max, etc. it uses more gas in the distribution process and also for each transaction than constant usage.


```solidity
file:/src/V3Vault.sol
637     params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
 638           params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)


 1046            fees0 = type(uint128).max;
 1047           fees1 = type(uint128).max;

 1068                fees0 = type(uint128).max;
 1069              fees1 = type(uint128).max;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol/src/V3Vault.sol#L636-L637
```solidity
file:
209    INonfungiblePositionManager.CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/automators/Automator.sol#L209

```solidity
file:/src/transformers/AutoCompound.sol
110                 params.tokenId, address(this), type(uint128).max, type(uint128).max
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoCompound.sol#L110

```solidity
file:
280            SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoCompound.sol#L280
## [G-10]  Use hardcode address instead address(this)
 
 Instead of using address(this), it is more gas-efficient to pre-calculate and use the hardcoded address. Foundry’s script.sol and solmate’s LibRlp.sol contracts can help achieve this.
References: https://book.getfoundry.sh/reference/forge-std/compute-create-address
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L285
```solidity
file:/src/automators/Automator.sol
112            uint256 balance = IERC20(tokens[i]).balanceOf(address(this));
128        uint256 balance = address(this).balance;
209  INonfungiblePositionManager.CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max) );
       
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/automators/Automator.sol#L112
```solidity
file:/src/transformers/AutoCompound.sol
92            params.tokenId, address(this), abi.encodeWithSelector(AutoCompound.execute.selector, params)
110                params.tokenId, address(this), type(uint128).max, type(uint128).max
278        uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager));
282        uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoCompound.sol#L92

```solidity
file:
102            params.tokenId, address(this), abi.encodeWithSelector(AutoRange.execute.selector, params)
232            nonfungiblePositionManager.safeTransferFrom(address(this), state.owner, state.newTokenId);

```https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoRange.sol#L102