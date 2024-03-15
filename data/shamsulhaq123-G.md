## Gas Optimization

## Summary


|No|Issue|Instence|
|:-|:-|:-|
|[G-01]|Change public function visibility to external|10|
|[G-02]|Setting the constructor to payable|11|
|[G-03]|Use hardcode address instead address(this)|41|
|[G-04]|Use selfbalance() instead of address(this).balance|1|
|[G-05]|+= costs more gas than = + for state variables|13|
|[G-06]| Use assembly for loops|2|
|[G-07]|Using mappings instead of arrays to avoid length checks save gas|5|
|[G-08]| Unnecessary look up in if condition|19|
|[G-09]|address(this) can be stored in state variable that will ultimately cost less|41|
|[G-10]| Use constants instead of type(uintx).max|12|
|[G-11]|Default value initialization|11|
|[G-12]|Use assembly in place of abi.decode to extract calldata values more efficiently|13|
|[G-13]| Emitting constants wastes gas|43|
|[G-14]|Use of Custom Errors Instead of String|15|
|[G-15]| Do not calculate constants|4|
|[G-16]| Empty Blocks Should Be Removed Or Emit Something|3|
|[G-17]|Consider using OZ EnumerateSet in place of nested mappings|1|
|[G-18]|Multiple address/ID mappings can be combined into a single mapping of an address/ID to a struct, where appropriate|9|
|[G-19]| Use nested if and, avoid multiple check combinations|24|
|[G-20]|Using bools for storage incurs overhead|9|
|[G-21]|Use assembly to emit events|43|
|[G-22]|Superfluous event fields|9|
|[G-23]| >= costs less gas than >|28|
|[G-24]| Use assembly to check for address(0) |13|


## [G-01] Change public function visibility to external
Since the following public functions are not called from within the contract, their visibility can be made external for gas optimization.

```solidity

file: V3Vault.sol

277    function decimals() public view override(IERC20Metadata, ERC20) returns (uint8) {
        return assetDecimals;
    }

284  function totalAssets() public view override returns (uint256) {
        return IERC20(asset).balanceOf(address(this));
    }

334    function previewDeposit(uint256 assets) public view override returns (uint256) {
        (, uint256 lendExchangeRateX96) = _calculateGlobalInterest();
        return _convertToShares(assets, lendExchangeRateX96, Math.Rounding.Down);
    }

    /// @inheritdoc IERC4626
    function previewMint(uint256 shares) public view override returns (uint256) {
        (, uint256 lendExchangeRateX96) = _calculateGlobalInterest();
        return _convertToAssets(shares, lendExchangeRateX96, Math.Rounding.Up);
    }

    /// @inheritdoc IERC4626
    function previewWithdraw(uint256 assets) public view override returns (uint256) {
        (, uint256 lendExchangeRateX96) = _calculateGlobalInterest();
        return _convertToShares(assets, lendExchangeRateX96, Math.Rounding.Up);
    }

    /// @inheritdoc IERC4626
352    function previewRedeem(uint256 shares) public view override returns (uint256) {
        (, uint256 lendExchangeRateX96) = _calculateGlobalInterest();
        return _convertToAssets(shares, lendExchangeRateX96, Math.Rounding.Down);
    }
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L277
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L284
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L334-L352

```solidity

file: V3Oracle.sol

162 function getPositionBreakdown(uint256 tokenId)
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
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L162

```solidity

file: InterestRateModel.sol

58   function getRatesPerSecondX96(uint256 cash, uint256 debt)
        public
        view
        override
        returns (uint256 borrowRateX96, uint256 supplyRateX96

182     function setValues(
        uint256 baseRatePerYearX96,
        uint256 multiplierPerYearX96,
        uint256 jumpMultiplierPerYearX96,
        uint256 _kinkX96
    ) public onlyOwner 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L58
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L82

```solidity

file: automators/Automator.sol#

59   function setWithdrawer(address _withdrawer) public onlyOwner {
        emit WithdrawerChanged(_withdrawer);
        withdrawer = _withdrawer;
    }

69    function setOperator(address _operator, bool _active) public onlyOwner {
        emit OperatorChanged(_operator, _active);
        operators[_operator] = _active;
    }

79  function setVault(address _vault, bool _active) public onlyOwner {
        emit VaultChanged(_vault, _active);
        vaults[_vault] = _active;
    }

87   function setTWAPConfig(uint16 _maxTWAPTickDifference, uint32 _TWAPSeconds) public onlyOwner {
        if (_TWAPSeconds < MIN_TWAP_SECONDS) {
            revert InvalidConfig();
        }
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L59
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L69
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L79
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L87

## [G-02] Setting the constructor to payable
You can cut out 10 opcodes in the creation-time EVM bytecode if you declare a constructor payable. Making the constructor payable eliminates the need for an initial check of msg.value == 0 and saves 13 gas on deployment with no security risks.\

```solidity

file: V3Vault.sol

169    constructor(
        string memory name,
        string memory symbol,
        address _asset,
        INonfungiblePositionManager _nonfungiblePositionManager,
        IInterestRateModel _interestRateModel,
        IV3Oracle _oracle,
        IPermit2 _permit2
    )
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L169

```solidity

file: V3Oracle.sol

74   constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _referenceToken,
        address _chainlinkReferenceToken
    )

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L74

```solidity

file: InterestRateModel.sol

33   constructor(
        uint256 baseRatePerYearX96,
        uint256 multiplierPerYearX96,
        uint256 jumpMultiplierPerYearX96,
        uint256 _kinkX96
    )

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L33

```solidity

file: automators/AutoExit.sol

33  constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) 

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L33

```solidity

file: automators/Automator.sol

41  constructor(
        INonfungiblePositionManager npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    ) 

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L41

```solidity

file: transformers/AutoCompound.sol

37     constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference
    ) 

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L37

```solidity

file: transformers/AutoRange.sol

25   constructor(
        INonfungiblePositionManager _npm,
        address _operator,
        address _withdrawer,
        uint32 _TWAPSeconds,
        uint16 _maxTWAPTickDifference,
        address _zeroxRouter,
        address _universalRouter
    )

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L25

```solidity

file: transformers/LeverageTransformer.sol

13  constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L13

```solidity

file: transformers/V3Utils.sol

31  constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _zeroxRouter,
        address _universalRouter,
        address _permit2
    ) 

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L31

```solidity

file: utils/FlashloanLiquidator.sol

24  constructor(INonfungiblePositionManager _nonfungiblePositionManager, address _zeroxRouter, address _universalRouter)

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L24

