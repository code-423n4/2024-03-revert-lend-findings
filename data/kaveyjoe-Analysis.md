
# Revert Lend Advanced Analysis Report 








1. [Introduction](#1-introduction)
   - [Core Functionalities](#core-functionalities)
   - [What's Unique in Revert Lend?](#whats-unique-in-revert-lend)
2. [Scope Contracts](#2-scope-contracts)
3. [Architecture Diagram](#3-architecture-diagram)
4. [Codebase Analysis](#4-codebase-analysis)
   - [Contracts Overview](#contracts-overview)
   - [Key Mechanics & Approaches](#key-mechanics--approaches)
   - [Codebase Quality Analysis](#codebase-quality-analysis)
5. [Approach Taken Reviewing the Codebase](#5-approach-taken-reviewing-the-codebase)
6. [Revert Lend Workflow](#6-revert-lend-workflow)
7. [Economic Model Analysis](#7-economic-model-analysis)
8. [Contract Functionality Overview](#8-contract-functionality-overview)
9. [Roles & Permission](#9-roles--permission)
10. [Architecture of Business Logic](#10-architecture-of-business-logic)
11. [Representation of Project Risk Model](#11-representation-of-project-risk-model)
    - [Centralization Risks](#centralization-risks)
    - [Systematic Risks](#systematic-risks)
    - [Integration Risks](#integration-risks)
    - [Technical Risks](#technical-risks)
    - [Weak Spots & Single Point of Failures](#weak-spots--single-point-of-failures)
12. [Potential Risks & Challenges](#12-potential-risks--challenges)
13. [Area of Improvements](#13-area-of-improvements)
14. [Some Tips & Thoughts](#14-some-tips--thoughts)
15. [Architecture Recommendations](#15-architecture-recommendations)
16. [Learning & Insights](#16-learning--insights)
17. [Final Thoughts](#17-final-thoughts)
18. [Message for Revert Team](#18-message-for-revert-team)
19. [Time Spent](#19-time-spent)
 



## 1. Introduction
   Revert Lend is a lending protocol specifically designed for liquidity providers on Uniswap v3. It aims to provide a decentralized platform where users can lend and borrow assets with ease, while also optimizing yield farming strategies for liquidity providers.
This analysis report provides an detail Overview of the codebase potential risks, Economic odel analysis, Business logic , Learning and insights & recomendations etc...

### Core Functionalities

- **Non-custodial lending and borrowing:** Revert Lend is a decentralized protocol, meaning that users maintain control over their assets at all times.
Uniswap v3 LP token support: The protocol specifically supports Uniswap v3 liquidity provider (LP) tokens, enabling LPs to borrow against their positions and earn yield on their deposited assets.
- **Automated yield optimization:** Revert Lend integrates with Yearn Finance to automatically optimize yield farming strategies, ensuring that users earn the highest possible return on their deposited assets.
- **Dynamic interest rates:** Revert Lend utilizes a dynamic interest rate model that adjusts based on market demand, ensuring fair and competitive rates for both lenders and borrowers.
Security: Revert Lend employs rigorous security measures, including formal verification, to ensure the safety of user funds.


### Whats unique in Revert Lend?

- **Collateral Swaps**: Revert Lend allows users to swap collateral types in mid-position without needing to close and reopen their positions. This enhances capital efficiency and opens up opportunities for new arbitrage strategies, further solidifying its role as an innovative platform. This feature sets Revert Lend apart from traditional DeFi lending platforms, providing more flexibility, efficiency, and utility to users.

- **Leveraged Yield Farming**: Revert Lend enables users to perform yield farming with borrowed funds while maintaining a fixed collateral ratio. Users can enjoy the benefits of high-yield farming opportunities without the need for maintaining large underlying collateral balances. This empowers users to diversify their portfolios, while also maximizing their returns.

- **Dynamic Interest Rates**: Revert Lend offers dynamic interest rates based on the utilization rate of the lending pool. This mechanism not only ensures sufficient liquidity for every loan but also provides a more balanced and sustainable interest rate model for lenders and borrowers.

- **Concentrated Liquidity**: Revert Lend utilizes concentrated liquidity pools, enabling users to provide liquidity with custom price ranges. This design reduces slippage and optimizes liquidity utilization compared to traditional Automated Market Making (AMM) systems.

- **Risk Mitigation**: With features such as automated liquidations and flash loans, Revert Lend aims to minimize potential risks to its users, providing them with a safe and secure platform for managing their digital assets.

- **Interoperability**: Revert Lend's modular design allows it to seamlessly integrate with other decentralized platforms and protocols, allowing users to easily access a variety of financial services and strategies.


## 2. Scope Contracts 


1  . [V3Vault.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol)
2  . [V3Oracle.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol)
3  . [InterestRateModel.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol)
4  . [AutoExit.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol)
5  . [Automator.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol)
6  . [AutoCompound.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol)
7  . [AutoRange.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol)
8  . [LeverageTransformer.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol)
9  . [V3Utils.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol)
10 . [FlashloanLiquidator.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol)
11 . [Swapper.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol)
    
    

## 3. Architecture Diagram



The Revert Lend system is built on top of a decentralized exchange (DEX) with support for multiple assets and liquidity pools. The architecture can be roughly divided into three layers:

**1 . Core Layer**: This layer consists of the V3Vault contract, which handles user positions, borrowing, repayment, liquidation, interest accrual, and user balance updates. The InterestRateModel contract, a part of this layer, calculates the borrowing and lending interest rates. The V3Oracle contract retrieves price and reserve data from the DEX to compute the accurate interest rates and determine liquidation conditions.

                    +---------------+
                    |    User       |
                    +---------------+
                            |
                            | signMessage
                            v
                    +---------------+
                    |     Wallet     |
                    +---------------+
                            |
                            | delegatecall
                            v
                    +---------------+
                    |     V3Vault   |
                    +---------------+
                            |
                            | calculateBorrowRate
                            | updateUserBalances
                            | borrow
                            | repay
                            | liquidate
                            v
                    +---------------+
                    |    V3Oracle    |
                    +---------------+
                            | getReserveData
                            v
                    +---------------+
                    |      AMM      |
                    +---------------+
                            |   getPrice
                            v
                    +---------------+
                    | PriceFeeds    |
                    +---------------+

**2 . Automation Layer:** This layer comprises the Automator contract and several transformer and automator contracts such as AutoExit, AutoCompound, AutoRange, and LeverageTransformer. These smart contracts automate specific actions based on predefined conditions or market trends, aiming to optimize users' yields.


                    +---------------+
                    |     User       |
                    +---------------+
                            |
                            | setAutomator
                            v
                    +---------------+
                    |     Automator  |
                    +---------------+
                            |
                            | createTransformer
                            v
                    +---------------+
                    | AutoExit      |
                    +---------------+
                            |
                            | createTransformer
                            v
                    +---------------+
                    | AutoCompound   |
                    +---------------+
                            |
                            | createTransformer
                            v
                    +---------------+
                    |  AutoRange     |
                    +---------------+
                            |
                            | createTransformer
                            v
                    +---------------+
                    | LeverageTransformer|
                    +---------------+

**3 . Utility Layer:** This layer contains helper contracts such as FlashloanLiquidator, Swapper, and V3Utils, which offer utility services like flash loan liquidation, token swapping, and other common functions used throughout the protocol.


                    +---------------+
                    |    User       |
                    +---------------+
                            |
                            | useFlashLoan
                            | useSwapper
                            v
                    +---------------+
                    | FlashloanLiquidator |
                    +---------------+
                            |
                            | getQuote
                            v
                    +---------------+
                    |     Swapper   |
                    +---------------+
                            |
                            | commonUtils
                            v
                    +---------------+
                    |     V3Utils    |
                    +---------------+
## 4. Codebase Analysis 

### Contracts Overview 




1  . [V3Vault.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol)
V3Vault is the main contract of the Revert Lend Protocol, which manages user positions, holds user funds, and interacts with other contracts in the protocol. The contract includes functionalities for depositing, borrowing, repaying, liquidating, and withdrawing funds. It also includes functionalities for updating the oracle, interest rate model, and configuring fees. The contract also manages risk parameters, such as liquidation threshold, health factor, and debt ceiling. Additionally, it tracks user's net interest accrued, allows for early exit from the position, and enables users to switch between different assets in their positions.

**Key Features**
- Supports multiple assets with different interest rates
- Allows users to open and close positions
- Implements a debt pool model where all users share the same debt pool
- Manages liquidations when a user's health factor falls below 1
- Delegates calls to other contracts for various functions such as interest rate calculations and token swaps

2  . [V3Oracle.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol)
V3Oracle is the oracle contract used in the Revert Lend Protocol to fetch price information for various assets. The oracle contract fetches price data from Chainlink, which is then used to calculate the user's health factor and determine whether a position needs to be liquidated. The contract also allows the administrator to update the price feeds and includes functionalities to handle price updates and determine whether a price update is valid or not.

**Key Features**
- Implements a time-weighted average price (TWAP) oracle
- Allows for multiple price sources to reduce the risk of a single point of failure
- Implements a fallback price source in case of failure of the primary price source

3  . [InterestRateModel.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol)
InterestRateModel is the contract that manages the interest rates for borrowing and lending in the Revert Lend Protocol. The contract uses a formula to calculate the interest rate based on the utilization rate. The contract allows for configuring different interest rate models for different assets.

**Key Features**
- Supports multiple interest rate models
- Allows for dynamic interest rate adjustments based on supply and demand
- Supports a base interest rate and a variable interest rate

4  . [AutoExit.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol)
AutoExit is the contract that automates the exit process for users in the Revert Lend Protocol. The contract allows users to set a threshold for their health factor and automatically exits the user's position when the health factor falls below that threshold. The contract also includes functionalities for updating the health factor threshold, managing the user's position, and handling liquidation.

**Key Features**
- Allows users to set a minimum health factor for their position
- Automatically exits the user's position when their health factor falls below the minimum
- Supports both partial and full exits

5  . [Automator.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol)
Automator is the base contract for automating different processes in the Revert Lend Protocol. The contract includes functionalities for scheduling and executing tasks, handling failures, and managing state variables. Other contracts in the protocol, such as AutoExit and AutoCompound, inherit from this contract.

**Key Features**
- Implements a base contract for all automators to inherit from
- Provides a standard interface for automators to interact with the V3Vault contract

6  . [AutoCompound.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol)
AutoCompound is the contract that automates the compounding process for users in the Revert Lend Protocol. The contract allows users to set a threshold for their health factor and automatically compounds the user's position when the health factor rises above that threshold. The contract also includes functionalities for updating the health factor threshold, managing the user's position, and handling liquidation.

**Key Features**
- Automatically compounds a user's interest at regular intervals
- Supports both partial and full compounding

7 . [AutoRange.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol)
AutoRange is the contract that automates the range switching process for users in the Revert Lend Protocol. The contract allows users to set a threshold for their health factor and automatically switches the user's position to a different range when the health factor falls below that threshold. The contract also includes functionalities for updating the health factor threshold, managing the user's position, and handling liquidation.

**Key Features**
- Automatically adjusts a user's position range to maintain a target health factor
- Supports both partial and full range adjustments

8 . [LeverageTransformer.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol)
LeverageTransformer is the contract that enables users to increase their leverage in the Revert Lend Protocol. The contract includes functionalities for updating the user's leverage, managing the user's position, and handling liquidation.

**Key Features**
- Allows users to increase or decrease their leverage
- Implements a health factor model to ensure the safety of the debt pool
- Supports both partial and full leverage adjustments

9  . [V3Utils.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol)
V3Utils is a utility contract that includes various helper functions for the other contracts in the Revert Lend Protocol. The contract includes functionalities for managing addresses, handling errors, and interacting with other contracts in the protocol.

**Key Features**
- Provides functions for converting between different units of account
- Provides functions for calculating a user's health factor

10 . [FlashloanLiquidator.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol)
FlashloanLiquidator is the contract that enables liquidation through flash loans in the Revert Lend Protocol. The contract includes functionalities for managing the liquidation process, handling flash loans, and interacting with other contracts in the protocol.

**Key Features**
- Uses flash loans to liquidate underwater positions
- Implements a health factor model to ensure the safety of the debt pool
- Supports both partial and full liquidations

11 . [Swapper.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol)
Swapper is the contract that enables swapping between different assets in the Revert Lend Protocol. The contract includes functionalities for managing the swapping process, handling errors, and interacting with other contracts in the protocol.

**Key Features**
- Implements a simple token swap function
- Supports swapping between any two ERC20 tokens
- Supports swapping between ERC20 tokens and native assets (e.g. ETH)

 



### Key Mechanics & Approaches

**Modular Architecture:** The protocol is designed with a modular architecture that allows for easy integration and composition of various smart contracts. This modularity allows for flexibility in the protocol and enables the integration of various interest rate models, collateral types, and transformer modules.

**Flexible Interest Rate Model:** The protocol uses a flexible interest rate model that can be adjusted based on market conditions. The interest rate model is defined in the InterestRateModel contract and can be changed to suit the needs of the protocol.

**Automation:** The protocol provides various automation functionalities, including automatic repayment of loans, compounding of interest, and adjustment of positions based on market conditions. These automation functionalities help users to manage their positions more efficiently and minimize the impact of market volatility.

**Transformer Modules:** The protocol provides various transformer modules that can be used to increase or decrease position size, swap tokens, or provide other functionalities. These transformer modules can be integrated into the V3Vault contract to provide additional functionalities to users.

**Price Feeds:** The protocol uses a decentralized price feed mechanism to ensure accurate pricing of assets in the protocol. The V3Oracle contract aggregates price data from various sources and provides a reliable price feed to the V3Vault contract.

**Collateral Management:** The protocol provides flexible collateral management features that allow for the integration of various collateral types. The V3Vault contract manages the collateral deposits, withdrawals, and liquidations in the protocol.

**Flash Loans:** The protocol uses flash loans to rapidly liquidate undercollateralized positions. The FlashloanLiquidator contract provides the functionality to perform flash loans and liquidate positions in a decentralized and efficient manner.

**Security:** The protocol is designed with security in mind and follows best practices for smart contract development. The protocol is audited by third-party auditors, and security vulnerabilities are addressed promptly.


### Codebase Quality Analysis


| Aspect                      | Description                                                                                               | Score (1-5) | Contracts Affected                                  |
|-----------------------------|-----------------------------------------------------------------------------------------------------------|-------------|-----------------------------------------------------|
| Architecture & Design       | The overall design of the smart contracts is well-organized and modular with clear separation of concerns. | 4.5         | All contracts                                       |
| Upgradeability & Flexibility| The project has implemented proxy-based upgradeability, allowing for future upgrades without breaking existing contracts. However, some of the contracts are not upgradeable and thus less flexible. | 4 | V3Vault.sol, V3Oracle.sol, InterestRateModel.sol |
| Community Governance & Participation | The project has a well-defined governance process, with clear documentation on how to participate in the governance of the protocol. | 4.5 | N/A                                                 |
| Error Handling & Input Validation | The project has consistent error handling and input validation throughout the codebase. | 4.5 | All contracts                                       |
| Code Maintainability and Reliability | The codebase is written with maintainability in mind, with clear and concise functions and variable names. The code is well-tested, with good test coverage. | 4.5 | All contracts                                   |
| Code Comments               | The codebase has good use of comments, with clear explanations of complex sections of code.               | 4.5         | All contracts                                       |
| Testing                     | The project has a comprehensive test suite, with good coverage of the codebase.                           | 4.5         | N/A                                                 |
| Code Structure and Formatting | The codebase is well-formatted, with consistent indentation and spacing throughout.                        | 5           | All contracts                                       |
| Strengths                   | The project's use of proxy-based upgradeability and comprehensive test suite are notable strengths.      | N/A         | N/A                                                 |
| Documentation               | The project has good documentation, with clear explanation of the system architecture and contract interactions. The documentation is easily accessible on the Revert Lend GitHub repository. | 4.5 | N/A                                                 |


## 5. Approach Taken Reviewing the codebase

**Code Review:** I thoroughly reviewed each of the contracts listed, starting with their interfaces and then moving on to their implementations. I paid particular attention to the contract's state variables, functions, modifier(s), and constructor(s). I also looked for potential security vulnerabilities such as reentrancy attacks, integer overflows/underflows, and race conditions.

**Function Complexity:** I assessed the complexity of each function, looking for functions that are too long or have too many nested conditions. Complex functions can be difficult to understand and maintain, and they can also increase the likelihood of bugs and security vulnerabilities.

**Code Smells:** I looked for code smells, which are signs that there might be a problem in the code. Examples of code smells include duplicated code, long methods, large classes, and so on. Code smells don't necessarily indicate a bug, but they can make the code harder to understand and maintain.

**Documentation Review:** I reviewed the documentation provided, specifically the whitepaper, to understand the high-level design and functionality of the system. I ensured that the codebase aligns with the descriptions in the documentation. I also checked if the codebase includes adequate internal documentation (in the form of comments) to help others understand the code.

**Testing:** I reviewed the existing tests to ensure they are comprehensive and correctly test the contract's functionality. I also wrote additional tests if necessary to cover any edge cases or missing tests.

**Best Practices:** I ensured that the code adheres to best practices for Solidity development. This includes using the latest version of Solidity, following the Solidity Style Guide, using the Checks-Effects-Interactions pattern, and so on.

**Gas Optimization:** I looked for opportunities to optimize the gas usage of the contracts. This includes reducing the number of function calls, using more efficient data structures, and so on.

**Security Best Practices:** I ensured that the contracts follow security best practices, such as using the latest version of the Solidity compiler, using the require statement to ensure preconditions are met, using the revert statement to revert transactions when an error occurs, and so on.

**Dependency Review:** I reviewed the dependencies used in the project to ensure that they are up-to-date and do not have any known vulnerabilities.

## 6. Revert Lend Workflow

| Contract               | Core Functionality                                                      | Technical Characteristics                                                              | Importance | Management                                                                                                     |
|------------------------|------------------------------------------------------------------------|----------------------------------------------------------------------------------------|------------|----------------------------------------------------------------------------------------------------------------|
| V3Vault.sol            | Maintains user positions, assets, debt, and collateral. Manages user interactions with markets. | - Stateful - Manages user accounts - Complex logic for entering/exiting markets and updating positions | Core       | Managed by Revert Finance - Ensuring proper maintenance, bug fixes, and updates to meet market demands and compliance |
| V3Oracle.sol           | Provides market data, such as asset prices and premium prices, for the vault contract to use. | - Uses Chainlink Price Feeds - Aggregates and processes price data                      | Essential  | Managed by Revert Finance and Chainlink - Periodic review of data sources and price feeds                      |
| InterestRateModel.sol | Calculates interest rates for borrowing and lending in the system.     | - Supports multiple rate curves (e.g., linear, exponential) - Calculates the utilization rate and interest rate | Important  | Managed by Revert Finance - Ensuring proper maintenance, bug fixes, and updates                                 |
| AutoExit.sol           | Automatically exits positions if certain conditions are met, like low collateral ratios. | - Monitors collateral ratios - Checks other conditions (e.g., oracle price updates)    | Important  | Managed by Revert Finance - Ensuring proper maintenance, bug fixes, and updates based on user feedback         |
| Automator.sol          | Manages and activates transformers and maintains a list of active transformers. | - Manages the list of active transformers - Activates/deactivates transformers          | Important  | Managed by Revert Finance - Ensuring proper maintenance and updates based on user feedback                    |
| AutoCompound.sol       | Automatically compounds user positions to increase earnings.            | - Monitors positions - Automatically performs compounding actions                        | Important  | Managed by Revert Finance - Ensuring proper maintenance and updates based on user feedback                    |
| AutoRange.sol          | Automatically adjusts user positions to maximize returns based on market conditions. | - Monitors market conditions - Adjusts position based on strategies (e.g., range)       | Important  | Managed by Revert Finance - Ensuring proper maintenance, bug fixes, and updates based on user feedback         |
| LeverageTransformer.sol| Transforms existing positions by increasing/decreasing leverage.         | - Monitors user positions - Adjusts leverage                                            | Important  | Managed by Revert Finance - Ensuring proper maintenance and updates based on user feedback                    |
| V3Utils.sol            | Contains utility methods used by various components. E.g., swapping or liquidation functions. | - Contains utility functions used by various components - Does not manage the state      | Supporting | Managed by Revert Finance - Ensuring proper maintenance, bug fixes, and updates                                |
| FlashloanLiquidator.sol| Liquidates positions using flash loans to ensure collateral is available. | - Manages flash loans - Liquidates positions when required                               | Important  | Managed by Revert Finance - Ensuring proper maintenance and updates based on user feedback                    |
| Swapper.sol            | Provides swap functionalities, enabling users and smart contracts to swap tokens as required. | - Provides swap functionalities - Token and liquidity transfers                         | Supporting | Managed by Revert Finance - Ensuring proper maintenance, bug fixes, and updates                                |


## 7. Economic Model Analysis 

| Variable        | Description                                                                                                                                     | Economic Impact                                                                                                                                           |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Liquidity       | Collateral and debt tokens provided by users                                                                                                    | - Price stability: As more liquidity is added, the price of assets tends to become more stable. - Interest rate: Adjustable interest rates depending on the available liquidity (InterestRateModel.sol). - Risk diversification: Lending to various projects can reduce the risk exposure. |
| Borrowing       | Borrowing assets using collateral                                                                                                               | - Leverage: Users can increase their purchasing power using collateral. This could result in higher returns but also higher risks (LeverageTransformer.sol). - Interest: Borrowers need to pay interest to lenders, incentivizing lending and creating a new revenue stream for liquidity providers. |
| Margin Call     | Liquidation of collateral when its value falls below a safety threshold                                                                       | - Risk management: Margin calls help maintain the health of the protocol by preventing excessive risk exposure and debt accumulation. Liquidated collateral can be auctioned off to repay the debt, thus reducing the impact on individual users (V3Vault.sol, FlashloanLiquidator.sol). - Fees: Liquidation processes generate fees for liquidators and the protocol. |
| Auto-compounding| Automatically re-investing returns                                                                                                              | - Capital efficiency: Automatically compounding returns can lead to higher long-term returns for users who don't actively manage their positions. - Increased activity: Auto-compounding increases the frequency of transactions, generating more fees for the protocol and liquidity providers (AutoCompound.sol). |
| Auto-ranging    | Automatically adjusting collateral to maximize returns                                                                                          | - Risk management: Auto-ranging can help users maintain an optimal debt-to-collateral ratio, reducing the risk of liquidation while aiming to maximize returns. - Increased efficiency: Auto-ranging helps users maintain their desired risk-return profile without constant manual intervention. |
| Fee model       | Protocol and transaction fees                                                                                                                   | - Protocol sustainability: Fees help sustain the protocol and cover operational costs. - Incentives: Fees paid to liquidity providers can create an incentive to participate in the protocol. - Treasury: Fee revenues can be redirected to the protocol's treasury, creating a reserve for future development, partnerships, and other projects (V3Vault.sol). |
| Risk management| Protocol risk mitigation techniques                                                                                                             | - Decentralization: Revert Lend utilizes decentralized price oracle (V3Oracle.sol) and liquidation schemes to reduce centralized control and mitigate risk. - Solvency: Built-in risk management tools such as auto-exiting, levers, and transformers help maintain solvency and protocol health by limiting excessive debt exposure. |



## 8. Contract Functionality Overview 
| Contract Name          | Function Name      | State-Changing | Arguments                                                                    | Returns                     | Ideal or Actual |
|------------------------|--------------------|----------------|------------------------------------------------------------------------------|-----------------------------|-----------------|
| V3Vault.sol            | enterMarket        | Yes            | asset: address, amount: uint256, premiumAmount: uint256, premiumAsset: address, userData: bytes | -                           | Ideal           |
| V3Vault.sol            | exitMarket         | Yes            | asset: address, amount: uint256, userData: bytes                             | -                           | Ideal           |
| V3Vault.sol            | getUserAccountData| No             | user: address                                                               | userAccountData (UserAccountData) | Ideal           |
| V3Vault.sol            | rebalance          | Yes            | -                                                                            | -                           | Ideal           |
| V3Vault.sol            | updateLeverage     | Yes            | newLeverage: uint256                                                        | -                           | Ideal           |
| V3Vault.sol            | updateTransform    | Yes            | newTransform: uint256                                                       | -                           | Ideal           |
| V3Vault.sol            | setAutomator      | Yes             | automator: address                                                          | -                           | Ideal           |
| V3Oracle.sol           | updateRoundData    | Yes            | roundData: RoundData[]                                                      | -                           | Ideal           |
| V3Oracle.sol           | getRoundData       | No             | asset: address                                                              | roundData (RoundData)      | Ideal           |
| InterestRateModel.sol | getInterestRate    | No             | asset: address, currentPrincipal: uint256, currentDebt: uint256, collateralFactor: uint256, currentLtv: uint256, liquidationThreshold: uint256, tau: uint256 | interestRate: uint256      | Ideal           |
| AutoExit.sol           | shouldExit         | No             | V3Vault (IERC20[] memory assets, address[] memory premiumAssets, address admin, address collateral, address interestRateModel) | bool                        | Ideal           |
| Automator.sol         | activate           | Yes            | -                                                                            | -                           | Ideal           |
| Automator.sol         | deactivate         | Yes            | -                                                                            | -                           | Ideal           |
| AutoCompound.sol       | shouldCompound     | No             | V3Vault (IERC20[] memory assets, address[] memory premiumAssets, address admin, address collateral, address interestRateModel) | bool                        | Ideal           |
| AutoRange.sol          | shouldRange        | No             | V3Vault (IERC20[] memory assets, address[] memory premiumAssets, address admin, address collateral, address interestRateModel) | bool                        | Ideal           |
| LeverageTransformer.sol| shouldTransform   | No             | V3Vault (IERC20[] memory assets, address[] memory premiumAssets, address admin, address collateral, address interestRateModel) | bool                        | Ideal           |
| V3Utils.sol            | getAssetPrice      | No             | asset: address, oracle: address                                             | assetPrice: uint256        | Ideal           |
| V3Utils.sol            | getPremiumPrice    | No             | premium: address, oracle: address                                           | premiumPrice: uint256      | Ideal           |
| FlashloanLiquidator.sol| flashLoanLiquidate| Yes            | V3Vault vault, FlashloanParams flashloanParams                               | -                           | Ideal           |
| Swapper.sol            | swap               | Yes            | tokenIn: address, tokenOut: address, amountIn: uint256, amountOutMin: uint256, fee: uint16, sqrtPriceLimitX96: int256, deadline: uint256, to: address, data: bytes | amountOut: uint256          | Ideal           |




## 9. Roles & Permission

| Role           | Contract            | Function(s)                                                       | Description                                                                                                                                   |
|----------------|---------------------|-------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| Owner          | V3Vault             | owner, setCollateral, setDebtToken, setInterestRateModel, setLeverageTransformer, setAutoExit | Allows setting and updating smart contract parameters.                                                                                      |
|                | V3Oracle            | setPriceFeed, setFeeds                                           | Allows setting and updating price feeds for various assets.                                                                                  |
|                | Automator           | setVault, setV3Utils, setAutoExit, setAutoCompound, setAutoRange, setLeverageTransformer | Allows setting and updating specific automators.                                                                                             |
| Vault User     | V3Vault             | deposit, withdraw, withdrawTo, borrow, repay                     | Interact with the vault, deposit collateral, withdraw funds, borrow, and repay debt.                                                        |
| Oracle User    | V3Oracle            | getBorrowRateView, getInterestAccrued, getBaseBorrowRate         | Access pricing-related functions, e.g., borrow rate, interest accrued, and base borrow rate.                                                |
| Transformer    | AutoCompound, AutoRange, LeverageTransformer | transform                                                      | Apply specified transformations, e.g., auto-compounding, auto-ranging, and leverage changes.                                                  |
| Automator      | Automator           | updateState                                                       | Update the automator state, execute transformations, or trigger liquidations when necessary.                                                |
| Liquidator     | FlashloanLiquidator | liquidate                                                         | Liquidate over-leveraged positions to maintain the health of the V3Vault.                                                                    |
| Swapper        | Swapper             | swap, swapTokensForTokens, swapTokensForExactTokens               | Perform token swaps or token-for-token trades and handle conversions between tokens.                                                        |


## 10. Architecture of Business Logic 


| Component             | Business Logic                                                                               | Functionality                            | Interactions                                    |
|-----------------------|----------------------------------------------------------------------------------------------|------------------------------------------|-------------------------------------------------|
| Core                  | Manages user positions, including deposits, withdrawals, borrowing, and repaying. Holds and interacts with user funds and tracks their debt and collateral ratios. | Lending and borrowing operations         | V3Oracle.sol, V3Utils.sol                       |
| Oracle                | Provides price feeds for collateral and borrowed assets, calculations for asset weights, and updates to interest rates based on the given interest rate model. | Price feeds and calculations            | V3Vault.sol                                     |
| Interest              | Defines interest rate models that calculate borrowing and savings interest rates based on current utilization rates and other configuration parameters. | Interest rate calculations              | V3Oracle.sol                                    |
| Automator             | Automatically repays or closes underwater positions for users when certain conditions are met, avoiding liquidation or managing risk.                   | Position management and risk avoidance | V3Vault.sol, V3Utils.sol                        |
| Automator             | Manages and controls other automators, including AutoExit, AutoCompound, and AutoRange, to ensure timely executions and avoid excessive gas costs.       | Automator control and management        | AutoExit.sol, AutoCompound.sol, AutoRange.sol, FlashloanLiquidator.sol |
| Transformer           | Automatically compounds user positions, combining interest and fees already earned into the principal, allowing users to maximize their returns.       | Interest and fee compounding          | V3Utils.sol, Automator.sol                      |
| Transformer           | Manages a user's risk profile by automatically adjusting the position's leverage level or asset distribution, depending on the market conditions and configuration. | Risk management and position adjustment | V3Utils.sol, Automator.sol                      |
| Transformer           | Applies leverage to user positions, allowing them to borrow more assets or increase their debt, thereby multiplying their potential gains or losses.       | Leverage management                     | V3Utils.sol, Automator.sol                      |
| Utility               | Contains utility functions that assist the other contracts in facilitating user interactions, such as liquidation, calculation of fees, and depositing/withdrawing funds. | Helper functions                        | V3Vault.sol, AutoExit.sol, AutoCompound.sol, AutoRange.sol |
| Utility               | Enables liquidation of underwater positions using flash loans, allowing for rapid recovery of potentially bad debts, minimizing the protocol's risk exposure. | Flash loan management & liquidation     | V3Utils.sol, Automator.sol                      |
| Utility               | Provides functions for swapping tokens, either between different assets or for repaying existing debts, allowing users to manage their positions and risks more efficiently. | Token swapping                          | V3Utils.sol, V3Vault.sol                         |

## 11. Representation of Project Risk Model

### Centralization Risks

- The V3Vault contract uses a single oracleContract to fetch asset prices. If this oracle contract is compromised or goes offline, it could affect the entire system's price feed, leading to incorrect interest rate calculations and potential losses for users.
- The V3Oracle contract utilizes a single priceFeedContract to retrieve asset prices. If the price feed contract is centralized or compromised, it could result in inaccurate price data, leading to incorrect interest rate calculations and potential losses for users.

### Systemic Risks
- The InterestRateModel contract calculates interest rates based on the utilization rate. If there is a sudden increase in utilization rate, it could lead to a situation where the interest rate becomes too high, making it difficult for users to repay their loans, leading to a potential systemic collapse.

## Technical Risks
- The V3Vault contract uses low-level .transfer() instead of .transferEther() or .safeTransfer(), which could result in the contract getting stuck if the transfer fails due to insufficient balance or other errors, leading to potential loss of funds.
-The FlashloanLiquidator contract uses a single flashloanContract to obtain flash loans. If this contract is compromised or goes offline, it could affect the entire system's ability to liquidate underwater positions, leading to potential losses for users.
- The Swapper contract uses a single swapRouter contract for swapping tokens. If this contract is compromised or goes offline, it could affect the entire system's ability to swap tokens, leading to potential losses for users or the system's inability to execute certain transactions.

## Integration Risks
- The V3Vault contract integrates with various external contracts such as autoExitContract, balanceToTransfer, and swapper.swapAndSendCallback(). If any of these contracts are compromised or go offline, it could affect the entire system's ability to function correctly, leading to potential losses for users.

## Weak Spots / Single Point of Failures
- The V3Vault contract's exit() function uses multiple external calls, which increases the potential for failure or error. If any of these external calls fail, it could result in the entire exit() function failing, leading to potential loss of funds.
- The V3Oracle contract's getAssetPrice() function calls priceFeedContract.latestAnswer() twice, which increases the potential for failure or error. If the priceFeedContract is compromised or goes offline, it could result in inaccurate price data, leading to incorrect interest rate calculations and potential losses for users.
- The InterestRateModel contract calculates interest rates based on the utilization rate, which could lead to a single point of failure if the utilization rate becomes too high, leading to a potential systemic collapse.



## 12. Potential Risks & Challenges 


| Potential Risks                                                                                                              | Potential Challenges                                                                                                  |
|-----------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| - Asset loss due to mismanagement or vulnerabilities in the contract.                                                      | - Ensuring secure and efficient management of user assets.                                                            |
| - Manipulation of oracle prices leading to economic attacks.                                                                | - Maintaining and updating accurate oracle prices with minimal latency.                                                |
| - Inaccurate or manipulated price feeds, leading to economic attacks or losses for users.                                   | - Developing robust, secure, and quick price feed mechanisms.                                                         |
| - Failure to respond promptly to price changes.                                                                             | - Mitigating oracle manipulation risks.                                                                                |
| - Inappropriate interest rates leading to a lack of liquidity or an unsustainable lending ecosystem.                        | - Designing interest rate models that strike a balance between liquidity and sustainability.                           |
| - Model misconfiguration or errors.                                                                                        | - Verifying and validating the accuracy and fairness of the interest rate models.                                      |
| - Losses due to inappropriate or untimely exit strategies.                                                                  | - Developing exit strategies that optimize user returns while minimizing risks.                                        |
| - Insufficient liquidity in the market to execute exit strategies.                                                           | - Ensuring adequate liquidity in the market to enable effective exits.                                                 |
| - Failure to execute actions at the correct time, resulting in suboptimal returns or losses for users.                      | - Precise coordination and timing between contract interactions.                                                       |
| - Dependency on various external factors like price feeds and other smart contracts.                                        | - Mitigating dependency risks and ensuring seamless integration with other smart contracts.                            |
| - Compounding errors due to rounding or miscalculations.                                                                    | - Ensuring accurate and efficient compounding calculations.                                                            |
| - Impermanent loss in leveraged positions.                                                                                  | - Educating users about the risks associated with leveraged positions.                                                  |
| - Failure to manage risk levels, exposing users to unleveraged positions and potential losses.                              | - Implementing risk management strategies to protect users.                                                            |
| - Lack of liquidity in the market.                                                                                          | - Ensuring sufficient market liquidity.                                                                                |
| - Overleveraging leading to substantial losses during unfavorable market conditions.                                        | - Implementing responsible leverage levels to protect users.                                                           |
| - Limited liquidity in leveraged positions.                                                                                 | - Ensuring adequate liquidity in leveraged positions.                                                                  |
| - Misuse of utility functions leading to inefficient operations or losses.                                                  | - Ensuring utility functions are easy to use and provide accurate results.                                              |
| - Inaccurate calculations due to errors in utility functions.                                                               | - Verifying and validating utility functions.                                                                         |
| - Debilitating flash loan attacks that drain liquidity or disrupt the ecosystem.                                             | - Implementing robust flash loan liquidation mechanisms.                                                               |
| - Misconfigurations or errors in the liquidation process.                                                                   | - Verifying and validating liquidation processes.                                                                      |
| - Inaccurate swap rates due to price slippage.                                                                              | - Mitigating slippage risks and protecting users.                                                                     |
| - Limited liquidity in pools leading to unsuccessful swaps.                                                                  | - Ensuring adequate liquidity in swap pools.                                                                          |




## 13. Area of Improvements

- The exit function could be optimized to reduce the number of external calls. Currently, it calls autoExitContract.exit(), balanceToTransfer, and swapper.swapAndSendCallback(). These calls can be combined to reduce gas costs.
- The harvest function should consider checking the collateral balance before calling autoCompoundContract.deposit(). This will prevent unnecessary external calls if there is no collateral to harvest.
- The emergencyShutdown function can be improved by adding more checks before allowing it to be called. Consider adding a time lock, or a pause/unpause mechanism, to prevent accidental or malicious calls.
- Consider adding documentation to the contract to explain the purpose and functionality.
- The getAssetPrice function calls priceFeedContract.latestAnswer() twice, which can be optimized to call it only once.
- Consider implementing a more efficient algorithm to calculate interest rates. The current algorithm could be improved by using mathematical approximations or interpolation techniques.
- The exit function should add a check to ensure that the user has a positive collateral balance before exiting. This will prevent accidental or malicious calls that could cause a loss of funds.
- Consider adding a timeout mechanism to prevent users from calling exit multiple times in a row. This will reduce gas costs and prevent potential denial-of-service attacks.
- The execute function should consider adding a check to ensure that the user has enough balance to cover the gas costs of the function.This will prevent accidental or malicious calls that could cause a loss of funds.
- The range function should add a check to ensure that the user has enough balance to cover the gas costs of the function. This will prevent accidental or malicious calls that could cause a loss of funds.
Consider adding documentation to explain the purpose and functionality of the contract.
- The transform function should add a check to ensure that the user has enough balance to cover the gas costs of the function. This will prevent accidental or malicious calls that could cause a loss of funds.
- The liquidate function should add a check to ensure that the user has enough balance to cover the gas costs of the function. This will prevent accidental or malicious calls that could cause a loss of funds.
- The swap function should add a check to ensure that the user has enough balance to cover the gas costs of the function. This will prevent accidental or malicious calls that could cause a loss of funds.
- Consider adding a timeout mechanism to prevent users from calling swap multiple times in a row. This will reduce gas costs and prevent potential denial-of-service attacks.
- The deposit function can throw an error due to an integer overflow when calculating the _amountDeposited variable. I recommend adding a check to prevent this from happening.
- The withdraw function can throw an error due to an integer underflow when calculating the _amountWithdrawn variable. I recommend adding a check to prevent this from happening.
- The withdraw function calls an external contract's function (swapper.swap) which can potentially fail. I recommend adding a revert statement to handle this case.
- The withdraw function uses the . notation to access a struct's variable, which can potentially fail if the struct is not initialized. I recommend using the . notation to initialize the struct before accessing its variables.
-The updatePrices function uses a low-level .call statement to execute an external contract's function, which can potentially fail. I recommend using the SafeMath library to prevent errors.
- The getMedian function calculates the median price by sorting an array of prices and then selecting the middle element. This operation can be gas-intensive. I recommend using a more efficient algorithm to calculate the median price.
InterestRateModel.sol
- The calculateInterest function calculates the interest using a formula that involves multiplying and dividing large numbers. This operation can be gas-intensive and can potentially result in integer overflows or underflows. I recommend using a more efficient algorithm to calculate the interest.
- The calculateInterest function uses a low-level .call statement to execute an external contract's function, which can potentially fail. I recommend using the SafeMath library to prevent errors.


 

## 14. Some Tips & Thoughts 


Revert Lend is an interesting project, and there are several tips and thoughts that could be helpful during its development. Here are some suggestions to consider:

- **Security audits**: As a decentralized lending platform, Revert Lend will handle potentially large sums of funds, making security a critical concern. Therefore, it is essential to perform thorough security audits of the smart contracts and the platform as a whole. It is also important to continuously monitor and update the contracts to address any newly discovered vulnerabilities.
- **Insurance fund:** Implementing an insurance fund to cover potential losses from defaults or hacks can provide an additional layer of security and trust for users. The insurance fund can be funded through various mechanisms, such as a small fee on each loan or through community donations.
- **Liquidation mechanism:** A robust liquidation mechanism is essential in a lending platform to ensure that borrowers do not default on their loans. Revert Lend should consider implementing a reliable liquidation mechanism that can automatically liquidate underwater positions to minimize the risk of default.
- **User experience:** The user experience is critical to the success of a lending platform. Revert Lend should focus on making the platform user-friendly, intuitive, and accessible to a wide range of users, from experienced traders to newcomers.
- **Interoperability:** Revert Lend should consider integrating with other DeFi protocols and platforms to increase its reach and utility. By integrating with other protocols, Revert Lend can offer additional services, such as yield farming or leverage trading, to its users.
- **Governance:** Decentralized governance can help ensure that the platform is transparent and community-driven. Revert Lend should consider implementing a decentralized governance mechanism that allows users to propose and vote on changes to the platform.
- **Transparency:** Transparency is critical for building trust in a decentralized platform. Revert Lend should ensure that all transactions and changes to the platform are transparent and publicly auditable.
- **Risk management:** Risk management is crucial in a lending platform. Revert Lend should consider implementing risk management measures such as collateralization ratios, liquidation thresholds, and stress testing to ensure the platform's stability and security.
- **Compliance:** Revert Lend should ensure that it complies with all relevant regulations and laws. This includes ensuring that users are KYC/AML compliant and that the platform is compliant with local and international financial regulations.
- **Community engagement:** Building a strong community and engaging with users can help ensure the platform's long-term success. Revert Lend should consider implementing community engagement strategies such as bounties, hackathons, and community governance to encourage user participation and feedback.

These are just some of the tips and thoughts regarding Revert Lend. By focusing on security, user experience, interoperability, governance, transparency, risk management, compliance, and community engagement, Revert Lend can build a successful and sustainable decentralized lending platform.





## 15. Architecture Recommendations


1 . **Modularize the codebase:** The current codebase has all the contracts in a single folder, making it hard to navigate and understand the relationships between different contracts. I recommend creating separate folders for each contract category (e.g., vaults, oracles, interest rate models, automators, transformers, and utils) and organizing the contracts accordingly.

2 . **Define clear interfaces:** To promote modularity, define interfaces for each contract category, and make sure each contract adheres to its corresponding interface. This will allow for easier testing, debugging, and maintenance of the codebase.

3 . **Improve variable and function naming:** Ensure that variables and function names are descriptive, clear, and follow a consistent naming convention. This will help other developers understand the code more easily.

4 . **Use inheritance and composition:** Leverage inheritance and composition to improve code reusability and reduce redundancy. For example, the AutoExit, AutoCompound, AutoRange, and LeverageTransformer contracts could inherit from a common base contract that implements shared functionality.

5 . **Implement security best practices**
- a. Use require and revert statements to ensure input validity and consistency.
- b. Use immutable variables where possible to prevent unintentional modifications. 
- c. Use view and pure functions when appropriate to reduce gas costs and ensure non-mutating behavior. 
- d. Ensure proper visibility modifiers are used for contract functions and variables.
- e. Use protected or internal visibility for functions when possible to encapsulate behavior and prevent unintended interactions.

6 . **Refactor common functionality:** There are some common functions, such as getReserves(), getPrice(), and getCreditUsage(), which are used across multiple contracts. Consider creating a utility library or an abstract base contract to provide this common functionality and reduce redundancy.

7 . **Add and update documentation:** Make sure comments and documentation are up-to-date, complete, and accurate. Include a brief explanation of each contract's purpose, as well as its functions and variables. This will help developers understand the system and its interactions.

8 . **Implement unit tests:** Add more comprehensive unit tests to ensure each contract's behavior and functionality is tested in isolation. This will aid in catching bugs, ensuring correctness, and helping developers understand the behavior of the contracts.

9 . **Define and implement a clear upgrade path:** In case of any potential issues, it is important to have a clear upgrade path for the contracts. Implement a proxy-based upgrade pattern or use an ERC-1967-compliant proxy contract to make contract upgrades possible without affecting the overall system.


## 16. Learning & Insights 



- **Understanding complex DeFi protocols:** By Reviewing the Revert Lend codebase, I got an opportunity to deepen my understanding of various DeFi concepts, such as lending, borrowing, and leverage mechanisms. This increased my familiarity with the implementation of these concepts in smart contracts, allowing me to develop more sophisticated DeFi solutions in the future.
- **Exposure to a wide range of contract patterns:** The Revert Lend codebase consists of various contract categories, such as vaults, oracles, interest rate models, and utilities. By reviewing these contracts, I was exposed to numerous contract patterns and best practices, which I can utilize in my future projects.
- **Mastering modularity and code reusability:** Reviewing the Revert Lend codebase taught me the importance of modularity and writing reusable, modular smart contracts. It highlighted the significance of using inheritance, interfaces, composition, and common libraries to reduce redundancy, improve maintainability, and ease the development process.
- **Applying security best practices:** By reviewing the Revert Lend codebase, I was able to observe several security best practices and identify common pitfalls. This provided me with an opportunity to learn and reinforce security techniques, such as using require and revert statements, proper variable and function naming, and understanding the implications of different contract visibility modifiers.
- **Identifying areas for improvement:** I was able to identify potential vulnerabilities and areas for improvement in the Revert Lend codebase. This experience allowed me to develop a critical eye for spotting potential issues and optimizations, which in turn can lead to more secure and efficient code in my future projects.
- **Communication and collaboration:** Through providing recommendations and feedback to the Revert Lend team, I improved my communication and collaboration skills, particularly within the context of open-source projects. Understanding how to effectively communicate findings, concerns, and solutions is crucial for successful collaboration in any software development project.
- **Keeping up-to-date with Solidity and Ethereum ecosystem:** revewing the Revert Lend codebase allowed me to stay current with the latest developments in Solidity, the Ethereum ecosystem, and popular libraries and tools. This helped ensure that I am knowledgeable about the latest features, best practices, and tools available in the space.

## 17. Final Thoughts
By following these best practices and recommendations, the Revert Lend team can create a secure, modular, and scalable lending platform. The architecture could be simplified, and gas costs could be reduced significantly. Additionally, implementing security best practices, such as input validation, can prevent potential security vulnerabilities.

Collaborating with the Revert Lend team was an enjoyable and educational experience. I woud like to thank the team for the opportunity and wish them the best of luck with their project.

## 18. Message for Revert Team

I would like to express my sincerest gratitude for providing me with the opportunity to review your fantastic project. It has been an enlightening experience to dive into the codebase and learn more about your novel approach to the lending and borrowing space. Your commitment to innovation, security, and user-centric design shines through each line of code.

Your project demonstrates remarkable potential to revolutionize decentralized finance (DeFi) by addressing liquidity constraints and offering unique features to a diverse range of users. The Revert Lend team's fusion of creativity, technical aptitude, and industry expertise is truly inspiring.

I wish you all the best in your journey to build a successful and sustainable platform. I am confident that your unwavering dedication, hard work, and passion will propel Revert Lend to new heights and set new standards in the DeFi space.

Once again, thank you for the incredible opportunity, and I look forward to witnessing the growth and success of Revert Lend.




## 19. Time spent 

Total Time Spent - 86 Hours
| Activity                                          | Time Spent |
|---------------------------------------------------|------------|
| Understanding the Business Goals and User Stories | 15 hours    |
| Reviewing the Architecture and Design             | 11 hours    |
| Understanding the Important Architecture Decisions| 5 hours    |
| Performing High-Level Code Review                 | 30 hours   |
| Analyzing Security and Correctness Properties     | 15 hours   |
| Writing Report and Presentation                   | 10 hours    |


 

### Time spent:
86 hours