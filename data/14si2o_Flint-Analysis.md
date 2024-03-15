# Analysis of Revert Lend
![image](https://github.com/14si2o/C4-Revert/assets/111807030/911890ef-1af6-4ec5-acb1-86921b77b796)

## 1. Description Revert Lend

Revert have been developing analytical tools and dashboards to simplify and facility interaction with AMM protocols since June 2022. It is their stated belief that AMM protocols will play a pivotal role in the financial crypto markets in the coming years and they wish to help retails invests interact with these complex and sometimes obtuse protocols. These tools are mainly focused on Uniswap v3.

Revert Lend is their newest initiative, an ERC4626 lending protocol that takes a unique approach by allowing the Uniswap v3 NFT position to be used as collateral to facilitate the acquisition of ERC20 token loans, while allowing the users to retain control and management of their capital within Uniswap v3 Pools. As a consequence, it becomes possible to unify all the liquidity provided from all accepted tokens into one pool.   

Another rare aspect of the protocol is the variable interest rate, which is completely dependent on the ebb and flow of the market. 

## 2. Approach taken for this contest

### Time spent on this audit: 11 days

**Day 1: 7h35** 
 - Reading the whitepaper and documentation
 - Studying Uniswap V3, ERC4626
 - Researching hacks of similar protocols
 - Creating giant checklist of possible issues

**Day 2-3: 13h37**
 - First pass through the code, adding questions to note.md while I read.
 - Creating hand-drawn functional diagrams of all functions available to normal users in Excalidraw. 

**Day 4-6 : 17h50** 
 - Second Pass through the code

**Day 7-8: 11h06**
  - Go through notes one-by-one answering all questions and adding to preliminary findings 
  - Finalising preliminary findings
  - Trying to test as many as I can in Foundry
  
**Day 9-11: 20h55** 
  - Writing reports & analysis

## 3. Architecture

![image](https://github.com/14si2o/C4-Revert/assets/111807030/dd81cf7a-a47f-488f-9c24-b506bd8ddd31)

In order to properly understand the architecture of the protocol, it is neccessary to understand its history. 

Revert started back in June of 2022 with a mission of building actionable analytics for liquidity providers in AMM protcols, with a focus on Uniswap. To this end they developed the [initiator](https://mirror.xyz/revertfinance.eth/n7HcSKIUcZGVLmduPFFhu5vmKWUU8HKdUNfLR1o9LRE) and over time they added new functionalities and products such as V3Utils, Auto-Compound, Auto-Exist, Leverage-Transformer and Auto-Range. Revert Lend is their newest product which aims to introduce an ERC4626 vault. 

As such, the architure should not be seen as a master drawing of "the Architect", but as many layers of architectural drawings, each becoming more complex and integrating what came before. As ingenious as it may be, the more custom functionality that has to be developed to allow everthing to fit together, the higher the chances of something being overlooked and exploited. 

### Architectural Risks

This becomes apparant when we evaluate how the V3Vault interacts with the automated contracts through `tranform()`. 

For `AutoCompound` and `AutoRange`:
 - user calls `executeWithVault` from the transformer
 - this calls `Ivault(vault).transform()`
 - the vault calls back `execute()` to the transformer

For `AutoExit`,`FlashloanLiquidator`,`LeverageTransformer` and `V3Utils`:
 - user calls `transform()` from the vault.

I could find no explanation anywhere in the documentation for having 2 different patterns. In itself this is not a security risk, but the chance of their being an oversight and a risk today or in future incarnations of the protocol, increases exponentially with each additional pattern.    

Another issue is the multiplication of similar functionalities across the different contracts. When we look at Uniswap `decreaseLiquidity`, we can see that every contract besides `FlashloanLiquidator` can call this on a position. Again, in itself not a security risk, but the effort required to make sure that all instances are correctly configured and there exists no difference that be exploited, increases exponentially with each added similar functionality. 

### Recommandations

1. Streamline and perhaps externalise (ITransform) the access pattern between the vault and transformers so that there is only one correct way in which the communication between the two can happen.

2. Re-factor some of the existing contracts to reduce multiplication of similar functionality.  


## 4. Main contracts and functionality

For each contract we will give a short description, an overview of the most important functions available to users and a custom function diagram to visualise internal and external calls. Furthermore, any findings will be mentioned with the relevant function.

Please refer to below Legend to understand the diagrams.   
![image](https://github.com/14si2o/C4-Revert/assets/111807030/9101d413-dfda-4459-9c59-04aeff6ecdd9)


### **V3Vault.sol**: 
An IERC4626 compliant contract that manages one ERC20 asset for lending and borrowing. It accepts Uniswap v3 positions as collateral where these positions are composed of any 2 tokens which each have been configured to have a collateralFactor > 0. 

#### External view functions:

![image](https://github.com/14si2o/C4-Revert/assets/111807030/26875ba3-fbc8-4c12-a681-e0fe8ed46994)
- **vaultInfo()**
  - This functions retrieves the global information about the vault.
  - It makes use of the following internal functions:
    - _calculateGlobalInterest()
    - _getAvailableBalance()
    - _convertToAssets() x2

![image](https://github.com/14si2o/C4-Revert/assets/111807030/06ebfff5-38d0-45e2-9303-a9d938df63e1)
- **lendInfo()**: 
  - Here the lending information for a specified account is retrieved
  - It makes use of the following internal functions:
    - _calculateGlobalInterest()
    - _convertToAssets() 
    - When we compare `vaultInfo` and `lendInfo`, we can see that the rounding for calculating the lending information is different. Due to this, the total lent from `vaultInfo` will be greater then the sum of `lendInfo` from all accounts. This could be considered a breaking of a fundamental invariant, as detailed in finding `[L-03] Inconsistent Lending rounding in view functions`.

![image](https://github.com/14si2o/C4-Revert/assets/111807030/eaa61c95-8c11-415a-b1e8-bf64ae38bbe2)
- **loanInfo()**: 
  - The tokenId, which is the corresponding Uniswap V3 position, is used as input to retrieve the details of a loan.
  - It makes use of the following internal functions:
    - _calculateGlobalInterest()
    - _convertToAssets() 
    - _checkLoanIsHealthy()
    - _calculateLiquidation()
    - When we look at the NatSpec and the naming of the function, it would seem obvious that you will receive the information for one **specific** loan. The code however, tells a different story. It calculate the debt as the sum of ALL loans taken against a position and calculate the health threshold on this global figure. This will gives users a completely erroneous understanding of their situation. This is further detailed in finding `[NC-01] Incorrect naming and Natspec of loanInfo`.

#### IERC4626 overriden external view functions:
![image](https://github.com/14si2o/C4-Revert/assets/111807030/1614a5c0-4059-4e9b-a454-cc659d43920f)
- **totalAssets()**
  - Note that totalAssets makes use of `balanceOf(address(this))`, which opens an important attack vector of inflation attacks as detailed in finding `H- Inflation attack due to the absence of dead shares and the reliance on balanceOf`. 
- **convertToShares()**
  - It makes use of the following internal functions:
    - _calculateGlobalInterest()
    - _convertToShares()
- **convertToAssets()**
  - It makes use of the following internal functions:
    - _calculateGlobalInterest()
    - _convertToAssets()
- **maxDeposit()**
  - It makes use of the following internal functions:
    - _calculateGlobalInterest()
    - _convertToAssets()
- **maxMint()**
  - It makes use of the following internal functions:
    - _calculateGlobalInterest()
    - _convertToShares()
- **maxWithdraw()**
  - It makes use of the following internal functions:
    - _calculateGlobalInterest()
    - _convertToAssets()
- **maxRedeem()**
  - balanceOf(owner)
- **previewDeposit()**
  - It makes use of the following internal functions:
    - _calculateGlobalInterest()
    - _convertToShares()
- **previewMint()**
  - It makes use of the following internal functions:
    - _calculateGlobalInterest()
    - _convertToAssets()
- **previewWithdraw()**
  - It makes use of the following internal functions:
    - _calculateGlobalInterest()
    - _convertToShares()
- **previewRedeel()**
  - It makes use of the following internal functions:
    - _calculateGlobalInterest()
    - _convertToShares()

#### IERC4626 overriden external functions:
![image](https://github.com/14si2o/C4-Revert/assets/111807030/03baab40-76df-46ea-a634-3a627d072872)

- **deposit(assets, receiver)**
  - It makes use of the following internal functions:
    - _deposit()
- **mint(shares, receiver)**
  - It makes use of the following internal functions:
    - _deposit()
- **deposit(shares, receiver, permitData)**
  - It makes use of the following internal functions:
    - _deposit()
- **mint(shares, receiver, permitData)**
  - It makes use of the following internal functions:
    - _deposit()

![image](https://github.com/14si2o/C4-Revert/assets/111807030/167b7e96-eafe-440c-8a21-1127528a6985)

- **withdraw(assets, receiver, owner)**
  - It makes use of the following internal functions:
    - _withdraw()
- **redeem(shares, receiver, owner)**
  - It makes use of the following internal functions:
    - _withdraw()
  - Note that `withdraw` and `redeem` are the only functions to not have a permit2 version. Even though the use-case is rare, for completeness those version should be added. More information in finding `[NC-03] lacking permit2 functions`


#### External functions:
![image](https://github.com/14si2o/C4-Revert/assets/111807030/73c7339b-a4c5-4f8f-b4bd-a1a80bb74378)

- **create()**
  - The Uniswap V3 NFT position is transferred to the Vault contract and ownership is set to msg.sender or recipient if he is defined through `onERC721Received`.
  - Note that the `onERC721Received` is inconsistent with the EIP721 standard, as detailin finding `[L-06] onERC721Received not compliant with EIP721`.

![image](https://github.com/14si2o/C4-Revert/assets/111807030/7f200279-a749-4c19-a004-9f7ca189890c)

- **createWithPermit()**
  - The permit version of the abovementioned create() function. 
  - Ownership of position is transferred to the Vault contract and set to msg.sender or recipient if he is defined through `onERC721Received` 
- **approveTransform()**
  - A user can approve automated agents (tranformers/automators) which will allow them to call the `transform` function.
    

![image](https://github.com/14si2o/C4-Revert/assets/111807030/908bba99-4441-4b53-8df5-23caf35099da)

- **transform()**
  - This function is the entry point for all the automated tools developed by the Revert protocol. Users approve these tools through `approveTransform`, which allows them to call transform to perform any user actions in an automated fashion.
  - It makes use of the following internal functions:
    - _updateGlobalInterest()
    - _convertToAssets()
    - _requireLoanIsHealthy()  
  - Note that the code comments for "Unauthorized" check are incorrect, as detailed in finding `[NC-04] Incorrect code comments`.

![image](https://github.com/14si2o/C4-Revert/assets/111807030/edac0c07-2163-414b-912d-29af9b11511f)

- **borrow()**
  - A pivotal function in any lending protocol, the borrow functions allow a user to borrow assets with the uniswap position as collateral.
  - It makes use of the following internal functions:
    - _updateGlobalInterest()
    - _resetDailyDebtIncreaseLimit()
    - _convertToShares()
    - _updateAndCheckCollateral()
    - _convertToAssets()

![image](https://github.com/14si2o/C4-Revert/assets/111807030/bf76e440-bb6e-437e-8d1a-2cba049eb7a8)

- **decreaseLiquidityAndCollect**
  - A user can decrease the liquidity of a given position and resultant assets and potential fees.
  - It is of remark that transformers are not allowed to use this function since they can call the methods directly on the nonFungiblePositionManager.    
  - It makes use of the following internal functions:
    - _updateGlobalInterest()
    - _convertToAssets()
    - _requireLoanIsHealthy()


![image](https://github.com/14si2o/C4-Revert/assets/111807030/72cf9024-d55e-4eab-a1a2-60dfbeb44ec0)

- **repay(tokenId, amount, IsShare)**
  - Used to repay borrowed tokens. Can be denominated in assets or shares. 
  - It makes use of the following internal functions:
    - _repay()
- **repay(tokenId, amount, IsShare, permitData)**
  - The permit version of repay. 
  - Used to repay borrowed tokens. Can be denominated in assets or shares. 
  - It makes use of the following internal functions:
    - _repay()

 
![image](https://github.com/14si2o/C4-Revert/assets/111807030/6f9cb2c9-36ee-470c-befa-36486236c620)

- **liquidate()**
  - This function is used to liquidate unhealthy loans. 
  - Transformers cannot call this fucntion directly.
  - It makes use of the following internal functions:
    - _updateGlobalInterest()
    - _convertToAssets()
    - _checkLoanIsHealthy()
    - _calculateLiquidation()
    - _handleReserveLiquidation()
    - _sendPositionValue()
    - _cleanupLoan()
    - Note that the `liquidate` function has a major flaw in that it only transfers fees from the owner to the liquidator and not decreased liquidity. This causes the liquidator to not obtain the liquidity he paid for and the owner receives part of the liquidity he should have lost. More details can be found in finding `H-Liquidation only transfers fees to liquidator, while part or all of the decreased liquidity is transferred back to the defaulting owner`.
    - Also note that the decreaseLiquidity call is performed with **100% slippage tolerance**, which can cause the liquidity returned to be close to zero. As detailed in finding `[L-02] No slippage protection in Vault:liquidate`



### **V3Oracle.sol**: 

This is contract is in V3Vault to calculate the value of positions. It is the main vector of obtaining price data and uses both Chainlink aswell as Uniswap v3 TWAP. Futhermore, it also provides emergency fallback mode. 
![image](https://github.com/14si2o/C4-Revert/assets/111807030/aed44bcb-0d82-42a6-a565-fbbc73d62d35)

**getValue**
- The function obtais value and prices of a Uniswap v3 LP Posiotion in specified token. It uses the configured oracles and verifies price on a second oracle. This the main function used by V3Vault functions to obtain price data.
- It makes use of the following functions:
  - getPositionBreakDown()
  - _getReferenceTokenPriceX96()
  - _checkPoolPrice()
- Note that a minor issue exists in `_requireMaxDifference`, which is called by `_checkPoolPrice`, as detailed in finding `[L-05] Limit set to low in _requireMaxDifference`.

![image](https://github.com/14si2o/C4-Revert/assets/111807030/e9884d2e-b4dd-4c09-b1f1-9775a6683b35)

**getPositionBreakDown**
- it returns a breakdown of a Uniswap v3 position (tokens and fee tier, liquidity, current liquidity amounts, uncollected fees).
- It makes use of the following internal functions:
  - _initializeState()
  - _getAmounts()

### **V3Utils.sol**:

Stateless contract with utility functions for Uniswap V3 positions. 


**executeWithPermit**
- This function calls `execute` with EIP712 permit.
- It makes use of the following functions:
  - execute()
 
![image](https://github.com/14si2o/C4-Revert/assets/111807030/4871cb00-45c0-4ab5-b41a-e11e3b70a511)

**execute**
- This functions executes the provided instructions by pulling approved NFT instead of direct safeTransferFrom.
- It can make use of the following internal functions:
  - _decreaseLiquidity()
  - _collectFees()
  - _swapAndIncrease()
  - _swapAndMint()
  - _routerSwap()
  - _transferToken()

 
![image](https://github.com/14si2o/C4-Revert/assets/111807030/6223c3a3-2142-433a-bfc5-ea71125babdb)

**swap**
- This function swaps amountIn for tokenOut - returning at least minAmountOut.
- It makes use of the following internal functions:
  - _prepareAddPermit2()
  - _prepareAddApproved()
  - _routerSwap()
  - _transferToken()

![image](https://github.com/14si2o/C4-Revert/assets/111807030/69aa6489-6080-4b76-8ff2-04c0055f17bd)
**swapAndMint**
- This function performs 1 or 2 swaps from swapSourceToken to token0 and token1 and adds as much as possible liquidity to a newly minted position.
- It makes use of the following internal functions:
  - _prepareAddPermit2()
  - _prepareAddApproved()
  - _swapAndMint()


![image](https://github.com/14si2o/C4-Revert/assets/111807030/dc09708f-3e18-4fac-ad5a-79c28cf62188)
**swapAndIncreaseLiquidity**
- This function performs 1 or 2 swaps from swapSourceToken to token0 and token1 and adds as much as possible liquidity to any existing position.
- It makes use of the following internal functions:
  - _prepareAddPermit2()
  - _prepareAddApproved()
  - _swapAndincrease()

### **AutoExit.sol**: 

This automator contract allows a v3 position to be automatically removed (limit order) or to be swapped to the opposite token (stop loss order) when it reaches a certain tick. The execution of the optimized swap is delegated to a revert controlled bot (operator) using an externalswap router.


![image](https://github.com/14si2o/C4-Revert/assets/111807030/866138ad-024b-45c8-8e44-3e4e4059fad9)

**execute**
- This can only be from a configured operator account. Furthermore, the swap need to be executed within the maximum price difference allowed from the current pool price. 
- It makes use of the following internal functions:
  - _getPool()
  - _decreaseFullLiquidityAndCollect()
  - _validateSwap()
  - _routerSwap()
  - _transferToken()

### **FlashloanLiquidator.sol**:
- A helper contract which allows atomic liquidation and needed swaps by using Uniswap v3 Flashloan.
![image](https://github.com/14si2o/C4-Revert/assets/111807030/a7d6201d-bade-4347-adb7-bc625c605873)

**liquidate**
- This function liquidates a loan from the V3Vault.
- It makes use of the following functions:
  - flashLoanPool.flash()
  - This causes uniswapV3FlashCallback() to be invoked

### **LeverageTransformer.sol**:
- This contract offers functionality to leverage or deleverage Uniswap v3 positions in one transaction.


![image](https://github.com/14si2o/C4-Revert/assets/111807030/6b5f5bbf-d398-421d-be1d-a4098ed3236f)

**leverageUp**
- The liquidity of a Uniswap v3 position is increased by this function. 
- It can only be called through the `transform` function in `V3Vault.sol`
- It makes use of the following functions:
  - IVault(msg.sender).borrow()
  - _routerSwap()


![image](https://github.com/14si2o/C4-Revert/assets/111807030/2603ea03-54cb-428f-902f-ed828559d375)

**leverageDown**
- The liquidity of a Uniswap v3 position is decreased by this function. 
- It can only be called through the `transform` function in `V3Vault.sol`
- It makes use of the following functions:
  - _routerSwap()
  - IVault(msg.sender).repay()

### **AutoCompound.sol**: 
This contract allows an approved operator of AutoCompound to compound a position. When called from outside the vault, the positions need to be approved, when called inside, the owner needs to approve the position to be transformed by the contract. 

![image](https://github.com/14si2o/C4-Revert/assets/111807030/4b7bc164-fc1a-4161-ae27-5916a4971d73)

**executeWithVault**
- The token position in the vault is adjusted through the transform function. It can only be called from the configured operator account or from the vault.
- It makes use of the following function:
  - IVault(vault).transform()
  
![image](https://github.com/14si2o/C4-Revert/assets/111807030/c52f5bf7-3bbe-4107-8c84-6eb728b652f6)

**execute**
- This adjusts the token directly and only be called from the configured operator account or by the vault through `transform`.
- It makes use of the following internal functions:
  - _getPool()
  - _hasMaxTWAPTickDifference()
  - _poolSwap()
  - _checkApprovals()
  - _setBalance()
  - _increaseBalance()

### **AutoRange.sol** 
This contract allows an approved operator of AutoRange to change the range for the configured position. If called inside Vault, it will use the transform method. If outside, the positions need to be approved for the contract and configures with configToken function. 

![image](https://github.com/14si2o/C4-Revert/assets/111807030/fb183b7a-22e3-48c5-a874-83a20350828a)

**executeWithVault**
- The token position in the vault is adjusted through the transform function. It can only be called from the configured operator account or from the vault.
- It makes use of the following function:
  - IVault(vault).transform()

![image](https://github.com/14si2o/C4-Revert/assets/111807030/430d1768-1e16-451e-9af3-505e2616995e)


**execute**
- This adjusts the token directly and only be called from the configured operator account or by the vault through `transform`.
- It makes use of the following internal functions:
  - _decreaseFullLiquidityAndCollect()
  - _getPool()
  - _getTickSpacing()
  - _routerSwap()
  - _transferToken()




## 5. Codebase Quality

On the whole, I evaluate the quality of `Revert Lend` codebase to be "Good". The contract and function design are clearly well though out, access control is properly implemented and the various standards are well implemented. Some improvements on attention on detail would be advisable and there are architectural complexities. Details are explained below:

| Codebase Quality Categories              | Comments                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Architecture**                | Each of the seperate products of Revert is well designed, segregating functionality into distinct contracts (e.g., automators, interfaces, transformers, utils) for clarity and ease of maintenance. Further seperating the interest model from the vault indicates a clear intention for seperation of concerns. When we take entire complex puzzle of all the products together, there are certain concerns as explained above in the Architecture part. |
| **Upgradeability**         | In the whitepaper (page 5), it is stated:`Revert Lend implements a nonupgradable contract design. This decision ensures the integrity of the protocol, minimizing the risk of introducing errors or modifying security trade-offs, through any future modifications.` This represents, in my humble opinion, a grave error in judgement. The primary reason why most, if not all, major protocols implement some form of upgradeability, is that bugs and errors are almost assured to happen no matter the quality of the codebase. Regardless of the number of audits, there cannot be a guarantee that a bug will not be found. If the bug stops users from obtaining their funds or allow malicious users to steal with impunity, the protocol team is powerless to act without some form of control. I would strongly recommend the team to implement upgradeability which can easily be burned after a certain amount of time has passed and the risk of problems becomes minute.|
| **Code Comments**                        | The contracts are accompanied by comprehensive comments, facilitating an understanding of the functional logic and critical operations within the code. Functions are described purposefully, and complex sections are elucidated with comments to guide readers through the logic. However, there are several instances where comments remain when the code logic has changed. The protocol could benefit from a spring cleaning excercise where the code comments are all reviewed. |
| **Testing**                              | The protocol has an excellent level of test coverage, approaching nearly 100%. This ensures that a wide array of functionalities and edge cases are tested, contributing to the reliability and security of the code. However, to further enhance the testing framework, the incorporation of fuzz testing and invariant testing is recommended.      |
| **Security Practices**    | The contracts demonstrate awareness of common security pitfalls in Solidity development. Functions are guarded with appropriate access control modifiers (e.g., `onlyOwner`,`emergencyAdmin`, `transformer mode` checks), and state-changing functions are protected against reentrancy attacks. One area of concern is the intention of the protocol to implement `transient` storage for the `transformedTokenId` variable, which guards against reentrancy, once the Dencun upgrade goes live. Transient storage is extremely new and there have already been realistic [formulations](https://chainsecurity.com/tstore-low-gas-reentrancy/) of reentrancy attacks through the use transient storage. As such I would recommend much caution in implementing these transiant variables and/or request an additional audit to explore these specific security issues.  |   
| **Error Handling**    | The custom errors are defined in IErrors and correctly applied throughout the codebase. However, in some cases it would have usefull to implement the errors with a more expansive message. | 
| **Documentation**   | The sole documentation for the V3Vault is the whitepaper, which is excellently written. Nevertheless, more documentation describing the protocol would be very usefull.|


## 6. Centralization Risks

The protocol defines 2 privileged roles:  `Owner` and `EmergencyAdmin`.

The `Owner` is set to a Multisig and Timelock according to the contest README and has the following rights:
- In `V3Oracle`:
  - setTokenConfig
  - setEmergencyAdmin
  - setMaxPoolPriceDifference
- In `V3Vault`:
  - withdrawReserves
  - setTransformer
  - setLimits
  - setReserveFactor
  - setReserveProtectionFactor
  - setTokenConfig
  - setEmergencyAdmin  
- In `AutoCompound`:
  - setReward

The main issue with the owner design is that all changes are One-Step operations. Regardless whether it is changing the owner itself or setting a token configuration, even the tiniest mistake could case major damage to the protocol. Either by setting the owner to a random address or wrongly setting twap seconds or a token address, which would give hackers an immediate and easy attack vector to drain the protocol, a single mistake is devastating.  

I would recommend the implementation of a two-step approval process for the most critical of operations. Also, the contest README states that the owner is a multisig subject to a Timelock, but nothing of the sorts can be seen in the contract code.

The `EmergencyAdmin` is set to a Multisig according to the contest README and has the following rights: 
- In `V3Oracle`:
  - setOracleMode
- In `V3Vault`:
  - setLimits

The emergencyAdmin can essentially pause the protocol by setting the limits to `0` and it can change the oracle from TWAP to Chainlink or change the verification mode. However, if issues are found that are not affected by these limits (liquidation, transformer misbehaving), then the emergencyAdmin does not have the powers to take action.   

Instead of a custom role, I would recommend to implement the standardised pattern of **pause/unpause**, and adding the `whenNotPaused` modifier to all functions which change state in the protocol. Thus allowing the admin to freeze the entire protocol in case of emergency.    

## 7. Systemic & Integration Risks

1. Reliance on double Oracle.
- The protocols obtain the price information from either Chainlink or Uniswap TWAP and uses the other to verify the price against manipulation. In itself an excellent design but it does mean that the oracle will malfunction if either of the oracle sources malfunctions. This has happened before and even though it is certainly not a reason to not use double verification, it is a risk that should be acknowledged.
- Note that proper configuration is also of paramount importance, since the currect code will malfunction due to the absence of a L2 sequencer check when deploying on Arbitrum. 

2. Off-chain Router
- Many of the transformers make use of an off-chain router to execute swaps. The router is outside the scope of the audit and we cannot evaluate it's design or assess it's security. As such, if the router were to go off-line or be compromised, the entire protocol will be compromised.    

3. Integrating ERC4626 Vault with Transformers
- Transformers are treated as trusted actors and can effect state-changing calls on the Vault. In itself, this is not a problem. However, as noted above in the architectural risks part, the multiplication of similar functionality exponentially increases the risk of a security oversight.
- Futhermore, the current design allows future transformers, which might have security issues or unforeseen side-effects when interacting with the vault, to be quickly added as a trusted source.

4. Lack of Upgradeability
- The absence of any upgradeability leaves the protocol powerless when critical bugs and errors are found. While it is true that upgrades can also introducing security issues (Euler [hack](https://www.euler.finance/blog/war-peace-behind-the-scenes-of-eulers-240m-exploit-recovery) is a famous example), bugs are as certain as death & taxes, so functionality to resolve these should be implemented.
- I would recommend implementing the [UUPS](https://eips.ethereum.org/EIPS/eip-1822) proxy pattern since this allows the protocol to resolve bugs and burn the upgradeability once the protocol has been live for a significant amount of time and the likelyhood of new bugs becomes minute.

5. Transient Storage
- The protocol intents (code comment) to use transient storage for the `transformedTokenId` variable, which is critical for guarding against reentrancy. This could a problem since it is a new and fairly unexplored functionality. Since some theoretical [reentrancy](https://chainsecurity.com/tstore-low-gas-reentrancy/) attacks are already being discussed, I would suggest much prudence in implementing this.  






### Time spent:
71 hours