```solidity

file: utils/Swapper.sol

37 constructor(
        INonfungiblePositionManager _nonfungiblePositionManager,
        address _zeroxRouter,
        address _universalRouter
    ) 

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L37

## [G-03] Use hardcode address instead address(this)
Instead of using address(this), it is more gas-efficient to pre-calculate and use the hardcoded address. Foundry’s script.sol and solmate’s LibRlp.sol contracts can help achieve this.

```solidity

file: V3Vault.sol

285  return IERC20(asset).balanceOf(address(this));

401   nonfungiblePositionManager.safeTransferFrom(msg.sender, address(this), tokenId, abi.encode(recipient));

423     nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);
424    nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));

435  if (msg.sender != address(nonfungiblePositionManager) || from == address(this))

532  if (owner != address(this))

561  if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender)

722  ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost),

728  SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);

791   transformer == address(0) || transformer == address(this) || transformer == asset

897   permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature

901   SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);

982    permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature

986  SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);

1083  nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L285
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L401
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L423-L424
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L435
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L532
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L561
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L722
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L728
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L791
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L897
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L901
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L982
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L986
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1083

```solidity

file: automators/Automator.sol

112   uint256 balance = IERC20(tokens[i]).balanceOf(address(this));

128  uint256 balance = address(this).balance;

209  INonfungiblePositionManager.CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max)
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L112
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L128
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L209

```solidity

file: transformers/AutoCompound.sol

92    params.tokenId, address(this), abi.encodeWithSelector(AutoCompound.execute.selector, params)

110  params.tokenId, address(this), type(uint128).max, type(uint128).max

278  uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager));

282    uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L92
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L110
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L278
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L282

```solidity

file: transformers/AutoRange.sol

102     params.tokenId, address(this), abi.encodeWithSelector(AutoRange.execute.selector, params)

208  address(this), 

232    nonfungiblePositionManager.safeTransferFrom(address(this), state.owner, state.newTokenId);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L102
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L208
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L232

```solidity

file: transformers/LeverageTransformer.sol

138   address(this),

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L138

```solidity

file: transformers/V3Utils.sol

106     nonfungiblePositionManager.permit(address(this), tokenId, instructions.deadline, v, r, s);

367  if (from == address(this)) 

376    nonfungiblePositionManager.safeTransferFrom(address(this), from, tokenId, instructions.returnData);

578         SafeERC20.safeTransferFrom(token0, msg.sender, address(this), needed0);
       
            SafeERC20.safeTransferFrom(token1, msg.sender, address(this), needed1);
       
584         SafeERC20.safeTransferFrom(otherToken, msg.sender, address(this), neededOther);

618     state.balanceBefore0 = token0.balanceOf(address(this));
            transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed0);
        
            state.balanceBefore1 = token1.balanceOf(address(this));
            transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed1);
       
            state.balanceBeforeOther = otherToken.balanceOf(address(this));
626            transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.neededOther);

635    if (token0.balanceOf(address(this)) - state.balanceBefore0 != state.needed0) {
            
       
            if (token1.balanceOf(address(this)) - state.balanceBefore1 != state.needed1) {           
645         if (otherToken.balanceOf(address(this)) - state.balanceBeforeOther != state.neededOther) 

721  address(this),

727    nonfungiblePositionManager.safeTransferFrom(address(this), params.recipientNFT, tokenId, params.returnData);

896   uint256 balanceBefore0 = token0.balanceOf(address(this));
        uint256 balanceBefore1 = token1.balanceOf(address(this));
        (amount0, amount1) = nonfungiblePositionManager.collect(
          
        uint256 balanceAfter0 = token0.balanceOf(address(this));
902     uint256 balanceAfter1 = token1.balanceOf(address(this));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L106
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L367
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L376
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L578-L584
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L618-L626
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L635
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L721
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L727
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L896-L902

```solidity

file: utils/FlashloanLiquidator.sol

64  params.flashLoanPool.flash(address(this), isAsset0 ? liquidationCost : 0, !isAsset0 ? liquidationCost : 0, data);

75       data.tokenId, data.debtShares, data.swap0.amountIn, data.swap1.amountIn, address(this), ""

89    uint256 balance = data.swap0.tokenIn.balanceOf(address(this));

95  uint256 balance = data.swap1.tokenIn.balanceOf(address(this));

101  uint256 balance = data.asset.balanceOf(address(this));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L64
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L75
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L89
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L95
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L101

```solidity

file: utils/Swapper.sol

78  uint256 balanceInBefore = params.tokenIn.balanceOf(address(this));
79  uint256 balanceOutBefore = params.tokenOut.balanceOf(address(this));

104   uint256 balanceInAfter = params.tokenIn.balanceOf(address(this));
105  uint256 balanceOutAfter = params.tokenOut.balanceOf(address(this));

135   address(this),
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L78-L79
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L104-L105
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L135

## [G-4] Use selfbalance() instead of address(this).balance

```solidity

file: automators/Automator.sol

128 uint256 balance = address(this).balance;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L128

## [G-05] += costs more gas than = + for state variables
use = + or = - instead to save gas

```solidity

file: V3Vault.sol

569  debtSharesTotal += shares;

949  dailyLendIncreaseLimitLeft += assets;

995    dailyDebtIncreaseLimitLeft += assets;

1220  tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
1221   tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L569
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L949
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L995
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1220-L1221

```solidity

file: V3Oracle.sol

440 fees0 += state.tokensOwed0;
441 fees1 += state.tokensOwed1;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L440-L441

```solidity

file: transformers/LeverageTransformer.sol

62  amount0 += amountOut;

74  amount1 += amountOut;

153  amount += amountOut;

162  amount += amountOut;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L62
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L74
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L153
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L162

```solidity

file: transformers/V3Utils.sol

319 targetAmount += amountOutDelta;

321  targetAmount += amount0;

336  targetAmount += amountOutDelta;

338  targetAmount += amount1;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L319
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L321
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L336
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L338

## [G-06]  Use assembly for loops
In the following instances, assembly is used for more gas efficient loops.

```solidity

file:automators/Automator.sol

111   for (; i < count; ++i) 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L111

```solidity

file: transformers/AutoCompound.sol

233   for (; i < count; ++i) 

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L233

## [G-07] Using mappings instead of arrays to avoid length checks save gas
Just by using a mapping, we get a gas saving of 2102 gas. When you read the value of an index of an array, solidity adds bytecode that checks that you are reading from a valid index 

```solidity

file: V3Oracle.sol

365  uint32[] memory secondsAgos = new uint32[](2);

368 (int56[] memory tickCumulatives,) = pool.observe(secondsAgos); 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L365
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L368

```solidity

