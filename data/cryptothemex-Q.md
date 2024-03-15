### [L-01]<a name="l-01"></a> Local variable shadowing

Shadowing of other variables using local variables.  **Recom** Rename the local variables that shadow another component.

*There are 21 instance(s) of this issue:*

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault._repay(uint256,uint256,bool,bytes).owner (L#1001) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
1001:         address owner = tokenOwner[tokenId];
```

*GitHub* : [1001-1001](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1001-L1001)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault._cleanupLoan(uint256,uint256,uint256,address).owner (L#1077) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
1077:     function _cleanupLoan(uint256 tokenId, uint256 debtExchangeRateX96, uint256 lendExchangeRateX96, address owner)
```

*GitHub* : [1077-1077](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1077-L1077)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.transform(uint256,address,bytes).owner (L#531) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 531:         address owner = nonfungiblePositionManager.ownerOf(tokenId);
```

*GitHub* : [531-531](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L531-L531)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.loanCount(address).owner (L#264) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 264:     function loanCount(address owner) external view override returns (uint256) {
```

*GitHub* : [264-264](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L264-L264)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.withdraw(uint256,address,address).owner (L#372) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 372:     function withdraw(uint256 assets, address receiver, address owner) external override returns (uint256) {
```

*GitHub* : [372-372](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L372-L372)

```solidity
File: src/automators/AutoExit.sol

/// @audit ******************* Issue Detail *******************
AutoExit.configToken(uint256,AutoExit.PositionConfig).owner (L#219) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 219:         address owner = nonfungiblePositionManager.ownerOf(tokenId);
```

*GitHub* : [219-219](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L219-L219)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.liquidate(IVault.LiquidateParams).owner (L#741) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 741:         address owner = tokenOwner[params.tokenId];
```

*GitHub* : [741-741](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L741-L741)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.constructor(string,string,address,INonfungiblePositionManager,IInterestRateModel,IV3Oracle,IPermit2).symbol (L#171) shadows:
	- ERC20.symbol() (L#70-72) (function)
	- IERC20Metadata.symbol() (L#22) (function)

/// @audit ****************** Affected Code *******************
 171:         string memory symbol,
```

*GitHub* : [171-171](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L171-L171)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.loanAtIndex(address,uint256).owner (L#271) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 271:     function loanAtIndex(address owner, uint256 index) external view override returns (uint256) {
```

*GitHub* : [271-271](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L271-L271)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.borrow(uint256,uint256).owner (L#595) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 595:         address owner = tokenOwner[tokenId];
```

*GitHub* : [595-595](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L595-L595)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.createWithPermit(uint256,address,address,uint256,uint8,bytes32,bytes32).owner (L#412) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 412:         address owner,
```

*GitHub* : [412-412](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L412-L412)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.maxRedeem(address).owner (L#329) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 329:     function maxRedeem(address owner) external view override returns (uint256) {
```

*GitHub* : [329-329](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L329-L329)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit ******************* Issue Detail *******************
AutoCompound.withdrawLeftoverBalances(uint256,address).owner (L#201) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 201:         address owner = nonfungiblePositionManager.ownerOf(tokenId);
```

*GitHub* : [201-201](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L201-L201)

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Automator._validateOwner(uint256,address).owner (L#230) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 230:     function _validateOwner(uint256 tokenId, address vault) internal returns (address owner) {
```

*GitHub* : [230-230](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L230-L230)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.onERC721Received(address,address,uint256,bytes).owner (L#442) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 442:             address owner = from;
```

*GitHub* : [442-442](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L442-L442)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.decreaseLiquidityAndCollect(IVault.DecreaseLiquidityAndCollectParams).owner (L#619) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 619:         address owner = tokenOwner[params.tokenId];
```

*GitHub* : [619-619](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L619-L619)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.redeem(uint256,address,address).owner (L#378) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 378:     function redeem(uint256 shares, address receiver, address owner) external override returns (uint256) {
```

*GitHub* : [378-378](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L378-L378)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.constructor(string,string,address,INonfungiblePositionManager,IInterestRateModel,IV3Oracle,IPermit2).name (L#170) shadows:
	- ERC20.name() (L#62-64) (function)
	- IERC20Metadata.name() (L#17) (function)

/// @audit ****************** Affected Code *******************
 170:         string memory name,
```

*GitHub* : [170-170](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L170-L170)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault._withdraw(address,address,uint256,bool).owner (L#920) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 920:     function _withdraw(address receiver, address owner, uint256 amount, bool isShare)
```

*GitHub* : [920-920](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L920-L920)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.ownerOf(uint256).owner (L#258) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 258:     function ownerOf(uint256 tokenId) external view override returns (address owner) {
```

*GitHub* : [258-258](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L258-L258)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault.maxWithdraw(address).owner (L#323) shadows:
	- Ownable.owner() (L#43-45) (function)

/// @audit ****************** Affected Code *******************
 323:     function maxWithdraw(address owner) external view override returns (uint256) {
```

*GitHub* : [323-323](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L323-L323)

### [L-02]<a name="l-02"></a> Calls inside a loop

Calls inside a loop might lead to a denial-of-service attack.  **Recom** Favor [pull over push](https://github.com/ethereum/wiki/wiki/Safety#favor-pull-over-push-for-external-calls) strategy for external calls.

*There are 1 instance(s) of this issue:*

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Automator.withdrawBalances(address[],address) (L#104-117) has external calls inside a loop:
	- balance = IERC20(tokens[i]).balanceOf(address(this)) (L#112)

/// @audit ************** Possible Issue Line(s) **************
	L#112,  

/// @audit ****************** Affected Code *******************
 104:     function withdrawBalances(address[] calldata tokens, address to) external virtual {
 105:         if (msg.sender != withdrawer) {
 106:             revert Unauthorized();
 107:         }
 108: 
 109:         uint256 i;
 110:         uint256 count = tokens.length;
 111:         for (; i < count; ++i) {
 112:             uint256 balance = IERC20(tokens[i]).balanceOf(address(this));
 113:             if (balance > 0) {
 114:                 _transferToken(to, IERC20(tokens[i]), balance, true);
 115:             }
 116:         }
 117:     }
```

*GitHub* : [104-117](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L104-L117)

### [L-03]<a name="l-03"></a> Benign reentrancy vulnerabilities

Possible benign reentrancy vulnerabilities (exploitation would have the same effect as two consecutive calls.)  **Recom** Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

*There are 4 instance(s) of this issue:*

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (benign) in V3Vault._withdraw(address,address,uint256,bool) (L#920-952):
	External calls:
	- SafeERC20.safeTransfer(IERC20(asset),receiver,assets) (L#946)
	State variables written after the call(s):
	- dailyLendIncreaseLimitLeft += assets (L#949)

/// @audit ************** Possible Issue Line(s) **************
	L#946,  L#949,  

/// @audit ****************** Affected Code *******************
 920:     function _withdraw(address receiver, address owner, uint256 amount, bool isShare)
 921:         internal
 922:         returns (uint256 assets, uint256 shares)
 923:     {
 924:         (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
 925: 
 926:         if (isShare) {
 927:             shares = amount;
 928:             assets = _convertToAssets(amount, newLendExchangeRateX96, Math.Rounding.Down);
 929:         } else {
 930:             assets = amount;
 931:             shares = _convertToShares(amount, newLendExchangeRateX96, Math.Rounding.Up);
 932:         }
 933: 
 934:         // if caller has allowance for owners shares - may call withdraw
 935:         if (msg.sender != owner) {
 936:             _spendAllowance(owner, msg.sender, shares);
 937:         }
 938: 
 939:         (, uint256 available,) = _getAvailableBalance(newDebtExchangeRateX96, newLendExchangeRateX96);
 940:         if (available < assets) {
 941:             revert InsufficientLiquidity();
 942:         }
 943: 
 944:         // fails if not enough shares
 945:         _burn(owner, shares);
 946:         SafeERC20.safeTransfer(IERC20(asset), receiver, assets);
 947: 
 948:         // when amounts are withdrawn - they may be deposited again
 949:         dailyLendIncreaseLimitLeft += assets;
 950: 
 951:         emit Withdraw(msg.sender, receiver, owner, assets, shares);
 952:     }
```

*GitHub* : [920-952](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L920-L952)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (benign) in V3Vault._deposit(address,uint256,bool,bytes) (L#877-917):
	External calls:
	- permit2.permitTransferFrom(permit,ISignatureTransfer.SignatureTransferDetails(address(this),assets),msg.sender,signature) (L#896-898)
	- SafeERC20.safeTransferFrom(IERC20(asset),msg.sender,address(this),assets) (L#901)
	State variables written after the call(s):
	- _mint(receiver,shares) (L#904)
		- _balances[account] += amount (L#267)
	- dailyLendIncreaseLimitLeft -= assets (L#913)

/// @audit ************** Possible Issue Line(s) **************
	L#896-898,  L#901,  L#904,  L#913,  

/// @audit ****************** Affected Code *******************
 877:     function _deposit(address receiver, uint256 amount, bool isShare, bytes memory permitData)
 878:         internal
 879:         returns (uint256 assets, uint256 shares)
 880:     {
 881:         (, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
 882: 
 883:         _resetDailyLendIncreaseLimit(newLendExchangeRateX96, false);
 884: 
 885:         if (isShare) {
 886:             shares = amount;
 887:             assets = _convertToAssets(shares, newLendExchangeRateX96, Math.Rounding.Up);
 888:         } else {
 889:             assets = amount;
 890:             shares = _convertToShares(assets, newLendExchangeRateX96, Math.Rounding.Down);
 891:         }
 892: 
 893:         if (permitData.length > 0) {
 894:             (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
 895:                 abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
 896:             permit2.permitTransferFrom(
 897:                 permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
 898:             );
 899:         } else {
 900:             // fails if not enough token approved
 901:             SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
 902:         }
 903: 
 904:         _mint(receiver, shares);
 905: 
 906:         if (totalSupply() > globalLendLimit) {
 907:             revert GlobalLendLimit();
 908:         }
 909: 
 910:         if (assets > dailyLendIncreaseLimitLeft) {
 911:             revert DailyLendIncreaseLimit();
 912:         } else {
 913:             dailyLendIncreaseLimitLeft -= assets;
 914:         }
 915: 
 916:         emit Deposit(msg.sender, receiver, assets, shares);
 917:     }
```

*GitHub* : [877-917](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L877-L917)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (benign) in V3Vault._repay(uint256,uint256,bool,bytes) (L#954-1014):
	External calls:
	- permit2.permitTransferFrom(permit,ISignatureTransfer.SignatureTransferDetails(address(this),assets),msg.sender,signature) (L#981-983)
	- SafeERC20.safeTransferFrom(IERC20(asset),msg.sender,address(this),assets) (L#986)
	State variables written after the call(s):
	- dailyDebtIncreaseLimitLeft += assets (L#995)
	- _updateAndCheckCollateral(tokenId,newDebtExchangeRateX96,newLendExchangeRateX96,loanDebtShares + shares,loanDebtShares) (L#997-999)
		- tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares) (L#1217)
		- tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares) (L#1218)
		- tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares) (L#1220)
		- tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares) (L#1221)

/// @audit ************** Possible Issue Line(s) **************
	L#981-983,  L#986,  L#995,  L#997-999,  L#1217,  L#1218,  L#1220,  L#1221,  

/// @audit ****************** Affected Code *******************
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
 990:         uint256 loanDebtShares = loan.debtShares - shares;
 991:         loan.debtShares = loanDebtShares;
 992:         debtSharesTotal -= shares;
 993: 
 994:         // when amounts are repayed - they maybe borrowed again
 995:         dailyDebtIncreaseLimitLeft += assets;
 996: 
 997:         _updateAndCheckCollateral(
 998:             tokenId, newDebtExchangeRateX96, newLendExchangeRateX96, loanDebtShares + shares, loanDebtShares
 999:         );
1000: 
1001:         address owner = tokenOwner[tokenId];
1002: 
1003:         // if fully repayed
1004:         if (currentShares == shares) {
1005:             _cleanupLoan(tokenId, newDebtExchangeRateX96, newLendExchangeRateX96, owner);
1006:         } else {
1007:             // if resulting loan is too small - revert
1008:             if (_convertToAssets(loanDebtShares, newDebtExchangeRateX96, Math.Rounding.Up) < minLoanSize) {
1009:                 revert MinLoanSize();
1010:             }
1011:         }
1012: 
1013:         emit Repay(tokenId, msg.sender, owner, assets, shares);
1014:     }
1217:                 tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1218:                 tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1220:                 tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
1221:                 tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
```

*GitHub* : [954-1014](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L954-L1014)

```solidity
File: src/transformers/AutoRange.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (benign) in AutoRange.configToken(uint256,address,AutoRange.PositionConfig) (L#276-297):
	External calls:
	- _validateOwner(tokenId,vault) (L#277)
		- owner = IVault(vault).ownerOf(tokenId) (L#240)
	State variables written after the call(s):
	- positionConfigs[tokenId] = config (L#284)

/// @audit ************** Possible Issue Line(s) **************
	L#277,  L#284,  

/// @audit ****************** Affected Code *******************
 276:     function configToken(uint256 tokenId, address vault, PositionConfig calldata config) external {
 277:         _validateOwner(tokenId, vault);
 278: 
 279:         // lower tick must be always below or equal to upper tick - if they are equal - range adjustment is deactivated
 280:         if (config.lowerTickDelta > config.upperTickDelta) {
 281:             revert InvalidConfig();
 282:         }
 283: 
 284:         positionConfigs[tokenId] = config;
 285: 
 286:         emit PositionConfigured(
 287:             tokenId,
 288:             config.lowerTickLimit,
 289:             config.upperTickLimit,
 290:             config.lowerTickDelta,
 291:             config.upperTickDelta,
 292:             config.token0SlippageX64,
 293:             config.token1SlippageX64,
 294:             config.onlyFees,
 295:             config.maxRewardX64
 296:         );
 297:     }
```

*GitHub* : [276-297](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L276-L297)

### [L-04]<a name="l-04"></a> Reentrancy vulnerabilities (events)

Possible Reentrancy vulnerabilities leading to out-of-order Events.  **Recom** Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

*There are 23 instance(s) of this issue:*

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Utils.execute(uint256,V3Utils.Instructions) (L#115-352):
	External calls:
	- (amount0,amount1) = _decreaseLiquidity(tokenId,instructions.liquidity,instructions.deadline,instructions.amountRemoveMin0,instructions.amountRemoveMin1) (L#121-127)
		- (amount0,amount1) = nonfungiblePositionManager.decreaseLiquidity(INonfungiblePositionManager.DecreaseLiquidityParams(tokenId,liquidity,token0Min,token1Min,deadline)) (L#885-887)
	- (newTokenId,None,None,None) = _swapAndMint(SwapAndMintParams(IERC20(token0),IERC20(token1),instructions.fee,instructions.tickLower,instructions.tickUpper,amount0,amount1,instructions.recipient,instructions.recipientNFT,instructions.deadline,IERC20(token0),0,0,,instructions.amountIn0,instructions.amountOut0Min,instructions.swapData0,instructions.amountAddMin0,instructions.amountAddMin1,instructions.swapAndMintReturnData,),instructions.unwrap) (L#248-273)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- weth.withdraw(amount) (L#866)
		- (sent) = to.call{value: amount}() (L#867)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- (tokenId,liquidity,added0,added1) = nonfungiblePositionManager.mint(mintParams) (L#726)
		- nonfungiblePositionManager.safeTransferFrom(address(this),params.recipientNFT,tokenId,params.returnData) (L#727)
		- SafeERC20.safeTransfer(token,to,amount) (L#872)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
		- SafeERC20.safeApprove(params.token0,address(nonfungiblePositionManager),0) (L#831)
		- SafeERC20.safeApprove(params.token0,address(nonfungiblePositionManager),total0) (L#832)
		- SafeERC20.safeApprove(params.token1,address(nonfungiblePositionManager),0) (L#835)
		- SafeERC20.safeApprove(params.token1,address(nonfungiblePositionManager),total1) (L#836)
	- (amount0,amount1) = _collectFees(tokenId,IERC20(token0),IERC20(token1),type()(uint128).max,type()(uint128).max) (L#129-139)
		- (amount0,amount1) = nonfungiblePositionManager.collect(INonfungiblePositionManager.CollectParams(tokenId,address(this),collectAmount0,collectAmount1)) (L#898-900)
	- (amount0,amount1) = _collectFees(tokenId,IERC20(token0),IERC20(token1),(amount0 + instructions.feeAmount0).toUint128(),(amount1 + instructions.feeAmount1).toUint128()) (L#129-139)
		- (amount0,amount1) = nonfungiblePositionManager.collect(INonfungiblePositionManager.CollectParams(tokenId,address(this),collectAmount0,collectAmount1)) (L#898-900)
	External calls sending eth:
	- (newTokenId,None,None,None) = _swapAndMint(SwapAndMintParams(IERC20(token0),IERC20(token1),instructions.fee,instructions.tickLower,instructions.tickUpper,amount0,amount1,instructions.recipient,instructions.recipientNFT,instructions.deadline,IERC20(token0),0,0,,instructions.amountIn0,instructions.amountOut0Min,instructions.swapData0,instructions.amountAddMin0,instructions.amountAddMin1,instructions.swapAndMintReturnData,),instructions.unwrap) (L#248-273)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- (sent) = to.call{value: amount}() (L#867)
	Event emitted after the call(s):
	- Swap(address(params.tokenIn),address(params.tokenOut),amountInDelta,amountOutDelta) (L#116)
		- (newTokenId,None,None,None) = _swapAndMint(SwapAndMintParams(IERC20(token0),IERC20(token1),instructions.fee,instructions.tickLower,instructions.tickUpper,amount0,amount1,instructions.recipient,instructions.recipientNFT,instructions.deadline,IERC20(token0),0,0,,instructions.amountIn0,instructions.amountOut0Min,instructions.swapData0,instructions.amountAddMin0,instructions.amountAddMin1,instructions.swapAndMintReturnData,),instructions.unwrap) (L#248-273)
	- SwapAndMint(tokenId,liquidity,added0,added1) (L#729)
		- (newTokenId,None,None,None) = _swapAndMint(SwapAndMintParams(IERC20(token0),IERC20(token1),instructions.fee,instructions.tickLower,instructions.tickUpper,amount0,amount1,instructions.recipient,instructions.recipientNFT,instructions.deadline,IERC20(token0),0,0,,instructions.amountIn0,instructions.amountOut0Min,instructions.swapData0,instructions.amountAddMin0,instructions.amountAddMin1,instructions.swapAndMintReturnData,),instructions.unwrap) (L#248-273)

/// @audit ************** Possible Issue Line(s) **************
	L#121-127,  L#885-887,  L#248-273,  L#866,  L#867,  L#726,  L#727,  L#872,  L#831,  L#832,  L#835,  L#836,  L#129-139,  L#898-900,  L#729,  

/// @audit ****************** Affected Code *******************
 115:     function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {
 116:         (,, address token0, address token1,,,, uint128 liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);
 117: 
 118:         uint256 amount0;
 119:         uint256 amount1;
 120:         if (instructions.liquidity != 0) {
 121:             (amount0, amount1) = _decreaseLiquidity(
 122:                 tokenId,
 123:                 instructions.liquidity,
 124:                 instructions.deadline,
 125:                 instructions.amountRemoveMin0,
 126:                 instructions.amountRemoveMin1
 127:             );
 128:         }
 129:         (amount0, amount1) = _collectFees(
 130:             tokenId,
 131:             IERC20(token0),
 132:             IERC20(token1),
 133:             instructions.feeAmount0 == type(uint128).max
 134:                 ? type(uint128).max
 135:                 : (amount0 + instructions.feeAmount0).toUint128(),
 136:             instructions.feeAmount1 == type(uint128).max
 137:                 ? type(uint128).max
 138:                 : (amount1 + instructions.feeAmount1).toUint128()
 139:         );
 140: 
 141:         // check if enough tokens are available for swaps
 142:         if (amount0 < instructions.amountIn0 || amount1 < instructions.amountIn1) {
 143:             revert AmountError();
 144:         }
 145: 
 146:         if (instructions.whatToDo == WhatToDo.COMPOUND_FEES) {
 147:             if (instructions.targetToken == token0) {
 148:                 (liquidity, amount0, amount1) = _swapAndIncrease(
 149:                     SwapAndIncreaseLiquidityParams(
 150:                         tokenId,
 151:                         amount0,
 152:                         amount1,
 153:                         instructions.recipient,
 154:                         instructions.deadline,
 155:                         IERC20(token1),
 156:                         instructions.amountIn1,
 157:                         instructions.amountOut1Min,
 158:                         instructions.swapData1,
 159:                         0,
 160:                         0,
 161:                         "",
 162:                         instructions.amountAddMin0,
 163:                         instructions.amountAddMin1,
 164:                         ""
 165:                     ),
 166:                     IERC20(token0),
 167:                     IERC20(token1),
 168:                     instructions.unwrap
 169:                 );
 170:             } else if (instructions.targetToken == token1) {
 171:                 (liquidity, amount0, amount1) = _swapAndIncrease(
 172:                     SwapAndIncreaseLiquidityParams(
 173:                         tokenId,
 174:                         amount0,
 175:                         amount1,
 176:                         instructions.recipient,
 177:                         instructions.deadline,
 178:                         IERC20(token0),
 179:                         0,
 180:                         0,
 181:                         "",
 182:                         instructions.amountIn0,
 183:                         instructions.amountOut0Min,
 184:                         instructions.swapData0,
 185:                         instructions.amountAddMin0,
 186:                         instructions.amountAddMin1,
 187:                         ""
 188:                     ),
 189:                     IERC20(token0),
 190:                     IERC20(token1),
 191:                     instructions.unwrap
 192:                 );
 193:             } else {
 194:                 // no swap is done here
 195:                 (liquidity, amount0, amount1) = _swapAndIncrease(
 196:                     SwapAndIncreaseLiquidityParams(
 197:                         tokenId,
 198:                         amount0,
 199:                         amount1,
 200:                         instructions.recipient,
 201:                         instructions.deadline,
 202:                         IERC20(address(0)),
 203:                         0,
 204:                         0,
 205:                         "",
 206:                         0,
 207:                         0,
 208:                         "",
 209:                         instructions.amountAddMin0,
 210:                         instructions.amountAddMin1,
 211:                         ""
 212:                     ),
 213:                     IERC20(token0),
 214:                     IERC20(token1),
 215:                     instructions.unwrap
 216:                 );
 217:             }
 218:             emit CompoundFees(tokenId, liquidity, amount0, amount1);
 219:         } else if (instructions.whatToDo == WhatToDo.CHANGE_RANGE) {
 220:             if (instructions.targetToken == token0) {
 221:                 (newTokenId,,,) = _swapAndMint(
 222:                     SwapAndMintParams(
 223:                         IERC20(token0),
 224:                         IERC20(token1),
 225:                         instructions.fee,
 226:                         instructions.tickLower,
 227:                         instructions.tickUpper,
 228:                         amount0,
 229:                         amount1,
 230:                         instructions.recipient,
 231:                         instructions.recipientNFT,
 232:                         instructions.deadline,
 233:                         IERC20(token1),
 234:                         instructions.amountIn1,
 235:                         instructions.amountOut1Min,
 236:                         instructions.swapData1,
 237:                         0,
 238:                         0,
 239:                         "",
 240:                         instructions.amountAddMin0,
 241:                         instructions.amountAddMin1,
 242:                         instructions.swapAndMintReturnData,
 243:                         ""
 244:                     ),
 245:                     instructions.unwrap
 246:                 );
 247:             } else if (instructions.targetToken == token1) {
 248:                 (newTokenId,,,) = _swapAndMint(
 249:                     SwapAndMintParams(
 250:                         IERC20(token0),
 251:                         IERC20(token1),
 252:                         instructions.fee,
 253:                         instructions.tickLower,
 254:                         instructions.tickUpper,
 255:                         amount0,
 256:                         amount1,
 257:                         instructions.recipient,
 258:                         instructions.recipientNFT,
 259:                         instructions.deadline,
 260:                         IERC20(token0),
 261:                         0,
 262:                         0,
 263:                         "",
 264:                         instructions.amountIn0,
 265:                         instructions.amountOut0Min,
 266:                         instructions.swapData0,
 267:                         instructions.amountAddMin0,
 268:                         instructions.amountAddMin1,
 269:                         instructions.swapAndMintReturnData,
 270:                         ""
 271:                     ),
 272:                     instructions.unwrap
 273:                 );
 274:             } else {
 275:                 // no swap is done here
 276:                 (newTokenId,,,) = _swapAndMint(
 277:                     SwapAndMintParams(
 278:                         IERC20(token0),
 279:                         IERC20(token1),
 280:                         instructions.fee,
 281:                         instructions.tickLower,
 282:                         instructions.tickUpper,
 283:                         amount0,
 284:                         amount1,
 285:                         instructions.recipient,
 286:                         instructions.recipientNFT,
 287:                         instructions.deadline,
 288:                         IERC20(address(0)),
 289:                         0,
 290:                         0,
 291:                         "",
 292:                         0,
 293:                         0,
 294:                         "",
 295:                         instructions.amountAddMin0,
 296:                         instructions.amountAddMin1,
 297:                         instructions.swapAndMintReturnData,
 298:                         ""
 299:                     ),
 300:                     instructions.unwrap
 301:                 );
 302:             }
 303:             emit ChangeRange(tokenId, newTokenId);
 304:         } else if (instructions.whatToDo == WhatToDo.WITHDRAW_AND_COLLECT_AND_SWAP) {
 305:             uint256 targetAmount;
 306:             if (token0 != instructions.targetToken) {
 307:                 (uint256 amountInDelta, uint256 amountOutDelta) = _routerSwap(
 308:                     Swapper.RouterSwapParams(
 309:                         IERC20(token0),
 310:                         IERC20(instructions.targetToken),
 311:                         amount0,
 312:                         instructions.amountOut0Min,
 313:                         instructions.swapData0
 314:                     )
 315:                 );
 316:                 if (amountInDelta < amount0) {
 317:                     _transferToken(instructions.recipient, IERC20(token0), amount0 - amountInDelta, instructions.unwrap);
 318:                 }
 319:                 targetAmount += amountOutDelta;
 320:             } else {
 321:                 targetAmount += amount0;
 322:             }
 323:             if (token1 != instructions.targetToken) {
 324:                 (uint256 amountInDelta, uint256 amountOutDelta) = _routerSwap(
 325:                     Swapper.RouterSwapParams(
 326:                         IERC20(token1),
 327:                         IERC20(instructions.targetToken),
 328:                         amount1,
 329:                         instructions.amountOut1Min,
 330:                         instructions.swapData1
 331:                     )
 332:                 );
 333:                 if (amountInDelta < amount1) {
 334:                     _transferToken(instructions.recipient, IERC20(token1), amount1 - amountInDelta, instructions.unwrap);
 335:                 }
 336:                 targetAmount += amountOutDelta;
 337:             } else {
 338:                 targetAmount += amount1;
 339:             }
 340: 
 341:             // send complete target amount
 342:             if (targetAmount != 0 && instructions.targetToken != address(0)) {
 343:                 _transferToken(
 344:                     instructions.recipient, IERC20(instructions.targetToken), targetAmount, instructions.unwrap
 345:                 );
 346:             }
 347: 
 348:             emit WithdrawAndCollectAndSwap(tokenId, instructions.targetToken, targetAmount);
 349:         } else {
 350:             revert NotSupportedWhatToDo();
 351:         }
 352:     }
 726:         (tokenId, liquidity, added0, added1) = nonfungiblePositionManager.mint(mintParams);
 727:         nonfungiblePositionManager.safeTransferFrom(address(this), params.recipientNFT, tokenId, params.returnData);
 729:         emit SwapAndMint(tokenId, liquidity, added0, added1);
 831:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), 0);
 832:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), total0);
 835:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), 0);
 836:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), total1);
 866:             weth.withdraw(amount);
 867:             (bool sent,) = to.call{value: amount}("");
 872:             SafeERC20.safeTransfer(token, to, amount);
 885:             (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(
 886:                 INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, token0Min, token1Min, deadline)
 887:             );
 898:         (amount0, amount1) = nonfungiblePositionManager.collect(
 899:             INonfungiblePositionManager.CollectParams(tokenId, address(this), collectAmount0, collectAmount1)
 900:         );
```

*GitHub* : [115-352](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L115-L352)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Utils.executeWithPermit(uint256,V3Utils.Instructions,uint8,bytes32,bytes32) (L#98-110):
	External calls:
	- nonfungiblePositionManager.permit(address(this),tokenId,instructions.deadline,v,r,s) (L#106)
	- execute(tokenId,instructions) (L#107)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (amount0,amount1) = nonfungiblePositionManager.decreaseLiquidity(INonfungiblePositionManager.DecreaseLiquidityParams(tokenId,liquidity,token0Min,token1Min,deadline)) (L#885-887)
		- weth.withdraw(amount) (L#866)
		- (amount0,amount1) = nonfungiblePositionManager.collect(INonfungiblePositionManager.CollectParams(tokenId,address(this),collectAmount0,collectAmount1)) (L#898-900)
		- (sent) = to.call{value: amount}() (L#867)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- (liquidity,added0,added1) = nonfungiblePositionManager.increaseLiquidity(increaseLiquidityParams) (L#771)
		- (tokenId,liquidity,added0,added1) = nonfungiblePositionManager.mint(mintParams) (L#726)
		- nonfungiblePositionManager.safeTransferFrom(address(this),params.recipientNFT,tokenId,params.returnData) (L#727)
		- SafeERC20.safeTransfer(token,to,amount) (L#872)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
		- SafeERC20.safeApprove(params.token0,address(nonfungiblePositionManager),0) (L#831)
		- SafeERC20.safeApprove(params.token0,address(nonfungiblePositionManager),total0) (L#832)
		- SafeERC20.safeApprove(params.token1,address(nonfungiblePositionManager),0) (L#835)
		- SafeERC20.safeApprove(params.token1,address(nonfungiblePositionManager),total1) (L#836)
	External calls sending eth:
	- execute(tokenId,instructions) (L#107)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- (sent) = to.call{value: amount}() (L#867)
	Event emitted after the call(s):
	- ChangeRange(tokenId,newTokenId) (L#303)
		- execute(tokenId,instructions) (L#107)
	- CompoundFees(tokenId,liquidity,amount0,amount1) (L#218)
		- execute(tokenId,instructions) (L#107)
	- Swap(address(params.tokenIn),address(params.tokenOut),amountInDelta,amountOutDelta) (L#116)
		- execute(tokenId,instructions) (L#107)
	- SwapAndIncreaseLiquidity(params.tokenId,liquidity,added0,added1) (L#773)
		- execute(tokenId,instructions) (L#107)
	- SwapAndMint(tokenId,liquidity,added0,added1) (L#729)
		- execute(tokenId,instructions) (L#107)
	- WithdrawAndCollectAndSwap(tokenId,instructions.targetToken,targetAmount) (L#348)
		- execute(tokenId,instructions) (L#107)

/// @audit ************** Possible Issue Line(s) **************
	L#106,  L#107,  L#885-887,  L#866,  L#898-900,  L#867,  L#771,  L#726,  L#727,  L#872,  L#831,  L#832,  L#835,  L#836,  L#303,  L#218,  L#773,  L#729,  L#348,  

/// @audit ****************** Affected Code *******************
  98:     function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)
  99:         public
 100:         returns (uint256 newTokenId)
 101:     {
 102:         if (nonfungiblePositionManager.ownerOf(tokenId) != msg.sender) {
 103:             revert Unauthorized();
 104:         }
 105: 
 106:         nonfungiblePositionManager.permit(address(this), tokenId, instructions.deadline, v, r, s);
 107:         return execute(tokenId, instructions);
 108: 
 109:         // NOTE: previous operator can not be reset as operator set by permit can not change operator - so this operator will stay until reset
 110:     }
 218:             emit CompoundFees(tokenId, liquidity, amount0, amount1);
 303:             emit ChangeRange(tokenId, newTokenId);
 348:             emit WithdrawAndCollectAndSwap(tokenId, instructions.targetToken, targetAmount);
 726:         (tokenId, liquidity, added0, added1) = nonfungiblePositionManager.mint(mintParams);
 727:         nonfungiblePositionManager.safeTransferFrom(address(this), params.recipientNFT, tokenId, params.returnData);
 729:         emit SwapAndMint(tokenId, liquidity, added0, added1);
 771:         (liquidity, added0, added1) = nonfungiblePositionManager.increaseLiquidity(increaseLiquidityParams);
 773:         emit SwapAndIncreaseLiquidity(params.tokenId, liquidity, added0, added1);
 831:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), 0);
 832:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), total0);
 835:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), 0);
 836:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), total1);
 866:             weth.withdraw(amount);
 867:             (bool sent,) = to.call{value: amount}("");
 872:             SafeERC20.safeTransfer(token, to, amount);
 885:             (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(
 886:                 INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, token0Min, token1Min, deadline)
 887:             );
 898:         (amount0, amount1) = nonfungiblePositionManager.collect(
 899:             INonfungiblePositionManager.CollectParams(tokenId, address(this), collectAmount0, collectAmount1)
 900:         );
```

*GitHub* : [98-110](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L98-L110)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Vault._repay(uint256,uint256,bool,bytes) (L#954-1014):
	External calls:
	- permit2.permitTransferFrom(permit,ISignatureTransfer.SignatureTransferDetails(address(this),assets),msg.sender,signature) (L#981-983)
	- SafeERC20.safeTransferFrom(IERC20(asset),msg.sender,address(this),assets) (L#986)
	- _cleanupLoan(tokenId,newDebtExchangeRateX96,newLendExchangeRateX96,owner) (L#1005)
		- nonfungiblePositionManager.safeTransferFrom(address(this),owner,tokenId) (L#1083)
	Event emitted after the call(s):
	- Remove(tokenId,owner) (L#1084)
		- _cleanupLoan(tokenId,newDebtExchangeRateX96,newLendExchangeRateX96,owner) (L#1005)
	- Repay(tokenId,msg.sender,owner,assets,shares) (L#1013)

/// @audit ************** Possible Issue Line(s) **************
	L#981-983,  L#986,  L#1005,  L#1083,  L#1084,  L#1013,  

/// @audit ****************** Affected Code *******************
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
 990:         uint256 loanDebtShares = loan.debtShares - shares;
 991:         loan.debtShares = loanDebtShares;
 992:         debtSharesTotal -= shares;
 993: 
 994:         // when amounts are repayed - they maybe borrowed again
 995:         dailyDebtIncreaseLimitLeft += assets;
 996: 
 997:         _updateAndCheckCollateral(
 998:             tokenId, newDebtExchangeRateX96, newLendExchangeRateX96, loanDebtShares + shares, loanDebtShares
 999:         );
1000: 
1001:         address owner = tokenOwner[tokenId];
1002: 
1003:         // if fully repayed
1004:         if (currentShares == shares) {
1005:             _cleanupLoan(tokenId, newDebtExchangeRateX96, newLendExchangeRateX96, owner);
1006:         } else {
1007:             // if resulting loan is too small - revert
1008:             if (_convertToAssets(loanDebtShares, newDebtExchangeRateX96, Math.Rounding.Up) < minLoanSize) {
1009:                 revert MinLoanSize();
1010:             }
1011:         }
1012: 
1013:         emit Repay(tokenId, msg.sender, owner, assets, shares);
1014:     }
1083:         nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId);
1084:         emit Remove(tokenId, owner);
```

*GitHub* : [954-1014](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L954-L1014)

```solidity
File: src/automators/AutoExit.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in AutoExit.execute(AutoExit.ExecuteParams) (L#100-214):
	External calls:
	- (state.amount0,state.amount1,state.feeAmount0,state.feeAmount1) = _decreaseFullLiquidityAndCollect(params.tokenId,state.liquidity,params.amountRemoveMin0,params.amountRemoveMin1,params.deadline) (L#143-145)
		- (feeAmount0,feeAmount1) = nonfungiblePositionManager.decreaseLiquidity(INonfungiblePositionManager.DecreaseLiquidityParams(tokenId,liquidity,amountRemoveMin0,amountRemoveMin1,deadline)) (L#202-206)
		- (amount0,amount1) = nonfungiblePositionManager.collect(INonfungiblePositionManager.CollectParams(tokenId,address(this),type()(uint128).max,type()(uint128).max)) (L#208-210)
	- (state.amountInDelta,state.amountOutDelta) = _routerSwap(Swapper.RouterSwapParams(IERC20(state.token1),IERC20(state.token0),state.swapAmount,state.amountOutMin,params.swapData)) (L#171-179)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
	External calls sending eth:
	- (state.amountInDelta,state.amountOutDelta) = _routerSwap(Swapper.RouterSwapParams(IERC20(state.token1),IERC20(state.token0),state.swapAmount,state.amountOutMin,params.swapData)) (L#171-179)
		- (success,returndata) = target.call{value: value}(data) (L#135)
	Event emitted after the call(s):
	- Swap(address(params.tokenIn),address(params.tokenOut),amountInDelta,amountOutDelta) (L#116)
		- (state.amountInDelta,state.amountOutDelta) = _routerSwap(Swapper.RouterSwapParams(IERC20(state.token1),IERC20(state.token0),state.swapAmount,state.amountOutMin,params.swapData)) (L#171-179)

/// @audit ************** Possible Issue Line(s) **************
	L#143-145,  L#171-179,  

/// @audit ****************** Affected Code *******************
 100:     function execute(ExecuteParams calldata params) external {
 101:         if (!operators[msg.sender]) {
 102:             revert Unauthorized();
 103:         }
 104: 
 105:         ExecuteState memory state;
 106:         PositionConfig memory config = positionConfigs[params.tokenId];
 107: 
 108:         if (!config.isActive) {
 109:             revert NotConfigured();
 110:         }
 111: 
 112:         if (
 113:             config.onlyFees && params.rewardX64 > config.maxRewardX64
 114:                 || !config.onlyFees && params.rewardX64 > config.maxRewardX64
 115:         ) {
 116:             revert ExceedsMaxReward();
 117:         }
 118: 
 119:         // get position info
 120:         (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
 121:             nonfungiblePositionManager.positions(params.tokenId);
 122: 
 123:         // so can be executed only once
 124:         if (state.liquidity == 0) {
 125:             revert NoLiquidity();
 126:         }
 127:         if (state.liquidity != params.liquidity) {
 128:             revert LiquidityChanged();
 129:         }
 130: 
 131:         state.pool = _getPool(state.token0, state.token1, state.fee);
 132:         (, state.tick,,,,,) = state.pool.slot0();
 133: 
 134:         // not triggered
 135:         if (config.token0TriggerTick <= state.tick && state.tick < config.token1TriggerTick) {
 136:             revert NotReady();
 137:         }
 138: 
 139:         state.isAbove = state.tick >= config.token1TriggerTick;
 140:         state.isSwap = !state.isAbove && config.token0Swap || state.isAbove && config.token1Swap;
 141: 
 142:         // decrease full liquidity for given position - and return fees as well
 143:         (state.amount0, state.amount1, state.feeAmount0, state.feeAmount1) = _decreaseFullLiquidityAndCollect(
 144:             params.tokenId, state.liquidity, params.amountRemoveMin0, params.amountRemoveMin1, params.deadline
 145:         );
 146: 
 147:         // swap to other token
 148:         if (state.isSwap) {
 149:             if (params.swapData.length == 0) {
 150:                 revert MissingSwapData();
 151:             }
 152: 
 153:             // reward is taken before swap - if from fees only
 154:             if (config.onlyFees) {
 155:                 state.amount0 -= state.feeAmount0 * params.rewardX64 / Q64;
 156:                 state.amount1 -= state.feeAmount1 * params.rewardX64 / Q64;
 157:             }
 158: 
 159:             state.swapAmount = state.isAbove ? state.amount1 : state.amount0;
 160: 
 161:             // checks if price in valid oracle range and calculates amountOutMin
 162:             (state.amountOutMin,,,) = _validateSwap(
 163:                 !state.isAbove,
 164:                 state.swapAmount,
 165:                 state.pool,
 166:                 TWAPSeconds,
 167:                 maxTWAPTickDifference,
 168:                 state.isAbove ? config.token1SlippageX64 : config.token0SlippageX64
 169:             );
 170: 
 171:             (state.amountInDelta, state.amountOutDelta) = _routerSwap(
 172:                 Swapper.RouterSwapParams(
 173:                     state.isAbove ? IERC20(state.token1) : IERC20(state.token0),
 174:                     state.isAbove ? IERC20(state.token0) : IERC20(state.token1),
 175:                     state.swapAmount,
 176:                     state.amountOutMin,
 177:                     params.swapData
 178:                 )
 179:             );
 180: 
 181:             state.amount0 = state.isAbove ? state.amount0 + state.amountOutDelta : state.amount0 - state.amountInDelta;
 182:             state.amount1 = state.isAbove ? state.amount1 - state.amountInDelta : state.amount1 + state.amountOutDelta;
 183: 
 184:             // when swap and !onlyFees - protocol reward is removed only from target token (to incentivize optimal swap done by operator)
 185:             if (!config.onlyFees) {
 186:                 if (state.isAbove) {
 187:                     state.amount0 -= state.amount0 * params.rewardX64 / Q64;
 188:                 } else {
 189:                     state.amount1 -= state.amount1 * params.rewardX64 / Q64;
 190:                 }
 191:             }
 192:         } else {
 193:             // reward is taken as configured
 194:             state.amount0 -= (config.onlyFees ? state.feeAmount0 : state.amount0) * params.rewardX64 / Q64;
 195:             state.amount1 -= (config.onlyFees ? state.feeAmount1 : state.amount1) * params.rewardX64 / Q64;
 196:         }
 197: 
 198:         state.owner = nonfungiblePositionManager.ownerOf(params.tokenId);
 199:         if (state.amount0 > 0) {
 200:             _transferToken(state.owner, IERC20(state.token0), state.amount0, true);
 201:         }
 202:         if (state.amount1 > 0) {
 203:             _transferToken(state.owner, IERC20(state.token1), state.amount1, true);
 204:         }
 205: 
 206:         // delete config for position
 207:         delete positionConfigs[params.tokenId];
 208:         emit PositionConfigured(params.tokenId, false, false, false, 0, 0, 0, 0, false, 0);
 209: 
 210:         // log event
 211:         emit Executed(
 212:             params.tokenId, msg.sender, state.isSwap, state.amount0, state.amount1, state.token0, state.token1
 213:         );
 214:     }
```

*GitHub* : [100-214](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L100-L214)

```solidity
File: src/transformers/AutoRange.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in AutoRange.execute(AutoRange.ExecuteParams) (L#111-272):
	External calls:
	- (state.amount0,state.amount1,state.feeAmount0,state.feeAmount1) = _decreaseFullLiquidityAndCollect(params.tokenId,state.liquidity,params.amountRemoveMin0,params.amountRemoveMin1,params.deadline) (L#137-139)
		- (feeAmount0,feeAmount1) = nonfungiblePositionManager.decreaseLiquidity(INonfungiblePositionManager.DecreaseLiquidityParams(tokenId,liquidity,amountRemoveMin0,amountRemoveMin1,deadline)) (L#202-206)
		- (amount0,amount1) = nonfungiblePositionManager.collect(INonfungiblePositionManager.CollectParams(tokenId,address(this),type()(uint128).max,type()(uint128).max)) (L#208-210)
	- SafeERC20.safeApprove(IERC20(state.token0),address(nonfungiblePositionManager),state.maxAddAmount0) (L#213)
	- SafeERC20.safeApprove(IERC20(state.token1),address(nonfungiblePositionManager),state.maxAddAmount1) (L#214)
	- (state.newTokenId,None,state.amountAdded0,state.amountAdded1) = nonfungiblePositionManager.mint(mintParams) (L#217)
	- SafeERC20.safeApprove(IERC20(state.token0),address(nonfungiblePositionManager),0) (L#220)
	- SafeERC20.safeApprove(IERC20(state.token1),address(nonfungiblePositionManager),0) (L#221)
	- state.realOwner = IVault(state.owner).ownerOf(params.tokenId) (L#228)
	- nonfungiblePositionManager.safeTransferFrom(address(this),state.owner,state.newTokenId) (L#232)
	- _transferToken(state.realOwner,IERC20(state.token0),state.amount0 - state.amountAdded0,true) (L#244)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- weth.withdraw(amount) (L#220)
		- (sent) = to.call{value: amount}() (L#221)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeTransfer(token,to,amount) (L#226)
	- _transferToken(state.realOwner,IERC20(state.token1),state.amount1 - state.amountAdded1,true) (L#247)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- weth.withdraw(amount) (L#220)
		- (sent) = to.call{value: amount}() (L#221)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeTransfer(token,to,amount) (L#226)
	- (state.amountInDelta,state.amountOutDelta) = _routerSwap(Swapper.RouterSwapParams(IERC20(state.token0),IERC20(state.token1),params.amountIn,state.amountOutMin,params.swapData)) (L#181-189)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
	- (state.amountInDelta,state.amountOutDelta) = _routerSwap(Swapper.RouterSwapParams(IERC20(state.token1),IERC20(state.token0),params.amountIn,state.amountOutMin,params.swapData)) (L#181-189)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
	External calls sending eth:
	- _transferToken(state.realOwner,IERC20(state.token0),state.amount0 - state.amountAdded0,true) (L#244)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- (sent) = to.call{value: amount}() (L#221)
	- _transferToken(state.realOwner,IERC20(state.token1),state.amount1 - state.amountAdded1,true) (L#247)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- (sent) = to.call{value: amount}() (L#221)
	- (state.amountInDelta,state.amountOutDelta) = _routerSwap(Swapper.RouterSwapParams(IERC20(state.token0),IERC20(state.token1),params.amountIn,state.amountOutMin,params.swapData)) (L#181-189)
		- (success,returndata) = target.call{value: value}(data) (L#135)
	- (state.amountInDelta,state.amountOutDelta) = _routerSwap(Swapper.RouterSwapParams(IERC20(state.token1),IERC20(state.token0),params.amountIn,state.amountOutMin,params.swapData)) (L#181-189)
		- (success,returndata) = target.call{value: value}(data) (L#135)
	Event emitted after the call(s):
	- PositionConfigured(state.newTokenId,config.lowerTickLimit,config.upperTickLimit,config.lowerTickDelta,config.upperTickDelta,config.token0SlippageX64,config.token1SlippageX64,config.onlyFees,config.maxRewardX64) (L#252-262)
	- PositionConfigured(params.tokenId,0,0,0,0,0,0,false,0) (L#266)
	- RangeChanged(params.tokenId,state.newTokenId) (L#268)

/// @audit ************** Possible Issue Line(s) **************
	L#137-139,  L#213,  L#214,  L#217,  L#220,  L#221,  L#228,  L#232,  L#244,  L#247,  L#181-189,  L#252-262,  L#266,  L#268,  

/// @audit ****************** Affected Code *******************
 111:     function execute(ExecuteParams calldata params) external {
 112:         if (!operators[msg.sender] && !vaults[msg.sender]) {
 113:             revert Unauthorized();
 114:         }
 115:         ExecuteState memory state;
 116:         PositionConfig memory config = positionConfigs[params.tokenId];
 117: 
 118:         if (config.lowerTickDelta == config.upperTickDelta) {
 119:             revert NotConfigured();
 120:         }
 121: 
 122:         if (
 123:             config.onlyFees && params.rewardX64 > config.maxRewardX64
 124:                 || !config.onlyFees && params.rewardX64 > config.maxRewardX64
 125:         ) {
 126:             revert ExceedsMaxReward();
 127:         }
 128: 
 129:         // get position info
 130:         (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
 131:             nonfungiblePositionManager.positions(params.tokenId);
 132: 
 133:         if (state.liquidity != params.liquidity) {
 134:             revert LiquidityChanged();
 135:         }
 136: 
 137:         (state.amount0, state.amount1, state.feeAmount0, state.feeAmount1) = _decreaseFullLiquidityAndCollect(
 138:             params.tokenId, state.liquidity, params.amountRemoveMin0, params.amountRemoveMin1, params.deadline
 139:         );
 140: 
 141:         // if only fees reward is removed before adding
 142:         if (config.onlyFees) {
 143:             state.protocolReward0 = state.feeAmount0 * params.rewardX64 / Q64;
 144:             state.protocolReward1 = state.feeAmount1 * params.rewardX64 / Q64;
 145:             state.amount0 -= state.protocolReward0;
 146:             state.amount1 -= state.protocolReward1;
 147:         }
 148: 
 149:         if (params.swap0To1 && params.amountIn > state.amount0 || !params.swap0To1 && params.amountIn > state.amount1) {
 150:             revert SwapAmountTooLarge();
 151:         }
 152: 
 153:         // get pool info
 154:         state.pool = _getPool(state.token0, state.token1, state.fee);
 155: 
 156:         // check oracle for swap
 157:         (state.amountOutMin, state.currentTick,,) = _validateSwap(
 158:             params.swap0To1,
 159:             params.amountIn,
 160:             state.pool,
 161:             TWAPSeconds,
 162:             maxTWAPTickDifference,
 163:             params.swap0To1 ? config.token0SlippageX64 : config.token1SlippageX64
 164:         );
 165: 
 166:         if (
 167:             state.currentTick < state.tickLower - config.lowerTickLimit
 168:                 || state.currentTick >= state.tickUpper + config.upperTickLimit
 169:         ) {
 170:             int24 tickSpacing = _getTickSpacing(state.fee);
 171:             int24 baseTick = state.currentTick - (((state.currentTick % tickSpacing) + tickSpacing) % tickSpacing);
 172: 
 173:             // check if new range same as old range
 174:             if (
 175:                 baseTick + config.lowerTickDelta == state.tickLower
 176:                     && baseTick + config.upperTickDelta == state.tickUpper
 177:             ) {
 178:                 revert SameRange();
 179:             }
 180: 
 181:             (state.amountInDelta, state.amountOutDelta) = _routerSwap(
 182:                 Swapper.RouterSwapParams(
 183:                     params.swap0To1 ? IERC20(state.token0) : IERC20(state.token1),
 184:                     params.swap0To1 ? IERC20(state.token1) : IERC20(state.token0),
 185:                     params.amountIn,
 186:                     state.amountOutMin,
 187:                     params.swapData
 188:                 )
 189:             );
 190: 
 191:             state.amount0 = params.swap0To1 ? state.amount0 - state.amountInDelta : state.amount0 + state.amountOutDelta;
 192:             state.amount1 = params.swap0To1 ? state.amount1 + state.amountOutDelta : state.amount1 - state.amountInDelta;
 193: 
 194:             // max amount to add - removing max potential fees (if config.onlyFees - the have been removed already)
 195:             state.maxAddAmount0 = config.onlyFees ? state.amount0 : state.amount0 * Q64 / (params.rewardX64 + Q64);
 196:             state.maxAddAmount1 = config.onlyFees ? state.amount1 : state.amount1 * Q64 / (params.rewardX64 + Q64);
 197: 
 198:             INonfungiblePositionManager.MintParams memory mintParams = INonfungiblePositionManager.MintParams(
 199:                 address(state.token0),
 200:                 address(state.token1),
 201:                 state.fee,
 202:                 SafeCast.toInt24(baseTick + config.lowerTickDelta), // reverts if out of valid range
 203:                 SafeCast.toInt24(baseTick + config.upperTickDelta), // reverts if out of valid range
 204:                 state.maxAddAmount0,
 205:                 state.maxAddAmount1,
 206:                 0,
 207:                 0,
 208:                 address(this), // is sent to real recipient aftwards
 209:                 params.deadline
 210:             );
 211: 
 212:             // approve npm
 213:             SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), state.maxAddAmount0);
 214:             SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), state.maxAddAmount1);
 215: 
 216:             // mint is done to address(this) first - its not a safemint
 217:             (state.newTokenId,, state.amountAdded0, state.amountAdded1) = nonfungiblePositionManager.mint(mintParams);
 218: 
 219:             // remove remaining approval
 220:             SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), 0);
 221:             SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), 0);
 222: 
 223:             state.owner = nonfungiblePositionManager.ownerOf(params.tokenId);
 224: 
 225:             // get the real owner - if owner is vault - for sending leftover tokens
 226:             state.realOwner = state.owner;
 227:             if (vaults[state.owner]) {
 228:                 state.realOwner = IVault(state.owner).ownerOf(params.tokenId);
 229:             }
 230: 
 231:             // send the new nft to the owner / vault
 232:             nonfungiblePositionManager.safeTransferFrom(address(this), state.owner, state.newTokenId);
 233: 
 234:             // protocol reward is calculated based on added amount (to incentivize optimal swap done by operator)
 235:             if (!config.onlyFees) {
 236:                 state.protocolReward0 = state.amountAdded0 * params.rewardX64 / Q64;
 237:                 state.protocolReward1 = state.amountAdded1 * params.rewardX64 / Q64;
 238:                 state.amount0 -= state.protocolReward0;
 239:                 state.amount1 -= state.protocolReward1;
 240:             }
 241: 
 242:             // send leftover to real owner
 243:             if (state.amount0 - state.amountAdded0 > 0) {
 244:                 _transferToken(state.realOwner, IERC20(state.token0), state.amount0 - state.amountAdded0, true);
 245:             }
 246:             if (state.amount1 - state.amountAdded1 > 0) {
 247:                 _transferToken(state.realOwner, IERC20(state.token1), state.amount1 - state.amountAdded1, true);
 248:             }
 249: 
 250:             // copy token config for new token
 251:             positionConfigs[state.newTokenId] = config;
 252:             emit PositionConfigured(
 253:                 state.newTokenId,
 254:                 config.lowerTickLimit,
 255:                 config.upperTickLimit,
 256:                 config.lowerTickDelta,
 257:                 config.upperTickDelta,
 258:                 config.token0SlippageX64,
 259:                 config.token1SlippageX64,
 260:                 config.onlyFees,
 261:                 config.maxRewardX64
 262:             );
 263: 
 264:             // delete config for old position
 265:             delete positionConfigs[params.tokenId];
 266:             emit PositionConfigured(params.tokenId, 0, 0, 0, 0, 0, 0, false, 0);
 267: 
 268:             emit RangeChanged(params.tokenId, state.newTokenId);
 269:         } else {
 270:             revert NotReady();
 271:         }
 272:     }
```

*GitHub* : [111-272](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L111-L272)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in LeverageTransformer.leverageDown(LeverageTransformer.LeverageDownParams) (L#123-175):
	External calls:
	- (amount0,amount1) = nonfungiblePositionManager.decreaseLiquidity(decreaseLiquidityParams) (L#134)
	- (amount0,amount1) = nonfungiblePositionManager.collect(collectParams) (L#142)
	- (amountIn,amountOut) = _routerSwap(Swapper.RouterSwapParams(IERC20(token0),IERC20(token),params.amountIn0,params.amountOut0Min,params.swapData0)) (L#147-151)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
	External calls sending eth:
	- (amountIn,amountOut) = _routerSwap(Swapper.RouterSwapParams(IERC20(token0),IERC20(token),params.amountIn0,params.amountOut0Min,params.swapData0)) (L#147-151)
		- (success,returndata) = target.call{value: value}(data) (L#135)
	Event emitted after the call(s):
	- Swap(address(params.tokenIn),address(params.tokenOut),amountInDelta,amountOutDelta) (L#116)
		- (amountIn,amountOut) = _routerSwap(Swapper.RouterSwapParams(IERC20(token0),IERC20(token),params.amountIn0,params.amountOut0Min,params.swapData0)) (L#147-151)

/// @audit ************** Possible Issue Line(s) **************
	L#134,  L#142,  L#147-151,  

/// @audit ****************** Affected Code *******************
 123:     function leverageDown(LeverageDownParams calldata params) external {
 124:         address token = IVault(msg.sender).asset();
 125:         (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(params.tokenId);
 126: 
 127:         uint256 amount0;
 128:         uint256 amount1;
 129: 
 130:         INonfungiblePositionManager.DecreaseLiquidityParams memory decreaseLiquidityParams = INonfungiblePositionManager
 131:             .DecreaseLiquidityParams(
 132:             params.tokenId, params.liquidity, params.amountRemoveMin0, params.amountRemoveMin1, params.deadline
 133:         );
 134:         (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(decreaseLiquidityParams);
 135: 
 136:         INonfungiblePositionManager.CollectParams memory collectParams = INonfungiblePositionManager.CollectParams(
 137:             params.tokenId,
 138:             address(this),
 139:             params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
 140:             params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)
 141:         );
 142:         (amount0, amount1) = nonfungiblePositionManager.collect(collectParams);
 143: 
 144:         uint256 amount = token == token0 ? amount0 : (token == token1 ? amount1 : 0);
 145: 
 146:         if (params.amountIn0 > 0 && token != token0) {
 147:             (uint256 amountIn, uint256 amountOut) = _routerSwap(
 148:                 Swapper.RouterSwapParams(
 149:                     IERC20(token0), IERC20(token), params.amountIn0, params.amountOut0Min, params.swapData0
 150:                 )
 151:             );
 152:             amount0 -= amountIn;
 153:             amount += amountOut;
 154:         }
 155:         if (params.amountIn1 > 0 && token != token1) {
 156:             (uint256 amountIn, uint256 amountOut) = _routerSwap(
 157:                 Swapper.RouterSwapParams(
 158:                     IERC20(token1), IERC20(token), params.amountIn1, params.amountOut1Min, params.swapData1
 159:                 )
 160:             );
 161:             amount1 -= amountIn;
 162:             amount += amountOut;
 163:         }
 164: 
 165:         SafeERC20.safeApprove(IERC20(token), msg.sender, amount);
 166:         IVault(msg.sender).repay(params.tokenId, amount, false);
 167: 
 168:         // send leftover tokens
 169:         if (amount0 > 0 && token != token0) {
 170:             SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0);
 171:         }
 172:         if (amount1 > 0 && token != token1) {
 173:             SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1);
 174:         }
 175:     }
```

*GitHub* : [123-175](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L123-L175)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Utils._swapAndMint(V3Utils.SwapAndMintParams,bool) (L#705-732):
	External calls:
	- (total0,total1) = _swapAndPrepareAmounts(params,unwrap) (L#709)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- weth.withdraw(amount) (L#866)
		- (sent) = to.call{value: amount}() (L#867)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeTransfer(token,to,amount) (L#872)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
		- SafeERC20.safeApprove(params.token0,address(nonfungiblePositionManager),0) (L#831)
		- SafeERC20.safeApprove(params.token0,address(nonfungiblePositionManager),total0) (L#832)
		- SafeERC20.safeApprove(params.token1,address(nonfungiblePositionManager),0) (L#835)
		- SafeERC20.safeApprove(params.token1,address(nonfungiblePositionManager),total1) (L#836)
	- (tokenId,liquidity,added0,added1) = nonfungiblePositionManager.mint(mintParams) (L#726)
	- nonfungiblePositionManager.safeTransferFrom(address(this),params.recipientNFT,tokenId,params.returnData) (L#727)
	External calls sending eth:
	- (total0,total1) = _swapAndPrepareAmounts(params,unwrap) (L#709)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- (sent) = to.call{value: amount}() (L#867)
	Event emitted after the call(s):
	- SwapAndMint(tokenId,liquidity,added0,added1) (L#729)

/// @audit ************** Possible Issue Line(s) **************
	L#709,  L#866,  L#867,  L#872,  L#831,  L#832,  L#835,  L#836,  L#726,  L#727,  L#729,  

/// @audit ****************** Affected Code *******************
 705:     function _swapAndMint(SwapAndMintParams memory params, bool unwrap)
 706:         internal
 707:         returns (uint256 tokenId, uint128 liquidity, uint256 added0, uint256 added1)
 708:     {
 709:         (uint256 total0, uint256 total1) = _swapAndPrepareAmounts(params, unwrap);
 710: 
 711:         INonfungiblePositionManager.MintParams memory mintParams = INonfungiblePositionManager.MintParams(
 712:             address(params.token0),
 713:             address(params.token1),
 714:             params.fee,
 715:             params.tickLower,
 716:             params.tickUpper,
 717:             total0,
 718:             total1,
 719:             params.amountAddMin0,
 720:             params.amountAddMin1,
 721:             address(this), // is sent to real recipient aftwards
 722:             params.deadline
 723:         );
 724: 
 725:         // mint is done to address(this) because it is not a safemint and safeTransferFrom needs to be done manually afterwards
 726:         (tokenId, liquidity, added0, added1) = nonfungiblePositionManager.mint(mintParams);
 727:         nonfungiblePositionManager.safeTransferFrom(address(this), params.recipientNFT, tokenId, params.returnData);
 728: 
 729:         emit SwapAndMint(tokenId, liquidity, added0, added1);
 730: 
 731:         _returnLeftoverTokens(params.recipient, params.token0, params.token1, total0, total1, added0, added1, unwrap);
 732:     }
 831:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), 0);
 832:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), total0);
 835:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), 0);
 836:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), total1);
 866:             weth.withdraw(amount);
 867:             (bool sent,) = to.call{value: amount}("");
 872:             SafeERC20.safeTransfer(token, to, amount);
```

*GitHub* : [705-732](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L705-L732)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Vault.decreaseLiquidityAndCollect(IVault.DecreaseLiquidityAndCollectParams) (L#609-646):
	External calls:
	- (amount0,amount1) = nonfungiblePositionManager.decreaseLiquidity(INonfungiblePositionManager.DecreaseLiquidityParams(params.tokenId,params.liquidity,params.amount0Min,params.amount1Min,params.deadline)) (L#627-631)
	- (amount0,amount1) = nonfungiblePositionManager.collect(collectParams) (L#640)
	Event emitted after the call(s):
	- WithdrawCollateral(params.tokenId,owner,params.recipient,params.liquidity,amount0,amount1) (L#645)

/// @audit ************** Possible Issue Line(s) **************
	L#627-631,  L#640,  L#645,  

/// @audit ****************** Affected Code *******************
 609:     function decreaseLiquidityAndCollect(DecreaseLiquidityAndCollectParams calldata params)
 610:         external
 611:         override
 612:         returns (uint256 amount0, uint256 amount1)
 613:     {
 614:         // this method is not allowed during transform - can be called directly on nftmanager if needed from transform contract
 615:         if (transformedTokenId > 0) {
 616:             revert TransformNotAllowed();
 617:         }
 618: 
 619:         address owner = tokenOwner[params.tokenId];
 620: 
 621:         if (owner != msg.sender) {
 622:             revert Unauthorized();
 623:         }
 624: 
 625:         (uint256 newDebtExchangeRateX96,) = _updateGlobalInterest();
 626: 
 627:         (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(
 628:             INonfungiblePositionManager.DecreaseLiquidityParams(
 629:                 params.tokenId, params.liquidity, params.amount0Min, params.amount1Min, params.deadline
 630:             )
 631:         );
 632: 
 633:         INonfungiblePositionManager.CollectParams memory collectParams = INonfungiblePositionManager.CollectParams(
 634:             params.tokenId,
 635:             params.recipient,
 636:             params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
 637:             params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)
 638:         );
 639: 
 640:         (amount0, amount1) = nonfungiblePositionManager.collect(collectParams);
 641: 
 642:         uint256 debt = _convertToAssets(loans[params.tokenId].debtShares, newDebtExchangeRateX96, Math.Rounding.Up);
 643:         _requireLoanIsHealthy(params.tokenId, debt);
 644: 
 645:         emit WithdrawCollateral(params.tokenId, owner, params.recipient, params.liquidity, amount0, amount1);
 646:     }
```

*GitHub* : [609-646](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L609-L646)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in LeverageTransformer.leverageUp(LeverageTransformer.LeverageUpParams) (L#40-96):
	External calls:
	- IVault(msg.sender).borrow(params.tokenId,amount) (L#45)
	- (amountIn,amountOut) = _routerSwap(Swapper.RouterSwapParams(IERC20(token),IERC20(token0),params.amountIn0,params.amountOut0Min,params.swapData0)) (L#53-57)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
	External calls sending eth:
	- (amountIn,amountOut) = _routerSwap(Swapper.RouterSwapParams(IERC20(token),IERC20(token0),params.amountIn0,params.amountOut0Min,params.swapData0)) (L#53-57)
		- (success,returndata) = target.call{value: value}(data) (L#135)
	Event emitted after the call(s):
	- Swap(address(params.tokenIn),address(params.tokenOut),amountInDelta,amountOutDelta) (L#116)
		- (amountIn,amountOut) = _routerSwap(Swapper.RouterSwapParams(IERC20(token),IERC20(token0),params.amountIn0,params.amountOut0Min,params.swapData0)) (L#53-57)

/// @audit ************** Possible Issue Line(s) **************
	L#45,  L#53-57,  

/// @audit ****************** Affected Code *******************
  40:     function leverageUp(LeverageUpParams calldata params) external {
  41:         uint256 amount = params.borrowAmount;
  42: 
  43:         address token = IVault(msg.sender).asset();
  44: 
  45:         IVault(msg.sender).borrow(params.tokenId, amount);
  46: 
  47:         (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(params.tokenId);
  48: 
  49:         uint256 amount0 = token == token0 ? amount : 0;
  50:         uint256 amount1 = token == token1 ? amount : 0;
  51: 
  52:         if (params.amountIn0 > 0) {
  53:             (uint256 amountIn, uint256 amountOut) = _routerSwap(
  54:                 Swapper.RouterSwapParams(
  55:                     IERC20(token), IERC20(token0), params.amountIn0, params.amountOut0Min, params.swapData0
  56:                 )
  57:             );
  58:             if (token == token1) {
  59:                 amount1 -= amountIn;
  60:             }
  61:             amount -= amountIn;
  62:             amount0 += amountOut;
  63:         }
  64:         if (params.amountIn1 > 0) {
  65:             (uint256 amountIn, uint256 amountOut) = _routerSwap(
  66:                 Swapper.RouterSwapParams(
  67:                     IERC20(token), IERC20(token1), params.amountIn1, params.amountOut1Min, params.swapData1
  68:                 )
  69:             );
  70:             if (token == token0) {
  71:                 amount0 -= amountIn;
  72:             }
  73:             amount -= amountIn;
  74:             amount1 += amountOut;
  75:         }
  76: 
  77:         SafeERC20.safeIncreaseAllowance(IERC20(token0), address(nonfungiblePositionManager), amount0);
  78:         SafeERC20.safeIncreaseAllowance(IERC20(token1), address(nonfungiblePositionManager), amount1);
  79: 
  80:         INonfungiblePositionManager.IncreaseLiquidityParams memory increaseLiquidityParams = INonfungiblePositionManager
  81:             .IncreaseLiquidityParams(
  82:             params.tokenId, amount0, amount1, params.amountAddMin0, params.amountAddMin1, params.deadline
  83:         );
  84:         (, uint256 added0, uint256 added1) = nonfungiblePositionManager.increaseLiquidity(increaseLiquidityParams);
  85: 
  86:         // send leftover tokens
  87:         if (amount0 > added0) {
  88:             SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0 - added0);
  89:         }
  90:         if (amount1 > added1) {
  91:             SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1 - added1);
  92:         }
  93:         if (token != token0 && token != token1 && amount > 0) {
  94:             SafeERC20.safeTransfer(IERC20(token), params.recipient, amount);
  95:         }
  96:     }
```

*GitHub* : [40-96](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L40-L96)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Utils.swapAndMint(V3Utils.SwapAndMintParams) (L#467-501):
	External calls:
	- _prepareAddPermit2(params.token0,params.token1,params.swapSourceToken,params.amount0,params.amount1,params.amountIn0 + params.amountIn1,pbtf,signature) (L#479-488)
		- weth.deposit{value: msg.value}() (L#667)
		- permit2.permitTransferFrom(permit,transferDetails,msg.sender,signature) (L#631)
	- _prepareAddApproved(params.token0,params.token1,params.swapSourceToken,params.amount0,params.amount1,params.amountIn0 + params.amountIn1) (L#490-497)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- weth.deposit{value: msg.value}() (L#667)
		- SafeERC20.safeTransferFrom(token0,msg.sender,address(this),needed0) (L#578)
		- SafeERC20.safeTransferFrom(token1,msg.sender,address(this),needed1) (L#581)
		- SafeERC20.safeTransferFrom(otherToken,msg.sender,address(this),neededOther) (L#584)
	- (tokenId,liquidity,amount0,amount1) = _swapAndMint(params,msg.value != 0) (L#500)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- weth.withdraw(amount) (L#866)
		- (sent) = to.call{value: amount}() (L#867)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- (tokenId,liquidity,added0,added1) = nonfungiblePositionManager.mint(mintParams) (L#726)
		- nonfungiblePositionManager.safeTransferFrom(address(this),params.recipientNFT,tokenId,params.returnData) (L#727)
		- SafeERC20.safeTransfer(token,to,amount) (L#872)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
		- SafeERC20.safeApprove(params.token0,address(nonfungiblePositionManager),0) (L#831)
		- SafeERC20.safeApprove(params.token0,address(nonfungiblePositionManager),total0) (L#832)
		- SafeERC20.safeApprove(params.token1,address(nonfungiblePositionManager),0) (L#835)
		- SafeERC20.safeApprove(params.token1,address(nonfungiblePositionManager),total1) (L#836)
	External calls sending eth:
	- _prepareAddPermit2(params.token0,params.token1,params.swapSourceToken,params.amount0,params.amount1,params.amountIn0 + params.amountIn1,pbtf,signature) (L#479-488)
		- weth.deposit{value: msg.value}() (L#667)
	- _prepareAddApproved(params.token0,params.token1,params.swapSourceToken,params.amount0,params.amount1,params.amountIn0 + params.amountIn1) (L#490-497)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- weth.deposit{value: msg.value}() (L#667)
	- (tokenId,liquidity,amount0,amount1) = _swapAndMint(params,msg.value != 0) (L#500)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- (sent) = to.call{value: amount}() (L#867)
	Event emitted after the call(s):
	- Swap(address(params.tokenIn),address(params.tokenOut),amountInDelta,amountOutDelta) (L#116)
		- (tokenId,liquidity,amount0,amount1) = _swapAndMint(params,msg.value != 0) (L#500)
	- SwapAndMint(tokenId,liquidity,added0,added1) (L#729)
		- (tokenId,liquidity,amount0,amount1) = _swapAndMint(params,msg.value != 0) (L#500)

/// @audit ************** Possible Issue Line(s) **************
	L#479-488,  L#667,  L#631,  L#490-497,  L#578,  L#581,  L#584,  L#500,  L#866,  L#867,  L#726,  L#727,  L#872,  L#831,  L#832,  L#835,  L#836,  L#729,  

/// @audit ****************** Affected Code *******************
 467:     function swapAndMint(SwapAndMintParams calldata params)
 468:         external
 469:         payable
 470:         returns (uint256 tokenId, uint128 liquidity, uint256 amount0, uint256 amount1)
 471:     {
 472:         if (params.token0 == params.token1) {
 473:             revert SameToken();
 474:         }
 475: 
 476:         if (params.permitData.length > 0) {
 477:             (ISignatureTransfer.PermitBatchTransferFrom memory pbtf, bytes memory signature) =
 478:                 abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));
 479:             _prepareAddPermit2(
 480:                 params.token0,
 481:                 params.token1,
 482:                 params.swapSourceToken,
 483:                 params.amount0,
 484:                 params.amount1,
 485:                 params.amountIn0 + params.amountIn1,
 486:                 pbtf,
 487:                 signature
 488:             );
 489:         } else {
 490:             _prepareAddApproved(
 491:                 params.token0,
 492:                 params.token1,
 493:                 params.swapSourceToken,
 494:                 params.amount0,
 495:                 params.amount1,
 496:                 params.amountIn0 + params.amountIn1
 497:             );
 498:         }
 499: 
 500:         (tokenId, liquidity, amount0, amount1) = _swapAndMint(params, msg.value != 0);
 501:     }
 578:             SafeERC20.safeTransferFrom(token0, msg.sender, address(this), needed0);
 581:             SafeERC20.safeTransferFrom(token1, msg.sender, address(this), needed1);
 584:             SafeERC20.safeTransferFrom(otherToken, msg.sender, address(this), neededOther);
 631:         permit2.permitTransferFrom(permit, transferDetails, msg.sender, signature);
 667:             weth.deposit{value: msg.value}();
 726:         (tokenId, liquidity, added0, added1) = nonfungiblePositionManager.mint(mintParams);
 727:         nonfungiblePositionManager.safeTransferFrom(address(this), params.recipientNFT, tokenId, params.returnData);
 729:         emit SwapAndMint(tokenId, liquidity, added0, added1);
 831:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), 0);
 832:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), total0);
 835:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), 0);
 836:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), total1);
 866:             weth.withdraw(amount);
 867:             (bool sent,) = to.call{value: amount}("");
 872:             SafeERC20.safeTransfer(token, to, amount);
```

*GitHub* : [467-501](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L467-L501)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Vault.withdrawReserves(uint256,address) (L#765-783):
	External calls:
	- SafeERC20.safeTransfer(IERC20(asset),receiver,amount) (L#779)
	Event emitted after the call(s):
	- WithdrawReserves(amount,receiver) (L#782)

/// @audit ************** Possible Issue Line(s) **************
	L#779,  L#782,  

/// @audit ****************** Affected Code *******************
 765:     function withdrawReserves(uint256 amount, address receiver) external onlyOwner {
 766:         (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
 767: 
 768:         uint256 protected =
 769:             _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up) * reserveProtectionFactorX32 / Q32;
 770:         (uint256 balance,, uint256 reserves) = _getAvailableBalance(newDebtExchangeRateX96, newLendExchangeRateX96);
 771:         uint256 unprotected = reserves > protected ? reserves - protected : 0;
 772:         uint256 available = balance > unprotected ? unprotected : balance;
 773: 
 774:         if (amount > available) {
 775:             revert InsufficientLiquidity();
 776:         }
 777: 
 778:         if (amount > 0) {
 779:             SafeERC20.safeTransfer(IERC20(asset), receiver, amount);
 780:         }
 781: 
 782:         emit WithdrawReserves(amount, receiver);
 783:     }
```

*GitHub* : [765-783](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L765-L783)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Vault.borrow(uint256,uint256) (L#550-602):
	External calls:
	- SafeERC20.safeTransfer(IERC20(asset),msg.sender,assets) (L#599)
	- SafeERC20.safeTransfer(IERC20(asset),owner,assets) (L#599)
	Event emitted after the call(s):
	- Borrow(tokenId,owner,assets,shares) (L#601)

/// @audit ************** Possible Issue Line(s) **************
	L#599,  L#601,  

/// @audit ****************** Affected Code *******************
 550:     function borrow(uint256 tokenId, uint256 assets) external override {
 551:         bool isTransformMode =
 552:             transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];
 553: 
 554:         (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
 555: 
 556:         _resetDailyDebtIncreaseLimit(newLendExchangeRateX96, false);
 557: 
 558:         Loan storage loan = loans[tokenId];
 559: 
 560:         // if not in transfer mode - must be called from owner or the vault itself
 561:         if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {
 562:             revert Unauthorized();
 563:         }
 564: 
 565:         uint256 shares = _convertToShares(assets, newDebtExchangeRateX96, Math.Rounding.Up);
 566: 
 567:         uint256 loanDebtShares = loan.debtShares + shares;
 568:         loan.debtShares = loanDebtShares;
 569:         debtSharesTotal += shares;
 570: 
 571:         if (debtSharesTotal > _convertToShares(globalDebtLimit, newDebtExchangeRateX96, Math.Rounding.Down)) {
 572:             revert GlobalDebtLimit();
 573:         }
 574:         if (assets > dailyDebtIncreaseLimitLeft) {
 575:             revert DailyDebtIncreaseLimit();
 576:         } else {
 577:             dailyDebtIncreaseLimitLeft -= assets;
 578:         }
 579: 
 580:         _updateAndCheckCollateral(
 581:             tokenId, newDebtExchangeRateX96, newLendExchangeRateX96, loanDebtShares - shares, loanDebtShares
 582:         );
 583: 
 584:         uint256 debt = _convertToAssets(loanDebtShares, newDebtExchangeRateX96, Math.Rounding.Up);
 585: 
 586:         if (debt < minLoanSize) {
 587:             revert MinLoanSize();
 588:         }
 589: 
 590:         // only does check health here if not in transform mode
 591:         if (!isTransformMode) {
 592:             _requireLoanIsHealthy(tokenId, debt);
 593:         }
 594: 
 595:         address owner = tokenOwner[tokenId];
 596: 
 597:         // fails if not enough asset available
 598:         // if called from transform mode - send funds to transformer contract
 599:         SafeERC20.safeTransfer(IERC20(asset), isTransformMode ? msg.sender : owner, assets);
 600: 
 601:         emit Borrow(tokenId, owner, assets, shares);
 602:     }
```

*GitHub* : [550-602](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L550-L602)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Utils.swapAndIncreaseLiquidity(V3Utils.SwapAndIncreaseLiquidityParams) (L#532-564):
	External calls:
	- _prepareAddPermit2(IERC20(token0),IERC20(token1),params.swapSourceToken,params.amount0,params.amount1,params.amountIn0 + params.amountIn1,pbtf,signature) (L#542-551)
		- weth.deposit{value: msg.value}() (L#667)
		- permit2.permitTransferFrom(permit,transferDetails,msg.sender,signature) (L#631)
	- _prepareAddApproved(IERC20(token0),IERC20(token1),params.swapSourceToken,params.amount0,params.amount1,params.amountIn0 + params.amountIn1) (L#553-560)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- weth.deposit{value: msg.value}() (L#667)
		- SafeERC20.safeTransferFrom(token0,msg.sender,address(this),needed0) (L#578)
		- SafeERC20.safeTransferFrom(token1,msg.sender,address(this),needed1) (L#581)
		- SafeERC20.safeTransferFrom(otherToken,msg.sender,address(this),neededOther) (L#584)
	- (liquidity,amount0,amount1) = _swapAndIncrease(params,IERC20(token0),IERC20(token1),msg.value != 0) (L#563)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- weth.withdraw(amount) (L#866)
		- (sent) = to.call{value: amount}() (L#867)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- (liquidity,added0,added1) = nonfungiblePositionManager.increaseLiquidity(increaseLiquidityParams) (L#771)
		- SafeERC20.safeTransfer(token,to,amount) (L#872)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
		- SafeERC20.safeApprove(params.token0,address(nonfungiblePositionManager),0) (L#831)
		- SafeERC20.safeApprove(params.token0,address(nonfungiblePositionManager),total0) (L#832)
		- SafeERC20.safeApprove(params.token1,address(nonfungiblePositionManager),0) (L#835)
		- SafeERC20.safeApprove(params.token1,address(nonfungiblePositionManager),total1) (L#836)
	External calls sending eth:
	- _prepareAddPermit2(IERC20(token0),IERC20(token1),params.swapSourceToken,params.amount0,params.amount1,params.amountIn0 + params.amountIn1,pbtf,signature) (L#542-551)
		- weth.deposit{value: msg.value}() (L#667)
	- _prepareAddApproved(IERC20(token0),IERC20(token1),params.swapSourceToken,params.amount0,params.amount1,params.amountIn0 + params.amountIn1) (L#553-560)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- weth.deposit{value: msg.value}() (L#667)
	- (liquidity,amount0,amount1) = _swapAndIncrease(params,IERC20(token0),IERC20(token1),msg.value != 0) (L#563)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- (sent) = to.call{value: amount}() (L#867)
	Event emitted after the call(s):
	- Swap(address(params.tokenIn),address(params.tokenOut),amountInDelta,amountOutDelta) (L#116)
		- (liquidity,amount0,amount1) = _swapAndIncrease(params,IERC20(token0),IERC20(token1),msg.value != 0) (L#563)
	- SwapAndIncreaseLiquidity(params.tokenId,liquidity,added0,added1) (L#773)
		- (liquidity,amount0,amount1) = _swapAndIncrease(params,IERC20(token0),IERC20(token1),msg.value != 0) (L#563)

/// @audit ************** Possible Issue Line(s) **************
	L#542-551,  L#667,  L#631,  L#553-560,  L#578,  L#581,  L#584,  L#563,  L#866,  L#867,  L#771,  L#872,  L#831,  L#832,  L#835,  L#836,  L#773,  

/// @audit ****************** Affected Code *******************
 532:     function swapAndIncreaseLiquidity(SwapAndIncreaseLiquidityParams calldata params)
 533:         external
 534:         payable
 535:         returns (uint128 liquidity, uint256 amount0, uint256 amount1)
 536:     {
 537:         (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(params.tokenId);
 538: 
 539:         if (params.permitData.length > 0) {
 540:             (ISignatureTransfer.PermitBatchTransferFrom memory pbtf, bytes memory signature) =
 541:                 abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));
 542:             _prepareAddPermit2(
 543:                 IERC20(token0),
 544:                 IERC20(token1),
 545:                 params.swapSourceToken,
 546:                 params.amount0,
 547:                 params.amount1,
 548:                 params.amountIn0 + params.amountIn1,
 549:                 pbtf,
 550:                 signature
 551:             );
 552:         } else {
 553:             _prepareAddApproved(
 554:                 IERC20(token0),
 555:                 IERC20(token1),
 556:                 params.swapSourceToken,
 557:                 params.amount0,
 558:                 params.amount1,
 559:                 params.amountIn0 + params.amountIn1
 560:             );
 561:         }
 562: 
 563:         (liquidity, amount0, amount1) = _swapAndIncrease(params, IERC20(token0), IERC20(token1), msg.value != 0);
 564:     }
 578:             SafeERC20.safeTransferFrom(token0, msg.sender, address(this), needed0);
 581:             SafeERC20.safeTransferFrom(token1, msg.sender, address(this), needed1);
 584:             SafeERC20.safeTransferFrom(otherToken, msg.sender, address(this), neededOther);
 631:         permit2.permitTransferFrom(permit, transferDetails, msg.sender, signature);
 667:             weth.deposit{value: msg.value}();
 771:         (liquidity, added0, added1) = nonfungiblePositionManager.increaseLiquidity(increaseLiquidityParams);
 773:         emit SwapAndIncreaseLiquidity(params.tokenId, liquidity, added0, added1);
 831:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), 0);
 832:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), total0);
 835:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), 0);
 836:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), total1);
 866:             weth.withdraw(amount);
 867:             (bool sent,) = to.call{value: amount}("");
 872:             SafeERC20.safeTransfer(token, to, amount);
```

*GitHub* : [532-564](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L532-L564)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Vault._withdraw(address,address,uint256,bool) (L#920-952):
	External calls:
	- SafeERC20.safeTransfer(IERC20(asset),receiver,assets) (L#946)
	Event emitted after the call(s):
	- Withdraw(msg.sender,receiver,owner,assets,shares) (L#951)

/// @audit ************** Possible Issue Line(s) **************
	L#946,  L#951,  

/// @audit ****************** Affected Code *******************
 920:     function _withdraw(address receiver, address owner, uint256 amount, bool isShare)
 921:         internal
 922:         returns (uint256 assets, uint256 shares)
 923:     {
 924:         (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
 925: 
 926:         if (isShare) {
 927:             shares = amount;
 928:             assets = _convertToAssets(amount, newLendExchangeRateX96, Math.Rounding.Down);
 929:         } else {
 930:             assets = amount;
 931:             shares = _convertToShares(amount, newLendExchangeRateX96, Math.Rounding.Up);
 932:         }
 933: 
 934:         // if caller has allowance for owners shares - may call withdraw
 935:         if (msg.sender != owner) {
 936:             _spendAllowance(owner, msg.sender, shares);
 937:         }
 938: 
 939:         (, uint256 available,) = _getAvailableBalance(newDebtExchangeRateX96, newLendExchangeRateX96);
 940:         if (available < assets) {
 941:             revert InsufficientLiquidity();
 942:         }
 943: 
 944:         // fails if not enough shares
 945:         _burn(owner, shares);
 946:         SafeERC20.safeTransfer(IERC20(asset), receiver, assets);
 947: 
 948:         // when amounts are withdrawn - they may be deposited again
 949:         dailyLendIncreaseLimitLeft += assets;
 950: 
 951:         emit Withdraw(msg.sender, receiver, owner, assets, shares);
 952:     }
```

*GitHub* : [920-952](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L920-L952)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Utils._swapAndIncrease(V3Utils.SwapAndIncreaseLiquidityParams,IERC20,IERC20,bool) (L#735-776):
	External calls:
	- (total0,total1) = _swapAndPrepareAmounts(SwapAndMintParams(token0,token1,0,0,0,params.amount0,params.amount1,params.recipient,params.recipient,params.deadline,params.swapSourceToken,params.amountIn0,params.amountOut0Min,params.swapData0,params.amountIn1,params.amountOut1Min,params.swapData1,params.amountAddMin0,params.amountAddMin1,,params.permitData),unwrap) (L#739-764)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- weth.withdraw(amount) (L#866)
		- (sent) = to.call{value: amount}() (L#867)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeTransfer(token,to,amount) (L#872)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
		- SafeERC20.safeApprove(params.token0,address(nonfungiblePositionManager),0) (L#831)
		- SafeERC20.safeApprove(params.token0,address(nonfungiblePositionManager),total0) (L#832)
		- SafeERC20.safeApprove(params.token1,address(nonfungiblePositionManager),0) (L#835)
		- SafeERC20.safeApprove(params.token1,address(nonfungiblePositionManager),total1) (L#836)
	- (liquidity,added0,added1) = nonfungiblePositionManager.increaseLiquidity(increaseLiquidityParams) (L#771)
	External calls sending eth:
	- (total0,total1) = _swapAndPrepareAmounts(SwapAndMintParams(token0,token1,0,0,0,params.amount0,params.amount1,params.recipient,params.recipient,params.deadline,params.swapSourceToken,params.amountIn0,params.amountOut0Min,params.swapData0,params.amountIn1,params.amountOut1Min,params.swapData1,params.amountAddMin0,params.amountAddMin1,,params.permitData),unwrap) (L#739-764)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- (sent) = to.call{value: amount}() (L#867)
	Event emitted after the call(s):
	- SwapAndIncreaseLiquidity(params.tokenId,liquidity,added0,added1) (L#773)

/// @audit ************** Possible Issue Line(s) **************
	L#739-764,  L#866,  L#867,  L#872,  L#831,  L#832,  L#835,  L#836,  L#771,  L#773,  

/// @audit ****************** Affected Code *******************
 735:     function _swapAndIncrease(SwapAndIncreaseLiquidityParams memory params, IERC20 token0, IERC20 token1, bool unwrap)
 736:         internal
 737:         returns (uint128 liquidity, uint256 added0, uint256 added1)
 738:     {
 739:         (uint256 total0, uint256 total1) = _swapAndPrepareAmounts(
 740:             SwapAndMintParams(
 741:                 token0,
 742:                 token1,
 743:                 0,
 744:                 0,
 745:                 0,
 746:                 params.amount0,
 747:                 params.amount1,
 748:                 params.recipient,
 749:                 params.recipient,
 750:                 params.deadline,
 751:                 params.swapSourceToken,
 752:                 params.amountIn0,
 753:                 params.amountOut0Min,
 754:                 params.swapData0,
 755:                 params.amountIn1,
 756:                 params.amountOut1Min,
 757:                 params.swapData1,
 758:                 params.amountAddMin0,
 759:                 params.amountAddMin1,
 760:                 "",
 761:                 params.permitData
 762:             ),
 763:             unwrap
 764:         );
 765: 
 766:         INonfungiblePositionManager.IncreaseLiquidityParams memory increaseLiquidityParams = INonfungiblePositionManager
 767:             .IncreaseLiquidityParams(
 768:             params.tokenId, total0, total1, params.amountAddMin0, params.amountAddMin1, params.deadline
 769:         );
 770: 
 771:         (liquidity, added0, added1) = nonfungiblePositionManager.increaseLiquidity(increaseLiquidityParams);
 772: 
 773:         emit SwapAndIncreaseLiquidity(params.tokenId, liquidity, added0, added1);
 774: 
 775:         _returnLeftoverTokens(params.recipient, token0, token1, total0, total1, added0, added1, unwrap);
 776:     }
 831:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), 0);
 832:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), total0);
 835:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), 0);
 836:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), total1);
 866:             weth.withdraw(amount);
 867:             (bool sent,) = to.call{value: amount}("");
 872:             SafeERC20.safeTransfer(token, to, amount);
```

*GitHub* : [735-776](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L735-L776)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in FlashloanLiquidator.uniswapV3FlashCallback(uint256,uint256,bytes) (L#67-109):
	External calls:
	- SafeERC20.safeApprove(data.asset,address(data.vault),data.liquidationCost) (L#72)
	- data.vault.liquidate(IVault.LiquidateParams(data.tokenId,data.debtShares,data.swap0.amountIn,data.swap1.amountIn,address(this),)) (L#73-77)
	- SafeERC20.safeApprove(data.asset,address(data.vault),0) (L#78)
	- _routerSwap(data.swap0) (L#81)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
	External calls sending eth:
	- _routerSwap(data.swap0) (L#81)
		- (success,returndata) = target.call{value: value}(data) (L#135)
	Event emitted after the call(s):
	- Swap(address(params.tokenIn),address(params.tokenOut),amountInDelta,amountOutDelta) (L#116)
		- _routerSwap(data.swap0) (L#81)

/// @audit ************** Possible Issue Line(s) **************
	L#72,  L#73-77,  L#78,  L#81,  

/// @audit ****************** Affected Code *******************
  67:     function uniswapV3FlashCallback(uint256 fee0, uint256 fee1, bytes calldata callbackData) external {
  68:         // no origin check is needed - because the contract doesn't hold any funds - there is no benefit in calling uniswapV3FlashCallback() from another context
  69: 
  70:         FlashCallbackData memory data = abi.decode(callbackData, (FlashCallbackData));
  71: 
  72:         SafeERC20.safeApprove(data.asset, address(data.vault), data.liquidationCost);
  73:         data.vault.liquidate(
  74:             IVault.LiquidateParams(
  75:                 data.tokenId, data.debtShares, data.swap0.amountIn, data.swap1.amountIn, address(this), ""
  76:             )
  77:         );
  78:         SafeERC20.safeApprove(data.asset, address(data.vault), 0);
  79: 
  80:         // do swaps
  81:         _routerSwap(data.swap0);
  82:         _routerSwap(data.swap1);
  83: 
  84:         // transfer lent amount + fee (only one token can have fee) - back to pool
  85:         SafeERC20.safeTransfer(data.asset, msg.sender, data.liquidationCost + (fee0 + fee1));
  86: 
  87:         // return all leftover tokens to liquidator
  88:         if (data.swap0.tokenIn != data.asset) {
  89:             uint256 balance = data.swap0.tokenIn.balanceOf(address(this));
  90:             if (balance > 0) {
  91:                 SafeERC20.safeTransfer(data.swap0.tokenIn, data.liquidator, balance);
  92:             }
  93:         }
  94:         if (data.swap1.tokenIn != data.asset) {
  95:             uint256 balance = data.swap1.tokenIn.balanceOf(address(this));
  96:             if (balance > 0) {
  97:                 SafeERC20.safeTransfer(data.swap1.tokenIn, data.liquidator, balance);
  98:             }
  99:         }
 100:         {
 101:             uint256 balance = data.asset.balanceOf(address(this));
 102:             if (balance < data.minReward) {
 103:                 revert NotEnoughReward();
 104:             }
 105:             if (balance > 0) {
 106:                 SafeERC20.safeTransfer(data.asset, data.liquidator, balance);
 107:             }
 108:         }
 109:     }
```

*GitHub* : [67-109](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L67-L109)

```solidity
File: src/transformers/AutoRange.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in AutoRange.configToken(uint256,address,AutoRange.PositionConfig) (L#276-297):
	External calls:
	- _validateOwner(tokenId,vault) (L#277)
		- owner = IVault(vault).ownerOf(tokenId) (L#240)
	Event emitted after the call(s):
	- PositionConfigured(tokenId,config.lowerTickLimit,config.upperTickLimit,config.lowerTickDelta,config.upperTickDelta,config.token0SlippageX64,config.token1SlippageX64,config.onlyFees,config.maxRewardX64) (L#286-296)

/// @audit ************** Possible Issue Line(s) **************
	L#277,  L#286-296,  

/// @audit ****************** Affected Code *******************
 276:     function configToken(uint256 tokenId, address vault, PositionConfig calldata config) external {
 277:         _validateOwner(tokenId, vault);
 278: 
 279:         // lower tick must be always below or equal to upper tick - if they are equal - range adjustment is deactivated
 280:         if (config.lowerTickDelta > config.upperTickDelta) {
 281:             revert InvalidConfig();
 282:         }
 283: 
 284:         positionConfigs[tokenId] = config;
 285: 
 286:         emit PositionConfigured(
 287:             tokenId,
 288:             config.lowerTickLimit,
 289:             config.upperTickLimit,
 290:             config.lowerTickDelta,
 291:             config.upperTickDelta,
 292:             config.token0SlippageX64,
 293:             config.token1SlippageX64,
 294:             config.onlyFees,
 295:             config.maxRewardX64
 296:         );
 297:     }
```

*GitHub* : [276-297](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L276-L297)

```solidity
File: src/utils/Swapper.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in Swapper._routerSwap(Swapper.RouterSwapParams) (L#73-118):
	External calls:
	- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
	- (success) = zeroxRouter.call(data.data) (L#89)
	- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
	- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
	- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
	Event emitted after the call(s):
	- Swap(address(params.tokenIn),address(params.tokenOut),amountInDelta,amountOutDelta) (L#116)

/// @audit ************** Possible Issue Line(s) **************
	L#87,  L#89,  L#94,  L#98,  L#99,  L#116,  

/// @audit ****************** Affected Code *******************
  73:     function _routerSwap(RouterSwapParams memory params)
  74:         internal
  75:         returns (uint256 amountInDelta, uint256 amountOutDelta)
  76:     {
  77:         if (params.amountIn != 0 && params.swapData.length != 0 && address(params.tokenOut) != address(0)) {
  78:             uint256 balanceInBefore = params.tokenIn.balanceOf(address(this));
  79:             uint256 balanceOutBefore = params.tokenOut.balanceOf(address(this));
  80: 
  81:             // get router specific swap data
  82:             (address router, bytes memory routerData) = abi.decode(params.swapData, (address, bytes));
  83: 
  84:             if (router == zeroxRouter) {
  85:                 ZeroxRouterData memory data = abi.decode(routerData, (ZeroxRouterData));
  86:                 // approve needed amount
  87:                 SafeERC20.safeApprove(params.tokenIn, data.allowanceTarget, params.amountIn);
  88:                 // execute swap
  89:                 (bool success,) = zeroxRouter.call(data.data);
  90:                 if (!success) {
  91:                     revert SwapFailed();
  92:                 }
  93:                 // reset approval
  94:                 SafeERC20.safeApprove(params.tokenIn, data.allowanceTarget, 0);
  95:             } else if (router == universalRouter) {
  96:                 UniversalRouterData memory data = abi.decode(routerData, (UniversalRouterData));
  97:                 // tokens are transfered to Universalrouter directly (data.commands must include sweep action!)
  98:                 SafeERC20.safeTransfer(params.tokenIn, universalRouter, params.amountIn);
  99:                 IUniversalRouter(universalRouter).execute(data.commands, data.inputs, data.deadline);
 100:             } else {
 101:                 revert WrongContract();
 102:             }
 103: 
 104:             uint256 balanceInAfter = params.tokenIn.balanceOf(address(this));
 105:             uint256 balanceOutAfter = params.tokenOut.balanceOf(address(this));
 106: 
 107:             amountInDelta = balanceInBefore - balanceInAfter;
 108:             amountOutDelta = balanceOutAfter - balanceOutBefore;
 109: 
 110:             // amountMin slippage check
 111:             if (amountOutDelta < params.amountOutMin) {
 112:                 revert SlippageError();
 113:             }
 114: 
 115:             // event for any swap with exact swapped value
 116:             emit Swap(address(params.tokenIn), address(params.tokenOut), amountInDelta, amountOutDelta);
 117:         }
 118:     }
```

*GitHub* : [73-118](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L73-L118)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Vault.liquidate(IVault.LiquidateParams) (L#685-757):
	External calls:
	- permit2.permitTransferFrom(permit,ISignatureTransfer.SignatureTransferDetails(address(this),state.liquidatorCost),msg.sender,signature) (L#720-725)
	- SafeERC20.safeTransferFrom(IERC20(asset),msg.sender,address(this),state.liquidatorCost) (L#728)
	- (amount0,amount1) = _sendPositionValue(params.tokenId,state.liquidationValue,state.fullValue,state.feeValue,msg.sender) (L#734-735)
		- nonfungiblePositionManager.decreaseLiquidity(INonfungiblePositionManager.DecreaseLiquidityParams(tokenId,liquidity,0,0,block.timestamp)) (L#1065-1067)
		- (amount0,amount1) = nonfungiblePositionManager.collect(INonfungiblePositionManager.CollectParams(tokenId,recipient,fees0,fees1)) (L#1070-1072)
	- _cleanupLoan(params.tokenId,state.newDebtExchangeRateX96,state.newLendExchangeRateX96,owner) (L#744)
		- nonfungiblePositionManager.safeTransferFrom(address(this),owner,tokenId) (L#1083)
	Event emitted after the call(s):
	- Liquidate(params.tokenId,msg.sender,owner,state.fullValue,state.liquidatorCost,amount0,amount1,state.reserveCost,state.missing) (L#746-756)
	- Remove(tokenId,owner) (L#1084)
		- _cleanupLoan(params.tokenId,state.newDebtExchangeRateX96,state.newLendExchangeRateX96,owner) (L#744)

/// @audit ************** Possible Issue Line(s) **************
	L#720-725,  L#728,  L#734-735,  L#1065-1067,  L#1070-1072,  L#744,  L#1083,  L#746-756,  L#1084,  

/// @audit ****************** Affected Code *******************
 685:     function liquidate(LiquidateParams calldata params) external override returns (uint256 amount0, uint256 amount1) {
 686:         // liquidation is not allowed during transformer mode
 687:         if (transformedTokenId > 0) {
 688:             revert TransformNotAllowed();
 689:         }
 690: 
 691:         LiquidateState memory state;
 692: 
 693:         (state.newDebtExchangeRateX96, state.newLendExchangeRateX96) = _updateGlobalInterest();
 694: 
 695:         uint256 debtShares = loans[params.tokenId].debtShares;
 696:         if (debtShares != params.debtShares) {
 697:             revert DebtChanged();
 698:         }
 699: 
 700:         state.debt = _convertToAssets(debtShares, state.newDebtExchangeRateX96, Math.Rounding.Up);
 701: 
 702:         (state.isHealthy, state.fullValue, state.collateralValue, state.feeValue) =
 703:             _checkLoanIsHealthy(params.tokenId, state.debt);
 704:         if (state.isHealthy) {
 705:             revert NotLiquidatable();
 706:         }
 707: 
 708:         (state.liquidationValue, state.liquidatorCost, state.reserveCost) =
 709:             _calculateLiquidation(state.debt, state.fullValue, state.collateralValue);
 710: 
 711:         // calculate reserve (before transfering liquidation money - otherwise calculation is off)
 712:         if (state.reserveCost > 0) {
 713:             state.missing =
 714:                 _handleReserveLiquidation(state.reserveCost, state.newDebtExchangeRateX96, state.newLendExchangeRateX96);
 715:         }
 716: 
 717:         if (params.permitData.length > 0) {
 718:             (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
 719:                 abi.decode(params.permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
 720:             permit2.permitTransferFrom(
 721:                 permit,
 722:                 ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost),
 723:                 msg.sender,
 724:                 signature
 725:             );
 726:         } else {
 727:             // take value from liquidator
 728:             SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);
 729:         }
 730: 
 731:         debtSharesTotal -= debtShares;
 732: 
 733:         // send promised collateral tokens to liquidator
 734:         (amount0, amount1) =
 735:             _sendPositionValue(params.tokenId, state.liquidationValue, state.fullValue, state.feeValue, msg.sender);
 736: 
 737:         if (amount0 < params.amount0Min || amount1 < params.amount1Min) {
 738:             revert SlippageError();
 739:         }
 740: 
 741:         address owner = tokenOwner[params.tokenId];
 742: 
 743:         // disarm loan and send remaining position to owner
 744:         _cleanupLoan(params.tokenId, state.newDebtExchangeRateX96, state.newLendExchangeRateX96, owner);
 745: 
 746:         emit Liquidate(
 747:             params.tokenId,
 748:             msg.sender,
 749:             owner,
 750:             state.fullValue,
 751:             state.liquidatorCost,
 752:             amount0,
 753:             amount1,
 754:             state.reserveCost,
 755:             state.missing
 756:         );
 757:     }
1065:             nonfungiblePositionManager.decreaseLiquidity(
1066:                 INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp)
1067:             );
1070:         (amount0, amount1) = nonfungiblePositionManager.collect(
1071:             INonfungiblePositionManager.CollectParams(tokenId, recipient, fees0, fees1)
1072:         );
1083:         nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId);
1084:         emit Remove(tokenId, owner);
```

*GitHub* : [685-757](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L685-L757)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Utils.swap(V3Utils.SwapParams) (L#397-429):
	External calls:
	- _prepareAddPermit2(params.tokenIn,IERC20(address(0)),IERC20(address(0)),params.amountIn,0,0,pbtf,signature) (L#405-407)
		- weth.deposit{value: msg.value}() (L#667)
		- permit2.permitTransferFrom(permit,transferDetails,msg.sender,signature) (L#631)
	- _prepareAddApproved(params.tokenIn,IERC20(address(0)),IERC20(address(0)),params.amountIn,0,0) (L#409)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- weth.deposit{value: msg.value}() (L#667)
		- SafeERC20.safeTransferFrom(token0,msg.sender,address(this),needed0) (L#578)
		- SafeERC20.safeTransferFrom(token1,msg.sender,address(this),needed1) (L#581)
		- SafeERC20.safeTransferFrom(otherToken,msg.sender,address(this),neededOther) (L#584)
	- (amountInDelta,amountOut) = _routerSwap(Swapper.RouterSwapParams(params.tokenIn,params.tokenOut,params.amountIn,params.minAmountOut,params.swapData)) (L#413-417)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
	External calls sending eth:
	- _prepareAddPermit2(params.tokenIn,IERC20(address(0)),IERC20(address(0)),params.amountIn,0,0,pbtf,signature) (L#405-407)
		- weth.deposit{value: msg.value}() (L#667)
	- _prepareAddApproved(params.tokenIn,IERC20(address(0)),IERC20(address(0)),params.amountIn,0,0) (L#409)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- weth.deposit{value: msg.value}() (L#667)
	- (amountInDelta,amountOut) = _routerSwap(Swapper.RouterSwapParams(params.tokenIn,params.tokenOut,params.amountIn,params.minAmountOut,params.swapData)) (L#413-417)
		- (success,returndata) = target.call{value: value}(data) (L#135)
	Event emitted after the call(s):
	- Swap(address(params.tokenIn),address(params.tokenOut),amountInDelta,amountOutDelta) (L#116)
		- (amountInDelta,amountOut) = _routerSwap(Swapper.RouterSwapParams(params.tokenIn,params.tokenOut,params.amountIn,params.minAmountOut,params.swapData)) (L#413-417)

/// @audit ************** Possible Issue Line(s) **************
	L#405-407,  L#667,  L#631,  L#409,  L#578,  L#581,  L#584,  L#413-417,  

/// @audit ****************** Affected Code *******************
 397:     function swap(SwapParams calldata params) external payable returns (uint256 amountOut) {
 398:         if (params.tokenIn == params.tokenOut) {
 399:             revert SameToken();
 400:         }
 401: 
 402:         if (params.permitData.length > 0) {
 403:             (ISignatureTransfer.PermitBatchTransferFrom memory pbtf, bytes memory signature) =
 404:                 abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));
 405:             _prepareAddPermit2(
 406:                 params.tokenIn, IERC20(address(0)), IERC20(address(0)), params.amountIn, 0, 0, pbtf, signature
 407:             );
 408:         } else {
 409:             _prepareAddApproved(params.tokenIn, IERC20(address(0)), IERC20(address(0)), params.amountIn, 0, 0);
 410:         }
 411: 
 412:         uint256 amountInDelta;
 413:         (amountInDelta, amountOut) = _routerSwap(
 414:             Swapper.RouterSwapParams(
 415:                 params.tokenIn, params.tokenOut, params.amountIn, params.minAmountOut, params.swapData
 416:             )
 417:         );
 418: 
 419:         // send swapped amount of tokenOut
 420:         if (amountOut != 0) {
 421:             _transferToken(params.recipient, params.tokenOut, amountOut, params.unwrap);
 422:         }
 423: 
 424:         // if not all was swapped - return leftovers of tokenIn
 425:         uint256 leftOver = params.amountIn - amountInDelta;
 426:         if (leftOver != 0) {
 427:             _transferToken(params.recipient, params.tokenIn, leftOver, params.unwrap);
 428:         }
 429:     }
 578:             SafeERC20.safeTransferFrom(token0, msg.sender, address(this), needed0);
 581:             SafeERC20.safeTransferFrom(token1, msg.sender, address(this), needed1);
 584:             SafeERC20.safeTransferFrom(otherToken, msg.sender, address(this), neededOther);
 631:         permit2.permitTransferFrom(permit, transferDetails, msg.sender, signature);
 667:             weth.deposit{value: msg.value}();
```

*GitHub* : [397-429](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L397-L429)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Utils._swapAndPrepareAmounts(V3Utils.SwapAndMintParams,bool) (L#779-838):
	External calls:
	- (amountInDelta0,amountOutDelta0) = _routerSwap(Swapper.RouterSwapParams(params.swapSourceToken,params.token0,params.amountIn0,params.amountOut0Min,params.swapData0)) (L#806-810)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
	- (amountInDelta1,amountOutDelta1) = _routerSwap(Swapper.RouterSwapParams(params.swapSourceToken,params.token1,params.amountIn1,params.amountOut1Min,params.swapData1)) (L#811-815)
		- returndata = address(token).functionCall(data,SafeERC20: low-level call failed) (L#110)
		- (success,returndata) = target.call{value: value}(data) (L#135)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,params.amountIn) (L#87)
		- (success) = zeroxRouter.call(data.data) (L#89)
		- SafeERC20.safeApprove(params.tokenIn,data.allowanceTarget,0) (L#94)
		- SafeERC20.safeTransfer(params.tokenIn,universalRouter,params.amountIn) (L#98)
		- IUniversalRouter(universalRouter).execute(data_scope_0.commands,data_scope_0.inputs,data_scope_0.deadline) (L#99)
	External calls sending eth:
	- (amountInDelta0,amountOutDelta0) = _routerSwap(Swapper.RouterSwapParams(params.swapSourceToken,params.token0,params.amountIn0,params.amountOut0Min,params.swapData0)) (L#806-810)
		- (success,returndata) = target.call{value: value}(data) (L#135)
	- (amountInDelta1,amountOutDelta1) = _routerSwap(Swapper.RouterSwapParams(params.swapSourceToken,params.token1,params.amountIn1,params.amountOut1Min,params.swapData1)) (L#811-815)
		- (success,returndata) = target.call{value: value}(data) (L#135)
	Event emitted after the call(s):
	- Swap(address(params.tokenIn),address(params.tokenOut),amountInDelta,amountOutDelta) (L#116)
		- (amountInDelta1,amountOutDelta1) = _routerSwap(Swapper.RouterSwapParams(params.swapSourceToken,params.token1,params.amountIn1,params.amountOut1Min,params.swapData1)) (L#811-815)

/// @audit ************** Possible Issue Line(s) **************
	L#806-810,  L#811-815,  

/// @audit ****************** Affected Code *******************
 779:     function _swapAndPrepareAmounts(SwapAndMintParams memory params, bool unwrap)
 780:         internal
 781:         returns (uint256 total0, uint256 total1)
 782:     {
 783:         if (params.swapSourceToken == params.token0) {
 784:             if (params.amount0 < params.amountIn1) {
 785:                 revert AmountError();
 786:             }
 787:             (uint256 amountInDelta, uint256 amountOutDelta) = _routerSwap(
 788:                 Swapper.RouterSwapParams(
 789:                     params.token0, params.token1, params.amountIn1, params.amountOut1Min, params.swapData1
 790:                 )
 791:             );
 792:             total0 = params.amount0 - amountInDelta;
 793:             total1 = params.amount1 + amountOutDelta;
 794:         } else if (params.swapSourceToken == params.token1) {
 795:             if (params.amount1 < params.amountIn0) {
 796:                 revert AmountError();
 797:             }
 798:             (uint256 amountInDelta, uint256 amountOutDelta) = _routerSwap(
 799:                 Swapper.RouterSwapParams(
 800:                     params.token1, params.token0, params.amountIn0, params.amountOut0Min, params.swapData0
 801:                 )
 802:             );
 803:             total1 = params.amount1 - amountInDelta;
 804:             total0 = params.amount0 + amountOutDelta;
 805:         } else if (address(params.swapSourceToken) != address(0)) {
 806:             (uint256 amountInDelta0, uint256 amountOutDelta0) = _routerSwap(
 807:                 Swapper.RouterSwapParams(
 808:                     params.swapSourceToken, params.token0, params.amountIn0, params.amountOut0Min, params.swapData0
 809:                 )
 810:             );
 811:             (uint256 amountInDelta1, uint256 amountOutDelta1) = _routerSwap(
 812:                 Swapper.RouterSwapParams(
 813:                     params.swapSourceToken, params.token1, params.amountIn1, params.amountOut1Min, params.swapData1
 814:                 )
 815:             );
 816:             total0 = params.amount0 + amountOutDelta0;
 817:             total1 = params.amount1 + amountOutDelta1;
 818: 
 819:             // return third token leftover if any
 820:             uint256 leftOver = params.amountIn0 + params.amountIn1 - amountInDelta0 - amountInDelta1;
 821: 
 822:             if (leftOver != 0) {
 823:                 _transferToken(params.recipient, params.swapSourceToken, leftOver, unwrap);
 824:             }
 825:         } else {
 826:             total0 = params.amount0;
 827:             total1 = params.amount1;
 828:         }
 829: 
 830:         if (total0 != 0) {
 831:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), 0);
 832:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), total0);
 833:         }
 834:         if (total1 != 0) {
 835:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), 0);
 836:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), total1);
 837:         }
 838:     }
```

*GitHub* : [779-838](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L779-L838)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Vault._deposit(address,uint256,bool,bytes) (L#877-917):
	External calls:
	- permit2.permitTransferFrom(permit,ISignatureTransfer.SignatureTransferDetails(address(this),assets),msg.sender,signature) (L#896-898)
	- SafeERC20.safeTransferFrom(IERC20(asset),msg.sender,address(this),assets) (L#901)
	Event emitted after the call(s):
	- Deposit(msg.sender,receiver,assets,shares) (L#916)
	- Transfer(address(0),account,amount) (L#269)
		- _mint(receiver,shares) (L#904)

/// @audit ************** Possible Issue Line(s) **************
	L#896-898,  L#901,  L#916,  L#904,  

/// @audit ****************** Affected Code *******************
 877:     function _deposit(address receiver, uint256 amount, bool isShare, bytes memory permitData)
 878:         internal
 879:         returns (uint256 assets, uint256 shares)
 880:     {
 881:         (, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
 882: 
 883:         _resetDailyLendIncreaseLimit(newLendExchangeRateX96, false);
 884: 
 885:         if (isShare) {
 886:             shares = amount;
 887:             assets = _convertToAssets(shares, newLendExchangeRateX96, Math.Rounding.Up);
 888:         } else {
 889:             assets = amount;
 890:             shares = _convertToShares(assets, newLendExchangeRateX96, Math.Rounding.Down);
 891:         }
 892: 
 893:         if (permitData.length > 0) {
 894:             (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
 895:                 abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
 896:             permit2.permitTransferFrom(
 897:                 permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
 898:             );
 899:         } else {
 900:             // fails if not enough token approved
 901:             SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
 902:         }
 903: 
 904:         _mint(receiver, shares);
 905: 
 906:         if (totalSupply() > globalLendLimit) {
 907:             revert GlobalLendLimit();
 908:         }
 909: 
 910:         if (assets > dailyLendIncreaseLimitLeft) {
 911:             revert DailyLendIncreaseLimit();
 912:         } else {
 913:             dailyLendIncreaseLimitLeft -= assets;
 914:         }
 915: 
 916:         emit Deposit(msg.sender, receiver, assets, shares);
 917:     }
```

*GitHub* : [877-917](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L877-L917)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in V3Vault._cleanupLoan(uint256,uint256,uint256,address) (L#1077-1085):
	External calls:
	- nonfungiblePositionManager.safeTransferFrom(address(this),owner,tokenId) (L#1083)
	Event emitted after the call(s):
	- Remove(tokenId,owner) (L#1084)

/// @audit ************** Possible Issue Line(s) **************
	L#1083,  L#1084,  

/// @audit ****************** Affected Code *******************
1077:     function _cleanupLoan(uint256 tokenId, uint256 debtExchangeRateX96, uint256 lendExchangeRateX96, address owner)
1078:         internal
1079:     {
1080:         _removeTokenFromOwner(owner, tokenId);
1081:         _updateAndCheckCollateral(tokenId, debtExchangeRateX96, lendExchangeRateX96, loans[tokenId].debtShares, 0);
1082:         delete loans[tokenId];
1083:         nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId);
1084:         emit Remove(tokenId, owner);
1085:     }
```

*GitHub* : [1077-1085](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1077-L1085)

### [L-05]<a name="l-05"></a> Block timestamp

Dangerous usage of `block.timestamp`. `block.timestamp` can be manipulated by miners.  **Recom** Avoid relying on `block.timestamp`.

*There are 8 instance(s) of this issue:*

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault._resetDailyLendIncreaseLimit(uint256,bool) (L#1246-1256) uses timestamp for comparisons.
	Dangerous comparisons:
	- force || time > dailyLendIncreaseLimitLastReset (L#1249)

/// @audit ************** Possible Issue Line(s) **************
	L#1249,  

/// @audit ****************** Affected Code *******************
1246:     function _resetDailyLendIncreaseLimit(uint256 newLendExchangeRateX96, bool force) internal {
1247:         // daily lend limit reset handling
1248:         uint256 time = block.timestamp / 1 days;
1249:         if (force || time > dailyLendIncreaseLimitLastReset) {
1250:             uint256 lendIncreaseLimit = _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up)
1251:                 * (Q32 + MAX_DAILY_LEND_INCREASE_X32) / Q32;
1252:             dailyLendIncreaseLimitLeft =
1253:                 dailyLendIncreaseLimitMin > lendIncreaseLimit ? dailyLendIncreaseLimitMin : lendIncreaseLimit;
1254:             dailyLendIncreaseLimitLastReset = time;
1255:         }
1256:     }
```

*GitHub* : [1246-1256](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1246-L1256)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit ******************* Issue Detail *******************
AutoCompound._setBalance(uint256,address,uint256) (L#254-264) uses timestamp for comparisons.
	Dangerous comparisons:
	- amount != currentBalance (L#256)
	- amount > currentBalance (L#258)

/// @audit ************** Possible Issue Line(s) **************
	L#256,  L#258,  

/// @audit ****************** Affected Code *******************
 254:     function _setBalance(uint256 tokenId, address token, uint256 amount) internal {
 255:         uint256 currentBalance = positionBalances[tokenId][token];
 256:         if (amount != currentBalance) {
 257:             positionBalances[tokenId][token] = amount;
 258:             if (amount > currentBalance) {
 259:                 emit BalanceAdded(tokenId, token, amount - currentBalance);
 260:             } else {
 261:                 emit BalanceRemoved(tokenId, token, currentBalance - amount);
 262:             }
 263:         }
 264:     }
```

*GitHub* : [254-264](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L254-L264)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit ******************* Issue Detail *******************
AutoCompound.execute(AutoCompound.ExecuteParams) (L#101-193) uses timestamp for comparisons.
	Dangerous comparisons:
	- state.maxAddAmount0 > 0 || state.maxAddAmount1 > 0 (L#160)

/// @audit ************** Possible Issue Line(s) **************
	L#160,  

/// @audit ****************** Affected Code *******************
 101:     function execute(ExecuteParams calldata params) external nonReentrant {
 102:         if (!operators[msg.sender] && !vaults[msg.sender]) {
 103:             revert Unauthorized();
 104:         }
 105:         ExecuteState memory state;
 106: 
 107:         // collect fees - if the position doesn't have operator set or is called from vault - it won't work
 108:         (state.amount0, state.amount1) = nonfungiblePositionManager.collect(
 109:             INonfungiblePositionManager.CollectParams(
 110:                 params.tokenId, address(this), type(uint128).max, type(uint128).max
 111:             )
 112:         );
 113: 
 114:         // get position info
 115:         (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper,,,,,) =
 116:             nonfungiblePositionManager.positions(params.tokenId);
 117: 
 118:         // add previous balances from given tokens
 119:         state.amount0 = state.amount0 + positionBalances[params.tokenId][state.token0];
 120:         state.amount1 = state.amount1 + positionBalances[params.tokenId][state.token1];
 121: 
 122:         // only if there are balances to work with - start autocompounding process
 123:         if (state.amount0 > 0 || state.amount1 > 0) {
 124:             uint256 amountIn = params.amountIn;
 125: 
 126:             // if a swap is requested - check TWAP oracle
 127:             if (amountIn > 0) {
 128:                 IUniswapV3Pool pool = _getPool(state.token0, state.token1, state.fee);
 129:                 (state.sqrtPriceX96, state.tick,,,,,) = pool.slot0();
 130: 
 131:                 // how many seconds are needed for TWAP protection
 132:                 uint32 tSecs = TWAPSeconds;
 133:                 if (tSecs > 0) {
 134:                     if (!_hasMaxTWAPTickDifference(pool, tSecs, state.tick, maxTWAPTickDifference)) {
 135:                         // if there is no valid TWAP - disable swap
 136:                         amountIn = 0;
 137:                     }
 138:                 }
 139:                 // if still needed - do swap
 140:                 if (amountIn > 0) {
 141:                     // no slippage check done - because protected by TWAP check
 142:                     (state.amountInDelta, state.amountOutDelta) = _poolSwap(
 143:                         Swapper.PoolSwapParams(
 144:                             pool, IERC20(state.token0), IERC20(state.token1), state.fee, params.swap0To1, amountIn, 0
 145:                         )
 146:                     );
 147:                     state.amount0 =
 148:                         params.swap0To1 ? state.amount0 - state.amountInDelta : state.amount0 + state.amountOutDelta;
 149:                     state.amount1 =
 150:                         params.swap0To1 ? state.amount1 + state.amountOutDelta : state.amount1 - state.amountInDelta;
 151:                 }
 152:             }
 153: 
 154:             uint256 rewardX64 = totalRewardX64;
 155: 
 156:             state.maxAddAmount0 = state.amount0 * Q64 / (rewardX64 + Q64);
 157:             state.maxAddAmount1 = state.amount1 * Q64 / (rewardX64 + Q64);
 158: 
 159:             // deposit liquidity into tokenId
 160:             if (state.maxAddAmount0 > 0 || state.maxAddAmount1 > 0) {
 161:                 _checkApprovals(state.token0, state.token1);
 162: 
 163:                 (, state.compounded0, state.compounded1) = nonfungiblePositionManager.increaseLiquidity(
 164:                     INonfungiblePositionManager.IncreaseLiquidityParams(
 165:                         params.tokenId, state.maxAddAmount0, state.maxAddAmount1, 0, 0, block.timestamp
 166:                     )
 167:                 );
 168: 
 169:                 // fees are always calculated based on added amount (to incentivize optimal swap)
 170:                 state.amount0Fees = state.compounded0 * rewardX64 / Q64;
 171:                 state.amount1Fees = state.compounded1 * rewardX64 / Q64;
 172:             }
 173: 
 174:             // calculate remaining tokens for owner
 175:             _setBalance(params.tokenId, state.token0, state.amount0 - state.compounded0 - state.amount0Fees);
 176:             _setBalance(params.tokenId, state.token1, state.amount1 - state.compounded1 - state.amount1Fees);
 177: 
 178:             // add reward to protocol balance (token 0)
 179:             _increaseBalance(0, state.token0, state.amount0Fees);
 180:             _increaseBalance(0, state.token1, state.amount1Fees);
 181:         }
 182: 
 183:         emit AutoCompounded(
 184:             msg.sender,
 185:             params.tokenId,
 186:             state.compounded0,
 187:             state.compounded1,
 188:             state.amount0Fees,
 189:             state.amount1Fees,
 190:             state.token0,
 191:             state.token1
 192:         );
 193:     }
```

*GitHub* : [101-193](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L101-L193)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault._calculateGlobalInterest() (L#1167-1195) uses timestamp for comparisons.
	Dangerous comparisons:
	- lastRateUpdate > 0 (L#1186)

/// @audit ************** Possible Issue Line(s) **************
	L#1186,  

/// @audit ****************** Affected Code *******************
1167:     function _calculateGlobalInterest()
1168:         internal
1169:         view
1170:         returns (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96)
1171:     {
1172:         uint256 oldDebtExchangeRateX96 = lastDebtExchangeRateX96;
1173:         uint256 oldLendExchangeRateX96 = lastLendExchangeRateX96;
1174: 
1175:         (, uint256 available,) = _getAvailableBalance(oldDebtExchangeRateX96, oldLendExchangeRateX96);
1176: 
1177:         uint256 debt = _convertToAssets(debtSharesTotal, oldDebtExchangeRateX96, Math.Rounding.Up);
1178: 
1179:         (uint256 borrowRateX96, uint256 supplyRateX96) = interestRateModel.getRatesPerSecondX96(available, debt);
1180: 
1181:         supplyRateX96 = supplyRateX96.mulDiv(Q32 - reserveFactorX32, Q32);
1182: 
1183:         // always growing or equal
1184:         uint256 lastRateUpdate = lastExchangeRateUpdate;
1185: 
1186:         if (lastRateUpdate > 0) {
1187:             newDebtExchangeRateX96 = oldDebtExchangeRateX96
1188:                 + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;
1189:             newLendExchangeRateX96 = oldLendExchangeRateX96
1190:                 + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;
1191:         } else {
1192:             newDebtExchangeRateX96 = oldDebtExchangeRateX96;
1193:             newLendExchangeRateX96 = oldLendExchangeRateX96;
1194:         }
1195:     }
```

*GitHub* : [1167-1195](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1167-L1195)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault._resetDailyDebtIncreaseLimit(uint256,bool) (L#1258-1268) uses timestamp for comparisons.
	Dangerous comparisons:
	- force || time > dailyDebtIncreaseLimitLastReset (L#1261)

/// @audit ************** Possible Issue Line(s) **************
	L#1261,  

/// @audit ****************** Affected Code *******************
1258:     function _resetDailyDebtIncreaseLimit(uint256 newLendExchangeRateX96, bool force) internal {
1259:         // daily debt limit reset handling
1260:         uint256 time = block.timestamp / 1 days;
1261:         if (force || time > dailyDebtIncreaseLimitLastReset) {
1262:             uint256 debtIncreaseLimit = _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up)
1263:                 * (Q32 + MAX_DAILY_DEBT_INCREASE_X32) / Q32;
1264:             dailyDebtIncreaseLimitLeft =
1265:                 dailyDebtIncreaseLimitMin > debtIncreaseLimit ? dailyDebtIncreaseLimitMin : debtIncreaseLimit;
1266:             dailyDebtIncreaseLimitLastReset = time;
1267:         }
1268:     }
```

*GitHub* : [1258-1268](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1258-L1268)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit ******************* Issue Detail *******************
AutoCompound._checkApprovals(address,address) (L#276-286) uses timestamp for comparisons.
	Dangerous comparisons:
	- allowance0 == 0 (L#279)
	- allowance1 == 0 (L#283)

/// @audit ************** Possible Issue Line(s) **************
	L#279,  L#283,  

/// @audit ****************** Affected Code *******************
 276:     function _checkApprovals(address token0, address token1) internal {
 277:         // approve tokens once if not yet approved - to save gas during compounds
 278:         uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager));
 279:         if (allowance0 == 0) {
 280:             SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max);
 281:         }
 282:         uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager));
 283:         if (allowance1 == 0) {
 284:             SafeERC20.safeApprove(IERC20(token1), address(nonfungiblePositionManager), type(uint256).max);
 285:         }
 286:     }
```

*GitHub* : [276-286](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L276-L286)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
V3Oracle._getChainlinkPriceX96(address) (L#329-343) uses timestamp for comparisons.
	Dangerous comparisons:
	- updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0 (L#338)

/// @audit ************** Possible Issue Line(s) **************
	L#338,  

/// @audit ****************** Affected Code *******************
 329:     function _getChainlinkPriceX96(address token) internal view returns (uint256) {
 330:         if (token == chainlinkReferenceToken) {
 331:             return Q96;
 332:         }
 333: 
 334:         TokenConfig memory feedConfig = feedConfigs[token];
 335: 
 336:         // if stale data - revert
 337:         (, int256 answer,, uint256 updatedAt,) = feedConfig.feed.latestRoundData();
 338:         if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0) {
 339:             revert ChainlinkPriceError();
 340:         }
 341: 
 342:         return uint256(answer) * Q96 / (10 ** feedConfig.feedDecimals);
 343:     }
```

*GitHub* : [329-343](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L329-L343)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault._updateGlobalInterest() (L#1150-1165) uses timestamp for comparisons.
	Dangerous comparisons:
	- block.timestamp > lastExchangeRateUpdate (L#1155)

/// @audit ************** Possible Issue Line(s) **************
	L#1155,  

/// @audit ****************** Affected Code *******************
1150:     function _updateGlobalInterest()
1151:         internal
1152:         returns (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96)
1153:     {
1154:         // only needs to be updated once per block (when needed)
1155:         if (block.timestamp > lastExchangeRateUpdate) {
1156:             (newDebtExchangeRateX96, newLendExchangeRateX96) = _calculateGlobalInterest();
1157:             lastDebtExchangeRateX96 = newDebtExchangeRateX96;
1158:             lastLendExchangeRateX96 = newLendExchangeRateX96;
1159:             lastExchangeRateUpdate = block.timestamp;
1160:             emit ExchangeRateUpdate(newDebtExchangeRateX96, newLendExchangeRateX96);
1161:         } else {
1162:             newDebtExchangeRateX96 = lastDebtExchangeRateX96;
1163:             newLendExchangeRateX96 = lastLendExchangeRateX96;
1164:         }
1165:     }
```

*GitHub* : [1150-1165](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1150-L1165)

### [L-06]<a name="l-06"></a> `approve()`/`safeApprove()` may revert if the current approval is not zero

- Some tokens (like the *very popular* USDT) do not work when changing the allowance from an existing non-zero allowance value (it will revert if the current approval is not zero to protect against front-running changes of approvals). These tokens must first be approved for zero and then the actual allowance can be approved.
- Furthermore, OZ's implementation of safeApprove would throw an error if an approve is attempted from a non-zero value (`"SafeERC20: approve from non-zero to non-zero allowance"`)

Set the allowance to zero immediately before each of the existing allowance calls

*There are 17 instance(s) of this issue:*

```solidity
File: src/V3Vault.sol

520:         nonfungiblePositionManager.approve(transformer, tokenId);

537:         nonfungiblePositionManager.approve(address(0), tokenId);

```



*GitHub* : [520](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L520), [537](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L537)

```solidity
File: src/transformers/AutoCompound.sol

280:             SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max);

284:             SafeERC20.safeApprove(IERC20(token1), address(nonfungiblePositionManager), type(uint256).max);

```



*GitHub* : [280](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L280), [284](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L284)

```solidity
File: src/transformers/AutoRange.sol

213:             SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), state.maxAddAmount0);

214:             SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), state.maxAddAmount1);

220:             SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), 0);

221:             SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), 0);

```



*GitHub* : [213](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L213), [214](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L214), [220](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L220), [221](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L221)

```solidity
File: src/transformers/LeverageTransformer.sol

165:         SafeERC20.safeApprove(IERC20(token), msg.sender, amount);

```



*GitHub* : [165](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L165)

```solidity
File: src/transformers/V3Utils.sol

831:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), 0);

832:             SafeERC20.safeApprove(params.token0, address(nonfungiblePositionManager), total0);

835:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), 0);

836:             SafeERC20.safeApprove(params.token1, address(nonfungiblePositionManager), total1);

```



*GitHub* : [831](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L831), [832](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L832), [835](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L835), [836](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L836)

```solidity
File: src/utils/FlashloanLiquidator.sol

72:         SafeERC20.safeApprove(data.asset, address(data.vault), data.liquidationCost);

78:         SafeERC20.safeApprove(data.asset, address(data.vault), 0);

```



*GitHub* : [72](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L72), [78](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L78)

```solidity
File: src/utils/Swapper.sol

87:                 SafeERC20.safeApprove(params.tokenIn, data.allowanceTarget, params.amountIn);

94:                 SafeERC20.safeApprove(params.tokenIn, data.allowanceTarget, 0);

```


*GitHub* : [87](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L87), [94](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L94)

### [L-07]<a name="l-07"></a> Use a 2-step ownership transfer pattern

Recommend considering implementing a two step process where the owner or admin nominates an account and the nominated account needs to call an `acceptOwnership()` function for the transfer of ownership to fully succeed. This ensures the nominated EOA account is a valid and active account. Lack of two-step procedure for critical operations leaves them error-prone. Consider adding two step procedure on the critical functions.

*There are 4 instance(s) of this issue:*

```solidity
File: src/InterestRateModel.sol

11: contract InterestRateModel is Ownable, IInterestRateModel, IErrors {

```



*GitHub* : [11](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L11)

```solidity
File: src/V3Oracle.sol

24: contract V3Oracle is IV3Oracle, Ownable, IErrors {

```



*GitHub* : [24](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L24)

```solidity
File: src/V3Vault.sol

30: contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors {

```



*GitHub* : [30](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L30)

```solidity
File: src/automators/Automator.sol

19: abstract contract Automator is Swapper, Ownable {

```


*GitHub* : [19](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L19)

### [L-08]<a name="l-08"></a> `decimals()` is not a part of the ERC-20 standard

The `decimals()` function is not a part of the [ERC-20 standard](https://eips.ethereum.org/EIPS/eip-20), and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.

*There are 4 instance(s) of this issue:*

```solidity
File: src/V3Oracle.sol

82:         referenceTokenDecimals = IERC20Metadata(_referenceToken).decimals();

215:         uint8 feedDecimals = feed.decimals();			//Not reproted so far

216:         uint8 tokenDecimals = IERC20Metadata(token).decimals();

```



*GitHub* : [82](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L82), [215](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L215), [216](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L216)

```solidity
File: src/V3Vault.sol

179:         assetDecimals = IERC20Metadata(_asset).decimals();

```


*GitHub* : [179](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L179)

### [L-09]<a name="l-09"></a> Deprecated approve() function

Due to the inheritance of ERC20's approve function, there's a vulnerability to the ERC20 approve and double spend front running attack. Briefly, an authorized spender could spend both allowances by front running an allowance-changing transaction. 

*There are 2 instance(s) of this issue:*

```solidity
File: src/V3Vault.sol

520:         nonfungiblePositionManager.approve(transformer, tokenId);

537:         nonfungiblePositionManager.approve(address(0), tokenId);

```


*GitHub* : [520](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L520), [537](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L537)

### [L-10]<a name="l-10"></a> Division by zero not prevented

The divisions below take an input parameter which does not have any zero-value checks, which may lead to the functions reverting when zero is passed.

*There are 49 instance(s) of this issue:*

```solidity
File: src/InterestRateModel.sol

50:         return debt * Q96 / (cash + debt);

67:             borrowRateX96 = (utilizationRateX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;

69:             uint256 normalRateX96 = (kinkX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;

71:             borrowRateX96 = (excessUtilX96 * jumpMultiplierPerSecondX96 / Q96) + normalRateX96;

74:         supplyRateX96 = utilizationRateX96 * borrowRateX96 / Q96;

```



*GitHub* : [50](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L50), [67](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L67), [69](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L69), [71](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L71), [74](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L74)

```solidity
File: src/V3Oracle.sol

120:         value = (price0X96 * (amount0 + fees0) / Q96 + price1X96 * (amount1 + fees1) / Q96) * Q96 / priceTokenX96;

121:         feeValue = (price0X96 * fees0 / Q96 + price1X96 * fees1 / Q96) * Q96 / priceTokenX96;

122:         price0X96 = price0X96 * Q96 / priceTokenX96;

123:         price1X96 = price1X96 * Q96 / priceTokenX96;

129:         uint256 derivedPoolPriceX96 = price0X96 * Q96 / price1X96;

144:             ? (priceX96 - verifyPriceX96) * 10000 / priceX96

145:             : (verifyPriceX96 - priceX96) * 10000 / verifyPriceX96;

304:             chainlinkPriceX96 = (10 ** referenceTokenDecimals) * chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96

305:                 / (10 ** feedConfig.tokenDecimals);

342:         return uint256(answer) * Q96 / (10 ** feedConfig.feedDecimals);

353:             poolTWAPPriceX96 = Q96 * Q96 / priceX96;

369:             int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)));

```



*GitHub* : [120](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L120), [121](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L121), [122](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L122), [123](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L123), [129](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L129), [144](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L144), [145](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L145), [304](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L304), [305](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L305), [342](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L342), [353](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L353), [369](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L369)

```solidity
File: src/V3Vault.sol

769:             _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up) * reserveProtectionFactorX32 / Q32;

1054:                 fees0 = uint128(liquidationValue * fees0 / feeValue);

1055:                 fees1 = uint128(liquidationValue * fees1 / feeValue);

1060:                 liquidity = uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue));

1100:         uint256 maxPenaltyValue = debt * (Q32 + MAX_LIQUIDATION_PENALTY_X32) / Q32;

1105:             uint256 startLiquidationValue = debt * fullValue / collateralValue;

1107:                 (Q96 - ((fullValue - maxPenaltyValue) * Q96 / (startLiquidationValue - maxPenaltyValue)));

1109:                 + (MAX_LIQUIDATION_PENALTY_X32 - MIN_LIQUIDATION_PENALTY_X32) * penaltyFractionX96 / Q96;

1111:             liquidationValue = debt * (Q32 + penaltyX32) / Q32;

1116:             uint256 penaltyValue = fullValue * (Q32 - MAX_LIQUIDATION_PENALTY_X32) / Q32;

1137:             newLendExchangeRateX96 = (totalLent - missing) * newLendExchangeRateX96 / totalLent;

1188:                 + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;

1190:                 + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;

1230:                             > lentAssets * collateralValueLimitFactorX32 / Q32

1238:                             > lentAssets * collateralValueLimitFactorX32 / Q32

```



*GitHub* : [769](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L769), [1054](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1054), [1055](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1055), [1060](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1060), [1100](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1100), [1105](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1105), [1107](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1107), [1109](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1109), [1111](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1111), [1116](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1116), [1137](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1137), [1188](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1188), [1190](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1190), [1230](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1230), [1238](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1238)

```solidity
File: src/automators/AutoExit.sol

155:                 state.amount0 -= state.feeAmount0 * params.rewardX64 / Q64;

156:                 state.amount1 -= state.feeAmount1 * params.rewardX64 / Q64;

187:                     state.amount0 -= state.amount0 * params.rewardX64 / Q64;

189:                     state.amount1 -= state.amount1 * params.rewardX64 / Q64;

194:             state.amount0 -= (config.onlyFees ? state.feeAmount0 : state.amount0) * params.rewardX64 / Q64;

195:             state.amount1 -= (config.onlyFees ? state.feeAmount1 : state.amount1) * params.rewardX64 / Q64;

```



*GitHub* : [155](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L155), [156](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L156), [187](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L187), [189](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L189), [194](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L194), [195](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L195)

```solidity
File: src/automators/Automator.sol

187:             return (int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapPeriod))), true);

```



*GitHub* : [187](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L187)

```solidity
File: src/transformers/AutoCompound.sol

156:             state.maxAddAmount0 = state.amount0 * Q64 / (rewardX64 + Q64);

157:             state.maxAddAmount1 = state.amount1 * Q64 / (rewardX64 + Q64);

170:                 state.amount0Fees = state.compounded0 * rewardX64 / Q64;

171:                 state.amount1Fees = state.compounded1 * rewardX64 / Q64;

```



*GitHub* : [156](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L156), [157](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L157), [170](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L170), [171](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L171)

```solidity
File: src/transformers/AutoRange.sol

143:             state.protocolReward0 = state.feeAmount0 * params.rewardX64 / Q64;

144:             state.protocolReward1 = state.feeAmount1 * params.rewardX64 / Q64;

195:             state.maxAddAmount0 = config.onlyFees ? state.amount0 : state.amount0 * Q64 / (params.rewardX64 + Q64);

196:             state.maxAddAmount1 = config.onlyFees ? state.amount1 : state.amount1 * Q64 / (params.rewardX64 + Q64);

236:                 state.protocolReward0 = state.amountAdded0 * params.rewardX64 / Q64;

237:                 state.protocolReward1 = state.amountAdded1 * params.rewardX64 / Q64;

```


*GitHub* : [143](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L143), [144](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L144), [195](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L195), [196](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L196), [236](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L236), [237](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L237)

### [L-11]<a name="l-11"></a> External call recipient may consume all transaction gas

There is no limit specified on the amount of gas used, so the recipient can use up all of the transaction's gas, causing it to revert. Use `addr.call{gas: <amount>}("")` or [this](https://github.com/nomad-xyz/ExcessivelySafeCall) library instead.

*There are 5 instance(s) of this issue:*

```solidity
File: src/V3Vault.sol

522:         (bool success,) = transformer.call(data);

```



*GitHub* : [522](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L522)

```solidity
File: src/automators/Automator.sol

130:             (bool sent,) = to.call{value: balance}("");

221:             (bool sent,) = to.call{value: amount}("");

```



*GitHub* : [130](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L130), [221](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L221)

```solidity
File: src/transformers/V3Utils.sol

867:             (bool sent,) = to.call{value: amount}("");

```



*GitHub* : [867](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L867)

```solidity
File: src/utils/Swapper.sol

89:                 (bool success,) = zeroxRouter.call(data.data);

```


*GitHub* : [89](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L89)

### [L-12]<a name="l-12"></a> Signature use at deadlines should be allowed

According to [EIP-2612](https://github.com/ethereum/EIPs/blob/71dc97318013bf2ac572ab63fab530ac9ef419ca/EIPS/eip-2612.md?plain=1#L58), signatures used on exactly the deadline timestamp are supposed to be allowed. While the signature may or may not be used for the exact EIP-2612 use case (transfer approvals), for consistency's sake, all deadlines should follow this semantic. If the timestamp is an expiration rather than a deadline, consider whether it makes more sense to include the expiration timestamp as a valid timestamp, as is done for deadlines.

*There are 1 instance(s) of this issue:*

```solidity
File: src/V3Oracle.sol

338:         if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0) {

```


*GitHub* : [338](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L338)

### [L-13]<a name="l-13"></a> Possible rounding issue

Division by large numbers may result in the result being zero, due to solidity not supporting fractions. Consider requiring a minimum amount for the numerator to ensure that it is always larger than the denominator. Also, there is indication of multiplication and division without the use of parenthesis which could result in issues.

*There are 5 instance(s) of this issue:*

```solidity
File: src/InterestRateModel.sol

95:         baseRatePerSecondX96 = baseRatePerYearX96 / YEAR_SECS;

96:         multiplierPerSecondX96 = multiplierPerYearX96 / YEAR_SECS;

97:         jumpMultiplierPerSecondX96 = jumpMultiplierPerYearX96 / YEAR_SECS;

```



*GitHub* : [95](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L95), [96](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L96), [97](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L97)

```solidity
File: src/V3Vault.sol

1107:                 (Q96 - ((fullValue - maxPenaltyValue) * Q96 / (startLiquidationValue - maxPenaltyValue)));

1137:             newLendExchangeRateX96 = (totalLent - missing) * newLendExchangeRateX96 / totalLent;

```


*GitHub* : [1107](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1107), [1137](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1137)

### [L-14]<a name="l-14"></a> Use `Ownable2Step.transferOwnership` instead of `Ownable.transferOwnership`

Use [Ownable2Step.transferOwnership](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/Ownable2Step.sol) which is safer. Use it as it is more secure due to 2-stage ownership transfer.

**Recommended Mitigation Steps**

Use <a href="https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/Ownable2Step.sol">Ownable2Step.sol</a>
  
  ```solidity
      function acceptOwnership() external {
          address sender = _msgSender();
          require(pendingOwner() == sender, "Ownable2Step: caller is not the new owner");
          _transferOwnership(sender);
      }
```

*There are 4 instance(s) of this issue:*

```solidity
File: src/InterestRateModel.sol

4: import "@openzeppelin/contracts/access/Ownable.sol";

```



*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L4)

```solidity
File: src/V3Oracle.sol

15: import "@openzeppelin/contracts/access/Ownable.sol";

```



*GitHub* : [15](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L15)

```solidity
File: src/V3Vault.sol

16: import "@openzeppelin/contracts/access/Ownable.sol";

```



*GitHub* : [16](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L16)

```solidity
File: src/automators/Automator.sol

4: import "@openzeppelin/contracts/access/Ownable.sol";

```


*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L4)

### [L-15]<a name="l-15"></a> File allows a version of solidity that is susceptible to an assembly optimizer bug

In solidity versions 0.8.13 and 0.8.14, there is an [optimizer bug](https://github.com/ethereum/solidity-blog/blob/499ab8abc19391be7b7b34f88953a067029a5b45/_posts/2022-06-15-inline-assembly-memory-side-effects-bug.md) where, if the use of a variable is in a separate `assembly` block from the block in which it was stored, the `mstore` operation is optimized out, leading to uninitialized memory. The code currently does not have such a pattern of execution, but it does use `mstore`s in `assembly` blocks, so it is a risk for future changes. The affected solidity versions should be avoided if at all possible.

*There are 9 instance(s) of this issue:*

```solidity
File: src/InterestRateModel.sol

2: pragma solidity ^0.8.0;

```



*GitHub* : [2](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L2)

```solidity
File: src/V3Oracle.sol

2: pragma solidity ^0.8.0;

```



*GitHub* : [2](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L2)

```solidity
File: src/V3Vault.sol

2: pragma solidity ^0.8.0;

```



*GitHub* : [2](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L2)

```solidity
File: src/automators/AutoExit.sol

2: pragma solidity ^0.8.0;

```



*GitHub* : [2](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L2)

```solidity
File: src/transformers/AutoCompound.sol

2: pragma solidity ^0.8.0;

```



*GitHub* : [2](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L2)

```solidity
File: src/transformers/AutoRange.sol

2: pragma solidity ^0.8.0;

```



*GitHub* : [2](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L2)

```solidity
File: src/transformers/LeverageTransformer.sol

2: pragma solidity ^0.8.0;

```



*GitHub* : [2](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L2)

```solidity
File: src/transformers/V3Utils.sol

2: pragma solidity ^0.8.0;

```



*GitHub* : [2](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L2)

```solidity
File: src/utils/FlashloanLiquidator.sol

2: pragma solidity ^0.8.0;

```


*GitHub* : [2](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L2)

### [L-16]<a name="l-16"></a> Consider using OpenZeppelin's SafeCast library to prevent unexpected overflows when downcasting

Downcasting from `uint256`/`int256` in Solidity does not revert on overflow. This can result in undesired exploitation or bugs, since developers usually assume that overflows raise errors. [OpenZeppelin's SafeCast library](https://docs.openzeppelin.com/contracts/3.x/api/utils#SafeCast) restores this intuition by reverting the transaction when such an operation overflows. Using this library eliminates an entire class of bugs, so it's recommended to use it always. Some exceptions are acceptable like with the classic `uint256(uint160(address(variable)))`

*There are 12 instance(s) of this issue:*

```solidity
File: src/V3Oracle.sol

467:         fees0 = uint128(FullMath.mulDiv(feeGrowth0, position.liquidity, Q128));

468:         fees1 = uint128(FullMath.mulDiv(feeGrowth1, position.liquidity, Q128));

```



*GitHub* : [467](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L467), [468](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L468)

```solidity
File: src/V3Vault.sol

36:     uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%

38:     uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%

39:     uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%

41:     uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%

43:     uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%

44:     uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%

1054:                 fees0 = uint128(liquidationValue * fees0 / feeValue);

1055:                 fees1 = uint128(liquidationValue * fees1 / feeValue);

1060:                 liquidity = uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue));

```



*GitHub* : [36](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L36), [38](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L38), [39](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L39), [41](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L41), [43](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L43), [44](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L44), [1054](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1054), [1055](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1055), [1060](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1060)

```solidity
File: src/transformers/AutoCompound.sol

47:     uint64 public constant MAX_REWARD_X64 = uint64(Q64 / 50); // 2%

```


*GitHub* : [47](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L47)

### [L-17]<a name="l-17"></a> Unsafe ERC20 operation(s)



*There are 2 instance(s) of this issue:*

```solidity
File: src/V3Vault.sol

520:         nonfungiblePositionManager.approve(transformer, tokenId);

537:         nonfungiblePositionManager.approve(address(0), tokenId);

```


*GitHub* : [520](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L520), [537](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L537)

### [L-18]<a name="l-18"></a> Upgradeable contract not initialized

Upgradeable contracts are initialized via an initializer function rather than by a constructor. Leaving such a contract uninitialized may lead to it being taken over by a malicious user

*There are 2 instance(s) of this issue:*

```solidity
File: src/V3Oracle.sol

177:         PositionState memory state = _initializeState(tokenId);

395:     function _initializeState(uint256 tokenId) internal view returns (PositionState memory state) {

```


*GitHub* : [177](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L177), [395](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L395)

### [L-19]<a name="l-19"></a> Divide before multiply

Solidity  **Recom** Consider ordering multiplication before division.

*There are 1 instance(s) of this issue:*

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
V3Oracle.getValue(uint256,address) (L#95-131) performs a multiplication on the result of a division:
	- price0X96 = price0X96 * Q96 / priceTokenX96 (L#122)
	- derivedPoolPriceX96 = price0X96 * Q96 / price1X96 (L#129)

/// @audit ************** Possible Issue Line(s) **************
	L#122,  L#129,  

/// @audit ****************** Affected Code *******************
  95:     function getValue(uint256 tokenId, address token)
  96:         external
  97:         view
  98:         override
  99:         returns (uint256 value, uint256 feeValue, uint256 price0X96, uint256 price1X96)
 100:     {
 101:         (address token0, address token1, uint24 fee,, uint256 amount0, uint256 amount1, uint256 fees0, uint256 fees1) =
 102:             getPositionBreakdown(tokenId);
 103: 
 104:         uint256 cachedChainlinkReferencePriceX96;
 105: 
 106:         (price0X96, cachedChainlinkReferencePriceX96) =
 107:             _getReferenceTokenPriceX96(token0, cachedChainlinkReferencePriceX96);
 108:         (price1X96, cachedChainlinkReferencePriceX96) =
 109:             _getReferenceTokenPriceX96(token1, cachedChainlinkReferencePriceX96);
 110: 
 111:         uint256 priceTokenX96;
 112:         if (token0 == token) {
 113:             priceTokenX96 = price0X96;
 114:         } else if (token1 == token) {
 115:             priceTokenX96 = price1X96;
 116:         } else {
 117:             (priceTokenX96,) = _getReferenceTokenPriceX96(token, cachedChainlinkReferencePriceX96);
 118:         }
 119: 
 120:         value = (price0X96 * (amount0 + fees0) / Q96 + price1X96 * (amount1 + fees1) / Q96) * Q96 / priceTokenX96;
 121:         feeValue = (price0X96 * fees0 / Q96 + price1X96 * fees1 / Q96) * Q96 / priceTokenX96;
 122:         price0X96 = price0X96 * Q96 / priceTokenX96;
 123:         price1X96 = price1X96 * Q96 / priceTokenX96;
 124: 
 125:         // checks derived pool price for price manipulation attacks
 126:         // this prevents manipulations of pool to get distorted proportions of collateral tokens - for borrowing
 127:         // when a pool is in this state, liquidations will be disabled - but arbitrageurs (or liquidator himself)
 128:         // will move price back to reasonable range and enable liquidation
 129:         uint256 derivedPoolPriceX96 = price0X96 * Q96 / price1X96;
 130:         _checkPoolPrice(token0, token1, fee, derivedPoolPriceX96);
 131:     }
```

*GitHub* : [95-131](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L95-L131)

### [L-20]<a name="l-20"></a> Dangerous strict equalities

Use of strict equalities that can be easily manipulated by an attacker.  **Recom** Don

*There are 1 instance(s) of this issue:*

```solidity
File: src/transformers/AutoCompound.sol

/// @audit ******************* Issue Detail *******************
AutoCompound._checkApprovals(address,address) (L#276-286) uses a dangerous strict equality:
	- allowance1 == 0 (L#283)

/// @audit ************** Possible Issue Line(s) **************
	L#283,  

/// @audit ****************** Affected Code *******************
 276:     function _checkApprovals(address token0, address token1) internal {
 277:         // approve tokens once if not yet approved - to save gas during compounds
 278:         uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager));
 279:         if (allowance0 == 0) {
 280:             SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max);
 281:         }
 282:         uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager));
 283:         if (allowance1 == 0) {
 284:             SafeERC20.safeApprove(IERC20(token1), address(nonfungiblePositionManager), type(uint256).max);
 285:         }
 286:     }
```

*GitHub* : [276-286](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L276-L286)

### [L-21]<a name="l-21"></a> Unused return

The return value of an external call is not stored in a local or state variable.  **Recom** Ensure that all the return values of the function calls are used.

*There are 22 instance(s) of this issue:*

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit ******************* Issue Detail *******************
LeverageTransformer.leverageUp(LeverageTransformer.LeverageUpParams) (L#40-96) ignores return value by:
	- (token0,token1) = nonfungiblePositionManager.positions(params.tokenId) (L#47)

/// @audit ************** Possible Issue Line(s) **************
	L#47,  

/// @audit ****************** Affected Code *******************
  40:     function leverageUp(LeverageUpParams calldata params) external {
  41:         uint256 amount = params.borrowAmount;
  42: 
  43:         address token = IVault(msg.sender).asset();
  44: 
  45:         IVault(msg.sender).borrow(params.tokenId, amount);
  46: 
  47:         (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(params.tokenId);
  48: 
  49:         uint256 amount0 = token == token0 ? amount : 0;
  50:         uint256 amount1 = token == token1 ? amount : 0;
  51: 
  52:         if (params.amountIn0 > 0) {
  53:             (uint256 amountIn, uint256 amountOut) = _routerSwap(
  54:                 Swapper.RouterSwapParams(
  55:                     IERC20(token), IERC20(token0), params.amountIn0, params.amountOut0Min, params.swapData0
  56:                 )
  57:             );
  58:             if (token == token1) {
  59:                 amount1 -= amountIn;
  60:             }
  61:             amount -= amountIn;
  62:             amount0 += amountOut;
  63:         }
  64:         if (params.amountIn1 > 0) {
  65:             (uint256 amountIn, uint256 amountOut) = _routerSwap(
  66:                 Swapper.RouterSwapParams(
  67:                     IERC20(token), IERC20(token1), params.amountIn1, params.amountOut1Min, params.swapData1
  68:                 )
  69:             );
  70:             if (token == token0) {
  71:                 amount0 -= amountIn;
  72:             }
  73:             amount -= amountIn;
  74:             amount1 += amountOut;
  75:         }
  76: 
  77:         SafeERC20.safeIncreaseAllowance(IERC20(token0), address(nonfungiblePositionManager), amount0);
  78:         SafeERC20.safeIncreaseAllowance(IERC20(token1), address(nonfungiblePositionManager), amount1);
  79: 
  80:         INonfungiblePositionManager.IncreaseLiquidityParams memory increaseLiquidityParams = INonfungiblePositionManager
  81:             .IncreaseLiquidityParams(
  82:             params.tokenId, amount0, amount1, params.amountAddMin0, params.amountAddMin1, params.deadline
  83:         );
  84:         (, uint256 added0, uint256 added1) = nonfungiblePositionManager.increaseLiquidity(increaseLiquidityParams);
  85: 
  86:         // send leftover tokens
  87:         if (amount0 > added0) {
  88:             SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0 - added0);
  89:         }
  90:         if (amount1 > added1) {
  91:             SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1 - added1);
  92:         }
  93:         if (token != token0 && token != token1 && amount > 0) {
  94:             SafeERC20.safeTransfer(IERC20(token), params.recipient, amount);
  95:         }
  96:     }
```

*GitHub* : [40-96](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L40-L96)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit ******************* Issue Detail *******************
AutoCompound.withdrawLeftoverBalances(uint256,address) (L#200-219) ignores return value by:
	- (token0,token1) = nonfungiblePositionManager.positions(tokenId) (L#209)

/// @audit ************** Possible Issue Line(s) **************
	L#209,  

/// @audit ****************** Affected Code *******************
 200:     function withdrawLeftoverBalances(uint256 tokenId, address to) external nonReentrant {
 201:         address owner = nonfungiblePositionManager.ownerOf(tokenId);
 202:         if (vaults[owner]) {
 203:             owner = IVault(owner).ownerOf(tokenId);
 204:         }
 205:         if (owner != msg.sender) {
 206:             revert Unauthorized();
 207:         }
 208: 
 209:         (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(tokenId);
 210: 
 211:         uint256 balance0 = positionBalances[tokenId][token0];
 212:         if (balance0 > 0) {
 213:             _withdrawBalanceInternal(tokenId, token0, to, balance0, balance0);
 214:         }
 215:         uint256 balance1 = positionBalances[tokenId][token1];
 216:         if (balance1 > 0) {
 217:             _withdrawBalanceInternal(tokenId, token1, to, balance1, balance1);
 218:         }
 219:     }
```

*GitHub* : [200-219](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L200-L219)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
V3Oracle._getReferencePoolPriceX96(IUniswapV3Pool,uint32) (L#359-374) ignores return value by:
	- (sqrtPriceX96,None,None,None,None,None,None) = pool.slot0() (L#363)

/// @audit ************** Possible Issue Line(s) **************
	L#363,  

/// @audit ****************** Affected Code *******************
 359:     function _getReferencePoolPriceX96(IUniswapV3Pool pool, uint32 twapSeconds) internal view returns (uint256) {
 360:         uint160 sqrtPriceX96;
 361:         // if twap seconds set to 0 just use pool price
 362:         if (twapSeconds == 0) {
 363:             (sqrtPriceX96,,,,,,) = pool.slot0();
 364:         } else {
 365:             uint32[] memory secondsAgos = new uint32[](2);
 366:             secondsAgos[0] = 0; // from (before)
 367:             secondsAgos[1] = twapSeconds; // from (before)
 368:             (int56[] memory tickCumulatives,) = pool.observe(secondsAgos); // pool observe may fail when there is not enough history available (only use pool with enough history!)
 369:             int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)));
 370:             sqrtPriceX96 = TickMath.getSqrtRatioAtTick(tick);
 371:         }
 372: 
 373:         return FullMath.mulDiv(sqrtPriceX96, sqrtPriceX96, Q96);
 374:     }
```

*GitHub* : [359-374](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L359-L374)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit ******************* Issue Detail *******************
AutoCompound.execute(AutoCompound.ExecuteParams) (L#101-193) ignores return value by:
	- (state.sqrtPriceX96,state.tick,None,None,None,None,None) = pool.slot0() (L#129)

/// @audit ************** Possible Issue Line(s) **************
	L#129,  

/// @audit ****************** Affected Code *******************
 101:     function execute(ExecuteParams calldata params) external nonReentrant {
 102:         if (!operators[msg.sender] && !vaults[msg.sender]) {
 103:             revert Unauthorized();
 104:         }
 105:         ExecuteState memory state;
 106: 
 107:         // collect fees - if the position doesn't have operator set or is called from vault - it won't work
 108:         (state.amount0, state.amount1) = nonfungiblePositionManager.collect(
 109:             INonfungiblePositionManager.CollectParams(
 110:                 params.tokenId, address(this), type(uint128).max, type(uint128).max
 111:             )
 112:         );
 113: 
 114:         // get position info
 115:         (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper,,,,,) =
 116:             nonfungiblePositionManager.positions(params.tokenId);
 117: 
 118:         // add previous balances from given tokens
 119:         state.amount0 = state.amount0 + positionBalances[params.tokenId][state.token0];
 120:         state.amount1 = state.amount1 + positionBalances[params.tokenId][state.token1];
 121: 
 122:         // only if there are balances to work with - start autocompounding process
 123:         if (state.amount0 > 0 || state.amount1 > 0) {
 124:             uint256 amountIn = params.amountIn;
 125: 
 126:             // if a swap is requested - check TWAP oracle
 127:             if (amountIn > 0) {
 128:                 IUniswapV3Pool pool = _getPool(state.token0, state.token1, state.fee);
 129:                 (state.sqrtPriceX96, state.tick,,,,,) = pool.slot0();
 130: 
 131:                 // how many seconds are needed for TWAP protection
 132:                 uint32 tSecs = TWAPSeconds;
 133:                 if (tSecs > 0) {
 134:                     if (!_hasMaxTWAPTickDifference(pool, tSecs, state.tick, maxTWAPTickDifference)) {
 135:                         // if there is no valid TWAP - disable swap
 136:                         amountIn = 0;
 137:                     }
 138:                 }
 139:                 // if still needed - do swap
 140:                 if (amountIn > 0) {
 141:                     // no slippage check done - because protected by TWAP check
 142:                     (state.amountInDelta, state.amountOutDelta) = _poolSwap(
 143:                         Swapper.PoolSwapParams(
 144:                             pool, IERC20(state.token0), IERC20(state.token1), state.fee, params.swap0To1, amountIn, 0
 145:                         )
 146:                     );
 147:                     state.amount0 =
 148:                         params.swap0To1 ? state.amount0 - state.amountInDelta : state.amount0 + state.amountOutDelta;
 149:                     state.amount1 =
 150:                         params.swap0To1 ? state.amount1 + state.amountOutDelta : state.amount1 - state.amountInDelta;
 151:                 }
 152:             }
 153: 
 154:             uint256 rewardX64 = totalRewardX64;
 155: 
 156:             state.maxAddAmount0 = state.amount0 * Q64 / (rewardX64 + Q64);
 157:             state.maxAddAmount1 = state.amount1 * Q64 / (rewardX64 + Q64);
 158: 
 159:             // deposit liquidity into tokenId
 160:             if (state.maxAddAmount0 > 0 || state.maxAddAmount1 > 0) {
 161:                 _checkApprovals(state.token0, state.token1);
 162: 
 163:                 (, state.compounded0, state.compounded1) = nonfungiblePositionManager.increaseLiquidity(
 164:                     INonfungiblePositionManager.IncreaseLiquidityParams(
 165:                         params.tokenId, state.maxAddAmount0, state.maxAddAmount1, 0, 0, block.timestamp
 166:                     )
 167:                 );
 168: 
 169:                 // fees are always calculated based on added amount (to incentivize optimal swap)
 170:                 state.amount0Fees = state.compounded0 * rewardX64 / Q64;
 171:                 state.amount1Fees = state.compounded1 * rewardX64 / Q64;
 172:             }
 173: 
 174:             // calculate remaining tokens for owner
 175:             _setBalance(params.tokenId, state.token0, state.amount0 - state.compounded0 - state.amount0Fees);
 176:             _setBalance(params.tokenId, state.token1, state.amount1 - state.compounded1 - state.amount1Fees);
 177: 
 178:             // add reward to protocol balance (token 0)
 179:             _increaseBalance(0, state.token0, state.amount0Fees);
 180:             _increaseBalance(0, state.token1, state.amount1Fees);
 181:         }
 182: 
 183:         emit AutoCompounded(
 184:             msg.sender,
 185:             params.tokenId,
 186:             state.compounded0,
 187:             state.compounded1,
 188:             state.amount0Fees,
 189:             state.amount1Fees,
 190:             state.token0,
 191:             state.token1
 192:         );
 193:     }
```

*GitHub* : [101-193](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L101-L193)

```solidity
File: src/transformers/AutoRange.sol

/// @audit ******************* Issue Detail *******************
AutoRange.execute(AutoRange.ExecuteParams) (L#111-272) ignores return value by:
	- (state.newTokenId,None,state.amountAdded0,state.amountAdded1) = nonfungiblePositionManager.mint(mintParams) (L#217)

/// @audit ************** Possible Issue Line(s) **************
	L#217,  

/// @audit ****************** Affected Code *******************
 111:     function execute(ExecuteParams calldata params) external {
 112:         if (!operators[msg.sender] && !vaults[msg.sender]) {
 113:             revert Unauthorized();
 114:         }
 115:         ExecuteState memory state;
 116:         PositionConfig memory config = positionConfigs[params.tokenId];
 117: 
 118:         if (config.lowerTickDelta == config.upperTickDelta) {
 119:             revert NotConfigured();
 120:         }
 121: 
 122:         if (
 123:             config.onlyFees && params.rewardX64 > config.maxRewardX64
 124:                 || !config.onlyFees && params.rewardX64 > config.maxRewardX64
 125:         ) {
 126:             revert ExceedsMaxReward();
 127:         }
 128: 
 129:         // get position info
 130:         (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
 131:             nonfungiblePositionManager.positions(params.tokenId);
 132: 
 133:         if (state.liquidity != params.liquidity) {
 134:             revert LiquidityChanged();
 135:         }
 136: 
 137:         (state.amount0, state.amount1, state.feeAmount0, state.feeAmount1) = _decreaseFullLiquidityAndCollect(
 138:             params.tokenId, state.liquidity, params.amountRemoveMin0, params.amountRemoveMin1, params.deadline
 139:         );
 140: 
 141:         // if only fees reward is removed before adding
 142:         if (config.onlyFees) {
 143:             state.protocolReward0 = state.feeAmount0 * params.rewardX64 / Q64;
 144:             state.protocolReward1 = state.feeAmount1 * params.rewardX64 / Q64;
 145:             state.amount0 -= state.protocolReward0;
 146:             state.amount1 -= state.protocolReward1;
 147:         }
 148: 
 149:         if (params.swap0To1 && params.amountIn > state.amount0 || !params.swap0To1 && params.amountIn > state.amount1) {
 150:             revert SwapAmountTooLarge();
 151:         }
 152: 
 153:         // get pool info
 154:         state.pool = _getPool(state.token0, state.token1, state.fee);
 155: 
 156:         // check oracle for swap
 157:         (state.amountOutMin, state.currentTick,,) = _validateSwap(
 158:             params.swap0To1,
 159:             params.amountIn,
 160:             state.pool,
 161:             TWAPSeconds,
 162:             maxTWAPTickDifference,
 163:             params.swap0To1 ? config.token0SlippageX64 : config.token1SlippageX64
 164:         );
 165: 
 166:         if (
 167:             state.currentTick < state.tickLower - config.lowerTickLimit
 168:                 || state.currentTick >= state.tickUpper + config.upperTickLimit
 169:         ) {
 170:             int24 tickSpacing = _getTickSpacing(state.fee);
 171:             int24 baseTick = state.currentTick - (((state.currentTick % tickSpacing) + tickSpacing) % tickSpacing);
 172: 
 173:             // check if new range same as old range
 174:             if (
 175:                 baseTick + config.lowerTickDelta == state.tickLower
 176:                     && baseTick + config.upperTickDelta == state.tickUpper
 177:             ) {
 178:                 revert SameRange();
 179:             }
 180: 
 181:             (state.amountInDelta, state.amountOutDelta) = _routerSwap(
 182:                 Swapper.RouterSwapParams(
 183:                     params.swap0To1 ? IERC20(state.token0) : IERC20(state.token1),
 184:                     params.swap0To1 ? IERC20(state.token1) : IERC20(state.token0),
 185:                     params.amountIn,
 186:                     state.amountOutMin,
 187:                     params.swapData
 188:                 )
 189:             );
 190: 
 191:             state.amount0 = params.swap0To1 ? state.amount0 - state.amountInDelta : state.amount0 + state.amountOutDelta;
 192:             state.amount1 = params.swap0To1 ? state.amount1 + state.amountOutDelta : state.amount1 - state.amountInDelta;
 193: 
 194:             // max amount to add - removing max potential fees (if config.onlyFees - the have been removed already)
 195:             state.maxAddAmount0 = config.onlyFees ? state.amount0 : state.amount0 * Q64 / (params.rewardX64 + Q64);
 196:             state.maxAddAmount1 = config.onlyFees ? state.amount1 : state.amount1 * Q64 / (params.rewardX64 + Q64);
 197: 
 198:             INonfungiblePositionManager.MintParams memory mintParams = INonfungiblePositionManager.MintParams(
 199:                 address(state.token0),
 200:                 address(state.token1),
 201:                 state.fee,
 202:                 SafeCast.toInt24(baseTick + config.lowerTickDelta), // reverts if out of valid range
 203:                 SafeCast.toInt24(baseTick + config.upperTickDelta), // reverts if out of valid range
 204:                 state.maxAddAmount0,
 205:                 state.maxAddAmount1,
 206:                 0,
 207:                 0,
 208:                 address(this), // is sent to real recipient aftwards
 209:                 params.deadline
 210:             );
 211: 
 212:             // approve npm
 213:             SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), state.maxAddAmount0);
 214:             SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), state.maxAddAmount1);
 215: 
 216:             // mint is done to address(this) first - its not a safemint
 217:             (state.newTokenId,, state.amountAdded0, state.amountAdded1) = nonfungiblePositionManager.mint(mintParams);
 218: 
 219:             // remove remaining approval
 220:             SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), 0);
 221:             SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), 0);
 222: 
 223:             state.owner = nonfungiblePositionManager.ownerOf(params.tokenId);
 224: 
 225:             // get the real owner - if owner is vault - for sending leftover tokens
 226:             state.realOwner = state.owner;
 227:             if (vaults[state.owner]) {
 228:                 state.realOwner = IVault(state.owner).ownerOf(params.tokenId);
 229:             }
 230: 
 231:             // send the new nft to the owner / vault
 232:             nonfungiblePositionManager.safeTransferFrom(address(this), state.owner, state.newTokenId);
 233: 
 234:             // protocol reward is calculated based on added amount (to incentivize optimal swap done by operator)
 235:             if (!config.onlyFees) {
 236:                 state.protocolReward0 = state.amountAdded0 * params.rewardX64 / Q64;
 237:                 state.protocolReward1 = state.amountAdded1 * params.rewardX64 / Q64;
 238:                 state.amount0 -= state.protocolReward0;
 239:                 state.amount1 -= state.protocolReward1;
 240:             }
 241: 
 242:             // send leftover to real owner
 243:             if (state.amount0 - state.amountAdded0 > 0) {
 244:                 _transferToken(state.realOwner, IERC20(state.token0), state.amount0 - state.amountAdded0, true);
 245:             }
 246:             if (state.amount1 - state.amountAdded1 > 0) {
 247:                 _transferToken(state.realOwner, IERC20(state.token1), state.amount1 - state.amountAdded1, true);
 248:             }
 249: 
 250:             // copy token config for new token
 251:             positionConfigs[state.newTokenId] = config;
 252:             emit PositionConfigured(
 253:                 state.newTokenId,
 254:                 config.lowerTickLimit,
 255:                 config.upperTickLimit,
 256:                 config.lowerTickDelta,
 257:                 config.upperTickDelta,
 258:                 config.token0SlippageX64,
 259:                 config.token1SlippageX64,
 260:                 config.onlyFees,
 261:                 config.maxRewardX64
 262:             );
 263: 
 264:             // delete config for old position
 265:             delete positionConfigs[params.tokenId];
 266:             emit PositionConfigured(params.tokenId, 0, 0, 0, 0, 0, 0, false, 0);
 267: 
 268:             emit RangeChanged(params.tokenId, state.newTokenId);
 269:         } else {
 270:             revert NotReady();
 271:         }
 272:     }
```

*GitHub* : [111-272](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L111-L272)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit ******************* Issue Detail *******************
FlashloanLiquidator.liquidate(FlashloanLiquidator.LiquidateParams) (L#41-65) ignores return value by:
	- (token0,token1) = nonfungiblePositionManager.positions(params.tokenId) (L#47)

/// @audit ************** Possible Issue Line(s) **************
	L#47,  

/// @audit ****************** Affected Code *******************
  41:     function liquidate(LiquidateParams calldata params) external {
  42:         (,,, uint256 liquidationCost,) = params.vault.loanInfo(params.tokenId);
  43:         if (liquidationCost == 0) {
  44:             revert NotLiquidatable();
  45:         }
  46: 
  47:         (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(params.tokenId);
  48:         address asset = params.vault.asset();
  49: 
  50:         bool isAsset0 = params.flashLoanPool.token0() == asset;
  51:         bytes memory data = abi.encode(
  52:             FlashCallbackData(
  53:                 params.tokenId,
  54:                 params.debtShares,
  55:                 liquidationCost,
  56:                 params.vault,
  57:                 IERC20(asset),
  58:                 RouterSwapParams(IERC20(token0), IERC20(asset), params.amount0In, 0, params.swapData0),
  59:                 RouterSwapParams(IERC20(token1), IERC20(asset), params.amount1In, 0, params.swapData1),
  60:                 msg.sender,
  61:                 params.minReward
  62:             )
  63:         );
  64:         params.flashLoanPool.flash(address(this), isAsset0 ? liquidationCost : 0, !isAsset0 ? liquidationCost : 0, data);
  65:     }
```

*GitHub* : [41-65](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L41-L65)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
V3Oracle._getFeeGrowthInside(IUniswapV3Pool,int24,int24,int24,uint256,uint256) (L#472-496) ignores return value by:
	- (upperFeeGrowthOutside0X128,upperFeeGrowthOutside1X128) = pool.ticks(tickUpper) (L#481)

/// @audit ************** Possible Issue Line(s) **************
	L#481,  

/// @audit ****************** Affected Code *******************
 472:     function _getFeeGrowthInside(
 473:         IUniswapV3Pool pool,
 474:         int24 tickLower,
 475:         int24 tickUpper,
 476:         int24 tickCurrent,
 477:         uint256 feeGrowthGlobal0X128,
 478:         uint256 feeGrowthGlobal1X128
 479:     ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {
 480:         (,, uint256 lowerFeeGrowthOutside0X128, uint256 lowerFeeGrowthOutside1X128,,,,) = pool.ticks(tickLower);
 481:         (,, uint256 upperFeeGrowthOutside0X128, uint256 upperFeeGrowthOutside1X128,,,,) = pool.ticks(tickUpper);
 482: 
 483:         // allow overflow - this is as designed by uniswap - see PositionValue library (for solidity < 0.8)
 484:         unchecked {
 485:             if (tickCurrent < tickLower) {
 486:                 feeGrowthInside0X128 = lowerFeeGrowthOutside0X128 - upperFeeGrowthOutside0X128;
 487:                 feeGrowthInside1X128 = lowerFeeGrowthOutside1X128 - upperFeeGrowthOutside1X128;
 488:             } else if (tickCurrent < tickUpper) {
 489:                 feeGrowthInside0X128 = feeGrowthGlobal0X128 - lowerFeeGrowthOutside0X128 - upperFeeGrowthOutside0X128;
 490:                 feeGrowthInside1X128 = feeGrowthGlobal1X128 - lowerFeeGrowthOutside1X128 - upperFeeGrowthOutside1X128;
 491:             } else {
 492:                 feeGrowthInside0X128 = upperFeeGrowthOutside0X128 - lowerFeeGrowthOutside0X128;
 493:                 feeGrowthInside1X128 = upperFeeGrowthOutside1X128 - lowerFeeGrowthOutside1X128;
 494:             }
 495:         }
 496:     }
```

*GitHub* : [472-496](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L472-L496)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
V3Utils.swapAndIncreaseLiquidity(V3Utils.SwapAndIncreaseLiquidityParams) (L#532-564) ignores return value by:
	- (token0,token1) = nonfungiblePositionManager.positions(params.tokenId) (L#537)

/// @audit ************** Possible Issue Line(s) **************
	L#537,  

/// @audit ****************** Affected Code *******************
 532:     function swapAndIncreaseLiquidity(SwapAndIncreaseLiquidityParams calldata params)
 533:         external
 534:         payable
 535:         returns (uint128 liquidity, uint256 amount0, uint256 amount1)
 536:     {
 537:         (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(params.tokenId);
 538: 
 539:         if (params.permitData.length > 0) {
 540:             (ISignatureTransfer.PermitBatchTransferFrom memory pbtf, bytes memory signature) =
 541:                 abi.decode(params.permitData, (ISignatureTransfer.PermitBatchTransferFrom, bytes));
 542:             _prepareAddPermit2(
 543:                 IERC20(token0),
 544:                 IERC20(token1),
 545:                 params.swapSourceToken,
 546:                 params.amount0,
 547:                 params.amount1,
 548:                 params.amountIn0 + params.amountIn1,
 549:                 pbtf,
 550:                 signature
 551:             );
 552:         } else {
 553:             _prepareAddApproved(
 554:                 IERC20(token0),
 555:                 IERC20(token1),
 556:                 params.swapSourceToken,
 557:                 params.amount0,
 558:                 params.amount1,
 559:                 params.amountIn0 + params.amountIn1
 560:             );
 561:         }
 562: 
 563:         (liquidity, amount0, amount1) = _swapAndIncrease(params, IERC20(token0), IERC20(token1), msg.value != 0);
 564:     }
```

*GitHub* : [532-564](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L532-L564)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
V3Oracle._getChainlinkPriceX96(address) (L#329-343) ignores return value by:
	- (answer,updatedAt) = feedConfig.feed.latestRoundData() (L#337)

/// @audit ************** Possible Issue Line(s) **************
	L#337,  

/// @audit ****************** Affected Code *******************
 329:     function _getChainlinkPriceX96(address token) internal view returns (uint256) {
 330:         if (token == chainlinkReferenceToken) {
 331:             return Q96;
 332:         }
 333: 
 334:         TokenConfig memory feedConfig = feedConfigs[token];
 335: 
 336:         // if stale data - revert
 337:         (, int256 answer,, uint256 updatedAt,) = feedConfig.feed.latestRoundData();
 338:         if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0) {
 339:             revert ChainlinkPriceError();
 340:         }
 341: 
 342:         return uint256(answer) * Q96 / (10 ** feedConfig.feedDecimals);
 343:     }
```

*GitHub* : [329-343](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L329-L343)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
V3Oracle._initializeState(uint256) (L#395-423) ignores return value by:
	- (token0,token1,fee,tickLower,tickUpper,liquidity,feeGrowthInside0LastX128,feeGrowthInside1LastX128,tokensOwed0,tokensOwed1) = nonfungiblePositionManager.positions(tokenId) (L#396-409)

/// @audit ************** Possible Issue Line(s) **************
	L#396-409,  

/// @audit ****************** Affected Code *******************
 395:     function _initializeState(uint256 tokenId) internal view returns (PositionState memory state) {
 396:         (
 397:             ,
 398:             ,
 399:             address token0,
 400:             address token1,
 401:             uint24 fee,
 402:             int24 tickLower,
 403:             int24 tickUpper,
 404:             uint128 liquidity,
 405:             uint256 feeGrowthInside0LastX128,
 406:             uint256 feeGrowthInside1LastX128,
 407:             uint128 tokensOwed0,
 408:             uint128 tokensOwed1
 409:         ) = nonfungiblePositionManager.positions(tokenId);
 410:         state.tokenId = tokenId;
 411:         state.token0 = token0;
 412:         state.token1 = token1;
 413:         state.fee = fee;
 414:         state.tickLower = tickLower;
 415:         state.tickUpper = tickUpper;
 416:         state.liquidity = liquidity;
 417:         state.feeGrowthInside0LastX128 = feeGrowthInside0LastX128;
 418:         state.feeGrowthInside1LastX128 = feeGrowthInside1LastX128;
 419:         state.tokensOwed0 = tokensOwed0;
 420:         state.tokensOwed1 = tokensOwed1;
 421:         state.pool = _getPool(token0, token1, fee);
 422:         (state.sqrtPriceX96, state.tick,,,,,) = state.pool.slot0();
 423:     }
```

*GitHub* : [395-423](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L395-L423)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault._sendPositionValue(uint256,uint256,uint256,uint256,address) (L#1032-1073) ignores return value by:
	- (None,None,None,None,None,None,None,liquidity,None,None,None,None) = nonfungiblePositionManager.positions(tokenId) (L#1045)

/// @audit ************** Possible Issue Line(s) **************
	L#1045,  

/// @audit ****************** Affected Code *******************
1032:     function _sendPositionValue(
1033:         uint256 tokenId,
1034:         uint256 liquidationValue,
1035:         uint256 fullValue,
1036:         uint256 feeValue,
1037:         address recipient
1038:     ) internal returns (uint256 amount0, uint256 amount1) {
1039:         uint128 liquidity;
1040:         uint128 fees0;
1041:         uint128 fees1;
1042: 
1043:         // if full position is liquidated - no analysis needed
1044:         if (liquidationValue == fullValue) {
1045:             (,,,,,,, liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);
1046:             fees0 = type(uint128).max;
1047:             fees1 = type(uint128).max;
1048:         } else {
1049:             (,,, liquidity,,, fees0, fees1) = oracle.getPositionBreakdown(tokenId);
1050: 
1051:             // only take needed fees
1052:             if (liquidationValue < feeValue) {
1053:                 liquidity = 0;
1054:                 fees0 = uint128(liquidationValue * fees0 / feeValue);
1055:                 fees1 = uint128(liquidationValue * fees1 / feeValue);
1056:             } else {
1057:                 // take all fees and needed liquidity
1058:                 fees0 = type(uint128).max;
1059:                 fees1 = type(uint128).max;
1060:                 liquidity = uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue));
1061:             }
1062:         }
1063: 
1064:         if (liquidity > 0) {
1065:             nonfungiblePositionManager.decreaseLiquidity(
1066:                 INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp)
1067:             );
1068:         }
1069: 
1070:         (amount0, amount1) = nonfungiblePositionManager.collect(
1071:             INonfungiblePositionManager.CollectParams(tokenId, recipient, fees0, fees1)
1072:         );
1073:     }
```

*GitHub* : [1032-1073](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1032-L1073)

```solidity
File: src/transformers/AutoRange.sol

/// @audit ******************* Issue Detail *******************
AutoRange.executeWithVault(AutoRange.ExecuteParams,address) (L#97-104) ignores return value by:
	- IVault(vault).transform(params.tokenId,address(this),abi.encodeWithSelector(AutoRange.execute.selector,params)) (L#101-103)

/// @audit ************** Possible Issue Line(s) **************
	L#101-103,  

/// @audit ****************** Affected Code *******************
  97:     function executeWithVault(ExecuteParams calldata params, address vault) external {
  98:         if (!operators[msg.sender] || !vaults[vault]) {
  99:             revert Unauthorized();
 100:         }
 101:         IVault(vault).transform(
 102:             params.tokenId, address(this), abi.encodeWithSelector(AutoRange.execute.selector, params)
 103:         );
 104:     }
```

*GitHub* : [97-104](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L97-L104)

```solidity
File: src/automators/AutoExit.sol

/// @audit ******************* Issue Detail *******************
AutoExit.execute(AutoExit.ExecuteParams) (L#100-214) ignores return value by:
	- (None,None,state.token0,state.token1,state.fee,state.tickLower,state.tickUpper,state.liquidity,None,None,None,None) = nonfungiblePositionManager.positions(params.tokenId) (L#120-121)

/// @audit ************** Possible Issue Line(s) **************
	L#120-121,  

/// @audit ****************** Affected Code *******************
 100:     function execute(ExecuteParams calldata params) external {
 101:         if (!operators[msg.sender]) {
 102:             revert Unauthorized();
 103:         }
 104: 
 105:         ExecuteState memory state;
 106:         PositionConfig memory config = positionConfigs[params.tokenId];
 107: 
 108:         if (!config.isActive) {
 109:             revert NotConfigured();
 110:         }
 111: 
 112:         if (
 113:             config.onlyFees && params.rewardX64 > config.maxRewardX64
 114:                 || !config.onlyFees && params.rewardX64 > config.maxRewardX64
 115:         ) {
 116:             revert ExceedsMaxReward();
 117:         }
 118: 
 119:         // get position info
 120:         (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
 121:             nonfungiblePositionManager.positions(params.tokenId);
 122: 
 123:         // so can be executed only once
 124:         if (state.liquidity == 0) {
 125:             revert NoLiquidity();
 126:         }
 127:         if (state.liquidity != params.liquidity) {
 128:             revert LiquidityChanged();
 129:         }
 130: 
 131:         state.pool = _getPool(state.token0, state.token1, state.fee);
 132:         (, state.tick,,,,,) = state.pool.slot0();
 133: 
 134:         // not triggered
 135:         if (config.token0TriggerTick <= state.tick && state.tick < config.token1TriggerTick) {
 136:             revert NotReady();
 137:         }
 138: 
 139:         state.isAbove = state.tick >= config.token1TriggerTick;
 140:         state.isSwap = !state.isAbove && config.token0Swap || state.isAbove && config.token1Swap;
 141: 
 142:         // decrease full liquidity for given position - and return fees as well
 143:         (state.amount0, state.amount1, state.feeAmount0, state.feeAmount1) = _decreaseFullLiquidityAndCollect(
 144:             params.tokenId, state.liquidity, params.amountRemoveMin0, params.amountRemoveMin1, params.deadline
 145:         );
 146: 
 147:         // swap to other token
 148:         if (state.isSwap) {
 149:             if (params.swapData.length == 0) {
 150:                 revert MissingSwapData();
 151:             }
 152: 
 153:             // reward is taken before swap - if from fees only
 154:             if (config.onlyFees) {
 155:                 state.amount0 -= state.feeAmount0 * params.rewardX64 / Q64;
 156:                 state.amount1 -= state.feeAmount1 * params.rewardX64 / Q64;
 157:             }
 158: 
 159:             state.swapAmount = state.isAbove ? state.amount1 : state.amount0;
 160: 
 161:             // checks if price in valid oracle range and calculates amountOutMin
 162:             (state.amountOutMin,,,) = _validateSwap(
 163:                 !state.isAbove,
 164:                 state.swapAmount,
 165:                 state.pool,
 166:                 TWAPSeconds,
 167:                 maxTWAPTickDifference,
 168:                 state.isAbove ? config.token1SlippageX64 : config.token0SlippageX64
 169:             );
 170: 
 171:             (state.amountInDelta, state.amountOutDelta) = _routerSwap(
 172:                 Swapper.RouterSwapParams(
 173:                     state.isAbove ? IERC20(state.token1) : IERC20(state.token0),
 174:                     state.isAbove ? IERC20(state.token0) : IERC20(state.token1),
 175:                     state.swapAmount,
 176:                     state.amountOutMin,
 177:                     params.swapData
 178:                 )
 179:             );
 180: 
 181:             state.amount0 = state.isAbove ? state.amount0 + state.amountOutDelta : state.amount0 - state.amountInDelta;
 182:             state.amount1 = state.isAbove ? state.amount1 - state.amountInDelta : state.amount1 + state.amountOutDelta;
 183: 
 184:             // when swap and !onlyFees - protocol reward is removed only from target token (to incentivize optimal swap done by operator)
 185:             if (!config.onlyFees) {
 186:                 if (state.isAbove) {
 187:                     state.amount0 -= state.amount0 * params.rewardX64 / Q64;
 188:                 } else {
 189:                     state.amount1 -= state.amount1 * params.rewardX64 / Q64;
 190:                 }
 191:             }
 192:         } else {
 193:             // reward is taken as configured
 194:             state.amount0 -= (config.onlyFees ? state.feeAmount0 : state.amount0) * params.rewardX64 / Q64;
 195:             state.amount1 -= (config.onlyFees ? state.feeAmount1 : state.amount1) * params.rewardX64 / Q64;
 196:         }
 197: 
 198:         state.owner = nonfungiblePositionManager.ownerOf(params.tokenId);
 199:         if (state.amount0 > 0) {
 200:             _transferToken(state.owner, IERC20(state.token0), state.amount0, true);
 201:         }
 202:         if (state.amount1 > 0) {
 203:             _transferToken(state.owner, IERC20(state.token1), state.amount1, true);
 204:         }
 205: 
 206:         // delete config for position
 207:         delete positionConfigs[params.tokenId];
 208:         emit PositionConfigured(params.tokenId, false, false, false, 0, 0, 0, 0, false, 0);
 209: 
 210:         // log event
 211:         emit Executed(
 212:             params.tokenId, msg.sender, state.isSwap, state.amount0, state.amount1, state.token0, state.token1
 213:         );
 214:     }
```

*GitHub* : [100-214](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L100-L214)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault._calculateTokenCollateralFactorX32(uint256) (L#1143-1148) ignores return value by:
	- (token0,token1) = nonfungiblePositionManager.positions(tokenId) (L#1144)

/// @audit ************** Possible Issue Line(s) **************
	L#1144,  

/// @audit ****************** Affected Code *******************
1143:     function _calculateTokenCollateralFactorX32(uint256 tokenId) internal view returns (uint32) {
1144:         (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(tokenId);
1145:         uint32 factor0X32 = tokenConfigs[token0].collateralFactorX32;
1146:         uint32 factor1X32 = tokenConfigs[token1].collateralFactorX32;
1147:         return factor0X32 > factor1X32 ? factor1X32 : factor0X32;
1148:     }
```

*GitHub* : [1143-1148](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1143-L1148)

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Automator._getTWAPTick(IUniswapV3Pool,uint32) (L#180-191) ignores return value by:
	- (tickCumulatives) = pool.observe(secondsAgos) (L#186-190)

/// @audit ************** Possible Issue Line(s) **************
	L#186-190,  

/// @audit ****************** Affected Code *******************
 180:     function _getTWAPTick(IUniswapV3Pool pool, uint32 twapPeriod) internal view returns (int24, bool) {
 181:         uint32[] memory secondsAgos = new uint32[](2);
 182:         secondsAgos[0] = 0; // from (before)
 183:         secondsAgos[1] = twapPeriod; // from (before)
 184: 
 185:         // pool observe may fail when there is not enough history available
 186:         try pool.observe(secondsAgos) returns (int56[] memory tickCumulatives, uint160[] memory) {
 187:             return (int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapPeriod))), true);
 188:         } catch {
 189:             return (0, false);
 190:         }
 191:     }
```

*GitHub* : [180-191](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L180-L191)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit ******************* Issue Detail *******************
FlashloanLiquidator.uniswapV3FlashCallback(uint256,uint256,bytes) (L#67-109) ignores return value by:
	- data.vault.liquidate(IVault.LiquidateParams(data.tokenId,data.debtShares,data.swap0.amountIn,data.swap1.amountIn,address(this),)) (L#73-77)

/// @audit ************** Possible Issue Line(s) **************
	L#73-77,  

/// @audit ****************** Affected Code *******************
  67:     function uniswapV3FlashCallback(uint256 fee0, uint256 fee1, bytes calldata callbackData) external {
  68:         // no origin check is needed - because the contract doesn't hold any funds - there is no benefit in calling uniswapV3FlashCallback() from another context
  69: 
  70:         FlashCallbackData memory data = abi.decode(callbackData, (FlashCallbackData));
  71: 
  72:         SafeERC20.safeApprove(data.asset, address(data.vault), data.liquidationCost);
  73:         data.vault.liquidate(
  74:             IVault.LiquidateParams(
  75:                 data.tokenId, data.debtShares, data.swap0.amountIn, data.swap1.amountIn, address(this), ""
  76:             )
  77:         );
  78:         SafeERC20.safeApprove(data.asset, address(data.vault), 0);
  79: 
  80:         // do swaps
  81:         _routerSwap(data.swap0);
  82:         _routerSwap(data.swap1);
  83: 
  84:         // transfer lent amount + fee (only one token can have fee) - back to pool
  85:         SafeERC20.safeTransfer(data.asset, msg.sender, data.liquidationCost + (fee0 + fee1));
  86: 
  87:         // return all leftover tokens to liquidator
  88:         if (data.swap0.tokenIn != data.asset) {
  89:             uint256 balance = data.swap0.tokenIn.balanceOf(address(this));
  90:             if (balance > 0) {
  91:                 SafeERC20.safeTransfer(data.swap0.tokenIn, data.liquidator, balance);
  92:             }
  93:         }
  94:         if (data.swap1.tokenIn != data.asset) {
  95:             uint256 balance = data.swap1.tokenIn.balanceOf(address(this));
  96:             if (balance > 0) {
  97:                 SafeERC20.safeTransfer(data.swap1.tokenIn, data.liquidator, balance);
  98:             }
  99:         }
 100:         {
 101:             uint256 balance = data.asset.balanceOf(address(this));
 102:             if (balance < data.minReward) {
 103:                 revert NotEnoughReward();
 104:             }
 105:             if (balance > 0) {
 106:                 SafeERC20.safeTransfer(data.asset, data.liquidator, balance);
 107:             }
 108:         }
 109:     }
```

*GitHub* : [67-109](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L67-L109)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault._updateAndCheckCollateral(uint256,uint256,uint256,uint256,uint256) (L#1205-1244) ignores return value by:
	- (token0,token1) = nonfungiblePositionManager.positions(tokenId) (L#1213)

/// @audit ************** Possible Issue Line(s) **************
	L#1213,  

/// @audit ****************** Affected Code *******************
1205:     function _updateAndCheckCollateral(
1206:         uint256 tokenId,
1207:         uint256 debtExchangeRateX96,
1208:         uint256 lendExchangeRateX96,
1209:         uint256 oldShares,
1210:         uint256 newShares
1211:     ) internal {
1212:         if (oldShares != newShares) {
1213:             (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(tokenId);
1214: 
1215:             // remove previous collateral - add new collateral
1216:             if (oldShares > newShares) {
1217:                 tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1218:                 tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1219:             } else {
1220:                 tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
1221:                 tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
1222: 
1223:                 // check if current value of used collateral is more than allowed limit
1224:                 // if collateral is decreased - never revert
1225:                 uint256 lentAssets = _convertToAssets(totalSupply(), lendExchangeRateX96, Math.Rounding.Up);
1226:                 uint256 collateralValueLimitFactorX32 = tokenConfigs[token0].collateralValueLimitFactorX32;
1227:                 if (
1228:                     collateralValueLimitFactorX32 < type(uint32).max
1229:                         && _convertToAssets(tokenConfigs[token0].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
1230:                             > lentAssets * collateralValueLimitFactorX32 / Q32
1231:                 ) {
1232:                     revert CollateralValueLimit();
1233:                 }
1234:                 collateralValueLimitFactorX32 = tokenConfigs[token1].collateralValueLimitFactorX32;
1235:                 if (
1236:                     collateralValueLimitFactorX32 < type(uint32).max
1237:                         && _convertToAssets(tokenConfigs[token1].totalDebtShares, debtExchangeRateX96, Math.Rounding.Up)
1238:                             > lentAssets * collateralValueLimitFactorX32 / Q32
1239:                 ) {
1240:                     revert CollateralValueLimit();
1241:                 }
1242:             }
1243:         }
1244:     }
```

*GitHub* : [1205-1244](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1205-L1244)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
V3Utils.execute(uint256,V3Utils.Instructions) (L#115-352) ignores return value by:
	- (token0,token1,liquidity) = nonfungiblePositionManager.positions(tokenId) (L#116)

/// @audit ************** Possible Issue Line(s) **************
	L#116,  

/// @audit ****************** Affected Code *******************
 115:     function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {
 116:         (,, address token0, address token1,,,, uint128 liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);
 117: 
 118:         uint256 amount0;
 119:         uint256 amount1;
 120:         if (instructions.liquidity != 0) {
 121:             (amount0, amount1) = _decreaseLiquidity(
 122:                 tokenId,
 123:                 instructions.liquidity,
 124:                 instructions.deadline,
 125:                 instructions.amountRemoveMin0,
 126:                 instructions.amountRemoveMin1
 127:             );
 128:         }
 129:         (amount0, amount1) = _collectFees(
 130:             tokenId,
 131:             IERC20(token0),
 132:             IERC20(token1),
 133:             instructions.feeAmount0 == type(uint128).max
 134:                 ? type(uint128).max
 135:                 : (amount0 + instructions.feeAmount0).toUint128(),
 136:             instructions.feeAmount1 == type(uint128).max
 137:                 ? type(uint128).max
 138:                 : (amount1 + instructions.feeAmount1).toUint128()
 139:         );
 140: 
 141:         // check if enough tokens are available for swaps
 142:         if (amount0 < instructions.amountIn0 || amount1 < instructions.amountIn1) {
 143:             revert AmountError();
 144:         }
 145: 
 146:         if (instructions.whatToDo == WhatToDo.COMPOUND_FEES) {
 147:             if (instructions.targetToken == token0) {
 148:                 (liquidity, amount0, amount1) = _swapAndIncrease(
 149:                     SwapAndIncreaseLiquidityParams(
 150:                         tokenId,
 151:                         amount0,
 152:                         amount1,
 153:                         instructions.recipient,
 154:                         instructions.deadline,
 155:                         IERC20(token1),
 156:                         instructions.amountIn1,
 157:                         instructions.amountOut1Min,
 158:                         instructions.swapData1,
 159:                         0,
 160:                         0,
 161:                         "",
 162:                         instructions.amountAddMin0,
 163:                         instructions.amountAddMin1,
 164:                         ""
 165:                     ),
 166:                     IERC20(token0),
 167:                     IERC20(token1),
 168:                     instructions.unwrap
 169:                 );
 170:             } else if (instructions.targetToken == token1) {
 171:                 (liquidity, amount0, amount1) = _swapAndIncrease(
 172:                     SwapAndIncreaseLiquidityParams(
 173:                         tokenId,
 174:                         amount0,
 175:                         amount1,
 176:                         instructions.recipient,
 177:                         instructions.deadline,
 178:                         IERC20(token0),
 179:                         0,
 180:                         0,
 181:                         "",
 182:                         instructions.amountIn0,
 183:                         instructions.amountOut0Min,
 184:                         instructions.swapData0,
 185:                         instructions.amountAddMin0,
 186:                         instructions.amountAddMin1,
 187:                         ""
 188:                     ),
 189:                     IERC20(token0),
 190:                     IERC20(token1),
 191:                     instructions.unwrap
 192:                 );
 193:             } else {
 194:                 // no swap is done here
 195:                 (liquidity, amount0, amount1) = _swapAndIncrease(
 196:                     SwapAndIncreaseLiquidityParams(
 197:                         tokenId,
 198:                         amount0,
 199:                         amount1,
 200:                         instructions.recipient,
 201:                         instructions.deadline,
 202:                         IERC20(address(0)),
 203:                         0,
 204:                         0,
 205:                         "",
 206:                         0,
 207:                         0,
 208:                         "",
 209:                         instructions.amountAddMin0,
 210:                         instructions.amountAddMin1,
 211:                         ""
 212:                     ),
 213:                     IERC20(token0),
 214:                     IERC20(token1),
 215:                     instructions.unwrap
 216:                 );
 217:             }
 218:             emit CompoundFees(tokenId, liquidity, amount0, amount1);
 219:         } else if (instructions.whatToDo == WhatToDo.CHANGE_RANGE) {
 220:             if (instructions.targetToken == token0) {
 221:                 (newTokenId,,,) = _swapAndMint(
 222:                     SwapAndMintParams(
 223:                         IERC20(token0),
 224:                         IERC20(token1),
 225:                         instructions.fee,
 226:                         instructions.tickLower,
 227:                         instructions.tickUpper,
 228:                         amount0,
 229:                         amount1,
 230:                         instructions.recipient,
 231:                         instructions.recipientNFT,
 232:                         instructions.deadline,
 233:                         IERC20(token1),
 234:                         instructions.amountIn1,
 235:                         instructions.amountOut1Min,
 236:                         instructions.swapData1,
 237:                         0,
 238:                         0,
 239:                         "",
 240:                         instructions.amountAddMin0,
 241:                         instructions.amountAddMin1,
 242:                         instructions.swapAndMintReturnData,
 243:                         ""
 244:                     ),
 245:                     instructions.unwrap
 246:                 );
 247:             } else if (instructions.targetToken == token1) {
 248:                 (newTokenId,,,) = _swapAndMint(
 249:                     SwapAndMintParams(
 250:                         IERC20(token0),
 251:                         IERC20(token1),
 252:                         instructions.fee,
 253:                         instructions.tickLower,
 254:                         instructions.tickUpper,
 255:                         amount0,
 256:                         amount1,
 257:                         instructions.recipient,
 258:                         instructions.recipientNFT,
 259:                         instructions.deadline,
 260:                         IERC20(token0),
 261:                         0,
 262:                         0,
 263:                         "",
 264:                         instructions.amountIn0,
 265:                         instructions.amountOut0Min,
 266:                         instructions.swapData0,
 267:                         instructions.amountAddMin0,
 268:                         instructions.amountAddMin1,
 269:                         instructions.swapAndMintReturnData,
 270:                         ""
 271:                     ),
 272:                     instructions.unwrap
 273:                 );
 274:             } else {
 275:                 // no swap is done here
 276:                 (newTokenId,,,) = _swapAndMint(
 277:                     SwapAndMintParams(
 278:                         IERC20(token0),
 279:                         IERC20(token1),
 280:                         instructions.fee,
 281:                         instructions.tickLower,
 282:                         instructions.tickUpper,
 283:                         amount0,
 284:                         amount1,
 285:                         instructions.recipient,
 286:                         instructions.recipientNFT,
 287:                         instructions.deadline,
 288:                         IERC20(address(0)),
 289:                         0,
 290:                         0,
 291:                         "",
 292:                         0,
 293:                         0,
 294:                         "",
 295:                         instructions.amountAddMin0,
 296:                         instructions.amountAddMin1,
 297:                         instructions.swapAndMintReturnData,
 298:                         ""
 299:                     ),
 300:                     instructions.unwrap
 301:                 );
 302:             }
 303:             emit ChangeRange(tokenId, newTokenId);
 304:         } else if (instructions.whatToDo == WhatToDo.WITHDRAW_AND_COLLECT_AND_SWAP) {
 305:             uint256 targetAmount;
 306:             if (token0 != instructions.targetToken) {
 307:                 (uint256 amountInDelta, uint256 amountOutDelta) = _routerSwap(
 308:                     Swapper.RouterSwapParams(
 309:                         IERC20(token0),
 310:                         IERC20(instructions.targetToken),
 311:                         amount0,
 312:                         instructions.amountOut0Min,
 313:                         instructions.swapData0
 314:                     )
 315:                 );
 316:                 if (amountInDelta < amount0) {
 317:                     _transferToken(instructions.recipient, IERC20(token0), amount0 - amountInDelta, instructions.unwrap);
 318:                 }
 319:                 targetAmount += amountOutDelta;
 320:             } else {
 321:                 targetAmount += amount0;
 322:             }
 323:             if (token1 != instructions.targetToken) {
 324:                 (uint256 amountInDelta, uint256 amountOutDelta) = _routerSwap(
 325:                     Swapper.RouterSwapParams(
 326:                         IERC20(token1),
 327:                         IERC20(instructions.targetToken),
 328:                         amount1,
 329:                         instructions.amountOut1Min,
 330:                         instructions.swapData1
 331:                     )
 332:                 );
 333:                 if (amountInDelta < amount1) {
 334:                     _transferToken(instructions.recipient, IERC20(token1), amount1 - amountInDelta, instructions.unwrap);
 335:                 }
 336:                 targetAmount += amountOutDelta;
 337:             } else {
 338:                 targetAmount += amount1;
 339:             }
 340: 
 341:             // send complete target amount
 342:             if (targetAmount != 0 && instructions.targetToken != address(0)) {
 343:                 _transferToken(
 344:                     instructions.recipient, IERC20(instructions.targetToken), targetAmount, instructions.unwrap
 345:                 );
 346:             }
 347: 
 348:             emit WithdrawAndCollectAndSwap(tokenId, instructions.targetToken, targetAmount);
 349:         } else {
 350:             revert NotSupportedWhatToDo();
 351:         }
 352:     }
```

*GitHub* : [115-352](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L115-L352)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
V3Vault._checkLoanIsHealthy(uint256,uint256) (L#1270-1279) ignores return value by:
	- (fullValue,feeValue,None,None) = oracle.getValue(tokenId,address(asset)) (L#1275)

/// @audit ************** Possible Issue Line(s) **************
	L#1275,  

/// @audit ****************** Affected Code *******************
1270:     function _checkLoanIsHealthy(uint256 tokenId, uint256 debt)
1271:         internal
1272:         view
1273:         returns (bool isHealthy, uint256 fullValue, uint256 collateralValue, uint256 feeValue)
1274:     {
1275:         (fullValue, feeValue,,) = oracle.getValue(tokenId, address(asset));
1276:         uint256 collateralFactorX32 = _calculateTokenCollateralFactorX32(tokenId);
1277:         collateralValue = fullValue.mulDiv(collateralFactorX32, Q32);
1278:         isHealthy = collateralValue >= debt;
1279:     }
```

*GitHub* : [1270-1279](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1270-L1279)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit ******************* Issue Detail *******************
LeverageTransformer.leverageDown(LeverageTransformer.LeverageDownParams) (L#123-175) ignores return value by:
	- (token0,token1) = nonfungiblePositionManager.positions(params.tokenId) (L#125)

/// @audit ************** Possible Issue Line(s) **************
	L#125,  

/// @audit ****************** Affected Code *******************
 123:     function leverageDown(LeverageDownParams calldata params) external {
 124:         address token = IVault(msg.sender).asset();
 125:         (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(params.tokenId);
 126: 
 127:         uint256 amount0;
 128:         uint256 amount1;
 129: 
 130:         INonfungiblePositionManager.DecreaseLiquidityParams memory decreaseLiquidityParams = INonfungiblePositionManager
 131:             .DecreaseLiquidityParams(
 132:             params.tokenId, params.liquidity, params.amountRemoveMin0, params.amountRemoveMin1, params.deadline
 133:         );
 134:         (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(decreaseLiquidityParams);
 135: 
 136:         INonfungiblePositionManager.CollectParams memory collectParams = INonfungiblePositionManager.CollectParams(
 137:             params.tokenId,
 138:             address(this),
 139:             params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),
 140:             params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)
 141:         );
 142:         (amount0, amount1) = nonfungiblePositionManager.collect(collectParams);
 143: 
 144:         uint256 amount = token == token0 ? amount0 : (token == token1 ? amount1 : 0);
 145: 
 146:         if (params.amountIn0 > 0 && token != token0) {
 147:             (uint256 amountIn, uint256 amountOut) = _routerSwap(
 148:                 Swapper.RouterSwapParams(
 149:                     IERC20(token0), IERC20(token), params.amountIn0, params.amountOut0Min, params.swapData0
 150:                 )
 151:             );
 152:             amount0 -= amountIn;
 153:             amount += amountOut;
 154:         }
 155:         if (params.amountIn1 > 0 && token != token1) {
 156:             (uint256 amountIn, uint256 amountOut) = _routerSwap(
 157:                 Swapper.RouterSwapParams(
 158:                     IERC20(token1), IERC20(token), params.amountIn1, params.amountOut1Min, params.swapData1
 159:                 )
 160:             );
 161:             amount1 -= amountIn;
 162:             amount += amountOut;
 163:         }
 164: 
 165:         SafeERC20.safeApprove(IERC20(token), msg.sender, amount);
 166:         IVault(msg.sender).repay(params.tokenId, amount, false);
 167: 
 168:         // send leftover tokens
 169:         if (amount0 > 0 && token != token0) {
 170:             SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0);
 171:         }
 172:         if (amount1 > 0 && token != token1) {
 173:             SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1);
 174:         }
 175:     }
```

*GitHub* : [123-175](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L123-L175)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit ******************* Issue Detail *******************
AutoCompound.executeWithVault(AutoCompound.ExecuteParams,address) (L#87-94) ignores return value by:
	- IVault(vault).transform(params.tokenId,address(this),abi.encodeWithSelector(AutoCompound.execute.selector,params)) (L#91-93)

/// @audit ************** Possible Issue Line(s) **************
	L#91-93,  

/// @audit ****************** Affected Code *******************
  87:     function executeWithVault(ExecuteParams calldata params, address vault) external {
  88:         if (!operators[msg.sender] || !vaults[vault]) {
  89:             revert Unauthorized();
  90:         }
  91:         IVault(vault).transform(
  92:             params.tokenId, address(this), abi.encodeWithSelector(AutoCompound.execute.selector, params)
  93:         );
  94:     }
```

*GitHub* : [87-94](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L87-L94)

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Automator._validateSwap(bool,uint256,IUniswapV3Pool,uint32,uint16,uint64) (L#139-162) ignores return value by:
	- (sqrtPriceX96,currentTick,None,None,None,None,None) = pool.slot0() (L#148)

/// @audit ************** Possible Issue Line(s) **************
	L#148,  

/// @audit ****************** Affected Code *******************
 139:     function _validateSwap(
 140:         bool swap0For1,
 141:         uint256 amountIn,
 142:         IUniswapV3Pool pool,
 143:         uint32 twapPeriod,
 144:         uint16 maxTickDifference,
 145:         uint64 maxPriceDifferenceX64
 146:     ) internal view returns (uint256 amountOutMin, int24 currentTick, uint160 sqrtPriceX96, uint256 priceX96) {
 147:         // get current price and tick
 148:         (sqrtPriceX96, currentTick,,,,,) = pool.slot0();
 149: 
 150:         // check if current tick not too far from TWAP
 151:         if (!_hasMaxTWAPTickDifference(pool, twapPeriod, currentTick, maxTickDifference)) {
 152:             revert TWAPCheckFailed();
 153:         }
 154: 
 155:         // calculate min output price price and percentage
 156:         priceX96 = FullMath.mulDiv(sqrtPriceX96, sqrtPriceX96, Q96);
 157:         if (swap0For1) {
 158:             amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), priceX96, Q96 * Q64);
 159:         } else {
 160:             amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), Q96, priceX96 * Q64);
 161:         }
 162:     }
```

*GitHub* : [139-162](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L139-L162)


### NonCritical Risk Issues

### [N-01]<a name="n-01"></a> Different pragma directives are used

Different Solidity versions are used which may be produce incorrect results.  **Recom** Use one Solidity version.

*There are 1 instance(s) of this issue:*

```solidity
File: lib/v3-core/contracts/libraries/FixedPoint128.sol

/// @audit ******************* Issue Detail *******************
Different versions of Solidity are used:
	- Version used: ['>=0.4.0', '>=0.5.0', '>=0.7.5', '^0.8.0', '^0.8.1']
	- >=0.4.0 (lib/v3-core/contracts/libraries/FixedPoint128.sol#2)
	- >=0.4.0 (lib/v3-core/contracts/libraries/FixedPoint96.sol#2)
	- >=0.5.0 (lib/v3-core/contracts/interfaces/IUniswapV3Factory.sol#2)
	- >=0.5.0 (lib/v3-core/contracts/interfaces/IUniswapV3Pool.sol#2)
	- >=0.5.0 (lib/v3-core/contracts/interfaces/callback/IUniswapV3FlashCallback.sol#2)
	- >=0.5.0 (lib/v3-core/contracts/interfaces/callback/IUniswapV3SwapCallback.sol#2)
	- >=0.5.0 (lib/v3-core/contracts/interfaces/pool/IUniswapV3PoolActions.sol#2)
	- >=0.5.0 (lib/v3-core/contracts/interfaces/pool/IUniswapV3PoolDerivedState.sol#2)
	- >=0.5.0 (lib/v3-core/contracts/interfaces/pool/IUniswapV3PoolErrors.sol#2)
	- >=0.5.0 (lib/v3-core/contracts/interfaces/pool/IUniswapV3PoolEvents.sol#2)
	- >=0.5.0 (lib/v3-core/contracts/interfaces/pool/IUniswapV3PoolImmutables.sol#2)
	- >=0.5.0 (lib/v3-core/contracts/interfaces/pool/IUniswapV3PoolOwnerActions.sol#2)
	- >=0.5.0 (lib/v3-core/contracts/interfaces/pool/IUniswapV3PoolState.sol#2)
	- >=0.5.0 (lib/v3-periphery/contracts/interfaces/IPeripheryImmutableState.sol#2)
	- >=0.5.0 (lib/v3-periphery/contracts/libraries/LiquidityAmounts.sol#2)
	- >=0.5.0 (lib/v3-periphery/contracts/libraries/PoolAddress.sol#2)
	- >=0.7.5 (lib/v3-periphery/contracts/interfaces/IERC721Permit.sol#2)
	- >=0.7.5 (lib/v3-periphery/contracts/interfaces/INonfungiblePositionManager.sol#2)
	- >=0.7.5 (lib/v3-periphery/contracts/interfaces/IPeripheryPayments.sol#2)
	- >=0.7.5 (lib/v3-periphery/contracts/interfaces/IPoolInitializer.sol#2)
	- ^0.8.0 (lib/AggregatorV3Interface.sol#3)
	- ^0.8.0 (lib/IUniversalRouter.sol#2)
	- ^0.8.0 (lib/IWETH9.sol#2)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/access/Ownable.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/interfaces/IERC4626.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/security/ReentrancyGuard.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/token/ERC20/ERC20.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/token/ERC20/IERC20.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/token/ERC20/extensions/IERC20Metadata.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/token/ERC20/utils/SafeERC20.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/token/ERC721/IERC721.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/token/ERC721/IERC721Receiver.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/token/ERC721/extensions/IERC721Enumerable.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/token/ERC721/extensions/IERC721Metadata.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/utils/Context.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/utils/Multicall.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/utils/introspection/IERC165.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/utils/math/Math.sol#4)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/utils/math/SafeCast.sol#5)
	- ^0.8.0 (lib/openzeppelin-contracts/contracts/utils/math/SafeMath.sol#4)
	- ^0.8.0 (lib/permit2/src/interfaces/IAllowanceTransfer.sol#2)
	- ^0.8.0 (lib/permit2/src/interfaces/IEIP712.sol#2)
	- ^0.8.0 (lib/permit2/src/interfaces/IPermit2.sol#2)
	- ^0.8.0 (lib/permit2/src/interfaces/ISignatureTransfer.sol#2)
	- ^0.8.0 (lib/v3-core/contracts/libraries/FullMath.sol#2)
	- ^0.8.0 (lib/v3-core/contracts/libraries/TickMath.sol#2)
	- ^0.8.0 (src/InterestRateModel.sol#2)
	- ^0.8.0 (src/V3Oracle.sol#2)
	- ^0.8.0 (src/V3Vault.sol#2)
	- ^0.8.0 (src/automators/AutoExit.sol#2)
	- ^0.8.0 (src/automators/Automator.sol#2)
	- ^0.8.0 (src/interfaces/IErrors.sol#2)
	- ^0.8.0 (src/interfaces/IInterestRateModel.sol#2)
	- ^0.8.0 (src/interfaces/IV3Oracle.sol#2)
	- ^0.8.0 (src/interfaces/IVault.sol#2)
	- ^0.8.0 (src/transformers/AutoCompound.sol#2)
	- ^0.8.0 (src/transformers/AutoRange.sol#2)
	- ^0.8.0 (src/transformers/LeverageTransformer.sol#2)
	- ^0.8.0 (src/transformers/V3Utils.sol#2)
	- ^0.8.0 (src/utils/FlashloanLiquidator.sol#2)
	- ^0.8.0 (src/utils/Swapper.sol#2)
	- ^0.8.1 (lib/openzeppelin-contracts/contracts/utils/Address.sol#4)
	- v2 (lib/v3-periphery/contracts/interfaces/INonfungiblePositionManager.sol#3)
	- v2 (lib/v3-periphery/contracts/interfaces/IPoolInitializer.sol#3)

/// @audit ****************** Affected Code *******************
   2: pragma solidity >=0.4.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/lib/v3-core/contracts/libraries/FixedPoint128.sol#L2-L2)

### [N-02]<a name="n-02"></a> Cyclomatic complexity

Detects functions with high (> 11) cyclomatic complexity.  **Recom** Reduce cyclomatic complexity by splitting the function into several smaller subroutines.

*There are 3 instance(s) of this issue:*

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
V3Utils.execute(uint256,V3Utils.Instructions) (L#115-352) has a high cyclomatic complexity (16).

/// @audit ****************** Affected Code *******************
 115:     function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {
 116:         (,, address token0, address token1,,,, uint128 liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);
 117: 
 118:         uint256 amount0;
 119:         uint256 amount1;
 120:         if (instructions.liquidity != 0) {
 121:             (amount0, amount1) = _decreaseLiquidity(
 122:                 tokenId,
 123:                 instructions.liquidity,
 124:                 instructions.deadline,
 125:                 instructions.amountRemoveMin0,
 126:                 instructions.amountRemoveMin1
 127:             );
 128:         }
 129:         (amount0, amount1) = _collectFees(
 130:             tokenId,
 131:             IERC20(token0),
 132:             IERC20(token1),
 133:             instructions.feeAmount0 == type(uint128).max
 134:                 ? type(uint128).max
 135:                 : (amount0 + instructions.feeAmount0).toUint128(),
 136:             instructions.feeAmount1 == type(uint128).max
 137:                 ? type(uint128).max
 138:                 : (amount1 + instructions.feeAmount1).toUint128()
 139:         );
 140: 
 141:         // check if enough tokens are available for swaps
 142:         if (amount0 < instructions.amountIn0 || amount1 < instructions.amountIn1) {
 143:             revert AmountError();
 144:         }
 145: 
 146:         if (instructions.whatToDo == WhatToDo.COMPOUND_FEES) {
 147:             if (instructions.targetToken == token0) {
 148:                 (liquidity, amount0, amount1) = _swapAndIncrease(
 149:                     SwapAndIncreaseLiquidityParams(
 150:                         tokenId,
 151:                         amount0,
 152:                         amount1,
 153:                         instructions.recipient,
 154:                         instructions.deadline,
 155:                         IERC20(token1),
 156:                         instructions.amountIn1,
 157:                         instructions.amountOut1Min,
 158:                         instructions.swapData1,
 159:                         0,
 160:                         0,
 161:                         "",
 162:                         instructions.amountAddMin0,
 163:                         instructions.amountAddMin1,
 164:                         ""
 165:                     ),
 166:                     IERC20(token0),
 167:                     IERC20(token1),
 168:                     instructions.unwrap
 169:                 );
 170:             } else if (instructions.targetToken == token1) {
 171:                 (liquidity, amount0, amount1) = _swapAndIncrease(
 172:                     SwapAndIncreaseLiquidityParams(
 173:                         tokenId,
 174:                         amount0,
 175:                         amount1,
 176:                         instructions.recipient,
 177:                         instructions.deadline,
 178:                         IERC20(token0),
 179:                         0,
 180:                         0,
 181:                         "",
 182:                         instructions.amountIn0,
 183:                         instructions.amountOut0Min,
 184:                         instructions.swapData0,
 185:                         instructions.amountAddMin0,
 186:                         instructions.amountAddMin1,
 187:                         ""
 188:                     ),
 189:                     IERC20(token0),
 190:                     IERC20(token1),
 191:                     instructions.unwrap
 192:                 );
 193:             } else {
 194:                 // no swap is done here
 195:                 (liquidity, amount0, amount1) = _swapAndIncrease(
 196:                     SwapAndIncreaseLiquidityParams(
 197:                         tokenId,
 198:                         amount0,
 199:                         amount1,
 200:                         instructions.recipient,
 201:                         instructions.deadline,
 202:                         IERC20(address(0)),
 203:                         0,
 204:                         0,
 205:                         "",
 206:                         0,
 207:                         0,
 208:                         "",
 209:                         instructions.amountAddMin0,
 210:                         instructions.amountAddMin1,
 211:                         ""
 212:                     ),
 213:                     IERC20(token0),
 214:                     IERC20(token1),
 215:                     instructions.unwrap
 216:                 );
 217:             }
 218:             emit CompoundFees(tokenId, liquidity, amount0, amount1);
 219:         } else if (instructions.whatToDo == WhatToDo.CHANGE_RANGE) {
 220:             if (instructions.targetToken == token0) {
 221:                 (newTokenId,,,) = _swapAndMint(
 222:                     SwapAndMintParams(
 223:                         IERC20(token0),
 224:                         IERC20(token1),
 225:                         instructions.fee,
 226:                         instructions.tickLower,
 227:                         instructions.tickUpper,
 228:                         amount0,
 229:                         amount1,
 230:                         instructions.recipient,
 231:                         instructions.recipientNFT,
 232:                         instructions.deadline,
 233:                         IERC20(token1),
 234:                         instructions.amountIn1,
 235:                         instructions.amountOut1Min,
 236:                         instructions.swapData1,
 237:                         0,
 238:                         0,
 239:                         "",
 240:                         instructions.amountAddMin0,
 241:                         instructions.amountAddMin1,
 242:                         instructions.swapAndMintReturnData,
 243:                         ""
 244:                     ),
 245:                     instructions.unwrap
 246:                 );
 247:             } else if (instructions.targetToken == token1) {
 248:                 (newTokenId,,,) = _swapAndMint(
 249:                     SwapAndMintParams(
 250:                         IERC20(token0),
 251:                         IERC20(token1),
 252:                         instructions.fee,
 253:                         instructions.tickLower,
 254:                         instructions.tickUpper,
 255:                         amount0,
 256:                         amount1,
 257:                         instructions.recipient,
 258:                         instructions.recipientNFT,
 259:                         instructions.deadline,
 260:                         IERC20(token0),
 261:                         0,
 262:                         0,
 263:                         "",
 264:                         instructions.amountIn0,
 265:                         instructions.amountOut0Min,
 266:                         instructions.swapData0,
 267:                         instructions.amountAddMin0,
 268:                         instructions.amountAddMin1,
 269:                         instructions.swapAndMintReturnData,
 270:                         ""
 271:                     ),
 272:                     instructions.unwrap
 273:                 );
 274:             } else {
 275:                 // no swap is done here
 276:                 (newTokenId,,,) = _swapAndMint(
 277:                     SwapAndMintParams(
 278:                         IERC20(token0),
 279:                         IERC20(token1),
 280:                         instructions.fee,
 281:                         instructions.tickLower,
 282:                         instructions.tickUpper,
 283:                         amount0,
 284:                         amount1,
 285:                         instructions.recipient,
 286:                         instructions.recipientNFT,
 287:                         instructions.deadline,
 288:                         IERC20(address(0)),
 289:                         0,
 290:                         0,
 291:                         "",
 292:                         0,
 293:                         0,
 294:                         "",
 295:                         instructions.amountAddMin0,
 296:                         instructions.amountAddMin1,
 297:                         instructions.swapAndMintReturnData,
 298:                         ""
 299:                     ),
 300:                     instructions.unwrap
 301:                 );
 302:             }
 303:             emit ChangeRange(tokenId, newTokenId);
 304:         } else if (instructions.whatToDo == WhatToDo.WITHDRAW_AND_COLLECT_AND_SWAP) {
 305:             uint256 targetAmount;
 306:             if (token0 != instructions.targetToken) {
 307:                 (uint256 amountInDelta, uint256 amountOutDelta) = _routerSwap(
 308:                     Swapper.RouterSwapParams(
 309:                         IERC20(token0),
 310:                         IERC20(instructions.targetToken),
 311:                         amount0,
 312:                         instructions.amountOut0Min,
 313:                         instructions.swapData0
 314:                     )
 315:                 );
 316:                 if (amountInDelta < amount0) {
 317:                     _transferToken(instructions.recipient, IERC20(token0), amount0 - amountInDelta, instructions.unwrap);
 318:                 }
 319:                 targetAmount += amountOutDelta;
 320:             } else {
 321:                 targetAmount += amount0;
 322:             }
 323:             if (token1 != instructions.targetToken) {
 324:                 (uint256 amountInDelta, uint256 amountOutDelta) = _routerSwap(
 325:                     Swapper.RouterSwapParams(
 326:                         IERC20(token1),
 327:                         IERC20(instructions.targetToken),
 328:                         amount1,
 329:                         instructions.amountOut1Min,
 330:                         instructions.swapData1
 331:                     )
 332:                 );
 333:                 if (amountInDelta < amount1) {
 334:                     _transferToken(instructions.recipient, IERC20(token1), amount1 - amountInDelta, instructions.unwrap);
 335:                 }
 336:                 targetAmount += amountOutDelta;
 337:             } else {
 338:                 targetAmount += amount1;
 339:             }
 340: 
 341:             // send complete target amount
 342:             if (targetAmount != 0 && instructions.targetToken != address(0)) {
 343:                 _transferToken(
 344:                     instructions.recipient, IERC20(instructions.targetToken), targetAmount, instructions.unwrap
 345:                 );
 346:             }
 347: 
 348:             emit WithdrawAndCollectAndSwap(tokenId, instructions.targetToken, targetAmount);
 349:         } else {
 350:             revert NotSupportedWhatToDo();
 351:         }
 352:     }
```

*GitHub* : [115-352](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L115-L352)

```solidity
File: src/transformers/AutoRange.sol

/// @audit ******************* Issue Detail *******************
AutoRange.execute(AutoRange.ExecuteParams) (L#111-272) has a high cyclomatic complexity (19).

/// @audit ****************** Affected Code *******************
 111:     function execute(ExecuteParams calldata params) external {
 112:         if (!operators[msg.sender] && !vaults[msg.sender]) {
 113:             revert Unauthorized();
 114:         }
 115:         ExecuteState memory state;
 116:         PositionConfig memory config = positionConfigs[params.tokenId];
 117: 
 118:         if (config.lowerTickDelta == config.upperTickDelta) {
 119:             revert NotConfigured();
 120:         }
 121: 
 122:         if (
 123:             config.onlyFees && params.rewardX64 > config.maxRewardX64
 124:                 || !config.onlyFees && params.rewardX64 > config.maxRewardX64
 125:         ) {
 126:             revert ExceedsMaxReward();
 127:         }
 128: 
 129:         // get position info
 130:         (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
 131:             nonfungiblePositionManager.positions(params.tokenId);
 132: 
 133:         if (state.liquidity != params.liquidity) {
 134:             revert LiquidityChanged();
 135:         }
 136: 
 137:         (state.amount0, state.amount1, state.feeAmount0, state.feeAmount1) = _decreaseFullLiquidityAndCollect(
 138:             params.tokenId, state.liquidity, params.amountRemoveMin0, params.amountRemoveMin1, params.deadline
 139:         );
 140: 
 141:         // if only fees reward is removed before adding
 142:         if (config.onlyFees) {
 143:             state.protocolReward0 = state.feeAmount0 * params.rewardX64 / Q64;
 144:             state.protocolReward1 = state.feeAmount1 * params.rewardX64 / Q64;
 145:             state.amount0 -= state.protocolReward0;
 146:             state.amount1 -= state.protocolReward1;
 147:         }
 148: 
 149:         if (params.swap0To1 && params.amountIn > state.amount0 || !params.swap0To1 && params.amountIn > state.amount1) {
 150:             revert SwapAmountTooLarge();
 151:         }
 152: 
 153:         // get pool info
 154:         state.pool = _getPool(state.token0, state.token1, state.fee);
 155: 
 156:         // check oracle for swap
 157:         (state.amountOutMin, state.currentTick,,) = _validateSwap(
 158:             params.swap0To1,
 159:             params.amountIn,
 160:             state.pool,
 161:             TWAPSeconds,
 162:             maxTWAPTickDifference,
 163:             params.swap0To1 ? config.token0SlippageX64 : config.token1SlippageX64
 164:         );
 165: 
 166:         if (
 167:             state.currentTick < state.tickLower - config.lowerTickLimit
 168:                 || state.currentTick >= state.tickUpper + config.upperTickLimit
 169:         ) {
 170:             int24 tickSpacing = _getTickSpacing(state.fee);
 171:             int24 baseTick = state.currentTick - (((state.currentTick % tickSpacing) + tickSpacing) % tickSpacing);
 172: 
 173:             // check if new range same as old range
 174:             if (
 175:                 baseTick + config.lowerTickDelta == state.tickLower
 176:                     && baseTick + config.upperTickDelta == state.tickUpper
 177:             ) {
 178:                 revert SameRange();
 179:             }
 180: 
 181:             (state.amountInDelta, state.amountOutDelta) = _routerSwap(
 182:                 Swapper.RouterSwapParams(
 183:                     params.swap0To1 ? IERC20(state.token0) : IERC20(state.token1),
 184:                     params.swap0To1 ? IERC20(state.token1) : IERC20(state.token0),
 185:                     params.amountIn,
 186:                     state.amountOutMin,
 187:                     params.swapData
 188:                 )
 189:             );
 190: 
 191:             state.amount0 = params.swap0To1 ? state.amount0 - state.amountInDelta : state.amount0 + state.amountOutDelta;
 192:             state.amount1 = params.swap0To1 ? state.amount1 + state.amountOutDelta : state.amount1 - state.amountInDelta;
 193: 
 194:             // max amount to add - removing max potential fees (if config.onlyFees - the have been removed already)
 195:             state.maxAddAmount0 = config.onlyFees ? state.amount0 : state.amount0 * Q64 / (params.rewardX64 + Q64);
 196:             state.maxAddAmount1 = config.onlyFees ? state.amount1 : state.amount1 * Q64 / (params.rewardX64 + Q64);
 197: 
 198:             INonfungiblePositionManager.MintParams memory mintParams = INonfungiblePositionManager.MintParams(
 199:                 address(state.token0),
 200:                 address(state.token1),
 201:                 state.fee,
 202:                 SafeCast.toInt24(baseTick + config.lowerTickDelta), // reverts if out of valid range
 203:                 SafeCast.toInt24(baseTick + config.upperTickDelta), // reverts if out of valid range
 204:                 state.maxAddAmount0,
 205:                 state.maxAddAmount1,
 206:                 0,
 207:                 0,
 208:                 address(this), // is sent to real recipient aftwards
 209:                 params.deadline
 210:             );
 211: 
 212:             // approve npm
 213:             SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), state.maxAddAmount0);
 214:             SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), state.maxAddAmount1);
 215: 
 216:             // mint is done to address(this) first - its not a safemint
 217:             (state.newTokenId,, state.amountAdded0, state.amountAdded1) = nonfungiblePositionManager.mint(mintParams);
 218: 
 219:             // remove remaining approval
 220:             SafeERC20.safeApprove(IERC20(state.token0), address(nonfungiblePositionManager), 0);
 221:             SafeERC20.safeApprove(IERC20(state.token1), address(nonfungiblePositionManager), 0);
 222: 
 223:             state.owner = nonfungiblePositionManager.ownerOf(params.tokenId);
 224: 
 225:             // get the real owner - if owner is vault - for sending leftover tokens
 226:             state.realOwner = state.owner;
 227:             if (vaults[state.owner]) {
 228:                 state.realOwner = IVault(state.owner).ownerOf(params.tokenId);
 229:             }
 230: 
 231:             // send the new nft to the owner / vault
 232:             nonfungiblePositionManager.safeTransferFrom(address(this), state.owner, state.newTokenId);
 233: 
 234:             // protocol reward is calculated based on added amount (to incentivize optimal swap done by operator)
 235:             if (!config.onlyFees) {
 236:                 state.protocolReward0 = state.amountAdded0 * params.rewardX64 / Q64;
 237:                 state.protocolReward1 = state.amountAdded1 * params.rewardX64 / Q64;
 238:                 state.amount0 -= state.protocolReward0;
 239:                 state.amount1 -= state.protocolReward1;
 240:             }
 241: 
 242:             // send leftover to real owner
 243:             if (state.amount0 - state.amountAdded0 > 0) {
 244:                 _transferToken(state.realOwner, IERC20(state.token0), state.amount0 - state.amountAdded0, true);
 245:             }
 246:             if (state.amount1 - state.amountAdded1 > 0) {
 247:                 _transferToken(state.realOwner, IERC20(state.token1), state.amount1 - state.amountAdded1, true);
 248:             }
 249: 
 250:             // copy token config for new token
 251:             positionConfigs[state.newTokenId] = config;
 252:             emit PositionConfigured(
 253:                 state.newTokenId,
 254:                 config.lowerTickLimit,
 255:                 config.upperTickLimit,
 256:                 config.lowerTickDelta,
 257:                 config.upperTickDelta,
 258:                 config.token0SlippageX64,
 259:                 config.token1SlippageX64,
 260:                 config.onlyFees,
 261:                 config.maxRewardX64
 262:             );
 263: 
 264:             // delete config for old position
 265:             delete positionConfigs[params.tokenId];
 266:             emit PositionConfigured(params.tokenId, 0, 0, 0, 0, 0, 0, false, 0);
 267: 
 268:             emit RangeChanged(params.tokenId, state.newTokenId);
 269:         } else {
 270:             revert NotReady();
 271:         }
 272:     }
```

*GitHub* : [111-272](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L111-L272)

```solidity
File: src/automators/AutoExit.sol

/// @audit ******************* Issue Detail *******************
AutoExit.execute(AutoExit.ExecuteParams) (L#100-214) has a high cyclomatic complexity (21).

/// @audit ****************** Affected Code *******************
 100:     function execute(ExecuteParams calldata params) external {
 101:         if (!operators[msg.sender]) {
 102:             revert Unauthorized();
 103:         }
 104: 
 105:         ExecuteState memory state;
 106:         PositionConfig memory config = positionConfigs[params.tokenId];
 107: 
 108:         if (!config.isActive) {
 109:             revert NotConfigured();
 110:         }
 111: 
 112:         if (
 113:             config.onlyFees && params.rewardX64 > config.maxRewardX64
 114:                 || !config.onlyFees && params.rewardX64 > config.maxRewardX64
 115:         ) {
 116:             revert ExceedsMaxReward();
 117:         }
 118: 
 119:         // get position info
 120:         (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
 121:             nonfungiblePositionManager.positions(params.tokenId);
 122: 
 123:         // so can be executed only once
 124:         if (state.liquidity == 0) {
 125:             revert NoLiquidity();
 126:         }
 127:         if (state.liquidity != params.liquidity) {
 128:             revert LiquidityChanged();
 129:         }
 130: 
 131:         state.pool = _getPool(state.token0, state.token1, state.fee);
 132:         (, state.tick,,,,,) = state.pool.slot0();
 133: 
 134:         // not triggered
 135:         if (config.token0TriggerTick <= state.tick && state.tick < config.token1TriggerTick) {
 136:             revert NotReady();
 137:         }
 138: 
 139:         state.isAbove = state.tick >= config.token1TriggerTick;
 140:         state.isSwap = !state.isAbove && config.token0Swap || state.isAbove && config.token1Swap;
 141: 
 142:         // decrease full liquidity for given position - and return fees as well
 143:         (state.amount0, state.amount1, state.feeAmount0, state.feeAmount1) = _decreaseFullLiquidityAndCollect(
 144:             params.tokenId, state.liquidity, params.amountRemoveMin0, params.amountRemoveMin1, params.deadline
 145:         );
 146: 
 147:         // swap to other token
 148:         if (state.isSwap) {
 149:             if (params.swapData.length == 0) {
 150:                 revert MissingSwapData();
 151:             }
 152: 
 153:             // reward is taken before swap - if from fees only
 154:             if (config.onlyFees) {
 155:                 state.amount0 -= state.feeAmount0 * params.rewardX64 / Q64;
 156:                 state.amount1 -= state.feeAmount1 * params.rewardX64 / Q64;
 157:             }
 158: 
 159:             state.swapAmount = state.isAbove ? state.amount1 : state.amount0;
 160: 
 161:             // checks if price in valid oracle range and calculates amountOutMin
 162:             (state.amountOutMin,,,) = _validateSwap(
 163:                 !state.isAbove,
 164:                 state.swapAmount,
 165:                 state.pool,
 166:                 TWAPSeconds,
 167:                 maxTWAPTickDifference,
 168:                 state.isAbove ? config.token1SlippageX64 : config.token0SlippageX64
 169:             );
 170: 
 171:             (state.amountInDelta, state.amountOutDelta) = _routerSwap(
 172:                 Swapper.RouterSwapParams(
 173:                     state.isAbove ? IERC20(state.token1) : IERC20(state.token0),
 174:                     state.isAbove ? IERC20(state.token0) : IERC20(state.token1),
 175:                     state.swapAmount,
 176:                     state.amountOutMin,
 177:                     params.swapData
 178:                 )
 179:             );
 180: 
 181:             state.amount0 = state.isAbove ? state.amount0 + state.amountOutDelta : state.amount0 - state.amountInDelta;
 182:             state.amount1 = state.isAbove ? state.amount1 - state.amountInDelta : state.amount1 + state.amountOutDelta;
 183: 
 184:             // when swap and !onlyFees - protocol reward is removed only from target token (to incentivize optimal swap done by operator)
 185:             if (!config.onlyFees) {
 186:                 if (state.isAbove) {
 187:                     state.amount0 -= state.amount0 * params.rewardX64 / Q64;
 188:                 } else {
 189:                     state.amount1 -= state.amount1 * params.rewardX64 / Q64;
 190:                 }
 191:             }
 192:         } else {
 193:             // reward is taken as configured
 194:             state.amount0 -= (config.onlyFees ? state.feeAmount0 : state.amount0) * params.rewardX64 / Q64;
 195:             state.amount1 -= (config.onlyFees ? state.feeAmount1 : state.amount1) * params.rewardX64 / Q64;
 196:         }
 197: 
 198:         state.owner = nonfungiblePositionManager.ownerOf(params.tokenId);
 199:         if (state.amount0 > 0) {
 200:             _transferToken(state.owner, IERC20(state.token0), state.amount0, true);
 201:         }
 202:         if (state.amount1 > 0) {
 203:             _transferToken(state.owner, IERC20(state.token1), state.amount1, true);
 204:         }
 205: 
 206:         // delete config for position
 207:         delete positionConfigs[params.tokenId];
 208:         emit PositionConfigured(params.tokenId, false, false, false, 0, 0, 0, 0, false, 0);
 209: 
 210:         // log event
 211:         emit Executed(
 212:             params.tokenId, msg.sender, state.isSwap, state.amount0, state.amount1, state.token0, state.token1
 213:         );
 214:     }
```

*GitHub* : [100-214](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L100-L214)

### [N-03]<a name="n-03"></a> Incorrect versions of Solidity

`solc` frequently releases new compiler versions. Using an old or buggy version such as [0.4.22, 0.5.5, 0.5.6, 0.5.14, 0.6.9, 0.8.8, 0.8.20] prevents access to new Solidity security checks. We also recommend avoiding complex `pragma` statement.  

*There are 13 instance(s) of this issue:*

```solidity
File: src/interfaces/IV3Oracle.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/interfaces/IV3Oracle.sol#L2-L2)

```solidity
File: src/transformers/AutoRange.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L2-L2)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L2-L2)

```solidity
File: src/automators/AutoExit.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L2-L2)

```solidity
File: src/InterestRateModel.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L2-L2)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L2-L2)

```solidity
File: src/utils/Swapper.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L2-L2)

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L2-L2)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L2-L2)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L2-L2)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L2-L2)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L2-L2)

```solidity
File: src/interfaces/IInterestRateModel.sol

/// @audit ******************* Issue Detail *******************
Pragma version^0.8.0 (L#2) allows old versions

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;
```

*GitHub* : [2-2](https://github.com/code-423n4/2024-03-revert-lend/src/interfaces/IInterestRateModel.sol#L2-L2)

### [N-04]<a name="n-04"></a> Low-level calls

The use of low-level calls is error-prone. Low-level calls do not check for [code existence](https://solidity.readthedocs.io/en/v0.4.25/control-structures.html#error-handling-assert-require-revert-and-exceptions) or call success.  **Recom** Avoid low-level calls. Check the call success. If the call is meant for a contract, check for code existence.

*There are 5 instance(s) of this issue:*

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Low level call in Automator._transferToken(address,IERC20,uint256,bool) (L#218-228):
	- (sent) = to.call{value: amount}() (L#221)

/// @audit ************** Possible Issue Line(s) **************
	L#221,  

/// @audit ****************** Affected Code *******************
 218:     function _transferToken(address to, IERC20 token, uint256 amount, bool unwrap) internal {
 219:         if (address(weth) == address(token) && unwrap) {
 220:             weth.withdraw(amount);
 221:             (bool sent,) = to.call{value: amount}("");
 222:             if (!sent) {
 223:                 revert EtherSendFailed();
 224:             }
 225:         } else {
 226:             SafeERC20.safeTransfer(token, to, amount);
 227:         }
 228:     }
```

*GitHub* : [218-228](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L218-L228)

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Low level call in Automator.withdrawETH(address) (L#123-135):
	- (sent) = to.call{value: balance}() (L#130)

/// @audit ************** Possible Issue Line(s) **************
	L#130,  

/// @audit ****************** Affected Code *******************
 123:     function withdrawETH(address to) external {
 124:         if (msg.sender != withdrawer) {
 125:             revert Unauthorized();
 126:         }
 127: 
 128:         uint256 balance = address(this).balance;
 129:         if (balance > 0) {
 130:             (bool sent,) = to.call{value: balance}("");
 131:             if (!sent) {
 132:                 revert EtherSendFailed();
 133:             }
 134:         }
 135:     }
```

*GitHub* : [123-135](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L123-L135)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Low level call in V3Utils._transferToken(address,IERC20,uint256,bool) (L#864-874):
	- (sent) = to.call{value: amount}() (L#867)

/// @audit ************** Possible Issue Line(s) **************
	L#867,  

/// @audit ****************** Affected Code *******************
 864:     function _transferToken(address to, IERC20 token, uint256 amount, bool unwrap) internal {
 865:         if (address(weth) == address(token) && unwrap) {
 866:             weth.withdraw(amount);
 867:             (bool sent,) = to.call{value: amount}("");
 868:             if (!sent) {
 869:                 revert EtherSendFailed();
 870:             }
 871:         } else {
 872:             SafeERC20.safeTransfer(token, to, amount);
 873:         }
 874:     }
```

*GitHub* : [864-874](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L864-L874)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Low level call in V3Vault.transform(uint256,address,bytes) (L#497-545):
	- (success) = transformer.call(data) (L#522)

/// @audit ************** Possible Issue Line(s) **************
	L#522,  

/// @audit ****************** Affected Code *******************
 497:     function transform(uint256 tokenId, address transformer, bytes calldata data)
 498:         external
 499:         override
 500:         returns (uint256 newTokenId)
 501:     {
 502:         if (tokenId == 0 || !transformerAllowList[transformer]) {
 503:             revert TransformNotAllowed();
 504:         }
 505:         if (transformedTokenId > 0) {
 506:             revert Reentrancy();
 507:         }
 508:         transformedTokenId = tokenId;
 509: 
 510:         (uint256 newDebtExchangeRateX96,) = _updateGlobalInterest();
 511: 
 512:         address loanOwner = tokenOwner[tokenId];
 513: 
 514:         // only the owner of the loan, the vault itself or any approved caller can call this
 515:         if (loanOwner != msg.sender && !transformApprovals[loanOwner][tokenId][msg.sender]) {
 516:             revert Unauthorized();
 517:         }
 518: 
 519:         // give access to transformer
 520:         nonfungiblePositionManager.approve(transformer, tokenId);
 521: 
 522:         (bool success,) = transformer.call(data);
 523:         if (!success) {
 524:             revert TransformFailed();
 525:         }
 526: 
 527:         // may have changed in the meantime
 528:         tokenId = transformedTokenId;
 529: 
 530:         // check owner not changed (NEEDED because token could have been moved somewhere else in the meantime)
 531:         address owner = nonfungiblePositionManager.ownerOf(tokenId);
 532:         if (owner != address(this)) {
 533:             revert Unauthorized();
 534:         }
 535: 
 536:         // remove access for transformer
 537:         nonfungiblePositionManager.approve(address(0), tokenId);
 538: 
 539:         uint256 debt = _convertToAssets(loans[tokenId].debtShares, newDebtExchangeRateX96, Math.Rounding.Up);
 540:         _requireLoanIsHealthy(tokenId, debt);
 541: 
 542:         transformedTokenId = 0;
 543: 
 544:         return tokenId;
 545:     }
```

*GitHub* : [497-545](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L497-L545)

```solidity
File: src/utils/Swapper.sol

/// @audit ******************* Issue Detail *******************
Low level call in Swapper._routerSwap(Swapper.RouterSwapParams) (L#73-118):
	- (success) = zeroxRouter.call(data.data) (L#89)

/// @audit ************** Possible Issue Line(s) **************
	L#89,  

/// @audit ****************** Affected Code *******************
  73:     function _routerSwap(RouterSwapParams memory params)
  74:         internal
  75:         returns (uint256 amountInDelta, uint256 amountOutDelta)
  76:     {
  77:         if (params.amountIn != 0 && params.swapData.length != 0 && address(params.tokenOut) != address(0)) {
  78:             uint256 balanceInBefore = params.tokenIn.balanceOf(address(this));
  79:             uint256 balanceOutBefore = params.tokenOut.balanceOf(address(this));
  80: 
  81:             // get router specific swap data
  82:             (address router, bytes memory routerData) = abi.decode(params.swapData, (address, bytes));
  83: 
  84:             if (router == zeroxRouter) {
  85:                 ZeroxRouterData memory data = abi.decode(routerData, (ZeroxRouterData));
  86:                 // approve needed amount
  87:                 SafeERC20.safeApprove(params.tokenIn, data.allowanceTarget, params.amountIn);
  88:                 // execute swap
  89:                 (bool success,) = zeroxRouter.call(data.data);
  90:                 if (!success) {
  91:                     revert SwapFailed();
  92:                 }
  93:                 // reset approval
  94:                 SafeERC20.safeApprove(params.tokenIn, data.allowanceTarget, 0);
  95:             } else if (router == universalRouter) {
  96:                 UniversalRouterData memory data = abi.decode(routerData, (UniversalRouterData));
  97:                 // tokens are transfered to Universalrouter directly (data.commands must include sweep action!)
  98:                 SafeERC20.safeTransfer(params.tokenIn, universalRouter, params.amountIn);
  99:                 IUniversalRouter(universalRouter).execute(data.commands, data.inputs, data.deadline);
 100:             } else {
 101:                 revert WrongContract();
 102:             }
 103: 
 104:             uint256 balanceInAfter = params.tokenIn.balanceOf(address(this));
 105:             uint256 balanceOutAfter = params.tokenOut.balanceOf(address(this));
 106: 
 107:             amountInDelta = balanceInBefore - balanceInAfter;
 108:             amountOutDelta = balanceOutAfter - balanceOutBefore;
 109: 
 110:             // amountMin slippage check
 111:             if (amountOutDelta < params.amountOutMin) {
 112:                 revert SlippageError();
 113:             }
 114: 
 115:             // event for any swap with exact swapped value
 116:             emit Swap(address(params.tokenIn), address(params.tokenOut), amountInDelta, amountOutDelta);
 117:         }
 118:     }
```

*GitHub* : [73-118](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L73-L118)

### [N-05]<a name="n-05"></a> Conformance to Solidity naming conventions

Solidity defines a [naming convention](https://solidity.readthedocs.io/en/v0.4.25/style-guide.html#naming-conventions) that should be followed.  **Recom** Follow the Solidity [naming convention](https://solidity.readthedocs.io/en/v0.4.25/style-guide.html#naming-conventions).

*There are 15 instance(s) of this issue:*

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Parameter Automator.setTWAPConfig(uint16,uint32)._TWAPSeconds (L#87) is not in mixedCase

/// @audit ****************** Affected Code *******************
  87:     function setTWAPConfig(uint16 _maxTWAPTickDifference, uint32 _TWAPSeconds) public onlyOwner {
```

*GitHub* : [87-87](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L87-L87)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Parameter V3Vault.setLimits(uint256,uint256,uint256,uint256,uint256)._minLoanSize (L#808) is not in mixedCase

/// @audit ****************** Affected Code *******************
 808:         uint256 _minLoanSize,
```

*GitHub* : [808-808](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L808-L808)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Parameter V3Vault.setReserveFactor(uint32)._reserveFactorX32 (L#837) is not in mixedCase

/// @audit ****************** Affected Code *******************
 837:     function setReserveFactor(uint32 _reserveFactorX32) external onlyOwner {
```

*GitHub* : [837-837](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L837-L837)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Parameter V3Vault.setLimits(uint256,uint256,uint256,uint256,uint256)._dailyDebtIncreaseLimitMin (L#812) is not in mixedCase

/// @audit ****************** Affected Code *******************
 812:         uint256 _dailyDebtIncreaseLimitMin
```

*GitHub* : [812-812](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L812-L812)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Parameter V3Vault.setLimits(uint256,uint256,uint256,uint256,uint256)._globalDebtLimit (L#810) is not in mixedCase

/// @audit ****************** Affected Code *******************
 810:         uint256 _globalDebtLimit,
```

*GitHub* : [810-810](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L810-L810)

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Parameter Automator.setVault(address,bool)._vault (L#79) is not in mixedCase

/// @audit ****************** Affected Code *******************
  79:     function setVault(address _vault, bool _active) public onlyOwner {
```

*GitHub* : [79-79](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L79-L79)

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Parameter Automator.setOperator(address,bool)._active (L#69) is not in mixedCase

/// @audit ****************** Affected Code *******************
  69:     function setOperator(address _operator, bool _active) public onlyOwner {
```

*GitHub* : [69-69](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L69-L69)

```solidity
File: src/transformers/AutoCompound.sol

/// @audit ******************* Issue Detail *******************
Parameter AutoCompound.setReward(uint64)._totalRewardX64 (L#243) is not in mixedCase

/// @audit ****************** Affected Code *******************
 243:     function setReward(uint64 _totalRewardX64) external onlyOwner {
```

*GitHub* : [243-243](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L243-L243)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Parameter V3Vault.setLimits(uint256,uint256,uint256,uint256,uint256)._globalLendLimit (L#809) is not in mixedCase

/// @audit ****************** Affected Code *******************
 809:         uint256 _globalLendLimit,
```

*GitHub* : [809-809](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L809-L809)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
Parameter V3Oracle.setMaxPoolPriceDifference(uint16)._maxPoolPriceDifference (L#185) is not in mixedCase

/// @audit ****************** Affected Code *******************
 185:     function setMaxPoolPriceDifference(uint16 _maxPoolPriceDifference) external onlyOwner {
```

*GitHub* : [185-185](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L185-L185)

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Variable Automator.TWAPSeconds (L#38) is not in mixedCase

/// @audit ****************** Affected Code *******************
  38:     uint32 public TWAPSeconds;
```

*GitHub* : [38-38](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L38-L38)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Parameter V3Vault.setLimits(uint256,uint256,uint256,uint256,uint256)._dailyLendIncreaseLimitMin (L#811) is not in mixedCase

/// @audit ****************** Affected Code *******************
 811:         uint256 _dailyLendIncreaseLimitMin,
```

*GitHub* : [811-811](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L811-L811)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Parameter V3Vault.setReserveProtectionFactor(uint32)._reserveProtectionFactorX32 (L#844) is not in mixedCase

/// @audit ****************** Affected Code *******************
 844:     function setReserveProtectionFactor(uint32 _reserveProtectionFactorX32) external onlyOwner {
```

*GitHub* : [844-844](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L844-L844)

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Parameter Automator.setWithdrawer(address)._withdrawer (L#59) is not in mixedCase

/// @audit ****************** Affected Code *******************
  59:     function setWithdrawer(address _withdrawer) public onlyOwner {
```

*GitHub* : [59-59](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L59-L59)

```solidity
File: src/InterestRateModel.sol

/// @audit ******************* Issue Detail *******************
Parameter InterestRateModel.setValues(uint256,uint256,uint256,uint256)._kinkX96 (L#86) is not in mixedCase

/// @audit ****************** Affected Code *******************
  86:         uint256 _kinkX96
```

*GitHub* : [86-86](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L86-L86)

### [N-06]<a name="n-06"></a> Variable names too similar

Detect variables with names that are too similar.  **Recom** Prevent variables from having similar names.

*There are 20 instance(s) of this issue:*

```solidity
File: src/utils/Swapper.sol

/// @audit ******************* Issue Detail *******************
Variable Swapper._poolSwap(Swapper.PoolSwapParams).amount0Delta (L#134) is too similar to IUniswapV3SwapCallback.uniswapV3SwapCallback(int256,int256,bytes).amount1Delta (L#18)

/// @audit ****************** Affected Code *******************
 134:             (int256 amount0Delta, int256 amount1Delta) = params.pool.swap(
```

*GitHub* : [134-134](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L134-L134)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Variable V3Utils._collectFees(uint256,IERC20,IERC20,uint128,uint128).balanceBefore0 (L#896) is too similar to V3Utils._collectFees(uint256,IERC20,IERC20,uint128,uint128).balanceBefore1 (L#897)

/// @audit ************** Possible Issue Line(s) **************
	L#897,  

/// @audit ****************** Affected Code *******************
 896:         uint256 balanceBefore0 = token0.balanceOf(address(this));
 897:         uint256 balanceBefore1 = token1.balanceOf(address(this));
```

*GitHub* : [896-896](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L896-L896)

```solidity
File: src/utils/FlashloanLiquidator.sol

/// @audit ******************* Issue Detail *******************
Variable FlashloanLiquidator.uniswapV3FlashCallback(uint256,uint256,bytes).balance_scope_0 (L#95) is too similar to FlashloanLiquidator.uniswapV3FlashCallback(uint256,uint256,bytes).balance_scope_1 (L#101)

/// @audit ************** Possible Issue Line(s) **************
	L#101,  

/// @audit ****************** Affected Code *******************
  95:             uint256 balance = data.swap1.tokenIn.balanceOf(address(this));
 101:             uint256 balance = data.asset.balanceOf(address(this));
```

*GitHub* : [95-95](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L95-L95)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Variable V3Utils._collectFees(uint256,IERC20,IERC20,uint128,uint128).collectAmount0 (L#892) is too similar to V3Utils._collectFees(uint256,IERC20,IERC20,uint128,uint128).collectAmount1 (L#892)

/// @audit ************** Possible Issue Line(s) **************
	L#892,  

/// @audit ****************** Affected Code *******************
 892:     function _collectFees(uint256 tokenId, IERC20 token0, IERC20 token1, uint128 collectAmount0, uint128 collectAmount1)
```

*GitHub* : [892-892](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L892-L892)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
Variable V3Oracle._getFeeGrowthInside(IUniswapV3Pool,int24,int24,int24,uint256,uint256).upperFeeGrowthOutside0X128 (L#481) is too similar to V3Oracle._getFeeGrowthInside(IUniswapV3Pool,int24,int24,int24,uint256,uint256).upperFeeGrowthOutside1X128 (L#481)

/// @audit ************** Possible Issue Line(s) **************
	L#481,  

/// @audit ****************** Affected Code *******************
 481:         (,, uint256 upperFeeGrowthOutside0X128, uint256 upperFeeGrowthOutside1X128,,,,) = pool.ticks(tickUpper);
```

*GitHub* : [481-481](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L481-L481)

```solidity
File: src/automators/Automator.sol

/// @audit ******************* Issue Detail *******************
Variable Automator._decreaseFullLiquidityAndCollect(uint256,uint128,uint256,uint256,uint256).amountRemoveMin0 (L#196) is too similar to Automator._decreaseFullLiquidityAndCollect(uint256,uint128,uint256,uint256,uint256).amountRemoveMin1 (L#197)

/// @audit ************** Possible Issue Line(s) **************
	L#197,  

/// @audit ****************** Affected Code *******************
 196:         uint256 amountRemoveMin0,
 197:         uint256 amountRemoveMin1,
```

*GitHub* : [196-196](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L196-L196)

```solidity
File: lib/v3-core/contracts/interfaces/callback/IUniswapV3SwapCallback.sol

/// @audit ******************* Issue Detail *******************
Variable IUniswapV3SwapCallback.uniswapV3SwapCallback(int256,int256,bytes).amount0Delta (L#17) is too similar to Swapper.uniswapV3SwapCallback(int256,int256,bytes).amount1Delta (L#156)

/// @audit ****************** Affected Code *******************
  17:         int256 amount0Delta,
```

*GitHub* : [17-17](https://github.com/code-423n4/2024-03-revert-lend/lib/v3-core/contracts/interfaces/callback/IUniswapV3SwapCallback.sol#L17-L17)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Variable V3Vault.MAX_LIQUIDATION_PENALTY_X32 (L#39) is too similar to V3Vault.MIN_LIQUIDATION_PENALTY_X32 (L#38)

/// @audit ************** Possible Issue Line(s) **************
	L#38,  

/// @audit ****************** Affected Code *******************
  38:     uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%
  39:     uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%
```

*GitHub* : [39-39](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L39-L39)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
Variable V3Oracle._getUncollectedFees(V3Oracle.PositionState,int24).feeGrowthInside0LastX128 (L#450) is too similar to V3Oracle._getUncollectedFees(V3Oracle.PositionState,int24).feeGrowthInside1LastX128 (L#450)

/// @audit ************** Possible Issue Line(s) **************
	L#450,  

/// @audit ****************** Affected Code *******************
 450:         (uint256 feeGrowthInside0LastX128, uint256 feeGrowthInside1LastX128) = _getFeeGrowthInside(
```

*GitHub* : [450-450](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L450-L450)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Variable V3Utils._swapAndPrepareAmounts(V3Utils.SwapAndMintParams,bool).amountOutDelta0 (L#806) is too similar to V3Utils._swapAndPrepareAmounts(V3Utils.SwapAndMintParams,bool).amountOutDelta1 (L#811)

/// @audit ************** Possible Issue Line(s) **************
	L#811,  

/// @audit ****************** Affected Code *******************
 806:             (uint256 amountInDelta0, uint256 amountOutDelta0) = _routerSwap(
 811:             (uint256 amountInDelta1, uint256 amountOutDelta1) = _routerSwap(
```

*GitHub* : [806-806](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L806-L806)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
Variable V3Oracle._initializeState(uint256).tokensOwed0 (L#407) is too similar to V3Oracle._initializeState(uint256).tokensOwed1 (L#408)

/// @audit ************** Possible Issue Line(s) **************
	L#408,  

/// @audit ****************** Affected Code *******************
 407:             uint128 tokensOwed0,
 408:             uint128 tokensOwed1
```

*GitHub* : [407-407](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L407-L407)

```solidity
File: src/transformers/LeverageTransformer.sol

/// @audit ******************* Issue Detail *******************
Variable LeverageTransformer.leverageDown(LeverageTransformer.LeverageDownParams).decreaseLiquidityParams (L#130-133) is too similar to LeverageTransformer.leverageUp(LeverageTransformer.LeverageUpParams).increaseLiquidityParams (L#80-83)

/// @audit ************** Possible Issue Line(s) **************
	L#80-83,  

/// @audit ****************** Affected Code *******************
  80:         INonfungiblePositionManager.IncreaseLiquidityParams memory increaseLiquidityParams = INonfungiblePositionManager
  81:             .IncreaseLiquidityParams(
  82:             params.tokenId, amount0, amount1, params.amountAddMin0, params.amountAddMin1, params.deadline
  83:         );
 130:         INonfungiblePositionManager.DecreaseLiquidityParams memory decreaseLiquidityParams = INonfungiblePositionManager
 131:             .DecreaseLiquidityParams(
 132:             params.tokenId, params.liquidity, params.amountRemoveMin0, params.amountRemoveMin1, params.deadline
 133:         );
```

*GitHub* : [130-133](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L130-L133)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
Variable V3Oracle._getFeeGrowthInside(IUniswapV3Pool,int24,int24,int24,uint256,uint256).feeGrowthInside0X128 (L#479) is too similar to V3Oracle._getFeeGrowthInside(IUniswapV3Pool,int24,int24,int24,uint256,uint256).feeGrowthInside1X128 (L#479)

/// @audit ************** Possible Issue Line(s) **************
	L#479,  

/// @audit ****************** Affected Code *******************
 479:     ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {
```

*GitHub* : [479-479](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L479-L479)

```solidity
File: src/utils/Swapper.sol

/// @audit ******************* Issue Detail *******************
Variable Swapper.uniswapV3SwapCallback(int256,int256,bytes).amount0Delta (L#156) is too similar to Swapper._poolSwap(Swapper.PoolSwapParams).amount1Delta (L#134)

/// @audit ************** Possible Issue Line(s) **************
	L#134,  

/// @audit ****************** Affected Code *******************
 134:             (int256 amount0Delta, int256 amount1Delta) = params.pool.swap(
 156:     function uniswapV3SwapCallback(int256 amount0Delta, int256 amount1Delta, bytes calldata data) external override {
```

*GitHub* : [156-156](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L156-L156)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
Variable V3Oracle._getFeeGrowthInside(IUniswapV3Pool,int24,int24,int24,uint256,uint256).lowerFeeGrowthOutside0X128 (L#480) is too similar to V3Oracle._getFeeGrowthInside(IUniswapV3Pool,int24,int24,int24,uint256,uint256).lowerFeeGrowthOutside1X128 (L#480)

/// @audit ************** Possible Issue Line(s) **************
	L#480,  

/// @audit ****************** Affected Code *******************
 480:         (,, uint256 lowerFeeGrowthOutside0X128, uint256 lowerFeeGrowthOutside1X128,,,,) = pool.ticks(tickLower);
```

*GitHub* : [480-480](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L480-L480)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Variable V3Utils._prepareAdd(IERC20,IERC20,IERC20,uint256,uint256,uint256).amountAdded0 (L#661) is too similar to V3Utils._prepareAdd(IERC20,IERC20,IERC20,uint256,uint256,uint256).amountAdded1 (L#662)

/// @audit ************** Possible Issue Line(s) **************
	L#662,  

/// @audit ****************** Affected Code *******************
 661:         uint256 amountAdded0;
 662:         uint256 amountAdded1;
```

*GitHub* : [661-661](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L661-L661)

```solidity
File: src/transformers/V3Utils.sol

/// @audit ******************* Issue Detail *******************
Variable V3Utils._collectFees(uint256,IERC20,IERC20,uint128,uint128).balanceAfter0 (L#901) is too similar to V3Utils._collectFees(uint256,IERC20,IERC20,uint128,uint128).balanceAfter1 (L#902)

/// @audit ************** Possible Issue Line(s) **************
	L#902,  

/// @audit ****************** Affected Code *******************
 901:         uint256 balanceAfter0 = token0.balanceOf(address(this));
 902:         uint256 balanceAfter1 = token1.balanceOf(address(this));
```

*GitHub* : [901-901](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L901-L901)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
Variable V3Oracle._initializeState(uint256).feeGrowthInside0LastX128 (L#405) is too similar to V3Oracle._getUncollectedFees(V3Oracle.PositionState,int24).feeGrowthInside1LastX128 (L#450)

/// @audit ************** Possible Issue Line(s) **************
	L#450,  

/// @audit ****************** Affected Code *******************
 405:             uint256 feeGrowthInside0LastX128,
 450:         (uint256 feeGrowthInside0LastX128, uint256 feeGrowthInside1LastX128) = _getFeeGrowthInside(
```

*GitHub* : [405-405](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L405-L405)

```solidity
File: src/V3Oracle.sol

/// @audit ******************* Issue Detail *******************
Variable V3Oracle._getFeeGrowthInside(IUniswapV3Pool,int24,int24,int24,uint256,uint256).feeGrowthGlobal0X128 (L#477) is too similar to V3Oracle._getFeeGrowthInside(IUniswapV3Pool,int24,int24,int24,uint256,uint256).feeGrowthGlobal1X128 (L#478)

/// @audit ************** Possible Issue Line(s) **************
	L#478,  

/// @audit ****************** Affected Code *******************
 477:         uint256 feeGrowthGlobal0X128,
 478:         uint256 feeGrowthGlobal1X128
```

*GitHub* : [477-477](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L477-L477)

```solidity
File: src/V3Vault.sol

/// @audit ******************* Issue Detail *******************
Variable V3Vault.dailyDebtIncreaseLimitLastReset (L#145) is too similar to V3Vault.dailyLendIncreaseLimitLastReset (L#140)

/// @audit ************** Possible Issue Line(s) **************
	L#140,  

/// @audit ****************** Affected Code *******************
 140:     uint256 public dailyLendIncreaseLimitLastReset = 0;
 145:     uint256 public dailyDebtIncreaseLimitLastReset = 0;
```

*GitHub* : [145-145](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L145-L145)

### [N-07]<a name="n-07"></a> Critical Changes Should Use Two-step Procedure

The critical procedures should be two step process.

See similar findings in previous Code4rena contests for reference: <https://code4rena.com/reports/2022-06-illuminate/#2-critical-changes-should-use-two-step-procedure>

**Recommended Mitigation Steps**

Lack of two-step procedure for critical operations leaves them error-prone. Consider adding two step procedure on the critical functions.

*There are 2 instance(s) of this issue:*

```solidity
File: src/V3Oracle.sol

265:     function setEmergencyAdmin(address admin) external onlyOwner {

```



*GitHub* : [265](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L265)

```solidity
File: src/V3Vault.sol

870:     function setEmergencyAdmin(address admin) external onlyOwner {

```


*GitHub* : [870](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L870)

### [N-08]<a name="n-08"></a> Events that mark critical parameter changes should contain both the old and the new value

This should especially be done if the new value is not required to be different from the old value

*There are 17 instance(s) of this issue:*

```solidity
File: src/InterestRateModel.sol

82:     function setValues(
            uint256 baseRatePerYearX96,
            uint256 multiplierPerYearX96,
            uint256 jumpMultiplierPerYearX96,
            uint256 _kinkX96
        ) public onlyOwner {
            if (
                baseRatePerYearX96 > MAX_BASE_RATE_X96 || multiplierPerYearX96 > MAX_MULTIPLIER_X96
                    || jumpMultiplierPerYearX96 > MAX_MULTIPLIER_X96
            ) {
                revert InvalidConfig();
            }
    
            baseRatePerSecondX96 = baseRatePerYearX96 / YEAR_SECS;
            multiplierPerSecondX96 = multiplierPerYearX96 / YEAR_SECS;
            jumpMultiplierPerSecondX96 = jumpMultiplierPerYearX96 / YEAR_SECS;
            kinkX96 = _kinkX96;
    
            emit SetValues(baseRatePerYearX96, multiplierPerYearX96, jumpMultiplierPerYearX96, _kinkX96);

```



*GitHub* : [82](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L82-L100)

```solidity
File: src/V3Oracle.sol

185:     function setMaxPoolPriceDifference(uint16 _maxPoolPriceDifference) external onlyOwner {
             if (_maxPoolPriceDifference < MIN_PRICE_DIFFERENCE) {
                 revert InvalidConfig();
             }
             maxPoolPriceDifference = _maxPoolPriceDifference;
             emit SetMaxPoolPriceDifference(_maxPoolPriceDifference);

201:     function setTokenConfig(
             address token,
             AggregatorV3Interface feed,
             uint32 maxFeedAge,
             IUniswapV3Pool pool,
             uint32 twapSeconds,
             Mode mode,
             uint16 maxDifference
         ) external onlyOwner {
             // can not be unset
             if (mode == Mode.NOT_SET) {
                 revert InvalidConfig();
             }
     
             uint8 feedDecimals = feed.decimals();
             uint8 tokenDecimals = IERC20Metadata(token).decimals();
     
             TokenConfig memory config;
     
             if (token != referenceToken) {
                 if (maxDifference < MIN_PRICE_DIFFERENCE) {
                     revert InvalidConfig();
                 }
     
                 address token0 = pool.token0();
                 address token1 = pool.token1();
                 if (!(token0 == token && token1 == referenceToken || token0 == referenceToken && token1 == token)) {
                     revert InvalidPool();
                 }
                 bool isToken0 = token0 == token;
                 config = TokenConfig(
                     feed, maxFeedAge, feedDecimals, tokenDecimals, pool, isToken0, twapSeconds, mode, maxDifference
                 );
             } else {
                 config = TokenConfig(
                     feed, maxFeedAge, feedDecimals, tokenDecimals, IUniswapV3Pool(address(0)), false, 0, Mode.CHAINLINK, 0
                 );
             }
     
             feedConfigs[token] = config;
     
             emit TokenConfigUpdated(token, config);

201:     function setTokenConfig(
             address token,
             AggregatorV3Interface feed,
             uint32 maxFeedAge,
             IUniswapV3Pool pool,
             uint32 twapSeconds,
             Mode mode,
             uint16 maxDifference
         ) external onlyOwner {
             // can not be unset
             if (mode == Mode.NOT_SET) {
                 revert InvalidConfig();
             }
     
             uint8 feedDecimals = feed.decimals();
             uint8 tokenDecimals = IERC20Metadata(token).decimals();
     
             TokenConfig memory config;
     
             if (token != referenceToken) {
                 if (maxDifference < MIN_PRICE_DIFFERENCE) {
                     revert InvalidConfig();
                 }
     
                 address token0 = pool.token0();
                 address token1 = pool.token1();
                 if (!(token0 == token && token1 == referenceToken || token0 == referenceToken && token1 == token)) {
                     revert InvalidPool();
                 }
                 bool isToken0 = token0 == token;
                 config = TokenConfig(
                     feed, maxFeedAge, feedDecimals, tokenDecimals, pool, isToken0, twapSeconds, mode, maxDifference
                 );
             } else {
                 config = TokenConfig(
                     feed, maxFeedAge, feedDecimals, tokenDecimals, IUniswapV3Pool(address(0)), false, 0, Mode.CHAINLINK, 0
                 );
             }
     
             feedConfigs[token] = config;
     
             emit TokenConfigUpdated(token, config);
             emit OracleModeUpdated(token, mode);

249:     function setOracleMode(address token, Mode mode) external {
             if (msg.sender != emergencyAdmin && msg.sender != owner()) {
                 revert Unauthorized();
             }
     
             // can not be unset
             if (mode == Mode.NOT_SET) {
                 revert InvalidConfig();
             }
     
             feedConfigs[token].mode = mode;
             emit OracleModeUpdated(token, mode);

265:     function setEmergencyAdmin(address admin) external onlyOwner {
             emergencyAdmin = admin;
             emit SetEmergencyAdmin(admin);

```



*GitHub* : [185](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L185-L190), [201](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L201-L242), [201](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L201-L243), [249](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L249-L260), [265](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L265-L267)

```solidity
File: src/V3Vault.sol

788:     function setTransformer(address transformer, bool active) external onlyOwner {
             // protects protocol from owner trying to set dangerous transformer
             if (
                 transformer == address(0) || transformer == address(this) || transformer == asset
                     || transformer == address(nonfungiblePositionManager)
             ) {
                 revert InvalidConfig();
             }
     
             transformerAllowList[transformer] = active;
             emit SetTransformer(transformer, active);

807:     function setLimits(
             uint256 _minLoanSize,
             uint256 _globalLendLimit,
             uint256 _globalDebtLimit,
             uint256 _dailyLendIncreaseLimitMin,
             uint256 _dailyDebtIncreaseLimitMin
         ) external {
             if (msg.sender != emergencyAdmin && msg.sender != owner()) {
                 revert Unauthorized();
             }
     
             minLoanSize = _minLoanSize;
             globalLendLimit = _globalLendLimit;
             globalDebtLimit = _globalDebtLimit;
             dailyLendIncreaseLimitMin = _dailyLendIncreaseLimitMin;
             dailyDebtIncreaseLimitMin = _dailyDebtIncreaseLimitMin;
     
             (, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
     
             // force reset daily limits with new values
             _resetDailyLendIncreaseLimit(newLendExchangeRateX96, true);
             _resetDailyDebtIncreaseLimit(newLendExchangeRateX96, true);
     
             emit SetLimits(

837:     function setReserveFactor(uint32 _reserveFactorX32) external onlyOwner {
             reserveFactorX32 = _reserveFactorX32;
             emit SetReserveFactor(_reserveFactorX32);

844:     function setReserveProtectionFactor(uint32 _reserveProtectionFactorX32) external onlyOwner {
             if (_reserveProtectionFactorX32 < MIN_RESERVE_PROTECTION_FACTOR_X32) {
                 revert InvalidConfig();
             }
             reserveProtectionFactorX32 = _reserveProtectionFactorX32;
             emit SetReserveProtectionFactor(_reserveProtectionFactorX32);

856:     function setTokenConfig(address token, uint32 collateralFactorX32, uint32 collateralValueLimitFactorX32)
             external
             onlyOwner
         {
             if (collateralFactorX32 > MAX_COLLATERAL_FACTOR_X32) {
                 revert CollateralFactorExceedsMax();
             }
             tokenConfigs[token].collateralFactorX32 = collateralFactorX32;
             tokenConfigs[token].collateralValueLimitFactorX32 = collateralValueLimitFactorX32;
             emit SetTokenConfig(token, collateralFactorX32, collateralValueLimitFactorX32);

870:     function setEmergencyAdmin(address admin) external onlyOwner {
             emergencyAdmin = admin;
             emit SetEmergencyAdmin(admin);

```



*GitHub* : [788](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L788-L798), [807](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L807-L830), [837](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L837-L839), [844](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L844-L849), [856](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L856-L865), [870](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L870-L872)

```solidity
File: src/automators/Automator.sol

59:     function setWithdrawer(address _withdrawer) public onlyOwner {
            emit WithdrawerChanged(_withdrawer);

69:     function setOperator(address _operator, bool _active) public onlyOwner {
            emit OperatorChanged(_operator, _active);

79:     function setVault(address _vault, bool _active) public onlyOwner {
            emit VaultChanged(_vault, _active);

87:     function setTWAPConfig(uint16 _maxTWAPTickDifference, uint32 _TWAPSeconds) public onlyOwner {
            if (_TWAPSeconds < MIN_TWAP_SECONDS) {
                revert InvalidConfig();
            }
            if (_maxTWAPTickDifference > MAX_TWAP_TICK_DIFFERENCE) {
                revert InvalidConfig();
            }
            emit TWAPConfigChanged(_TWAPSeconds, _maxTWAPTickDifference);

```



*GitHub* : [59](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L59-L60), [69](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L69-L70), [79](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L79-L80), [87](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L87-L94)

```solidity
File: src/transformers/AutoCompound.sol

243:     function setReward(uint64 _totalRewardX64) external onlyOwner {
             require(_totalRewardX64 <= totalRewardX64, ">totalRewardX64");
             totalRewardX64 = _totalRewardX64;
             emit RewardUpdated(msg.sender, _totalRewardX64);

```


*GitHub* : [243](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L243-L246)

### [N-09]<a name="n-09"></a> Function ordering does not follow the Solidity style guide

According to the [Solidity style guide](https://docs.soliditylang.org/en/v0.8.17/style-guide.html#order-of-functions), functions should be laid out in the following order :`constructor()`, `receive()`, `fallback()`, `external`, `public`, `internal`, `private`, but the cases below do not follow this pattern

*There are 5 instance(s) of this issue:*

```solidity
File: src/V3Oracle.sol

1: 
   Current order:
   external getValue
   internal _checkPoolPrice
   internal _requireMaxDifference
   public getPositionBreakdown
   external setMaxPoolPriceDifference
   external setTokenConfig
   external setOracleMode
   external setEmergencyAdmin
   internal _getReferenceTokenPriceX96
   internal _getChainlinkPriceX96
   internal _getTWAPPriceX96
   internal _getReferencePoolPriceX96
   internal _initializeState
   internal _getAmounts
   internal _getUncollectedFees
   internal _getFeeGrowthInside
   internal _getPool
   
   Suggested order:
   external getValue
   external setMaxPoolPriceDifference
   external setTokenConfig
   external setOracleMode
   external setEmergencyAdmin
   public getPositionBreakdown
   internal _checkPoolPrice
   internal _requireMaxDifference
   internal _getReferenceTokenPriceX96
   internal _getChainlinkPriceX96
   internal _getTWAPPriceX96
   internal _getReferencePoolPriceX96
   internal _initializeState
   internal _getAmounts
   internal _getUncollectedFees
   internal _getFeeGrowthInside
   internal _getPool

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L1-L38)

```solidity
File: src/V3Vault.sol

1: 
   Current order:
   external vaultInfo
   external lendInfo
   external loanInfo
   external ownerOf
   external loanCount
   external loanAtIndex
   public decimals
   public totalAssets
   external convertToShares
   external convertToAssets
   external maxDeposit
   external maxMint
   external maxWithdraw
   external maxRedeem
   public previewDeposit
   public previewMint
   public previewWithdraw
   public previewRedeem
   external deposit
   external mint
   external withdraw
   external redeem
   external deposit
   external mint
   external create
   external createWithPermit
   external onERC721Received
   external approveTransform
   external transform
   external borrow
   external decreaseLiquidityAndCollect
   external repay
   external repay
   external liquidate
   external withdrawReserves
   external setTransformer
   external setLimits
   external setReserveFactor
   external setReserveProtectionFactor
   external setTokenConfig
   external setEmergencyAdmin
   internal _deposit
   internal _withdraw
   internal _repay
   internal _getAvailableBalance
   internal _sendPositionValue
   internal _cleanupLoan
   internal _calculateLiquidation
   internal _handleReserveLiquidation
   internal _calculateTokenCollateralFactorX32
   internal _updateGlobalInterest
   internal _calculateGlobalInterest
   internal _requireLoanIsHealthy
   internal _updateAndCheckCollateral
   internal _resetDailyLendIncreaseLimit
   internal _resetDailyDebtIncreaseLimit
   internal _checkLoanIsHealthy
   internal _convertToShares
   internal _convertToAssets
   internal _addTokenToOwner
   internal _removeTokenFromOwner
   
   Suggested order:
   external vaultInfo
   external lendInfo
   external loanInfo
   external ownerOf
   external loanCount
   external loanAtIndex
   external convertToShares
   external convertToAssets
   external maxDeposit
   external maxMint
   external maxWithdraw
   external maxRedeem
   external deposit
   external mint
   external withdraw
   external redeem
   external deposit
   external mint
   external create
   external createWithPermit
   external onERC721Received
   external approveTransform
   external transform
   external borrow
   external decreaseLiquidityAndCollect
   external repay
   external repay
   external liquidate
   external withdrawReserves
   external setTransformer
   external setLimits
   external setReserveFactor
   external setReserveProtectionFactor
   external setTokenConfig
   external setEmergencyAdmin
   public decimals
   public totalAssets
   public previewDeposit
   public previewMint
   public previewWithdraw
   public previewRedeem
   internal _deposit
   internal _withdraw
   internal _repay
   internal _getAvailableBalance
   internal _sendPositionValue
   internal _cleanupLoan
   internal _calculateLiquidation
   internal _handleReserveLiquidation
   internal _calculateTokenCollateralFactorX32
   internal _updateGlobalInterest
   internal _calculateGlobalInterest
   internal _requireLoanIsHealthy
   internal _updateAndCheckCollateral
   internal _resetDailyLendIncreaseLimit
   internal _resetDailyDebtIncreaseLimit
   internal _checkLoanIsHealthy
   internal _convertToShares
   internal _convertToAssets
   internal _addTokenToOwner
   internal _removeTokenFromOwner

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1-L126)

```solidity
File: src/automators/Automator.sol

1: 
   Current order:
   public setWithdrawer
   public setOperator
   public setVault
   public setTWAPConfig
   external withdrawBalances
   external withdrawETH
   internal _validateSwap
   internal _hasMaxTWAPTickDifference
   internal _getTWAPTick
   internal _decreaseFullLiquidityAndCollect
   internal _transferToken
   internal _validateOwner
   
   Suggested order:
   external withdrawBalances
   external withdrawETH
   public setWithdrawer
   public setOperator
   public setVault
   public setTWAPConfig
   internal _validateSwap
   internal _hasMaxTWAPTickDifference
   internal _getTWAPTick
   internal _decreaseFullLiquidityAndCollect
   internal _transferToken
   internal _validateOwner

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L1-L28)

```solidity
File: src/transformers/V3Utils.sol

1: 
   Current order:
   public executeWithPermit
   public execute
   external onERC721Received
   external swap
   external swapAndMint
   external swapAndIncreaseLiquidity
   internal _prepareAddApproved
   internal _prepareAddPermit2
   internal _prepareAdd
   internal _swapAndMint
   internal _swapAndIncrease
   internal _swapAndPrepareAmounts
   internal _returnLeftoverTokens
   internal _transferToken
   internal _decreaseLiquidity
   internal _collectFees
   
   Suggested order:
   external onERC721Received
   external swap
   external swapAndMint
   external swapAndIncreaseLiquidity
   public executeWithPermit
   public execute
   internal _prepareAddApproved
   internal _prepareAddPermit2
   internal _prepareAdd
   internal _swapAndMint
   internal _swapAndIncrease
   internal _swapAndPrepareAmounts
   internal _returnLeftoverTokens
   internal _transferToken
   internal _decreaseLiquidity
   internal _collectFees

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L1-L36)

```solidity
File: src/utils/Swapper.sol

1: 
   Current order:
   internal _routerSwap
   internal _poolSwap
   external uniswapV3SwapCallback
   internal _getPool
   
   Suggested order:
   external uniswapV3SwapCallback
   internal _routerSwap
   internal _poolSwap
   internal _getPool

```


*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L1-L12)

### [N-10]<a name="n-10"></a> Lack of checks in setters

Be it sanity checks (like checks against `0`-values) or initial setting checks: it's best for Setter functions to have them

*There are 6 instance(s) of this issue:*

```solidity
File: src/V3Oracle.sol

265:     function setEmergencyAdmin(address admin) external onlyOwner {
             emergencyAdmin = admin;
             emit SetEmergencyAdmin(admin);

```



*GitHub* : [265](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L265-L267)

```solidity
File: src/V3Vault.sol

837:     function setReserveFactor(uint32 _reserveFactorX32) external onlyOwner {
             reserveFactorX32 = _reserveFactorX32;
             emit SetReserveFactor(_reserveFactorX32);

870:     function setEmergencyAdmin(address admin) external onlyOwner {
             emergencyAdmin = admin;
             emit SetEmergencyAdmin(admin);

```



*GitHub* : [837](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L837-L839), [870](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L870-L872)

```solidity
File: src/automators/Automator.sol

59:     function setWithdrawer(address _withdrawer) public onlyOwner {
            emit WithdrawerChanged(_withdrawer);
            withdrawer = _withdrawer;

69:     function setOperator(address _operator, bool _active) public onlyOwner {
            emit OperatorChanged(_operator, _active);
            operators[_operator] = _active;

79:     function setVault(address _vault, bool _active) public onlyOwner {
            emit VaultChanged(_vault, _active);
            vaults[_vault] = _active;

```


*GitHub* : [59](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L59-L61), [69](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L69-L71), [79](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L79-L81)

### [N-11]<a name="n-11"></a> Incomplete NatSpec: `@return` is missing on actually documented functions

The following functions are missing `@return` NatSpec comments.

*There are 6 instance(s) of this issue:*

```solidity
File: src/transformers/V3Utils.sol

92:     /// @notice Execute instruction with EIP712 permit
        /// @param tokenId Token to process
        /// @param instructions Instructions to execute
        /// @param v Signature values for EIP712 permit
        /// @param r Signature values for EIP712 permit
        /// @param s Signature values for EIP712 permit
        function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)
            public
            returns (uint256 newTokenId)

112:     /// @notice Execute instruction by pulling approved NFT instead of direct safeTransferFrom call from owner
         /// @param tokenId Token to process
         /// @param instructions Instructions to execute
         function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {

354:     /// @notice ERC721 callback function. Called on safeTransferFrom and does manipulation as configured in encoded Instructions parameter.
         /// At the end the NFT (and any newly minted NFT) is returned to sender. The leftover tokens are sent to instructions.recipient.
         function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
             external
             override
             returns (bytes4)

393:     /// @notice Swaps amountIn of tokenIn for tokenOut - returning at least minAmountOut
         /// @param params Swap configuration
         /// If tokenIn is wrapped native token - both the token or the wrapped token can be sent (the sum of both must be equal to amountIn)
         /// Optionally unwraps any wrapped native token and returns native token instead
         function swap(SwapParams calldata params) external payable returns (uint256 amountOut) {

464:     /// @notice Does 1 or 2 swaps from swapSourceToken to token0 and token1 and adds as much as possible liquidity to a newly minted position.
         /// @param params Swap and mint configuration
         /// Newly minted NFT and leftover tokens are returned to recipient
         function swapAndMint(SwapAndMintParams calldata params)
             external
             payable
             returns (uint256 tokenId, uint128 liquidity, uint256 amount0, uint256 amount1)

529:     /// @notice Does 1 or 2 swaps from swapSourceToken to token0 and token1 and adds as much as possible liquidity to any existing position (no need to be position owner).
         /// @param params Swap and increase liquidity configuration
         // Sends any leftover tokens to recipient.
         function swapAndIncreaseLiquidity(SwapAndIncreaseLiquidityParams calldata params)
             external
             payable
             returns (uint128 liquidity, uint256 amount0, uint256 amount1)

```


*GitHub* : [92](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L92-L100), [112](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L112-L115), [354](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L354-L359), [393](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L393-L397), [464](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L464-L470), [529](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L529-L535)

### [N-12]<a name="n-12"></a> Use a `modifier` instead of a `require/if` statement for a special `msg.sender` actor

If a function is supposed to be access-controlled, a `modifier` should be used instead of a `require/if` statement for more readability.

*There are 26 instance(s) of this issue:*

```solidity
File: src/V3Oracle.sol

250:         if (msg.sender != emergencyAdmin && msg.sender != owner()) {

```



*GitHub* : [250](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L250)

```solidity
File: src/V3Vault.sol

419:         if (msg.sender != owner) {

435:         if (msg.sender != address(nonfungiblePositionManager) || from == address(this)) {

484:         if (tokenOwner[tokenId] != msg.sender) {

515:         if (loanOwner != msg.sender && !transformApprovals[loanOwner][tokenId][msg.sender]) {

561:         if (!isTransformMode && tokenOwner[tokenId] != msg.sender && address(this) != msg.sender) {

621:         if (owner != msg.sender) {

814:         if (msg.sender != emergencyAdmin && msg.sender != owner()) {

935:         if (msg.sender != owner) {

```



*GitHub* : [419](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L419), [435](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L435), [484](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L484), [515](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L515), [561](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L561), [621](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L621), [814](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L814), [935](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L935)

```solidity
File: src/automators/AutoExit.sol

101:         if (!operators[msg.sender]) {

220:         if (owner != msg.sender) {

```



*GitHub* : [101](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L101), [220](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L220)

```solidity
File: src/automators/Automator.sol

105:         if (msg.sender != withdrawer) {

124:         if (msg.sender != withdrawer) {

232:         if (vaults[msg.sender]) {

245:         if (owner != msg.sender) {

252:         if (msg.sender != address(weth)) {

```



*GitHub* : [105](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L105), [124](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L124), [232](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L232), [245](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L245), [252](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L252)

```solidity
File: src/transformers/AutoCompound.sol

88:         if (!operators[msg.sender] || !vaults[vault]) {

102:         if (!operators[msg.sender] && !vaults[msg.sender]) {

205:         if (owner != msg.sender) {

228:         if (msg.sender != withdrawer) {

```



*GitHub* : [88](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L88), [102](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L102), [205](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L205), [228](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L228)

```solidity
File: src/transformers/AutoRange.sol

98:         if (!operators[msg.sender] || !vaults[vault]) {

112:         if (!operators[msg.sender] && !vaults[msg.sender]) {

```



*GitHub* : [98](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L98), [112](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L112)

```solidity
File: src/transformers/V3Utils.sol

102:         if (nonfungiblePositionManager.ownerOf(tokenId) != msg.sender) {

362:         if (msg.sender != address(nonfungiblePositionManager)) {

915:         if (msg.sender != address(weth)) {

```



*GitHub* : [102](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L102), [362](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L362), [915](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L915)

```solidity
File: src/utils/Swapper.sol

161:         if (address(_getPool(tokenIn, tokenOut, fee)) != msg.sender) {

```


*GitHub* : [161](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L161)

### [N-13]<a name="n-13"></a> Constant state variables defined more than once

Rather than redefining state variable constant, consider using a library to store all constants as this will prevent data redundancy

*There are 4 instance(s) of this issue:*

```solidity
File: src/InterestRateModel.sol

12:     uint256 private constant Q96 = 2 ** 96;

```



*GitHub* : [12](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L12)

```solidity
File: src/V3Oracle.sol

27:     uint256 private constant Q96 = 2 ** 96;

```



*GitHub* : [27](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L27)

```solidity
File: src/V3Vault.sol

34:     uint256 private constant Q96 = 2 ** 96;

```



*GitHub* : [34](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L34)

```solidity
File: src/automators/Automator.sol

21:     uint256 internal constant Q96 = 2 ** 96;

```


*GitHub* : [21](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L21)

### [N-14]<a name="n-14"></a> Consider using named mappings

Consider moving to solidity version 0.8.18 or later, and using [named mappings](https://ethereum.stackexchange.com/questions/51629/how-to-name-the-arguments-in-mapping/145555#145555) to make it easier to understand the purpose of each mapping

*There are 13 instance(s) of this issue:*

```solidity
File: src/V3Oracle.sol

56:     mapping(address => TokenConfig) public feedConfigs;

```



*GitHub* : [56](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L56)

```solidity
File: src/V3Vault.sol

115:     mapping(address => TokenConfig) public tokenConfigs;

154:     mapping(uint256 => Loan) public loans; // tokenID -> loan mapping

157:     mapping(address => uint256[]) private ownedTokens; // Mapping from owner address to list of owned token IDs

158:     mapping(uint256 => uint256) private ownedTokensIndex; // Mapping from token ID to index of the owner tokens list (for removal without loop)

159:     mapping(uint256 => address) private tokenOwner; // Mapping from token ID to owner

163:     mapping(address => bool) public transformerAllowList; // contracts allowed to transform positions (selected audited contracts e.g. V3Utils)

164:     mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; // owners permissions for other addresses to call transform on owners behalf (e.g. AutoRange contract)

```



*GitHub* : [115](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L115), [154](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L154), [157](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L157), [158](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L158), [159](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L159), [163](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L163), [164](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L164)

```solidity
File: src/automators/AutoExit.sol

60:     mapping(uint256 => PositionConfig) public positionConfigs;

```



*GitHub* : [60](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L60)

```solidity
File: src/automators/Automator.sol

34:     mapping(address => bool) public operators;

35:     mapping(address => bool) public vaults;

```



*GitHub* : [34](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L34), [35](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L35)

```solidity
File: src/transformers/AutoCompound.sol

45:     mapping(uint256 => mapping(address => uint256)) public positionBalances;

```



*GitHub* : [45](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L45)

```solidity
File: src/transformers/AutoRange.sol

50:     mapping(uint256 => PositionConfig) public positionConfigs;

```


*GitHub* : [50](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L50)

### [N-15]<a name="n-15"></a> Adding a `return` statement when the function defines a named return variable, is redundant



*There are 6 instance(s) of this issue:*

```solidity
File: src/V3Oracle.sol

272:     function _getReferenceTokenPriceX96(address token, uint256 cachedChainlinkReferencePriceX96)
             internal
             view
             returns (uint256 priceX96, uint256 chainlinkReferencePriceX96)
         {
             if (token == referenceToken) {
                 return (Q96, chainlinkReferencePriceX96);

```



*GitHub* : [272](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L272-L278)

```solidity
File: src/V3Vault.sol

255:     /// @notice Retrieves owner of a loan
         /// @param tokenId The unique identifier of the loan - which is the corresponding UniV3 Position
         /// @return owner Owner of the loan
         function ownerOf(uint256 tokenId) external view override returns (address owner) {
             return tokenOwner[tokenId];

288:     /// @inheritdoc IERC4626
         function convertToShares(uint256 assets) external view override returns (uint256 shares) {
             (, uint256 lendExchangeRateX96) = _calculateGlobalInterest();
             return _convertToShares(assets, lendExchangeRateX96, Math.Rounding.Down);

294:     /// @inheritdoc IERC4626
         function convertToAssets(uint256 shares) external view override returns (uint256 assets) {
             (, uint256 lendExchangeRateX96) = _calculateGlobalInterest();
             return _convertToAssets(shares, lendExchangeRateX96, Math.Rounding.Down);

492:     /// @notice Method which allows a contract to transform a loan by changing it (and only at the end checking collateral)
         /// @param tokenId The token ID to be processed
         /// @param transformer The address of a whitelisted transformer contract
         /// @param data Encoded transformation params
         /// @return newTokenId Final token ID (may be different than input token ID when the position was replaced by transformation)
         function transform(uint256 tokenId, address transformer, bytes calldata data)
             external
             override
             returns (uint256 newTokenId)
         {
             if (tokenId == 0 || !transformerAllowList[transformer]) {
                 revert TransformNotAllowed();
             }
             if (transformedTokenId > 0) {
                 revert Reentrancy();
             }
             transformedTokenId = tokenId;
     
             (uint256 newDebtExchangeRateX96,) = _updateGlobalInterest();
     
             address loanOwner = tokenOwner[tokenId];
     
             // only the owner of the loan, the vault itself or any approved caller can call this
             if (loanOwner != msg.sender && !transformApprovals[loanOwner][tokenId][msg.sender]) {
                 revert Unauthorized();
             }
     
             // give access to transformer
             nonfungiblePositionManager.approve(transformer, tokenId);
     
             (bool success,) = transformer.call(data);
             if (!success) {
                 revert TransformFailed();
             }
     
             // may have changed in the meantime
             tokenId = transformedTokenId;
     
             // check owner not changed (NEEDED because token could have been moved somewhere else in the meantime)
             address owner = nonfungiblePositionManager.ownerOf(tokenId);
             if (owner != address(this)) {
                 revert Unauthorized();
             }
     
             // remove access for transformer
             nonfungiblePositionManager.approve(address(0), tokenId);
     
             uint256 debt = _convertToAssets(loans[tokenId].debtShares, newDebtExchangeRateX96, Math.Rounding.Up);
             _requireLoanIsHealthy(tokenId, debt);
     
             transformedTokenId = 0;
     
             return tokenId;

```



*GitHub* : [255](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L255-L259), [288](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L288-L291), [294](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L294-L297), [492](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L492-L544)

```solidity
File: src/transformers/V3Utils.sol

92:     /// @notice Execute instruction with EIP712 permit
        /// @param tokenId Token to process
        /// @param instructions Instructions to execute
        /// @param v Signature values for EIP712 permit
        /// @param r Signature values for EIP712 permit
        /// @param s Signature values for EIP712 permit
        function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)
            public
            returns (uint256 newTokenId)
        {
            if (nonfungiblePositionManager.ownerOf(tokenId) != msg.sender) {
                revert Unauthorized();
            }
    
            nonfungiblePositionManager.permit(address(this), tokenId, instructions.deadline, v, r, s);
            return execute(tokenId, instructions);

```


*GitHub* : [92](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L92-L107)

### [N-16]<a name="n-16"></a> `require()` / `revert()` statements should have descriptive reason strings



*There are 1 instance(s) of this issue:*

```solidity
File: src/utils/Swapper.sol

157:         require(amount0Delta > 0 || amount1Delta > 0); // swaps entirely within 0-liquidity regions are not supported

```


*GitHub* : [157](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L157)

### [N-17]<a name="n-17"></a> Take advantage of Custom Error's return value property

An important feature of Custom Error is that values such as address, tokenID, msg.value can be written inside the () sign, this kind of approach provides a serious advantage in debugging and examining the revert details of dapps such as tenderly.

*There are 102 instance(s) of this issue:*

```solidity
File: src/InterestRateModel.sol

92:             revert InvalidConfig();

```



*GitHub* : [92](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L92)

```solidity
File: src/V3Oracle.sol

148:             revert PriceDifferenceExceeded();

187:             revert InvalidConfig();

212:             revert InvalidConfig();

222:                 revert InvalidConfig();

228:                 revert InvalidPool();

251:             revert Unauthorized();

256:             revert InvalidConfig();

284:             revert NotConfigured();

339:             revert ChainlinkPriceError();

```



*GitHub* : [148](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L148), [187](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L187), [212](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L212), [222](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L222), [228](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L228), [251](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L251), [256](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L256), [284](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L284), [339](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L339)

```solidity
File: src/V3Vault.sol

420:             revert Unauthorized();

436:             revert WrongContract();

485:             revert Unauthorized();

503:             revert TransformNotAllowed();

506:             revert Reentrancy();

516:             revert Unauthorized();

524:             revert TransformFailed();

533:             revert Unauthorized();

562:             revert Unauthorized();

572:             revert GlobalDebtLimit();

575:             revert DailyDebtIncreaseLimit();

587:             revert MinLoanSize();

616:             revert TransformNotAllowed();

622:             revert Unauthorized();

688:             revert TransformNotAllowed();

697:             revert DebtChanged();

705:             revert NotLiquidatable();

738:             revert SlippageError();

775:             revert InsufficientLiquidity();

794:             revert InvalidConfig();

815:             revert Unauthorized();

846:             revert InvalidConfig();

861:             revert CollateralFactorExceedsMax();

907:             revert GlobalLendLimit();

911:             revert DailyLendIncreaseLimit();

941:             revert InsufficientLiquidity();

974:             revert RepayExceedsDebt();

1009:                 revert MinLoanSize();

1200:             revert CollateralFail();

1232:                     revert CollateralValueLimit();

1240:                     revert CollateralValueLimit();

```



*GitHub* : [420](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L420), [436](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L436), [485](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L485), [503](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L503), [506](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L506), [516](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L516), [524](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L524), [533](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L533), [562](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L562), [572](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L572), [575](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L575), [587](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L587), [616](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L616), [622](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L622), [688](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L688), [697](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L697), [705](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L705), [738](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L738), [775](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L775), [794](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L794), [815](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L815), [846](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L846), [861](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L861), [907](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L907), [911](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L911), [941](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L941), [974](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L974), [1009](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1009), [1200](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1200), [1232](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1232), [1240](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1240)

```solidity
File: src/automators/AutoExit.sol

102:             revert Unauthorized();

109:             revert NotConfigured();

116:             revert ExceedsMaxReward();

125:             revert NoLiquidity();

128:             revert LiquidityChanged();

136:             revert NotReady();

150:                 revert MissingSwapData();

221:             revert Unauthorized();

226:                 revert InvalidConfig();

```



*GitHub* : [102](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L102), [109](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L109), [116](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L116), [125](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L125), [128](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L128), [136](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L136), [150](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L150), [221](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L221), [226](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L226)

```solidity
File: src/automators/Automator.sol

89:             revert InvalidConfig();

92:             revert InvalidConfig();

106:             revert Unauthorized();

125:             revert Unauthorized();

132:                 revert EtherSendFailed();

152:             revert TWAPCheckFailed();

223:                 revert EtherSendFailed();

233:             revert Unauthorized();

238:                 revert Unauthorized();

246:             revert Unauthorized();

253:             revert NotWETH();

```



*GitHub* : [89](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L89), [92](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L92), [106](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L106), [125](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L125), [132](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L132), [152](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L152), [223](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L223), [233](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L233), [238](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L238), [246](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L246), [253](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L253)

```solidity
File: src/transformers/AutoCompound.sol

89:             revert Unauthorized();

103:             revert Unauthorized();

206:             revert Unauthorized();

229:             revert Unauthorized();

```



*GitHub* : [89](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L89), [103](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L103), [206](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L206), [229](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L229)

```solidity
File: src/transformers/AutoRange.sol

99:             revert Unauthorized();

113:             revert Unauthorized();

119:             revert NotConfigured();

126:             revert ExceedsMaxReward();

134:             revert LiquidityChanged();

150:             revert SwapAmountTooLarge();

178:                 revert SameRange();

270:             revert NotReady();

281:             revert InvalidConfig();

310:                 revert NotSupportedFeeTier();

```



*GitHub* : [99](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L99), [113](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L113), [119](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L119), [126](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L126), [134](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L134), [150](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L150), [178](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L178), [270](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L270), [281](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L281), [310](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L310)

```solidity
File: src/transformers/V3Utils.sol

103:             revert Unauthorized();

143:             revert AmountError();

350:             revert NotSupportedWhatToDo();

363:             revert WrongContract();

368:             revert SelfSend();

399:             revert SameToken();

473:             revert SameToken();

636:                 revert TransferError(); // reverts for fee-on-transfer tokens

641:                 revert TransferError(); // reverts for fee-on-transfer tokens

646:                 revert TransferError(); // reverts for fee-on-transfer tokens

672:                     revert TooMuchEtherSent();

677:                     revert TooMuchEtherSent();

682:                     revert TooMuchEtherSent();

685:                 revert NoEtherToken();

785:                 revert AmountError();

796:                 revert AmountError();

869:                 revert EtherSendFailed();

906:             revert CollectError();

909:             revert CollectError();

916:             revert NotWETH();

```



*GitHub* : [103](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L103), [143](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L143), [350](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L350), [363](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L363), [368](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L368), [399](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L399), [473](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L473), [636](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L636), [641](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L641), [646](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L646), [672](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L672), [677](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L677), [682](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L682), [685](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L685), [785](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L785), [796](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L796), [869](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L869), [906](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L906), [909](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L909), [916](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L916)

```solidity
File: src/utils/FlashloanLiquidator.sol

44:             revert NotLiquidatable();

103:                 revert NotEnoughReward();

```



*GitHub* : [44](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L44), [103](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L103)

```solidity
File: src/utils/Swapper.sol

91:                     revert SwapFailed();

101:                 revert WrongContract();

112:                 revert SlippageError();

150:                 revert SlippageError();

162:             revert Unauthorized();

```


*GitHub* : [91](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L91), [101](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L101), [112](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L112), [150](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L150), [162](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L162)

### [N-18]<a name="n-18"></a> Contract does not follow the Solidity style guide's suggested layout ordering

The [style guide](https://docs.soliditylang.org/en/v0.8.16/style-guide.html#order-of-layout) says that, within a contract, the ordering should be:

1) Type declarations
2) State variables
3) Events
4) Modifiers
5) Functions

However, the contract(s) below do not follow this ordering

*There are 11 instance(s) of this issue:*

```solidity
File: src/InterestRateModel.sol

1: 
   Current order:
   VariableDeclaration.Q96
   VariableDeclaration.YEAR_SECS
   VariableDeclaration.MAX_BASE_RATE_X96
   VariableDeclaration.MAX_MULTIPLIER_X96
   EventDefinition.SetValues
   VariableDeclaration.multiplierPerSecondX96
   VariableDeclaration.baseRatePerSecondX96
   VariableDeclaration.jumpMultiplierPerSecondX96
   VariableDeclaration.kinkX96
   FunctionDefinition.constructor
   FunctionDefinition.getUtilizationRateX96
   FunctionDefinition.getRatesPerSecondX96
   FunctionDefinition.setValues
   
   Suggested order:
   VariableDeclaration.Q96
   VariableDeclaration.YEAR_SECS
   VariableDeclaration.MAX_BASE_RATE_X96
   VariableDeclaration.MAX_MULTIPLIER_X96
   VariableDeclaration.multiplierPerSecondX96
   VariableDeclaration.baseRatePerSecondX96
   VariableDeclaration.jumpMultiplierPerSecondX96
   VariableDeclaration.kinkX96
   EventDefinition.SetValues
   FunctionDefinition.constructor
   FunctionDefinition.getUtilizationRateX96
   FunctionDefinition.getRatesPerSecondX96
   FunctionDefinition.setValues

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L1-L30)

```solidity
File: src/V3Oracle.sol

1: 
   Current order:
   VariableDeclaration.MIN_PRICE_DIFFERENCE
   VariableDeclaration.Q96
   VariableDeclaration.Q128
   EventDefinition.TokenConfigUpdated
   EventDefinition.OracleModeUpdated
   EventDefinition.SetMaxPoolPriceDifference
   EventDefinition.SetEmergencyAdmin
   EnumDefinition.Mode
   StructDefinition.TokenConfig
   VariableDeclaration.feedConfigs
   VariableDeclaration.factory
   VariableDeclaration.nonfungiblePositionManager
   VariableDeclaration.referenceToken
   VariableDeclaration.referenceTokenDecimals
   VariableDeclaration.maxPoolPriceDifference
   VariableDeclaration.chainlinkReferenceToken
   VariableDeclaration.emergencyAdmin
   FunctionDefinition.constructor
   FunctionDefinition.getValue
   FunctionDefinition._checkPoolPrice
   FunctionDefinition._requireMaxDifference
   FunctionDefinition.getPositionBreakdown
   FunctionDefinition.setMaxPoolPriceDifference
   FunctionDefinition.setTokenConfig
   FunctionDefinition.setOracleMode
   FunctionDefinition.setEmergencyAdmin
   FunctionDefinition._getReferenceTokenPriceX96
   FunctionDefinition._getChainlinkPriceX96
   FunctionDefinition._getTWAPPriceX96
   FunctionDefinition._getReferencePoolPriceX96
   StructDefinition.PositionState
   FunctionDefinition._initializeState
   FunctionDefinition._getAmounts
   FunctionDefinition._getUncollectedFees
   FunctionDefinition._getFeeGrowthInside
   FunctionDefinition._getPool
   
   Suggested order:
   VariableDeclaration.MIN_PRICE_DIFFERENCE
   VariableDeclaration.Q96
   VariableDeclaration.Q128
   VariableDeclaration.feedConfigs
   VariableDeclaration.factory
   VariableDeclaration.nonfungiblePositionManager
   VariableDeclaration.referenceToken
   VariableDeclaration.referenceTokenDecimals
   VariableDeclaration.maxPoolPriceDifference
   VariableDeclaration.chainlinkReferenceToken
   VariableDeclaration.emergencyAdmin
   EnumDefinition.Mode
   StructDefinition.TokenConfig
   StructDefinition.PositionState
   EventDefinition.TokenConfigUpdated
   EventDefinition.OracleModeUpdated
   EventDefinition.SetMaxPoolPriceDifference
   EventDefinition.SetEmergencyAdmin
   FunctionDefinition.constructor
   FunctionDefinition.getValue
   FunctionDefinition._checkPoolPrice
   FunctionDefinition._requireMaxDifference
   FunctionDefinition.getPositionBreakdown
   FunctionDefinition.setMaxPoolPriceDifference
   FunctionDefinition.setTokenConfig
   FunctionDefinition.setOracleMode
   FunctionDefinition.setEmergencyAdmin
   FunctionDefinition._getReferenceTokenPriceX96
   FunctionDefinition._getChainlinkPriceX96
   FunctionDefinition._getTWAPPriceX96
   FunctionDefinition._getReferencePoolPriceX96
   FunctionDefinition._initializeState
   FunctionDefinition._getAmounts
   FunctionDefinition._getUncollectedFees
   FunctionDefinition._getFeeGrowthInside
   FunctionDefinition._getPool

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L1-L76)

```solidity
File: src/V3Vault.sol

1: 
   Current order:
   UsingForDirective.Math
   VariableDeclaration.Q32
   VariableDeclaration.Q96
   VariableDeclaration.MAX_COLLATERAL_FACTOR_X32
   VariableDeclaration.MIN_LIQUIDATION_PENALTY_X32
   VariableDeclaration.MAX_LIQUIDATION_PENALTY_X32
   VariableDeclaration.MIN_RESERVE_PROTECTION_FACTOR_X32
   VariableDeclaration.MAX_DAILY_LEND_INCREASE_X32
   VariableDeclaration.MAX_DAILY_DEBT_INCREASE_X32
   VariableDeclaration.nonfungiblePositionManager
   VariableDeclaration.factory
   VariableDeclaration.interestRateModel
   VariableDeclaration.oracle
   VariableDeclaration.permit2
   VariableDeclaration.asset
   VariableDeclaration.assetDecimals
   EventDefinition.ApprovedTransform
   EventDefinition.Add
   EventDefinition.Remove
   EventDefinition.ExchangeRateUpdate
   EventDefinition.WithdrawCollateral
   EventDefinition.Borrow
   EventDefinition.Repay
   EventDefinition.Liquidate
   EventDefinition.WithdrawReserves
   EventDefinition.SetTransformer
   EventDefinition.SetLimits
   EventDefinition.SetReserveFactor
   EventDefinition.SetReserveProtectionFactor
   EventDefinition.SetTokenConfig
   EventDefinition.SetEmergencyAdmin
   StructDefinition.TokenConfig
   VariableDeclaration.tokenConfigs
   VariableDeclaration.reserveFactorX32
   VariableDeclaration.reserveProtectionFactorX32
   VariableDeclaration.debtSharesTotal
   VariableDeclaration.lastExchangeRateUpdate
   VariableDeclaration.lastDebtExchangeRateX96
   VariableDeclaration.lastLendExchangeRateX96
   VariableDeclaration.globalDebtLimit
   VariableDeclaration.globalLendLimit
   VariableDeclaration.minLoanSize
   VariableDeclaration.dailyLendIncreaseLimitMin
   VariableDeclaration.dailyLendIncreaseLimitLeft
   VariableDeclaration.dailyLendIncreaseLimitLastReset
   VariableDeclaration.dailyDebtIncreaseLimitMin
   VariableDeclaration.dailyDebtIncreaseLimitLeft
   VariableDeclaration.dailyDebtIncreaseLimitLastReset
   StructDefinition.Loan
   VariableDeclaration.loans
   VariableDeclaration.ownedTokens
   VariableDeclaration.ownedTokensIndex
   VariableDeclaration.tokenOwner
   VariableDeclaration.transformedTokenId
   VariableDeclaration.transformerAllowList
   VariableDeclaration.transformApprovals
   VariableDeclaration.emergencyAdmin
   FunctionDefinition.constructor
   FunctionDefinition.vaultInfo
   FunctionDefinition.lendInfo
   FunctionDefinition.loanInfo
   FunctionDefinition.ownerOf
   FunctionDefinition.loanCount
   FunctionDefinition.loanAtIndex
   FunctionDefinition.decimals
   FunctionDefinition.totalAssets
   FunctionDefinition.convertToShares
   FunctionDefinition.convertToAssets
   FunctionDefinition.maxDeposit
   FunctionDefinition.maxMint
   FunctionDefinition.maxWithdraw
   FunctionDefinition.maxRedeem
   FunctionDefinition.previewDeposit
   FunctionDefinition.previewMint
   FunctionDefinition.previewWithdraw
   FunctionDefinition.previewRedeem
   FunctionDefinition.deposit
   FunctionDefinition.mint
   FunctionDefinition.withdraw
   FunctionDefinition.redeem
   FunctionDefinition.deposit
   FunctionDefinition.mint
   FunctionDefinition.create
   FunctionDefinition.createWithPermit
   FunctionDefinition.onERC721Received
   FunctionDefinition.approveTransform
   FunctionDefinition.transform
   FunctionDefinition.borrow
   FunctionDefinition.decreaseLiquidityAndCollect
   FunctionDefinition.repay
   FunctionDefinition.repay
   StructDefinition.LiquidateState
   FunctionDefinition.liquidate
   FunctionDefinition.withdrawReserves
   FunctionDefinition.setTransformer
   FunctionDefinition.setLimits
   FunctionDefinition.setReserveFactor
   FunctionDefinition.setReserveProtectionFactor
   FunctionDefinition.setTokenConfig
   FunctionDefinition.setEmergencyAdmin
   FunctionDefinition._deposit
   FunctionDefinition._withdraw
   FunctionDefinition._repay
   FunctionDefinition._getAvailableBalance
   FunctionDefinition._sendPositionValue
   FunctionDefinition._cleanupLoan
   FunctionDefinition._calculateLiquidation
   FunctionDefinition._handleReserveLiquidation
   FunctionDefinition._calculateTokenCollateralFactorX32
   FunctionDefinition._updateGlobalInterest
   FunctionDefinition._calculateGlobalInterest
   FunctionDefinition._requireLoanIsHealthy
   FunctionDefinition._updateAndCheckCollateral
   FunctionDefinition._resetDailyLendIncreaseLimit
   FunctionDefinition._resetDailyDebtIncreaseLimit
   FunctionDefinition._checkLoanIsHealthy
   FunctionDefinition._convertToShares
   FunctionDefinition._convertToAssets
   FunctionDefinition._addTokenToOwner
   FunctionDefinition._removeTokenFromOwner
   
   Suggested order:
   UsingForDirective.Math
   VariableDeclaration.Q32
   VariableDeclaration.Q96
   VariableDeclaration.MAX_COLLATERAL_FACTOR_X32
   VariableDeclaration.MIN_LIQUIDATION_PENALTY_X32
   VariableDeclaration.MAX_LIQUIDATION_PENALTY_X32
   VariableDeclaration.MIN_RESERVE_PROTECTION_FACTOR_X32
   VariableDeclaration.MAX_DAILY_LEND_INCREASE_X32
   VariableDeclaration.MAX_DAILY_DEBT_INCREASE_X32
   VariableDeclaration.nonfungiblePositionManager
   VariableDeclaration.factory
   VariableDeclaration.interestRateModel
   VariableDeclaration.oracle
   VariableDeclaration.permit2
   VariableDeclaration.asset
   VariableDeclaration.assetDecimals
   VariableDeclaration.tokenConfigs
   VariableDeclaration.reserveFactorX32
   VariableDeclaration.reserveProtectionFactorX32
   VariableDeclaration.debtSharesTotal
   VariableDeclaration.lastExchangeRateUpdate
   VariableDeclaration.lastDebtExchangeRateX96
   VariableDeclaration.lastLendExchangeRateX96
   VariableDeclaration.globalDebtLimit
   VariableDeclaration.globalLendLimit
   VariableDeclaration.minLoanSize
   VariableDeclaration.dailyLendIncreaseLimitMin
   VariableDeclaration.dailyLendIncreaseLimitLeft
   VariableDeclaration.dailyLendIncreaseLimitLastReset
   VariableDeclaration.dailyDebtIncreaseLimitMin
   VariableDeclaration.dailyDebtIncreaseLimitLeft
   VariableDeclaration.dailyDebtIncreaseLimitLastReset
   VariableDeclaration.loans
   VariableDeclaration.ownedTokens
   VariableDeclaration.ownedTokensIndex
   VariableDeclaration.tokenOwner
   VariableDeclaration.transformedTokenId
   VariableDeclaration.transformerAllowList
   VariableDeclaration.transformApprovals
   VariableDeclaration.emergencyAdmin
   StructDefinition.TokenConfig
   StructDefinition.Loan
   StructDefinition.LiquidateState
   EventDefinition.ApprovedTransform
   EventDefinition.Add
   EventDefinition.Remove
   EventDefinition.ExchangeRateUpdate
   EventDefinition.WithdrawCollateral
   EventDefinition.Borrow
   EventDefinition.Repay
   EventDefinition.Liquidate
   EventDefinition.WithdrawReserves
   EventDefinition.SetTransformer
   EventDefinition.SetLimits
   EventDefinition.SetReserveFactor
   EventDefinition.SetReserveProtectionFactor
   EventDefinition.SetTokenConfig
   EventDefinition.SetEmergencyAdmin
   FunctionDefinition.constructor
   FunctionDefinition.vaultInfo
   FunctionDefinition.lendInfo
   FunctionDefinition.loanInfo
   FunctionDefinition.ownerOf
   FunctionDefinition.loanCount
   FunctionDefinition.loanAtIndex
   FunctionDefinition.decimals
   FunctionDefinition.totalAssets
   FunctionDefinition.convertToShares
   FunctionDefinition.convertToAssets
   FunctionDefinition.maxDeposit
   FunctionDefinition.maxMint
   FunctionDefinition.maxWithdraw
   FunctionDefinition.maxRedeem
   FunctionDefinition.previewDeposit
   FunctionDefinition.previewMint
   FunctionDefinition.previewWithdraw
   FunctionDefinition.previewRedeem
   FunctionDefinition.deposit
   FunctionDefinition.mint
   FunctionDefinition.withdraw
   FunctionDefinition.redeem
   FunctionDefinition.deposit
   FunctionDefinition.mint
   FunctionDefinition.create
   FunctionDefinition.createWithPermit
   FunctionDefinition.onERC721Received
   FunctionDefinition.approveTransform
   FunctionDefinition.transform
   FunctionDefinition.borrow
   FunctionDefinition.decreaseLiquidityAndCollect
   FunctionDefinition.repay
   FunctionDefinition.repay
   FunctionDefinition.liquidate
   FunctionDefinition.withdrawReserves
   FunctionDefinition.setTransformer
   FunctionDefinition.setLimits
   FunctionDefinition.setReserveFactor
   FunctionDefinition.setReserveProtectionFactor
   FunctionDefinition.setTokenConfig
   FunctionDefinition.setEmergencyAdmin
   FunctionDefinition._deposit
   FunctionDefinition._withdraw
   FunctionDefinition._repay
   FunctionDefinition._getAvailableBalance
   FunctionDefinition._sendPositionValue
   FunctionDefinition._cleanupLoan
   FunctionDefinition._calculateLiquidation
   FunctionDefinition._handleReserveLiquidation
   FunctionDefinition._calculateTokenCollateralFactorX32
   FunctionDefinition._updateGlobalInterest
   FunctionDefinition._calculateGlobalInterest
   FunctionDefinition._requireLoanIsHealthy
   FunctionDefinition._updateAndCheckCollateral
   FunctionDefinition._resetDailyLendIncreaseLimit
   FunctionDefinition._resetDailyDebtIncreaseLimit
   FunctionDefinition._checkLoanIsHealthy
   FunctionDefinition._convertToShares
   FunctionDefinition._convertToAssets
   FunctionDefinition._addTokenToOwner
   FunctionDefinition._removeTokenFromOwner

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1-L244)

```solidity
File: src/automators/AutoExit.sol

1: 
   Current order:
   EventDefinition.Executed
   EventDefinition.PositionConfigured
   FunctionDefinition.constructor
   StructDefinition.PositionConfig
   VariableDeclaration.positionConfigs
   StructDefinition.ExecuteParams
   StructDefinition.ExecuteState
   FunctionDefinition.execute
   FunctionDefinition.configToken
   
   Suggested order:
   VariableDeclaration.positionConfigs
   StructDefinition.PositionConfig
   StructDefinition.ExecuteParams
   StructDefinition.ExecuteState
   EventDefinition.Executed
   EventDefinition.PositionConfigured
   FunctionDefinition.constructor
   FunctionDefinition.execute
   FunctionDefinition.configToken

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L1-L22)

```solidity
File: src/automators/Automator.sol

1: 
   Current order:
   VariableDeclaration.Q64
   VariableDeclaration.Q96
   VariableDeclaration.MIN_TWAP_SECONDS
   VariableDeclaration.MAX_TWAP_TICK_DIFFERENCE
   EventDefinition.OperatorChanged
   EventDefinition.VaultChanged
   EventDefinition.WithdrawerChanged
   EventDefinition.TWAPConfigChanged
   VariableDeclaration.operators
   VariableDeclaration.vaults
   VariableDeclaration.withdrawer
   VariableDeclaration.TWAPSeconds
   VariableDeclaration.maxTWAPTickDifference
   FunctionDefinition.constructor
   FunctionDefinition.setWithdrawer
   FunctionDefinition.setOperator
   FunctionDefinition.setVault
   FunctionDefinition.setTWAPConfig
   FunctionDefinition.withdrawBalances
   FunctionDefinition.withdrawETH
   FunctionDefinition._validateSwap
   FunctionDefinition._hasMaxTWAPTickDifference
   FunctionDefinition._getTWAPTick
   FunctionDefinition._decreaseFullLiquidityAndCollect
   FunctionDefinition._transferToken
   FunctionDefinition._validateOwner
   FunctionDefinition.receive
   
   Suggested order:
   VariableDeclaration.Q64
   VariableDeclaration.Q96
   VariableDeclaration.MIN_TWAP_SECONDS
   VariableDeclaration.MAX_TWAP_TICK_DIFFERENCE
   VariableDeclaration.operators
   VariableDeclaration.vaults
   VariableDeclaration.withdrawer
   VariableDeclaration.TWAPSeconds
   VariableDeclaration.maxTWAPTickDifference
   EventDefinition.OperatorChanged
   EventDefinition.VaultChanged
   EventDefinition.WithdrawerChanged
   EventDefinition.TWAPConfigChanged
   FunctionDefinition.constructor
   FunctionDefinition.setWithdrawer
   FunctionDefinition.setOperator
   FunctionDefinition.setVault
   FunctionDefinition.setTWAPConfig
   FunctionDefinition.withdrawBalances
   FunctionDefinition.withdrawETH
   FunctionDefinition._validateSwap
   FunctionDefinition._hasMaxTWAPTickDifference
   FunctionDefinition._getTWAPTick
   FunctionDefinition._decreaseFullLiquidityAndCollect
   FunctionDefinition._transferToken
   FunctionDefinition._validateOwner
   FunctionDefinition.receive

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L1-L58)

```solidity
File: src/transformers/AutoCompound.sol

1: 
   Current order:
   EventDefinition.AutoCompounded
   EventDefinition.RewardUpdated
   EventDefinition.BalanceAdded
   EventDefinition.BalanceRemoved
   EventDefinition.BalanceWithdrawn
   FunctionDefinition.constructor
   VariableDeclaration.positionBalances
   VariableDeclaration.MAX_REWARD_X64
   VariableDeclaration.totalRewardX64
   StructDefinition.ExecuteParams
   StructDefinition.ExecuteState
   FunctionDefinition.executeWithVault
   FunctionDefinition.execute
   FunctionDefinition.withdrawLeftoverBalances
   FunctionDefinition.withdrawBalances
   FunctionDefinition.setReward
   FunctionDefinition._increaseBalance
   FunctionDefinition._setBalance
   FunctionDefinition._withdrawBalanceInternal
   FunctionDefinition._checkApprovals
   
   Suggested order:
   VariableDeclaration.positionBalances
   VariableDeclaration.MAX_REWARD_X64
   VariableDeclaration.totalRewardX64
   StructDefinition.ExecuteParams
   StructDefinition.ExecuteState
   EventDefinition.AutoCompounded
   EventDefinition.RewardUpdated
   EventDefinition.BalanceAdded
   EventDefinition.BalanceRemoved
   EventDefinition.BalanceWithdrawn
   FunctionDefinition.constructor
   FunctionDefinition.executeWithVault
   FunctionDefinition.execute
   FunctionDefinition.withdrawLeftoverBalances
   FunctionDefinition.withdrawBalances
   FunctionDefinition.setReward
   FunctionDefinition._increaseBalance
   FunctionDefinition._setBalance
   FunctionDefinition._withdrawBalanceInternal
   FunctionDefinition._checkApprovals

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L1-L44)

```solidity
File: src/transformers/AutoRange.sol

1: 
   Current order:
   EventDefinition.RangeChanged
   EventDefinition.PositionConfigured
   FunctionDefinition.constructor
   StructDefinition.PositionConfig
   VariableDeclaration.positionConfigs
   StructDefinition.ExecuteParams
   StructDefinition.ExecuteState
   FunctionDefinition.executeWithVault
   FunctionDefinition.execute
   FunctionDefinition.configToken
   FunctionDefinition._getTickSpacing
   
   Suggested order:
   VariableDeclaration.positionConfigs
   StructDefinition.PositionConfig
   StructDefinition.ExecuteParams
   StructDefinition.ExecuteState
   EventDefinition.RangeChanged
   EventDefinition.PositionConfigured
   FunctionDefinition.constructor
   FunctionDefinition.executeWithVault
   FunctionDefinition.execute
   FunctionDefinition.configToken
   FunctionDefinition._getTickSpacing

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L1-L26)

```solidity
File: src/transformers/LeverageTransformer.sol

1: 
   Current order:
   FunctionDefinition.constructor
   StructDefinition.LeverageUpParams
   FunctionDefinition.leverageUp
   StructDefinition.LeverageDownParams
   FunctionDefinition.leverageDown
   
   Suggested order:
   StructDefinition.LeverageUpParams
   StructDefinition.LeverageDownParams
   FunctionDefinition.constructor
   FunctionDefinition.leverageUp
   FunctionDefinition.leverageDown

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L1-L14)

```solidity
File: src/transformers/V3Utils.sol

1: 
   Current order:
   UsingForDirective.SafeCast
   VariableDeclaration.permit2
   EventDefinition.CompoundFees
   EventDefinition.ChangeRange
   EventDefinition.WithdrawAndCollectAndSwap
   EventDefinition.SwapAndMint
   EventDefinition.SwapAndIncreaseLiquidity
   FunctionDefinition.constructor
   EnumDefinition.WhatToDo
   StructDefinition.Instructions
   FunctionDefinition.executeWithPermit
   FunctionDefinition.execute
   FunctionDefinition.onERC721Received
   StructDefinition.SwapParams
   FunctionDefinition.swap
   StructDefinition.SwapAndMintParams
   FunctionDefinition.swapAndMint
   StructDefinition.SwapAndIncreaseLiquidityParams
   FunctionDefinition.swapAndIncreaseLiquidity
   FunctionDefinition._prepareAddApproved
   StructDefinition.PrepareAddPermit2State
   FunctionDefinition._prepareAddPermit2
   FunctionDefinition._prepareAdd
   FunctionDefinition._swapAndMint
   FunctionDefinition._swapAndIncrease
   FunctionDefinition._swapAndPrepareAmounts
   FunctionDefinition._returnLeftoverTokens
   FunctionDefinition._transferToken
   FunctionDefinition._decreaseLiquidity
   FunctionDefinition._collectFees
   FunctionDefinition.receive
   
   Suggested order:
   UsingForDirective.SafeCast
   VariableDeclaration.permit2
   EnumDefinition.WhatToDo
   StructDefinition.Instructions
   StructDefinition.SwapParams
   StructDefinition.SwapAndMintParams
   StructDefinition.SwapAndIncreaseLiquidityParams
   StructDefinition.PrepareAddPermit2State
   EventDefinition.CompoundFees
   EventDefinition.ChangeRange
   EventDefinition.WithdrawAndCollectAndSwap
   EventDefinition.SwapAndMint
   EventDefinition.SwapAndIncreaseLiquidity
   FunctionDefinition.constructor
   FunctionDefinition.executeWithPermit
   FunctionDefinition.execute
   FunctionDefinition.onERC721Received
   FunctionDefinition.swap
   FunctionDefinition.swapAndMint
   FunctionDefinition.swapAndIncreaseLiquidity
   FunctionDefinition._prepareAddApproved
   FunctionDefinition._prepareAddPermit2
   FunctionDefinition._prepareAdd
   FunctionDefinition._swapAndMint
   FunctionDefinition._swapAndIncrease
   FunctionDefinition._swapAndPrepareAmounts
   FunctionDefinition._returnLeftoverTokens
   FunctionDefinition._transferToken
   FunctionDefinition._decreaseLiquidity
   FunctionDefinition._collectFees
   FunctionDefinition.receive

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L1-L66)

```solidity
File: src/utils/FlashloanLiquidator.sol

1: 
   Current order:
   StructDefinition.FlashCallbackData
   FunctionDefinition.constructor
   StructDefinition.LiquidateParams
   FunctionDefinition.liquidate
   FunctionDefinition.uniswapV3FlashCallback
   
   Suggested order:
   StructDefinition.FlashCallbackData
   StructDefinition.LiquidateParams
   FunctionDefinition.constructor
   FunctionDefinition.liquidate
   FunctionDefinition.uniswapV3FlashCallback

```



*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L1-L14)

```solidity
File: src/utils/Swapper.sol

1: 
   Current order:
   EventDefinition.Swap
   VariableDeclaration.weth
   VariableDeclaration.factory
   VariableDeclaration.nonfungiblePositionManager
   VariableDeclaration.zeroxRouter
   VariableDeclaration.universalRouter
   FunctionDefinition.constructor
   StructDefinition.ZeroxRouterData
   StructDefinition.UniversalRouterData
   StructDefinition.RouterSwapParams
   FunctionDefinition._routerSwap
   StructDefinition.PoolSwapParams
   FunctionDefinition._poolSwap
   FunctionDefinition.uniswapV3SwapCallback
   FunctionDefinition._getPool
   
   Suggested order:
   VariableDeclaration.weth
   VariableDeclaration.factory
   VariableDeclaration.nonfungiblePositionManager
   VariableDeclaration.zeroxRouter
   VariableDeclaration.universalRouter
   StructDefinition.ZeroxRouterData
   StructDefinition.UniversalRouterData
   StructDefinition.RouterSwapParams
   StructDefinition.PoolSwapParams
   EventDefinition.Swap
   FunctionDefinition.constructor
   FunctionDefinition._routerSwap
   FunctionDefinition._poolSwap
   FunctionDefinition.uniswapV3SwapCallback
   FunctionDefinition._getPool

```


*GitHub* : [1](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L1-L34)

### [N-19]<a name="n-19"></a> Use Underscores for Number Literals (add an underscore every 3 digits)



*There are 5 instance(s) of this issue:*

```solidity
File: src/InterestRateModel.sol

13:     uint256 public constant YEAR_SECS = 31557600; // taking into account leap years

```



*GitHub* : [13](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L13)

```solidity
File: src/V3Oracle.sol

144:             ? (priceX96 - verifyPriceX96) * 10000 / priceX96

145:             : (verifyPriceX96 - priceX96) * 10000 / verifyPriceX96;

```



*GitHub* : [144](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L144), [145](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L145)

```solidity
File: src/transformers/AutoRange.sol

301:         if (fee == 10000) {

303:         } else if (fee == 3000) {

```


*GitHub* : [301](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L301), [303](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L303)

### [N-20]<a name="n-20"></a> Internal and private variables and functions names should begin with an underscore

According to the Solidity Style Guide, Non-`external` variable and function names should begin with an [underscore](https://docs.soliditylang.org/en/latest/style-guide.html#underscore-prefix-for-non-external-functions-and-variables)

*There are 4 instance(s) of this issue:*

```solidity
File: src/V3Vault.sol

157:     mapping(address => uint256[]) private ownedTokens; // Mapping from owner address to list of owned token IDs

158:     mapping(uint256 => uint256) private ownedTokensIndex; // Mapping from token ID to index of the owner tokens list (for removal without loop)

159:     mapping(uint256 => address) private tokenOwner; // Mapping from token ID to owner

161:     uint256 private transformedTokenId = 0; // transient storage (when available in dencun)

```


*GitHub* : [157](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L157), [158](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L158), [159](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L159), [161](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L161)

### [N-21]<a name="n-21"></a> `public` functions not called by the contract should be declared `external` instead



*There are 2 instance(s) of this issue:*

```solidity
File: src/automators/Automator.sol

79:     function setVault(address _vault, bool _active) public onlyOwner {

```



*GitHub* : [79](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L79)

```solidity
File: src/transformers/V3Utils.sol

98:     function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)

```


*GitHub* : [98](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L98)

### [N-22]<a name="n-22"></a> Variables need not be initialized to zero

The default value for variables is zero, so initializing them to zero is superfluous.

*There are 13 instance(s) of this issue:*

```solidity
File: src/V3Vault.sol

118:     uint32 public reserveFactorX32 = 0;

124:     uint256 public debtSharesTotal = 0;

127:     uint256 public lastExchangeRateUpdate = 0;

131:     uint256 public globalDebtLimit = 0;

132:     uint256 public globalLendLimit = 0;

135:     uint256 public minLoanSize = 0;

138:     uint256 public dailyLendIncreaseLimitMin = 0;

139:     uint256 public dailyLendIncreaseLimitLeft = 0;

140:     uint256 public dailyLendIncreaseLimitLastReset = 0;

143:     uint256 public dailyDebtIncreaseLimitMin = 0;

144:     uint256 public dailyDebtIncreaseLimitLeft = 0;

145:     uint256 public dailyDebtIncreaseLimitLastReset = 0;

161:     uint256 private transformedTokenId = 0; // transient storage (when available in dencun)

```


*GitHub* : [118](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L118), [124](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L124), [127](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L127), [131](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L131), [132](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L132), [135](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L135), [138](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L138), [139](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L139), [140](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L140), [143](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L143), [144](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L144), [145](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L145), [161](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L161)