file: automators/Automator.sol

181  uint32[] memory secondsAgos = new uint32[](2);

186 try pool.observe(secondsAgos) returns (int56[] memory tickCumulatives, uint160[] memory) 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L181
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L186

```solidity

file: transformers/AutoCompound.sol

227   function withdrawBalances(address[] calldata tokens, address to) external override nonReentrant 

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L227

## [G-08] Unnecessary look up in if condition

If the || condition isn’t required, the second condition will have been looked up unnecessarily.

```solidity

file: V3Vault.sol

435  if (msg.sender != address(nonfungiblePositionManager) || from == address(this))

502  if (tokenId == 0 || !transformerAllowList[transformer]) 

737   if (amount0 < params.amount0Min || amount1 < params.amount1Min) 

790   if (
791          transformer == address(0) || transformer == address(this) || transformer == asset
792              || transformer == address(nonfungiblePositionManager)

1249   if (force || time > dailyLendIncreaseLimitLastReset) 

1261  if (force || time > dailyDebtIncreaseLimitLastReset) 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L435
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L502
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L737
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L790L792
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1249
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1261

```solidity

file: 3Oracle.sol

227   if (!(token0 == token && token1 == referenceToken || token0 == referenceToken && token1 == token)) 

323  if (feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY)

338  if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0) 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L227
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L323
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L338

```solidity

file: InterestRateModel.sol

88         if (
            baseRatePerYearX96 > MAX_BASE_RATE_X96 || multiplierPerYearX96 > MAX_MULTIPLIER_X96
                || jumpMultiplierPerYearX96 > MAX_MULTIPLIER_X96
        ) 

112  if (
            config.onlyFees && params.rewardX64 > config.maxRewardX64
                || !config.onlyFees && params.rewardX64 > config.maxRewardX64
        )
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L88
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L112

```solidity

file: transformers/AutoCompound.sol

88 function executeWithVault(ExecuteParams calldata params, address vault) external {
        if (!operators[msg.sender] || !vaults[vault]) 

123    if (state.amount0 > 0 || state.amount1 > 0)

160  if (state.maxAddAmount0 > 0 || state.maxAddAmount1 > 0)
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L88
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L123
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L160

```solidity

file: transformers/AutoRange.sol#

98  if (!operators[msg.sender] || !vaults[vault])

122  if (
            config.onlyFees && params.rewardX64 > config.maxRewardX64
                || !config.onlyFees && params.rewardX64 > config.maxRewardX64
        )

149  if (params.swap0To1 && params.amountIn > state.amount0 || !params.swap0To1 && params.amountIn > state.amount1) {
            revert SwapAmountTooLarge();
        }     

166  if (
            state.currentTick < state.tickLower - config.lowerTickLimit
                || state.currentTick >= state.tickUpper + config.upperTickLimit
        )                   
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L98
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L122
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L149
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L166

```solidity

file: transformers/V3Utils.sol

142    if (amount0 < instructions.amountIn0 || amount1 < instructions.amountIn1) 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L142

### [G-09] address(this) can be stored in state variable that will ultimately cost less
than every time calculating this specifically when it used multiple times in a contract

```solidity

file: V3Vault.sol

285  return IERC20(asset).balanceOf(address(this));

401   nonfungiblePositionManager.safeTransferFrom(msg.sender, address(this), tokenId, abi.encode(recipient));

423     nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);
424    nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));

435  if (msg.sender != address(nonfungiblePositionManager) || from == address(this))

532  if (owner != address(this))

561  if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender)

722  ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost),

728  SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);

791   transformer == address(0) || transformer == address(this) || transformer == asset

897   permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature

901   SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);

982    permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature

986  SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);

1083  nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L285
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L401
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L423-L424
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L435
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L532
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L561
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L722
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L728
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L791
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L897
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L901
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L982
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L986
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1083

```solidity

file: automators/Automator.sol

112   uint256 balance = IERC20(tokens[i]).balanceOf(address(this));

128  uint256 balance = address(this).balance;

209  INonfungiblePositionManager.CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max)
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L112
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L128
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L209

```solidity

file: transformers/AutoCompound.sol

92    params.tokenId, address(this), abi.encodeWithSelector(AutoCompound.execute.selector, params)

110  params.tokenId, address(this), type(uint128).max, type(uint128).max

278  uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager));

282    uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L92
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L110
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L278
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L282

```solidity

file: transformers/AutoRange.sol

102     params.tokenId, address(this), abi.encodeWithSelector(AutoRange.execute.selector, params)

208  address(this), 

232    nonfungiblePositionManager.safeTransferFrom(address(this), state.owner, state.newTokenId);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L102
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L208
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L232

```solidity

file: transformers/LeverageTransformer.sol

138   address(this),

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L138

```solidity

file: transformers/V3Utils.sol

106     nonfungiblePositionManager.permit(address(this), tokenId, instructions.deadline, v, r, s);

367  if (from == address(this)) 

376    nonfungiblePositionManager.safeTransferFrom(address(this), from, tokenId, instructions.returnData);

578         SafeERC20.safeTransferFrom(token0, msg.sender, address(this), needed0);
       
            SafeERC20.safeTransferFrom(token1, msg.sender, address(this), needed1);
       
584         SafeERC20.safeTransferFrom(otherToken, msg.sender, address(this), neededOther);

618     state.balanceBefore0 = token0.balanceOf(address(this));
            transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed0);
        
            state.balanceBefore1 = token1.balanceOf(address(this));
            transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed1);
       
            state.balanceBeforeOther = otherToken.balanceOf(address(this));
626            transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.neededOther);

635    if (token0.balanceOf(address(this)) - state.balanceBefore0 != state.needed0) {
            
       
            if (token1.balanceOf(address(this)) - state.balanceBefore1 != state.needed1) {           
645         if (otherToken.balanceOf(address(this)) - state.balanceBeforeOther != state.neededOther) 

721  address(this),

727    nonfungiblePositionManager.safeTransferFrom(address(this), params.recipientNFT, tokenId, params.returnData);

896   uint256 balanceBefore0 = token0.balanceOf(address(this));
        uint256 balanceBefore1 = token1.balanceOf(address(this));
        (amount0, amount1) = nonfungiblePositionManager.collect(
          
        uint256 balanceAfter0 = token0.balanceOf(address(this));
902     uint256 balanceAfter1 = token1.balanceOf(address(this));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L106
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L367
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L376
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L578-L584
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L618-L626
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L635
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L721
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L727
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L896-L902

```solidity

file: utils/FlashloanLiquidator.sol

64  params.flashLoanPool.flash(address(this), isAsset0 ? liquidationCost : 0, !isAsset0 ? liquidationCost : 0, data);

75       data.tokenId, data.debtShares, data.swap0.amountIn, data.swap1.amountIn, address(this), ""

89    uint256 balance = data.swap0.tokenIn.balanceOf(address(this));

95  uint256 balance = data.swap1.tokenIn.balanceOf(address(this));

101  uint256 balance = data.asset.balanceOf(address(this));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L64
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L75
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L89
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L95
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L101

```solidity

file: utils/Swapper.sol

78  uint256 balanceInBefore = params.tokenIn.balanceOf(address(this));
79  uint256 balanceOutBefore = params.tokenOut.balanceOf(address(this));

104   uint256 balanceInAfter = params.tokenIn.balanceOf(address(this));
105  uint256 balanceOutAfter = params.tokenOut.balanceOf(address(this));

135   address(this),
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L78-L79
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L104-L105
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L135

## [G-10] Use constants instead of type(uintx).max

type(uint120).max or type(uint128).max, etc. it uses more gas in the distribution process and also for each transaction than constant usage.

```solidity

file: V3Vault.sol

636  params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
637    params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)

1046 fees0 = type(uint128).max;
1047 fees1 = type(uint128).max;

1058 fees0 = type(uint128).max;
1059 fees1 = type(uint128).max;

1228   collateralValueLimitFactorX32 < type(uint32).max

1236   collateralValueLimitFactorX32 < type(uint32).max
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L636-L637
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1046-L1047
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1058-L1059
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1228
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1236

```solidity

file:V3Oracle.sol

338  if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0)
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L338

```solidity

file: automators/Automator.sol

209  INonfungiblePositionManager.CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max)
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L209


```solidity

file: transformers/AutoCompound.sol

110   params.tokenId, address(this), type(uint128).max, type(uint128).max

280     SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max);

284  SafeERC20.safeApprove(IERC20(token1), address(nonfungiblePositionManager), type(uint256).max);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L110
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L280
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L284

```solidity

file: transformers/LeverageTransformer.sol#

139  params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
140    params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)


```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L139-L140

```solidity

file: transformers/V3Utils.sol

133   instructions.feeAmount0 == type(uint128).max
                ? type(uint128).max
                : (amount0 + instructions.feeAmount0).toUint128(),
            instructions.feeAmount1 == type(uint128).max
137                ? type(uint128).max
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L133-L137

## [G-11] Default value initialization
Problem
If a variable is not set/initialized, it is assumed to have the default value (0, false, 0x0 etc depending on the data type).
Explicitly initializing it with its default value is an anti-pattern and wastes gas.
Instances include:

```solidity

file: V3Vault.sol

118   uint32 public reserveFactorX32 = 0;

124   uint256 public debtSharesTotal = 0;

127 uint256 public lastExchangeRateUpdate = 0;

131    uint256 public globalDebtLimit = 0;
    uint256 public globalLendLimit = 0;
135    uint256 public minLoanSize = 0;

138  uint256 public dailyLendIncreaseLimitMin = 0;
    uint256 public dailyLendIncreaseLimitLeft = 0;
    uint256 public dailyLendIncreaseLimitLastReset = 0;

    // daily debt increase limit handling
    uint256 public dailyDebtIncreaseLimitMin = 0;
    uint256 public dailyDebtIncreaseLimitLeft = 0;
145 uint256 public dailyDebtIncreaseLimitLastReset = 0;

161   uint256 private transformedTokenId = 0; 

542   transformedTokenId = 0;

1053   liquidity = 0;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L118
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L124
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L127
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L131-L135 
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L138-L145 
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L161
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L542
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1053

```solidity

file: V3Oracle.sol

366   secondsAgos[0] = 0; 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L366

```solidity

file: automators/Automator.sol

182  secondsAgos[0] = 0; 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L182

```solidity

file: transformers/AutoCompound.sol

136  amountIn = 0;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L136

## [G-12] Use assembly in place of abi.decode to extract calldata values more efficiently
Using inline assembly to extract calldata values can be more gas-efficient than using abi.decode in Solidity. Inline assembly gives more direct access to EVM operations, enabling optimized usage of calldata. However, assembly should be used judiciously as it's more prone to errors. Opt for this approach when performance is critical and the complexity it introduces is manageable.

```solidity

file:V3Vault.sol

444    owner = abi.decode(data, (address));

719    abi.decode(params.permitData, (ISignatureTransfer.PermitTransferFrom, bytes));

895   abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));

980   abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L444
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L719
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L895
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L980

```solidity

file: transformers/V3Utils.sol

371   Instructions memory instructions = abi.decode(data, (Instructions));

404    abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));

478  abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));

541   abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L371
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L404
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L478
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L541

```solidity

file: utils/FlashloanLiquidator.sol

70  FlashCallbackData memory data = abi.decode(callbackData, (FlashCallbackData));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L70

```solidity

file: utils/Swapper.sol

82   (address router, bytes memory routerData) = abi.decode(params.swapData, (address, bytes));

85   ZeroxRouterData memory data = abi.decode(routerData, (ZeroxRouterData));

96   UniversalRouterData memory data = abi.decode(routerData, (UniversalRouterData));

160    (address tokenIn, address tokenOut, uint24 fee) = abi.decode(data, (address, address, uint24));
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L82
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L85
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L96
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L160

## [G-13] Emitting constants wastes gas
Every event parameter costs Glogdata (8 gas) per byte. You can avoid this extra cost, in cases where you're emitting a constant, by creating a new version of the event which doesn't have the parameter (and have users look to the contract's variables for its value instead). Alternatively, in the case of boolean constants, two events can be created - one representing the true case and one representing the false case.

```solidity

file: V3Vault.sol

449  emit Add(tokenId, owner, 0);

564    emit Add(tokenId, owner, oldTokenId);

489  emit ApprovedTransform(tokenId, msg.sender, target, isActive);

601  emit Borrow(tokenId, owner, assets, shares);

645  emit WithdrawCollateral(params.tokenId, owner, params.recipient, params.liquidity, amount0, amount1);

746  emit Liquidate(

782  emit WithdrawReserves(amount, receiver);  

798   emit SetTransformer(transformer, active);

830  emit SetLimits(
            _minLoanSize, _globalLendLimit, _globalDebtLimit, _dailyLendIncreaseLimitMin, _dailyDebtIncreaseLimitMin
        );

849  emit SetReserveProtectionFactor(_reserveProtectionFactorX32);

865  emit SetTokenConfig(token, collateralFactorX32, collateralValueLimitFactorX32);

916  emit Deposit(msg.sender, receiver, assets, shares);

951    emit Withdraw(msg.sender, receiver, owner, assets, shares);

1013  emit Repay(tokenId, msg.sender, owner, assets, shares);

1084  emit Remove(tokenId, owner);

1139    emit ExchangeRateUpdate(newDebtExchangeRateX96, newLendExchangeRateX96);

1160   emit ExchangeRateUpdate(newDebtExchangeRateX96, newLendExchangeRateX96);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L449
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L464
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L489
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L601
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L645
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L746
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L782
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L798
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L830
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L849
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L865
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L916
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L951
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1013
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1084
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1139
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1160

```solidity

file: V3Oracle.sol

190  emit SetMaxPoolPriceDifference(_maxPoolPriceDifference);

242 emit TokenConfigUpdated(token, config);
243 emit OracleModeUpdated(token, mode);

260  emit OracleModeUpdated(token, mode);

267   emit SetEmergencyAdmin(admin);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L190
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L242-L243
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L260
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L267

```solidity

file: InterestRateModel.sol

100    emit SetValues(baseRatePerYearX96, multiplierPerYearX96, jumpMultiplierPerYearX96, _kinkX96);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L100

```solidity

file: automators/AutoExit.sol

208     emit PositionConfigured(params.tokenId, false, false, false, 0, 0, 0, 0, false, 0);

211    emit Executed(
            params.tokenId, msg.sender, state.isSwap, state.amount0, state.amount1, state.token0, state.token1
        );

232  emit PositionConfigured(        
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L208
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L211
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L232
```solidity

file: automators/Automator.sol

59  emit WithdrawerChanged(_withdrawer);

70   emit OperatorChanged(_operator, _active);

80  emit VaultChanged(_vault, _active);

94   emit TWAPConfigChanged(_TWAPSeconds, _maxTWAPTickDifference);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L59
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L70
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L80
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L94


```solidity

file: transformers/AutoCompound.sol

183    emit AutoCompounded(

246  emit RewardUpdated(msg.sender, _totalRewardX64);

251   emit BalanceAdded(tokenId, token, amount);

269    emit BalanceAdded(tokenId, token, amount - currentBalance);
            
261     emit BalanceRemoved(tokenId, token, currentBalance - amount);

271   emit BalanceRemoved(tokenId, token, amount);
        
272    emit BalanceWithdrawn(tokenId, token, to, amount);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L183
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L246
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L251
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L259-L261 
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L271-L272

```solidity

file: transformers/AutoRange.sol

252    emit PositionConfigured(

266  emit PositionConfigured(params.tokenId, 0, 0, 0, 0, 0, 0, false, 0);

267   emit RangeChanged(params.tokenId, state.newTokenId);

286  emit PositionConfigured(
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L252
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L266-L267 
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L286

```solidity

file: transformers/V3Utils.sol

218  emit CompoundFees(tokenId, liquidity, amount0, amount1);

303 emit ChangeRange(tokenId, newTokenId);

248  emit WithdrawAndCollectAndSwap(tokenId, instructions.targetToken, targetAmount);

729  emit SwapAndMint(tokenId, liquidity, added0, added1);

773  emit SwapAndIncreaseLiquidity(params.tokenId, liquidity, added0, added1);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L218
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L303
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L348
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L729
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L773

```solidity

file: utils/Swapper.sol

116   emit Swap(address(params.tokenIn), address(params.tokenOut), amountInDelta, amountOutDelta);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L116

## [G-14] Use of Custom Errors Instead of String
To save some gas the use of custom errors leads to cheaper deploy time cost and run time cost. The run time cost is only relevant when the revert condition is met.

```solidity

file: V3Vault.sol

4 import "v3-core/interfaces/IUniswapV3Factory.sol";
import "v3-core/interfaces/IUniswapV3Pool.sol";
import "v3-core/libraries/TickMath.sol";
import "v3-core/libraries/FixedPoint128.sol";

import "v3-periphery/libraries/LiquidityAmounts.sol";
import "v3-periphery/interfaces/INonfungiblePositionManager.sol";

import "@openzeppelin/contracts/utils/math/Math.sol";
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/utils/math/SafeCast.sol";
import "@openzeppelin/contracts/utils/Multicall.sol";

import "permit2/interfaces/IPermit2.sol";

import "./interfaces/IVault.sol";
import "./interfaces/IV3Oracle.sol";
import "./interfaces/IInterestRateModel.sol";
import "./interfaces/IErrors.sol";
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L4-L25

```solidity

file: V3Oracle.sol

4 import "v3-core/interfaces/IUniswapV3Factory.sol";
import "v3-core/interfaces/IUniswapV3Pool.sol";

import "v3-core/libraries/TickMath.sol";

import "v3-periphery/libraries/PoolAddress.sol";
import "v3-periphery/libraries/LiquidityAmounts.sol";

import "v3-periphery/interfaces/INonfungiblePositionManager.sol";

import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

import "../lib/AggregatorV3Interface.sol";

import "./interfaces/IV3Oracle.sol";
import "./interfaces/IErrors.sol";
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L4-L20

```solidity

file: InterestRateModel.sol

4 import "@openzeppelin/contracts/access/Ownable.sol";

import "./interfaces/IInterestRateModel.sol";
import "./interfaces/IErrors.sol";
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L4-L7

```solidity

file: automators/AutoExit.sol

4 import "./Automator.sol";
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L4

```solidity

file: automators/Automator.sol

4 import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
import "@openzeppelin/contracts/utils/math/SafeCast.sol";

import "v3-core/interfaces/IUniswapV3Factory.sol";
import "v3-core/interfaces/IUniswapV3Pool.sol";
import "v3-core/libraries/TickMath.sol";
import "v3-core/libraries/FullMath.sol";

import "v3-periphery/interfaces/INonfungiblePositionManager.sol";

import "../../lib/IWETH9.sol";
import "../utils/Swapper.sol";
17 import "../interfaces/IVault.sol";
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L4-L17 

```solidity

file: transformers/AutoCompound.sol

4 import "@openzeppelin/contracts/security/ReentrancyGuard.sol";
import "@openzeppelin/contracts/utils/Multicall.sol";
import "@openzeppelin/contracts/utils/math/SafeMath.sol";

import "v3-periphery/interfaces/INonfungiblePositionManager.sol";

10 import "../automators/Automator.sol";

244  require(_totalRewardX64 <= totalRewardX64, ">totalRewardX64");

269  require(amount <= balance, "amount>balance");
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L4-L10 
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L244
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L269

```solidity

file: transformers/AutoRange.sol

4 import "../automators/Automator.sol";
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L4
```solidity

file: transformers/LeverageTransformer.sol

4 import "@openzeppelin/contracts/utils/math/SafeCast.sol";
import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

import "../utils/Swapper.sol";
import "../interfaces/IVault.sol";
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L4-L8


```solidity

file: transformers/V3Utils.sol

4 import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
import "@openzeppelin/contracts/utils/math/SafeCast.sol";

import "permit2/interfaces/IPermit2.sol";

9 import "../utils/Swapper.sol";

161  "",
            instructions.amountAddMin0,
             instructions.amountAddMin1,
164                 ""

181  "",
            instructions.amountIn0,
            instructions.amountOut0Min,
            instructions.swapData0,
            instructions.amountAddMin0,
            instructions.amountAddMin1,
187     ""
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L4-L9
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L161
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L181-L187 

```solidity

file: utils/FlashloanLiquidator.sol

4 import "v3-core/interfaces/IUniswapV3Pool.sol";
import "v3-core/interfaces/callback/IUniswapV3FlashCallback.sol";

import "../interfaces/IVault.sol";
8  import "./Swapper.sol";
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L4-L8 

```solidity

file: utils/Swapper.sol

4 import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

import "v3-core/interfaces/callback/IUniswapV3SwapCallback.sol";
import "v3-core/interfaces/IUniswapV3Pool.sol";
import "v3-core/libraries/TickMath.sol";

import "v3-periphery/interfaces/INonfungiblePositionManager.sol";

import "../../lib/IWETH9.sol";
import "../../lib/IUniversalRouter.sol";
14 import "../interfaces/IErrors.sol";
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L4-L14

## [G-15] Do not calculate constants
Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.

```solidity

file: V3Vault.sol

33   uint256 private constant Q32 = 2 ** 32;
    uint256 private constant Q96 = 2 ** 96;

    uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%

    uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
    uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%

    uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%

    uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%
44 uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L33-L44

```solidity

file: V3Oracle.sol

25 uint16 public constant MIN_PRICE_DIFFERENCE = 200; //2%

    uint256 private constant Q96 = 2 ** 96;
28    uint256 private constant Q128 = 2 ** 128;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L25-L28

```solidity

file: InterestRateModel.sol

12  uint256 private constant Q96 = 2 ** 96;
    uint256 public constant YEAR_SECS = 31557600; // taking into account leap years

    uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10; // 10%
16    uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L12

```solidity

file: automators/Automator.sol

20  uint256 internal constant Q64 = 2 ** 64;
    uint256 internal constant Q96 = 2 ** 96;

    uint32 public constant MIN_TWAP_SECONDS = 60; // 1 minute
24    uint32 public constant MAX_TWAP_TICK_DIFFERENCE = 200; // 2%
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L20-L24

## [G-16] Empty Blocks Should Be Removed Or Emit Something
The code should be refactored such that they no longer exist, or the block should do something useful, such as emitting an event or reverting. If the contract is meant to be extended, the contract should be abstract and the function signatures be added without any default implementation. If the block is an empty if-statement block to avoid doing subsequent checks in the else-if/else conditions, the else-if/else conditions should be nested under the negation of the if-statement, because they involve different classes of checks, which may lead to the introduction of errors when the code is later modified (if(x){}else if(y){…}else{…} => if(!x){if(y){…}else{…}})

```solidity

file: automators/AutoExit.sol

41 Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L41

```solidity

file: transformers/AutoCompound.sol#

43 Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, address(0), address(0)) {}
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L43

```solidity

file: transformers/AutoRange.sol

33  Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, _zeroxRouter, _universalRouter) {}
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L33

## [G-17] Consider using OZ EnumerateSet in place of nested mappings
Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).
A possible optimization involves manually concatenating the keys followed by a single hash operation and an sstore. However, this technique introduces the risk of storage collision, especially when there are other nested hash maps in the contract that use the same key types. Because Solidity is unaware of the number and structure of nested hash maps in a contract, it follows a conservative approach in computing the storage slot to avoid possible collisions.
OpenZeppelin's EnumerableSet provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios.

```solidity

file: V3Vault.sol

164  mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L164

```solidity

file: transformers/AutoCompound.sol#

45 mapping(uint256 => mapping(address => uint256)) public positionBalances;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L45

## [G-18] Multiple address/ID mappings can be combined into a single mapping of an address/ID to a struct, where appropriate
Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (20000 gas) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save ~42 gas per access due to not having to recalculate the key’s keccak256 hash (Gkeccak256 - 30 gas) and that calculation’s associated stack operations.

```solidity

file: V3Vault.sol#

115  mapping(address => TokenConfig) public tokenConfigs;

154  mapping(uint256 => Loan) public loans; // tokenID -> loan mapping

157     mapping(address => uint256[]) private ownedTokens;
        mapping(uint256 => uint256) private ownedTokensIndex; 
159    mapping(uint256 => address) private tokenOwner; 

163     mapping(address => bool) public transformerAllowList;
164   mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L115
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L154
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L157-L159
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L163-L164

```solidity

file: V3Oracle.sol

56  mapping(address => TokenConfig) public feedConfigs;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L56

```solidity

file: automators/AutoExit.sol

60    mapping(uint256 => PositionConfig) public positionConfigs;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L60

```solidity

file: utomators/Automator.sol

34  mapping(address => bool) public operators;
35 mapping(address => bool) public vaults;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L34-L35

```solidity

file: transformers/AutoCompound.sol

45  mapping(uint256 => mapping(address => uint256)) public positionBalances;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L45

```solidity

file: transformers/AutoRange.sol

50  mapping(uint256 => PositionConfig) public positionConfigs;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L50


## [G-19] Use nested if and, avoid multiple check combinations
Using nested is cheaper than using && multiple check combinations. There are more advantages, such as easier to read code and better coverage reports.

```solidity

file: V3Vault.sol

515  if (loanOwner != msg.sender && !transformApprovals[loanOwner][tokenId][msg.sender]) 

561   if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) 

814  if (msg.sender != emergencyAdmin && msg.sender != owner()) 

1229   && _convertToAssets(tokenConfigs[token0].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)

1237   && _convertToAssets(tokenConfigs[token1].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
``` 
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L515
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L561
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L814
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1229
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1237

```solidity

file: V3Oracle.sol

227  if (!(token0 == token && token1 == referenceToken || token0 == referenceToken && token1 == token)) 

250  if (msg.sender != emergencyAdmin && msg.sender != owner()) 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L227
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L250

```solidity

file: automators/AutoExit.sol

112 if (
            config.onlyFees && params.rewardX64 > config.maxRewardX64
   || !config.onlyFees && params.rewardX64 > config.maxRewardX64

135  if (config.token0TriggerTick <= state.tick && state.tick < config.token1TriggerTick) {
            revert NotReady();
        }
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L112
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L135

```solidity

file: automators/Automator.sol

172  if (twapOk) {
            return twapTick - currentTick >= -int16(maxDifference) && twapTick - currentTick <= int16(maxDifference);

219 if (address(weth) == address(token) && unwrap)             
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L172
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L219

```solidity

file: transformers/AutoCompound.sol

102   if (!operators[msg.sender] && !vaults[msg.sender])

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L102


```solidity

file: transformers/AutoRange.sol

112   if (!operators[msg.sender] && !vaults[msg.sender]) 

122  if (
            config.onlyFees && params.rewardX64 > config.maxRewardX64
                || !config.onlyFees && params.rewardX64 > config.maxRewardX64

149 if (params.swap0To1 && params.amountIn > state.amount0 || !params.swap0To1 && params.amountIn > state.amount1) {
            revert SwapAmountTooLarge();
        }                

174 if (
                baseTick + config.lowerTickDelta == state.tickLower
                    && baseTick + config.upperTickDelta == state.tickUpper
            )         
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L112
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L122
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L149
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L174

```solidity

file: transformers/LeverageTransformer.sol

93   if (token != token0 && token != token1 && amount > 0) {
            SafeERC20.safeTransfer(IERC20(token), params.recipient, amount);
        }

146   if (params.amountIn0 > 0 && token != token0) 

155 if (params.amountIn1 > 0 && token != token1) 

169   if (amount0 > 0 && token != token0) {
           
        }
172        if (amount1 > 0 && token != token1) 

342  if (targetAmount != 0 && instructions.targetToken != address(0)) 

696  if (
            amountOther > amountAddedOther && address(otherToken) != address(0) && token0 != otherToken
                && token1 != otherToken
        )

865  if (address(weth) == address(token) && unwrap)
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L93
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L146
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L155
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol#L169-L172
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L342
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L696
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L865

```solidity

file: utils/Swapper.sol

77   if (params.amountIn != 0 && params.swapData.length != 0 && address(params.tokenOut) != address(0))

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L77

## [G‑20] Using bools for storage incurs overhead
    // Booleans are more expensive than uint256 or any type that takes up a full
    // word because each write operation emits an extra SLOAD to first read the
    // slot's contents, replace the bits taken up by the boolean, and then write
    // back. This is the compiler's defense against contract upgrades and
    // pointer aliasing, and it cannot be disabled.

```solidity

file: V3Vault.sol#

115  mapping(address => TokenConfig) public tokenConfigs;

154  mapping(uint256 => Loan) public loans; // tokenID -> loan mapping

157     mapping(address => uint256[]) private ownedTokens;
        mapping(uint256 => uint256) private ownedTokensIndex; 
159    mapping(uint256 => address) private tokenOwner; 

163     mapping(address => bool) public transformerAllowList;
164   mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L115
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L154
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L157-L159
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L163-L164

```solidity

file: V3Oracle.sol

56  mapping(address => TokenConfig) public feedConfigs;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L56

```solidity

file: automators/AutoExit.sol

60    mapping(uint256 => PositionConfig) public positionConfigs;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L60

```solidity

file: utomators/Automator.sol

34  mapping(address => bool) public operators;
35 mapping(address => bool) public vaults;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L34-L35

```solidity

file: transformers/AutoCompound.sol

45  mapping(uint256 => mapping(address => uint256)) public positionBalances;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L45

```solidity

file: transformers/AutoRange.sol

50  mapping(uint256 => PositionConfig) public positionConfigs;

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L50


## [G-21] Use assembly to emit events
We can use assembly to emit events efficiently by utilizing `scratch space` and the `free memory pointer`. This will allow us to potentially avoid memory expansion costs. Note: In order to do this optimization safely, we will need to cache and restore the free memory pointer.

```solidity

file: V3Vault.sol

449  emit Add(tokenId, owner, 0);

564    emit Add(tokenId, owner, oldTokenId);

489  emit ApprovedTransform(tokenId, msg.sender, target, isActive);

601  emit Borrow(tokenId, owner, assets, shares);

645  emit WithdrawCollateral(params.tokenId, owner, params.recipient, params.liquidity, amount0, amount1);

746  emit Liquidate(

782  emit WithdrawReserves(amount, receiver);  

798   emit SetTransformer(transformer, active);

830  emit SetLimits(
            _minLoanSize, _globalLendLimit, _globalDebtLimit, _dailyLendIncreaseLimitMin, _dailyDebtIncreaseLimitMin
        );

849  emit SetReserveProtectionFactor(_reserveProtectionFactorX32);

865  emit SetTokenConfig(token, collateralFactorX32, collateralValueLimitFactorX32);

916  emit Deposit(msg.sender, receiver, assets, shares);

951    emit Withdraw(msg.sender, receiver, owner, assets, shares);

1013  emit Repay(tokenId, msg.sender, owner, assets, shares);

1084  emit Remove(tokenId, owner);

1139    emit ExchangeRateUpdate(newDebtExchangeRateX96, newLendExchangeRateX96);

1160   emit ExchangeRateUpdate(newDebtExchangeRateX96, newLendExchangeRateX96);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L449
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L464
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L489
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L601
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L645
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L746
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L782
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L798
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L830
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L849
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L865
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L916
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L951
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1013
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1084
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1139
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1160

```solidity

file: V3Oracle.sol

190  emit SetMaxPoolPriceDifference(_maxPoolPriceDifference);

242 emit TokenConfigUpdated(token, config);
243 emit OracleModeUpdated(token, mode);

260  emit OracleModeUpdated(token, mode);

267   emit SetEmergencyAdmin(admin);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L190
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L242-L243
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L260
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L267

```solidity

file: InterestRateModel.sol

100    emit SetValues(baseRatePerYearX96, multiplierPerYearX96, jumpMultiplierPerYearX96, _kinkX96);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L100

```solidity

file: automators/AutoExit.sol

208     emit PositionConfigured(params.tokenId, false, false, false, 0, 0, 0, 0, false, 0);

211    emit Executed(
            params.tokenId, msg.sender, state.isSwap, state.amount0, state.amount1, state.token0, state.token1
        );

232  emit PositionConfigured(        
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L208
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L211
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L232
```solidity

file: automators/Automator.sol

59  emit WithdrawerChanged(_withdrawer);

70   emit OperatorChanged(_operator, _active);

80  emit VaultChanged(_vault, _active);

94   emit TWAPConfigChanged(_TWAPSeconds, _maxTWAPTickDifference);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L59
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L70
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L80
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L94


```solidity

file: transformers/AutoCompound.sol

183    emit AutoCompounded(

246  emit RewardUpdated(msg.sender, _totalRewardX64);

251   emit BalanceAdded(tokenId, token, amount);

269    emit BalanceAdded(tokenId, token, amount - currentBalance);
            
261     emit BalanceRemoved(tokenId, token, currentBalance - amount);

271   emit BalanceRemoved(tokenId, token, amount);
        
272    emit BalanceWithdrawn(tokenId, token, to, amount);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L183
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L246
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L251
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L259-L261 
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L271-L272

```solidity

file: transformers/AutoRange.sol

252    emit PositionConfigured(

266  emit PositionConfigured(params.tokenId, 0, 0, 0, 0, 0, 0, false, 0);

267   emit RangeChanged(params.tokenId, state.newTokenId);

286  emit PositionConfigured(
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L252
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L266-L267 
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L286

```solidity

file: transformers/V3Utils.sol

218  emit CompoundFees(tokenId, liquidity, amount0, amount1);

303 emit ChangeRange(tokenId, newTokenId);

248  emit WithdrawAndCollectAndSwap(tokenId, instructions.targetToken, targetAmount);

729  emit SwapAndMint(tokenId, liquidity, added0, added1);

773  emit SwapAndIncreaseLiquidity(params.tokenId, liquidity, added0, added1);
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L218
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L303
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L348
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L729
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L773

```solidity

file: utils/Swapper.sol

116   emit Swap(address(params.tokenIn), address(params.tokenOut), amountInDelta, amountOutDelta);

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L116

## [G-22] Superfluous event fields
`block.timestamp` and `block.number` are added to event information by default so adding them manually wastes gas

```solidity

file: V3Vault.sol

1066  INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp)

1155   if (block.timestamp > lastExchangeRateUpdate) 

1159  lastExchangeRateUpdate = block.timestamp;

1188   + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;

1190   + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;

1248    uint256 time = block.timestamp / 1 days;

1260 uint256 time = block.timestamp / 1 days;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1066
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1155
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1159
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1188
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1190
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1248
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1260

```solidity

file: V3Oracle.sol

338   if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0) 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L338


```solidity

file: transformers/AutoCompound.sol#

165 params.tokenId, state.maxAddAmount0, state.maxAddAmount1, 0, 0, block.timestamp
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L165

## [G‑23] >= costs less gas than >
The compiler uses opcodes GT and ISZERO for solidity code that uses >, but only requires LT for >=, which saves 3 gas

```solidity

file: V3Vault.sol

304  if (value >= globalLendLimit)

443 if (data.length > 0) 

505    if (transformedTokenId > 0) 

552   transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];

574  if (assets > dailyDebtIncreaseLimitLeft)

615     if (transformedTokenId > 0) 

687  if (transformedTokenId > 0) 

712 if (state.reserveCost > 0) 

717  if (params.permitData.length > 0) 

771  uint256 unprotected = reserves > protected ? reserves - protected : 0;
772 uint256 available = balance > unprotected ? unprotected : balance;
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L304
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L443
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L505
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L552
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L574
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L615
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L687
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L712
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L717
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L771-L772 

```solidity

file: V3Oracle.so

143  if (differenceX10000 >= maxDifferenceX10000) 

431    if (state.liquidity > 0)
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L143
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L431

```solidity

file: InterestRateModel.sol

89  baseRatePerYearX96 > MAX_BASE_RATE_X96 || multiplierPerYearX96 > MAX_MULTIPLIER_X96
                || jumpMultiplierPerYearX96 > MAX_MULTIPLIER_X96

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L89

```solidity

file: automators/AutoExit.sol

113  config.onlyFees && params.rewardX64 > config.maxRewardX64
                || !config.onlyFees && params.rewardX64 > config.maxRewardX64


199  if (state.amount0 > 0) 

202   if (state.amount1 > 0) 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L113
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L199
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L202

```solidity

file: automators/Automator.sol

91   if (_maxTWAPTickDifference > MAX_TWAP_TICK_DIFFERENCE) 

113 if (balance > 0)

129 if (balance > 0)

200   if (liquidity > 0) 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L91
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L113
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L129
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L200


```solidity

file: transformers/AutoCompound.sol


123 if (state.amount0 > 0 || state.amount1 > 0) 

127 if (amountIn > 0) 

133  if (tSecs > 0) 

140  if (amountIn > 0)

160 if (state.maxAddAmount0 > 0 || state.maxAddAmount1 > 0) 

212    if (balance0 > 0) 

216     uint256 balance1 = positionBalances[tokenId][token1];
        if (balance1 > 0) 

258  if (amount > currentBalance) 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L123
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L127
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L133
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L140
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L160
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L212
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L216
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L258

## [G-24] Use assembly to check for address(0) 

```solidity

file: V3Vault.sol

537  nonfungiblePositionManager.approve(address(0), tokenId);

791 transformer == address(0) || transformer == address(this) || transformer == asset
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L537
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L791

```solidity

file: V3Oracle.sol

236  feed, maxFeedAge, feedDecimals, tokenDecimals, IUniswapV3Pool(address(0)), false, 0, Mode.CHAINLINK, 0


```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L236

```solidity

file: automators/Automator.sol#

236  if (vault != address(0)) 

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L236

```solidity

file: transformers/AutoCompound.sol

43 Automator(_npm, _operator, _withdrawer, _TWAPSeconds, _maxTWAPTickDifference, address(0), address(0))


```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L43

```solidity

file: transformers/V3Utils.sol

202   IERC20(address(0)),

288  IERC20(address(0)),

342   if (targetAmount != 0 && instructions.targetToken != address(0)) 

406    params.tokenIn, IERC20(address(0)), IERC20(address(0)), params.amountIn, 0, 0, pbtf, signature

409 _prepareAddApproved(params.tokenIn, IERC20(address(0)), IERC20(address(0)), params.amountIn, 0, 0);

697  amountOther > amountAddedOther && address(otherToken) != address(0) && token0 != otherToken

805 else if (address(params.swapSourceToken) != address(0)) 
```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L202
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L288
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L342
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L406
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L409
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L697
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol#L805

```solidity

file: utils/Swapper.sol

77  if (params.amountIn != 0 && params.swapData.length != 0 && address(params.tokenOut) != address(0)) 

```
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L77
