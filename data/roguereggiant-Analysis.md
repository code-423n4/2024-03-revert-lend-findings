### Introduction

Revert Lend emerges as a novel decentralized peer-to-pool lending protocol tailored specifically for Automated Market Maker Liquidity Providers. At its core, the protocol enables users to leverage their Uniswap v3 liquidity provider positions, represented as NFTs via the Uniswap NFT Manager, to secure loans in selected ERC-20 tokens. A standout feature of Revert Lend is its ability to let liquidity providers maintain operational control over their collateralized capital. This flexibility ensures that providers can continually manage and optimize their positions to adapt to the fluctuating demands of the liquidity market, thereby enhancing the efficacy and appeal of liquidity provision on platforms like Uniswap v3.

### Revert Lend Protocol Mechanics

The Revert Lend protocol simplifies the lending and borrowing processes through a series of intuitive steps, starting with the accumulation of lending assets into a communal pool governed by the ERC-4626 Tokenized Vault Standard. Lenders are issued rTokens, such as rUSD, signifying their stake in the pool, which appreciates in value as borrowers repay loans with interest. This model promotes a dynamic liquidity management system where interest rates automatically adjust based on pool conditions, thereby incentivizing lenders and borrowers to act in ways that maintain a healthy liquidity state. Furthermore, borrowers can collateralize their Uniswap v3 LP positions in a straightforward manner, with loans determined by a preset minimal collateral factor, emphasizing flexibility and efficiency without necessitating intricate negotiations over terms.

### Advanced Features and Governance

Revert Lend's architecture is built for resilience and adaptability, featuring non-upgradable contracts to safeguard protocol integrity and a comprehensive risk management framework within its unified liquidity market. This approach maximizes capital efficiency and streamlines operations across various collateral types, while also incorporating sophisticated mechanisms for position management, including position transformers and an innovative liquidation system. As Revert Lend matures, it aims to transition from an initial team-controlled governance model to a fully decentralized community governance structure, ensuring that protocol decisions align with the interests and feedback of its diverse stakeholder base. Through this, Revert Lend sets a new standard for flexibility, security, and user empowerment in the DeFi lending space.
| File Name  | File Description     |
|------------|----------------------|
| V3Vault.sol | This code implements a lending and borrowing system utilizing Uniswap V3 Liquidity Provider positions as collateral. It supports ERC20 for managing the lending pool, ERC721 for handling collateral positions, and integrates various utilities and safety measures to manage loans, interest rates, and liquidations efficiently.  |
| V3Oracle.sol | This code establishes an oracle system for a vault, integrating Chainlink and Uniswap V3 TWAP to determine the value of Uniswap V3 liquidity positions. It includes mechanisms for emergency fallback, price verification, and configuration updates for token price feeds.  |
| InterestRateModel.sol | This code outlines a model for calculating interest rates within a financial system, focusing on both the rates for borrowing and supplying assets. It allows for adjustments based on the system's cash flow and debt, featuring mechanisms to update and manage these rates effectively.  |
| AutoExit.sol | This contract automates the exit strategies for Uniswap V3 positions by executing either a removal or a swap when certain price conditions are met, acting on behalf of users through configured limit or stop loss orders. It integrates with external routers for optimized swap executions and requires positions to be approved and configured beforehand.  |
| Automator.sol | This contract facilitates automatic operations for Uniswap V3 positions, allowing for strategies such as stop-loss or limit orders executed by approved operators. It includes functionality for handling token swaps, position management, and withdrawing accumulated fees or ETH.  |
| AutoCompound.sol | This contract automates the compounding of Uniswap V3 positions by allowing approved operators to reinvest fees back into the position, optimizing its value over time. It includes functionality for fee collection, token swaps, liquidity adjustments, and rewards management.   |
| AutoRange.sol | This contract automates the adjustment of Uniswap V3 position ranges based on predefined conditions, allowing positions to be more efficiently managed and potentially increase profitability. It facilitates the automatic creation of new positions with updated ranges and transfers any remaining tokens back to the original owner. |
| LeverageTransformer.sol| This contract provides functionality to adjust the leverage of existing positions within a single transaction, enabling users to efficiently increase or decrease their exposure. It includes mechanisms to borrow additional funds, swap tokens, add liquidity, or do the reverse operations to reduce leverage, all while handling token approvals and transfers seamlessly.   |
| V3Utils.sol | This contract offers utility functions for Uniswap V3 positions, including leveraging swaps to alter position ranges, compound fees, or perform customized token transformations. It operates without holding any ERC20 or NFT assets itself, ensuring all operations are executed in a single transaction and the assets are immediately returned or redirected according to the specified instructions.  |
| FlashloanLiquidator.sol | This contract facilitates atomic liquidation of positions through Uniswap V3 Flash Loans, allowing for necessary swaps and liquidation processes within a single transaction. It utilizes the Swapper utility for executing swaps and implements the Uniswap V3 flash loan callback mechanism to manage loan repayments and rewards. |
| Swapper.sol | This contract provides the foundational structure for executing swaps across different routing protocols, integrating Uniswap V3 for liquidity management and swaps, while also accommodating external routers like 0x for trade execution. It supports slippage checks, Uniswap V3 swap callbacks, and facilitates token transfers for swap operations.  |

### Architecture Digram
Here is an architecture diagram that outlines the interactions within the system described in the contract:

[![ggt.jpg](https://i.postimg.cc/vm85XLgT/ggt.jpg)](https://postimg.cc/K1VK8T5h)


### Architecture Overview:
- The core of this system is the `Swapper` contract which handles token swaps using Uniswap V3 pools and external routing protocols for optimized trade execution.
- It implements the `IUniswapV3SwapCallback` interface to participate in Uniswap V3 swaps, enabling it to be called back by Uniswap pools during a swap operation.
- The contract interacts with external routers like the 0x Exchange Proxy and the Uniswap Universal Router for executing trades based on off-chain calculated instructions, providing flexibility in choosing the swap route.
- For operations involving the native wrapped token (WETH), it interacts directly with the `IWETH9` contract to wrap or unwrap ETH as necessary.
- It also interacts with the Uniswap V3 factory contract to dynamically compute pool addresses for token pairs, ensuring the contract can work with any token pair supported by Uniswap V3.
- The swapper contract manages the logistics of the swaps, including slippage checks and token transfers, to ensure that the swaps are executed according to the specified parameters and that any leftover tokens are handled correctly.
- 
### Sequence diagram
Here is a sequence diagram that outlines the process of a swap operation in the system described:

[![tlm.jpg](https://i.postimg.cc/L89V0MGm/tlm.jpg)](https://postimg.cc/F76c7w96)

### Sequence Overview:
- The user initiates a swap operation by interacting with the Swapper Contract. This can be done with or without using an EIP712 permit for token approval.
- If a permit is used, the Swapper Contract requests a signature from the user for token approval. If not, the user directly approves the Swapper Contract to transfer tokens on their behalf.
- The Swapper Contract then decides the best route for the swap, using either an external router like the 0x Exchange Proxy or the Uniswap Universal Router, based on the provided swap details.
- If a flash swap is part of the operation, the Uniswap V3 Pool calls back the Swapper Contract to complete the swap, which might involve wrapping or unwrapping ETH via the IWETH9 contract.
- For direct swaps on Uniswap V3, the Swapper Contract interacts with the Uniswap V3 Factory to get the appropriate pool address.
- After the swap is executed, any leftover tokens, including potentially wrapped or unwrapped ETH, are returned to the user. If the operation involved minting a new NFT (in case of swap and mint operations), it is also transferred to the user or a specified recipient.

### Overview of V3Vault Smart Contract Functions
[![f1-uml.jpg](https://i.postimg.cc/j57LtZLM/f1-uml.jpg)](https://postimg.cc/WFs27mmZ)

#### Main Functionalities

**1. Contract Initialization and Setup:**
- **Constructor:** Initializes the contract with essential parameters, including the ERC20 asset, Uniswap V3 components, interest rate model, oracle, and permit contract. It also sets up the ERC20 token representing shares of the lending pool.

**2. Vault Information:**
- **vaultInfo:** Provides global information about the vault, such as total debt, lent amount, available balance, and reserves.
- **lendInfo:** Returns the lent amount for a specific account.
- **loanInfo:** Details about a specific loan, including debt, full collateral value, and liquidation costs.
- **ownerOf:** Retrieves the owner of a specific loan token ID.
- **loanCount & loanAtIndex:** Functions for enumerating loans owned by an address.

**3. Lending and Borrowing:**
- **deposit & mint:** Functions to lend assets to the vault, either by specifying the asset amount (deposit) or the share amount (mint).
- **withdraw & redeem:** Allows lenders to withdraw their lent assets or redeem their shares from the vault.
- **borrow:** Borrow assets using a Uniswap V3 LP position as collateral.
- **repay:** Repay borrowed assets either in the form of assets or debt shares.
- **liquidate:** Liquidate undercollateralized positions, compensating the liquidator with a portion of the collateral.

**4. Collateral Management:**
- **create & createWithPermit:** Create a new collateralized position by transferring a Uniswap V3 LP token to the vault.
- **decreaseLiquidityAndCollect:** Decrease liquidity from a position and collect resultant assets.
- **transform:** Allows whitelisted contracts to transform a position by performing actions like range adjustments, with the final state being checked for adequate collateralization.

**5. Administration:**
- **withdrawReserves:** Withdraw excess reserves from the vault, subject to limitations for protecting the vault's liquidity.
- **setTransformer:** Configure which contracts are allowed to perform transformations on positions.
- **setLimits:** Update lending and borrowing limits, including global caps and minimum loan sizes.
- **setReserveFactor & setReserveProtectionFactor:** Adjust the factors determining how much interest is reserved for the protocol and how much lending capacity is protected by reserves.
- **setTokenConfig:** Configure collateral factors for different tokens used within the vault's positions.
- **setEmergencyAdmin:** Designate an emergency administrator capable of executing certain actions without the typical restrictions.

**6. Internal Mechanics:**
- Functions to manage collateral factors, calculate interest rates, handle liquidation proceeds, and ensure loans remain healthy (adequately collateralized).

**7. ERC721 & ERC20 Integrations:**
- Implements ERC721 receiver interface to handle incoming Uniswap V3 LP tokens.
- Extends ERC20 functionality to represent lenders' shares in the lending pool, with overrides for ERC4626 vault standard functions to integrate with the lending and borrowing mechanics.

**8. Miscellaneous:**
- **Multicall:** Enables batched calls to the contract, allowing users to perform multiple operations in a single transaction for efficiency and user experience enhancement.
[![f1-seq.jpg](https://i.postimg.cc/3N97TvCL/f1-seq.jpg)](https://postimg.cc/n9sNKMW7)
#### Key Points
- The contract manages a single ERC20 asset for lending and borrowing, using Uniswap V3 positions as collateral. 
- It includes a comprehensive set of features for managing loans, including creating, modifying, repaying, and liquidating positions based on their collateral value and market conditions.
- Administration functions allow for dynamic management of lending terms, collateral requirements, and other critical parameters to ensure the vault's stability and attractiveness to users.
- Integrates with Uniswap V3, Permit2, and an oracle for decentralized finance operations, offering users various strategies for yield generation and leverage.

### V3Oracle Smart Contract Functions Overview
[![f2-uml.jpg](https://i.postimg.cc/HkkNKNN1/f2-uml.jpg)](https://postimg.cc/KRCQ30F0)
#### Contract Setup

- **Constructor:** Initializes the oracle with references to Uniswap V3 components, reference tokens for TWAP and Chainlink, and sets the owner.

#### Oracle Functionality

- **getValue:** Calculates the value of a Uniswap V3 LP position and its constituent tokens in a specified asset token. It incorporates checks against price manipulation and supports multiple modes for deriving prices using Chainlink, TWAP, or both.

- **getPositionBreakdown:** Provides detailed information about a Uniswap V3 LP position, including token amounts, liquidity, and uncollected fees.

- **setMaxPoolPriceDifference:** Allows the contract owner to set the maximum allowed price difference between the oracle-derived pool price and the actual pool price.

- **setTokenConfig:** Configures or updates oracle settings for a token, including its Chainlink feed, TWAP settings, and operational mode.

- **setOracleMode:** Updates the operational mode for a token's price retrieval, which can be changed by the contract owner or an emergency admin for flexibility in response to market conditions or data source reliability.

- **setEmergencyAdmin:** Designates an emergency administrator capable of executing certain actions without the typical restrictions, enhancing the contract's ability to respond to unforeseen situations.

#### Internal Logic

- **_getReferenceTokenPriceX96:** Determines the price of a token relative to a reference token, utilizing the configured oracle mode to either fetch directly from Chainlink, calculate a TWAP from Uniswap V3, or use a combination of both with verification steps.

- **_checkPoolPrice & _requireMaxDifference:** Enforces checks to ensure the price derived from the oracle does not significantly deviate from the actual Uniswap V3 pool price, mitigating risks of price manipulation.

- **_getChainlinkPriceX96 & _getTWAPPriceX96:** Fetches token prices from Chainlink or calculates them based on Uniswap V3 TWAP, according to the token's configured oracle mode and parameters.

- **_initializeState & _getAmounts:** Helpers to fetch and calculate position details from Uniswap V3, including token amounts and liquidity based on current pool state.

- **_getUncollectedFees & _getFeeGrowthInside:** Calculates uncollected fees for a position and the fee growth within specified tick ranges, aiding in accurate value computation.

#### Administrative Functions

- Functions like **setMaxPoolPriceDifference**, **setTokenConfig**, **setOracleMode**, and **setEmergencyAdmin** provide the contract owner and emergency admin with the ability to adjust oracle parameters and modes. These adjustments can be crucial in maintaining accurate pricing, ensuring the oracle's reliability, and protecting against market anomalies or data source issues.

#### Security and Flexibility

- The contract incorporates mechanisms to switch between different price sources and verification methods, enhancing its resilience against data manipulation or source failure.
- The ability to update oracle modes and configurations allows for dynamic responses to changing market conditions or oracle data quality, ensuring the continued accuracy and reliability of the pricing information provided to the V3Vault and other consumers.

[![f2-seq.jpg](https://i.postimg.cc/L5rs7fHr/f2-seq.jpg)](https://postimg.cc/bS98SZST)

### InterestRateModel Smart Contract Functionality Overview
[![f3-uml.jpg](https://i.postimg.cc/4yb5zFXT/f3-uml.jpg)](https://postimg.cc/wRMLz2tW)
#### Contract Initialization

- **Constructor:** Sets up the interest rate model with initial parameters for base rate, multiplier, jump multiplier, and kink, all provided as yearly rates and kink utilization rate, converted to per-second values for computation efficiency.

#### Interest Rate Calculation

- **getUtilizationRateX96:** Calculates the utilization rate as a ratio of current debt to the sum of available cash and current debt, scaled by a factor of 2^96 (Q96) to maintain precision. This rate indicates how much of the available funds are being utilized as debt.

- **getRatesPerSecondX96:** Determines the borrow and supply rates based on the current cash, debt, and predefined model parameters. The function adjusts the borrow rate depending on whether the utilization rate is above or below the kink. The supply rate is then derived from the borrow rate and the utilization rate.

#### Model Parameters Adjustment

- **setValues:** Allows the contract owner to update the model's parameters, including the base rate, multiplier, jump multiplier, and kink. These parameters are set on a per-year basis and internally converted to per-second rates for calculation purposes. This function also enforces maximum limits on the base rate and multipliers to ensure the model's stability and prevent excessive interest rates.

#### Events

- **SetValues:** Emitted when the interest rate model's parameters are updated, providing visibility into changes in the model's configuration.

#### Internal Mechanics and Safety Checks

- The contract incorporates safety checks through the **InvalidConfig** error to prevent setting rates or multipliers that exceed predefined maximum values, ensuring that the model remains within reasonable bounds.
- Interest rates are calculated on a per-second basis, considering the continuous compounding of interest, which aligns with real-world lending and borrowing dynamics in decentralized finance (DeFi) platforms.
- Utilization rate calculation and interest rate adjustments based on this rate ensure that the model dynamically responds to changes in supply and demand, maintaining a balanced and responsive economic model for lending and borrowing activities.

#### Administrative Control

- The **onlyOwner** modifier restricts the ability to update the model's parameters to the contract's owner, providing a mechanism for governance and adjustment of the model in response to market conditions or strategic considerations.

### Summary

The **InterestRateModel** smart contract offers a flexible and dynamic framework for calculating interest rates in a lending/borrowing environment. By adjusting rates based on utilization, the model incentivizes supply and demand balance. The ability to update model parameters ensures adaptability to evolving economic conditions, supporting sustainable lending and borrowing activities within the associated DeFi platform.
[![f3-seq.jpg](https://i.postimg.cc/WpXSbCYM/f3-seq.jpg)](https://postimg.cc/7bJSKsk6)

### Overview of the AutoExit Smart Contract
[![f4-uml.jpg](https://i.postimg.cc/x82G1rWS/f4-uml.jpg)](https://postimg.cc/ft8S8PzH)

The `AutoExit` smart contract facilitates the automatic execution of positions in a decentralized finance (DeFi) context, specifically targeting Uniswap V3 positions. It provides functionalities for setting up automated exit strategies for liquidity positions, including limit orders (automatic removal) and stop-loss orders (swap to the opposite token), based on predefined price triggers.

#### Key Functionalities

- **execute:** This function allows an approved operator to trigger the configured exit strategy for a given position when certain conditions are met, such as reaching a specific price level (tick). The strategy could involve either removing the position entirely or swapping it to another token, based on the predefined configuration. The function ensures that operations are executed only if they meet slippage requirements and are within the defined reward parameters.

- **configToken:** Enables position owners to configure or update the exit strategy for their positions. This includes setting parameters such as activation status, trigger ticks for both tokens in the position, slippage tolerances, and the reward mechanism for the executing operator. It ensures that only the position owner can make such configurations.

#### Event Notifications

- **Executed:** Emitted after an exit strategy is successfully executed, detailing the tokenId, whether a swap occurred, the amounts returned, and the involved tokens.

- **PositionConfigured:** Announced when a position's exit strategy is configured or updated, detailing the tokenId, the active status, swap directions, trigger ticks, slippage tolerances, and reward configurations.

#### Constructor and Initialization

- The contract's constructor initializes the `Automator` contract with parameters like the Nonfungible Position Manager (`_npm`), operator address (`_operator`), withdrawal address (`_withdrawer`), and routers for swap operations.

#### Exit Strategy Execution Mechanism

- The execution process involves validating the current state and configuration of the position, determining whether the position's current price triggers the exit strategy, performing the necessary liquidity removal or token swap based on the strategy, and transferring the resultant tokens back to the position owner.

- The function incorporates checks for liquidity consistency, trigger conditions, and slippage tolerances to ensure that actions are performed as expected and within safe parameters.

- Operators are incentivized through rewards, defined as a percentage of the fees generated or the total value of the position, with limits on the maximum reward to prevent exploitation.

#### Configuration and Governance

- Position owners have the flexibility to activate or deactivate their exit strategies, choose between limit order and stop-loss functionalities, and set precise conditions for their execution, including trigger prices and acceptable slippage.

- The contract includes mechanisms to prevent unauthorized access and modifications, ensuring that only position owners and approved operators can configure strategies and execute them, respectively.

- Parameters for the contract's operation, such as TWAP intervals and maximum TWAP tick differences, are set during initialization to align with market conditions and prevent manipulation.

### Summary

The `AutoExit` contract provides a robust framework for automating exit strategies for Uniswap V3 positions, enhancing the flexibility and efficiency of managing liquidity in DeFi markets. Through detailed configuration options and secure execution mechanisms, it supports both risk management practices, like stop-loss orders, and profit-taking strategies, such as limit orders, contributing to a more sophisticated and user-friendly trading environment.
[![f4-seq.jpg](https://i.postimg.cc/pTsHCxR2/f4-seq.jpg)](https://postimg.cc/YGLZ25vV)
### Overview of the Automator Smart Contract
[![f5-uml.jpg](https://i.postimg.cc/MKQkLgSm/f5-uml.jpg)](https://postimg.cc/ppR1hGym)
The `Automator` smart contract serves as a foundational component designed to automate certain operations in the context of DeFi, specifically focusing on Uniswap V3 positions. It extends the functionality of the `Swapper` contract, adding a layer of administrative control and execution logic for automated tasks.

#### Main Functionalities

##### Administrative Controls

- **setWithdrawer:** Assigns the address authorized to withdraw accumulated fees (in token or ETH form) from the contract.

- **setOperator:** Toggles the activation status of an operator, which is an external entity or contract allowed to execute automated operations.

- **setVault:** Toggles the activation status of a vault, enabling or disabling it from participating in automated operations.

- **setTWAPConfig:** Configures the Time-Weighted Average Price (TWAP) parameters, including the observation period and the maximum allowed tick difference, to safeguard against price manipulation.

##### Withdrawal Operations

- **withdrawBalances:** Allows the designated withdrawer to transfer out accumulated ERC20 tokens from the contract.

- **withdrawETH:** Enables the designated withdrawer to transfer out accumulated Ether from the contract.

##### Validation and Execution Utilities

- **_validateSwap:** Verifies whether a swap operation can be performed based on specified oracle parameters and ensures it adheres to slippage constraints.

- **_hasMaxTWAPTickDifference:** Checks if the current price tick is within an acceptable range of the TWAP tick, preventing execution if the price has deviated excessively.

- **_getTWAPTick:** Retrieves the TWAP tick from a Uniswap V3 pool for a specified observation period, helping to assess price stability.

- **_decreaseFullLiquidityAndCollect:** Removes all liquidity from a specified Uniswap V3 position and collects any accumulated fees.

- **_transferToken:** Safely transfers tokens or unwraps and transfers Ether, supporting both ERC20 and Ether withdrawals.

- **_validateOwner:** Validates the ownership of a token or position, ensuring that automated operations are authorized.

#### Event Notifications

- **OperatorChanged:** Announces changes to the activation status of an operator.

- **VaultChanged:** Announces changes to the activation status of a vault.

- **WithdrawerChanged:** Indicates when the withdrawer address has been updated.

- **TWAPConfigChanged:** Broadcasts updates to the TWAP configuration parameters.

#### Constructor and Initialization

Upon deployment, the constructor initializes the contract with essential references such as the Nonfungible Position Manager (for interacting with Uniswap V3 positions), and sets the initial operator, withdrawer, and TWAP configuration.

### Summary

The `Automator` contract provides a secure and flexible framework for automating operations related to Uniswap V3 positions. Through its comprehensive set of administrative controls, withdrawal functionalities, and execution utilities, it empowers contract owners and designated entities to efficiently manage automated tasks while ensuring operational integrity and adherence to specified risk parameters.
[![f5-seq.jpg](https://i.postimg.cc/bJV5d9QT/f5-seq.jpg)](https://postimg.cc/yg9jb9pg)
### AutoCompound Smart Contract Overview
[![f6-uml.jpg](https://i.postimg.cc/VNWq7sv0/f6-uml.jpg)](https://postimg.cc/cK6tCSQd)
The `AutoCompound` contract extends the `Automator` contract, integrating with the Uniswap V3 Non-Fungible Position Manager (NPM) to provide functionalities for compounding Uniswap V3 positions. It utilizes `Multicall` for batched calls and `ReentrancyGuard` to prevent re-entrancy attacks.

#### Key Functionalities:

##### Compound Execution:

- **executeWithVault:** Enables the operator to compound a position within a vault. It requires the position to be configured and the vault to be approved. The function invokes a transformation on the position through the vault.
  
- **execute:** Directly compounds a position not within a vault. It can be invoked by the operator or the vault (via transform). It collects fees, potentially swaps tokens to optimize position value, adds liquidity, and adjusts token balances accordingly.

##### Configuration and Management:

- **configToken:** Not explicitly defined in the contract but inherited functionality that allows position configuration for automation.

- **setReward:** Allows the contract owner to adjust the reward percentage for auto-compounding, ensuring it does not exceed predefined limits.

##### Balance Management:

- **withdrawLeftoverBalances:** Permits position owners to withdraw any remaining token balances not utilized in compounding.

- **withdrawBalances (overridden):** Allows the designated withdrawer to collect accumulated fees in ERC20 tokens, differing from standard Automator behavior to account for specific fee handling in auto-compounding.

##### Internal Utilities:

- **_increaseBalance:** Internally tracks the addition of token balances to a position.

- **_setBalance:** Adjusts the recorded token balance for a position, emitting events based on the adjustment type (addition or removal).

- **_withdrawBalanceInternal:** Facilitates the withdrawal of token balances, ensuring the amount does not exceed the recorded balance.

- **_checkApprovals:** Ensures the contract has sufficient allowances to interact with the NPM using the position’s tokens.

#### Events:

- **AutoCompounded:** Notifies when a position has been successfully auto-compounded, detailing the amounts added and rewards.
  
- **RewardUpdated:** Indicates when the reward setting has been changed.
  
- **BalanceAdded/Removed/Withdrawn:** Track the changes in token balances associated with a position.

### Summary

The `AutoCompound` contract automates the process of compounding Uniswap V3 positions by collecting trading fees, optionally swapping tokens to balance the position for optimal growth, and reinvesting the proceeds back into the position. It provides mechanisms for safe interaction, rewards management, and balance tracking, thereby enhancing the value and efficiency of liquidity provision on Uniswap V3.
[![f6-seq.jpg](https://i.postimg.cc/rwK5k6jz/f6-seq.jpg)](https://postimg.cc/zyYyCc91)
### AutoRange Smart Contract Overview
[![f6-uml-1.jpg](https://i.postimg.cc/c6yHHYJY/f6-uml-1.jpg)](https://postimg.cc/V0g1ZJnL)
The `AutoRange` smart contract, inheriting from `Automator`, enables the dynamic adjustment of Uniswap V3 positions' ranges based on market conditions. It allows a designated operator, typically a bot, to shift the range of liquidity provision to optimize for profitability or risk management.

#### Core Functionalities:

##### Range Adjustment Execution:
- **executeWithVault:** Enables the execution of range adjustments for positions within a vault. It requires the caller to be an approved operator and the vault to be recognized by the contract. This method initiates the range adjustment by invoking a transformation through the vault.

- **execute:** Directly performs range adjustment on a position not housed within a vault. This method can be called by an approved operator or through a vault transformation. It facilitates the entire process of range adjustment, including potential token swaps, liquidity adjustments, and reward distribution.

##### Position Configuration:
- **configToken:** Configures a token for range adjustment. This involves specifying limits and deltas for the tick range, slippage parameters, reward mechanisms, and the maximum allowed reward. The configuration applies to a specific token ID and dictates how and when the position's range can be adjusted.

#### Supporting Structures and Mechanisms:
- **PositionConfig Structure:** Holds the configuration for each position, including the tick range limits and deltas, slippage tolerances, and reward settings. This structure is key to determining the conditions under which a range adjustment is permissible and how it should be executed.

- **ExecuteParams Structure:** Contains parameters for executing a range adjustment. This includes the token ID, swap direction and amount, liquidity information, and reward considerations. These parameters guide the execution logic in adjusting the position's range.

- **ExecuteState Structure:** Maintains state information during the execution of a range adjustment. This includes details about the position, tokens involved, liquidity amounts, and outcomes of actions taken during execution. The state facilitates the handling of liquidity removal, token swaps, and liquidity re-addition in the new range.

#### Events:
- **RangeChanged:** Emitted when a position's range has been successfully adjusted. It indicates the transition from the old token ID to the new token ID representing the adjusted position.

- **PositionConfigured:** Signals the configuration or reconfiguration of a position for range adjustment. It details the tick range limits and deltas, slippage settings, and reward parameters for the position identified by its token ID.

### Summary

`AutoRange` automates the strategic adjustment of Uniswap V3 liquidity positions' ranges. By configuring positions with specific parameters, operators can enable automatic range adjustments based on predefined criteria, optimizing for market conditions and enhancing the position's performance. The contract ensures that adjustments are executed within set parameters, including slippage tolerances and reward limits, to maintain control over the risk and profitability of liquidity provision.
[![file7-seq.jpg](https://i.postimg.cc/3rtS0T2k/file7-seq.jpg)](https://postimg.cc/Z0yFXX7m)
### LeverageTransformer Smart Contract Overview
[![f8-uml.jpg](https://i.postimg.cc/c4rSrTtN/f8-uml.jpg)](https://postimg.cc/nCb5W41d)
The `LeverageTransformer` contract provides mechanisms to leverage or deleverage Uniswap V3 positions directly within a single transaction. It is designed to interact with liquidity positions to either increase (leverage up) or decrease (leverage down) their exposure with borrowed funds or by repaying debt.

#### Leverage Up Functionality

- **leverageUp(LeverageUpParams calldata params):** This function increases the leverage of a specified Uniswap V3 position. It allows borrowing a specific amount of tokens, swapping a portion of the borrowed tokens for the position's tokens (if necessary), and then adding the borrowed and swapped tokens to the position as liquidity. Leftover tokens after the operation can be sent to a specified recipient.

  Parameters include details about the position to leverage, borrow amounts, swap details for converting borrowed tokens into position tokens, and slippage parameters for adding liquidity.

#### Leverage Down Functionality

- **leverageDown(LeverageDownParams calldata params):** This function decreases the leverage of a specified Uniswap V3 position. It involves removing liquidity from the position, optionally collecting fees, swapping a portion of the position tokens for the borrowed token (if different from the position tokens), and then using the proceeds to repay the borrowed amount. Any leftover tokens after deleveraging can be sent to a specified recipient.

  Parameters detail the position to deleverage, the amount of liquidity to remove, swap details for converting position tokens back into the borrowed token, and slippage parameters for the swaps.

#### Shared Mechanisms

- Both leverage and deleverage functionalities utilize swaps to convert between the borrowed token and the position tokens. These swaps can be executed via the 0x protocol or another specified router, as detailed in the swap parameters of each function call.

- The contract inherits from `Swapper`, utilizing its functionalities for executing token swaps and managing allowances for token transfers.

- **Constructor:** Initializes the contract with references to the Nonfungible Position Manager (for interacting with Uniswap V3 positions), a 0x protocol router address, and a universal router address for swaps.

#### Safety and Access Control

- These functions are intended to be called by authorized entities only, typically through a controlled mechanism like a vault contract that integrates with the `LeverageTransformer`. The contract itself does not include explicit access control checks for these functions, relying instead on the calling context (e.g., a vault) to enforce authorization.

#### Usage Scenario

The `LeverageTransformer` contract is designed to be used in sophisticated DeFi strategies that involve leveraging liquidity positions for increased exposure or deleveraging them to reduce risk or repay debt. These operations can be crucial components of yield farming strategies, automated trading systems, or portfolio management tools that seek to optimize returns or manage risk dynamically.

### Summary

The `LeverageTransformer` smart contract provides advanced functionality for dynamically adjusting the leverage of Uniswap V3 positions, allowing users to either increase their exposure through borrowing or decrease it by repaying borrowed funds. It leverages the inherited `Swapper` functionalities for executing necessary token swaps and manages the complex interactions involved in adjusting position leverage within a single transaction.
[![f8-seq.jpg](https://i.postimg.cc/qqrxWmf6/f8-seq.jpg)](https://postimg.cc/XG25CkYn)
### V3Utils Smart Contract Overview
[![f9-uml.jpg](https://i.postimg.cc/BbD7W8wt/f9-uml.jpg)](https://postimg.cc/bSy9kvPj)
The `V3Utils` contract is a utility contract for Uniswap V3 positions. It incorporates various functionalities, such as swapping tokens, minting new positions, and adjusting liquidity, all without holding any state or ownership of assets. This contract operates on the principle of executing instructions sent along with Uniswap V3 NFTs (Non-Fungible Tokens) through ERC721 transactions.

#### Constructor

- Initializes the contract by setting up the Nonfungible Position Manager, 0x Exchange Proxy for swaps, a universal router for additional swapping capabilities, and the Permit2 contract for managing permits.

#### Core Functionalities

1. **Compound Fees, Change Range, Withdraw & Collect & Swap:**
   - These functionalities are determined by the `WhatToDo` enumeration within the `Instructions` structure, allowing for a variety of actions to be performed on Uniswap V3 positions based on the instruction provided.
   
2. **executeWithPermit:**
   - This function allows executing instructions with an EIP712 permit, allowing operations on a Uniswap V3 position without the need for an explicit ERC721 transfer. It's useful for operations that require permission, like compounding fees or changing the position's range.

3. **execute:**
   - Executes the specified instructions on a Uniswap V3 position token. The operations could include changing the range of the position, compounding fees back into the position, or performing a swap followed by liquidity adjustment. The specific action is dictated by the `whatToDo` parameter within the instructions.

4. **onERC721Received:**
   - This function is called when the contract receives an ERC721 token. It decodes the data parameter to extract instructions for operation on the received Uniswap V3 position token and executes those instructions.

5. **swap:**
   - Performs a token swap operation based on the given parameters, such as the tokens to swap, amounts, and the recipient for any leftover tokens. This function can handle both ERC20 tokens and ETH (wrapped as WETH).

6. **swapAndMint:**
   - Executes one or two swap operations to adjust token balances as specified, then uses these tokens to mint a new Uniswap V3 position with specified parameters. Leftover tokens are returned to the specified recipient.

7. **swapAndIncreaseLiquidity:**
   - Similar to `swapAndMint`, this function performs swaps as needed and uses the resulting tokens to increase the liquidity of an existing Uniswap V3 position. Leftover tokens are returned to the specified recipient.

#### Helper Functions

- Several internal helper functions facilitate operations such as token swaps (`_routerSwap`), liquidity adjustments (`_decreaseLiquidity`, `_collectFees`), and permission management for token operations (`_prepareAddApproved`, `_prepareAddPermit2`). These functions ensure that the contract can perform complex operations on Uniswap V3 positions efficiently and securely.

#### Safety Features

- The contract includes safety checks and permission management to ensure that operations are authorized and that token transfers are performed securely. It also manages WETH wrapping and unwrapping for operations involving ETH.

#### Summary

`V3Utils` is a versatile and ownerless contract designed to interact with Uniswap V3 positions, offering a wide range of functionalities from swapping tokens to adjusting liquidity and managing position ranges. It leverages the capabilities of the Uniswap V3 ecosystem, the Permit2 system for permission management, and the 0x protocol for efficient token swaps, all while maintaining a stateless design that doesn't hold assets or permissions, ensuring security and flexibility in operations.
[![f9-seq.jpg](https://i.postimg.cc/cH8GHLbG/f9-seq.jpg)](https://postimg.cc/k69pYqCT)
### FlashloanLiquidator Smart Contract Overview
[![f10-uml.jpg](https://i.postimg.cc/yxsKbzLq/f10-uml.jpg)](https://postimg.cc/YGnTvTc8)
#### Purpose
The `FlashloanLiquidator` contract utilizes Uniswap V3's Flashloan functionality to perform atomic liquidation of positions and necessary token swaps.

#### Key Components

1. **Constructor:**
   - Initializes the contract with the Non-fungible Position Manager, 0x Exchange Proxy, and a Universal Router addresses.

2. **Structs:**
   - **FlashCallbackData:** Holds all necessary data for executing the flashloan callback, including information about the token to liquidate, debt shares, liquidation cost, vault details, assets involved, swap parameters, liquidator's address, and the minimum reward expected from the operation.
   - **LiquidateParams:** Contains parameters required to initiate a liquidation process, including the tokenId of the position to be liquidated, debt shares, vault address, flash loan pool, amounts for swaps, swap data for both tokens involved, and minimum reward requirement.

3. **Functions:**

   - **liquidate:** Initiates the liquidation process by taking a flashloan from a specified Uniswap V3 pool. It encodes all necessary data for the flashloan callback and executes the flashloan.

   - **uniswapV3FlashCallback:** A callback function that is automatically invoked by the Uniswap V3 pool after providing the flashloan. It performs the liquidation by approving the asset transfer to the vault, executing the liquidation on the vault, and then handling the token swaps as per the given parameters. After completing these operations, it ensures the flashloan, along with the associated fee, is repaid to the pool. Finally, it returns any leftover tokens to the liquidator.

4. **Security and Logic Checks:**
   - Ensures that only positions eligible for liquidation are processed.
   - Guarantees that the liquidation cost and minimum reward expectations are met.
   - Handles token approvals and transfers securely, clearing approvals post-liquidation to prevent unauthorized access.
   - Ensures that the contract doesn't hold any funds at the end by transferring all leftover assets to the liquidator.

5. **Error Handling:**
   - Includes custom error messages for various failure scenarios such as "NotLiquidatable", "NotEnoughReward", and more, providing clarity on the cause of failures.

#### Summary
The `FlashloanLiquidator` contract leverages Uniswap V3 flashloans to facilitate atomic liquidation of undercollateralized loans. It performs the necessary swaps to cover the liquidation cost and repay the flashloan, ensuring that the operation is profitable by checking against a minimum reward threshold. The contract operates transparently, returning all excess funds to the initiating liquidator, thereby enforcing a secure and efficient liquidation process.
[![f10-seq.jpg](https://i.postimg.cc/Nf0q9DVx/f10-seq.jpg)](https://postimg.cc/F1wnwyhf)
### Swapper Smart Contract Overview
[![f11-uml.jpg](https://i.postimg.cc/3xCgsj8P/f11-uml.jpg)](https://postimg.cc/QFC95TWb)
#### Introduction
The `Swapper` contract provides a foundational layer for executing swaps across various platforms, including direct swaps on Uniswap V3 pools and via external routers such as 0x and Uniswap's Universal Router. It's designed to be extended by other contracts that require swap functionalities.

#### Key Features

1. **Contract Initialization:**
   - The constructor initializes key components including the Uniswap V3 Non-fungible Position Manager, 0x Exchange Proxy, Universal Router, and the Wrapped Ether (WETH) contract addresses.

2. **Data Structures:**
   - **ZeroxRouterData:** Contains allowance target and swap data for executing swaps via the 0x Exchange Proxy.
   - **UniversalRouterData:** Encapsulates commands, inputs, and a deadline for performing swaps via the Uniswap Universal Router.
   - **RouterSwapParams:** Holds parameters for a generic swap, including input/output tokens, amounts, and swap data.

3. **Functionality:**
   - **_routerSwap():** Executes a swap using either the 0x Exchange Proxy or the Uniswap Universal Router, based on off-chain calculated instructions. It ensures that the minimum output amount is met and returns the actual input and output amounts.
   - **_poolSwap():** Directly executes a swap on a specified Uniswap V3 pool. It requires the amounts to be available on the contract and performs a slippage check with the `amountOutMin` parameter.
   - **uniswapV3SwapCallback():** A callback function required by Uniswap V3 for flash swaps. It validates the call's origin and transfers the necessary amount of input tokens to the pool to complete the swap.

4. **Event:**
   - **Swap:** Emitted after a successful swap, detailing the tokens involved, the amount in, and the amount out.

5. **Utilities and Helpers:**
   - Provides mechanisms to easily integrate swaps into broader contract functionalities, supporting a range of use cases from flash loans to complex trading strategies.
   - Includes error handling through custom errors (like `SwapFailed`, `SlippageError`, etc.) and OpenZeppelin's SafeERC20 library for secure token transfers.

#### Summary
The `Swapper` contract acts as a versatile backbone for implementing swap operations within DeFi protocols. It abstracts away the complexities of interacting with different swapping mechanisms, offering a unified and secure interface for swaps. By leveraging Uniswap V3's capabilities and integrating with external protocols like 0x, it facilitates a wide array of trading and liquidity strategies.
[![f11-seq.jpg](https://i.postimg.cc/vTFLLzLT/f11-seq.jpg)](https://postimg.cc/wy2m9DrY)
### Risk Assessment

#### Centralization Risks

1. **Contract Dependencies:**
   - The system relies on external contracts and services (Uniswap V3, 0x Exchange, WETH, etc.), which introduces dependency on their security, longevity, and governance models. Changes or failures in these dependencies could impact the Swapper's functionalities.

2. **Operator Privileges:**
   - Certain operations, particularly those involving external routers or swaps, may require permissions or approvals. If these privileges are centralized (e.g., a single account or contract with the authority to approve swaps or update critical contract addresses), it poses a risk of misuse or single points of failure.

#### Systematic Risks

1. **Market Volatility:**
   - Swaps, by their nature, are exposed to market conditions. Sudden volatility can lead to significant slippage, impacting the effectiveness of trades. While `amountOutMin` checks attempt to mitigate this, extreme market conditions can still pose risks.

2. **Liquidity Constraints:**
   - Operations depend on the liquidity available in pools on Uniswap V3 and other platforms. Insufficient liquidity or large trades can lead to unfavorable swap rates, impacting the contract's ability to execute swaps efficiently.

#### Architectural Risks

1. **Integration Complexity:**
   - The contract integrates with multiple protocols, each with its own interface and behavior (e.g., Uniswap V3's callback mechanism). This complexity can introduce bugs or inefficiencies, especially when protocols update or change their interfaces.

2. **Flash Loan Attacks:**
   - The use of Uniswap V3's flash swap functionality introduces risks of flash loan attacks if not properly managed. These attacks can manipulate market prices or exploit contract vulnerabilities within a single transaction.

#### Complexity Risks

1. **Upgradeability and Interoperability:**
   - The contract's design to work with various protocols increases its complexity. Ensuring compatibility and managing upgrades in a multi-contract system can introduce risks, especially if one part of the system is updated or contains vulnerabilities.

2. **Error Handling:**
   - The reliance on external calls (to Uniswap, 0x, etc.) and complex operations (like flash swaps) necessitates robust error handling and validation. Inadequate checks can lead to unexpected behaviors, such as failed swaps or loss of funds.

In summary, while the Swapper contract provides a versatile tool for executing swaps across multiple platforms, it is subject to risks stemming from its dependencies on external contracts, market conditions, the complexity of its integrations, and the need for careful management of permissions and error handling. Mitigating these risks requires thorough testing, monitoring of integrated protocols, and potentially introducing mechanisms for upgradeability and decentralization of control.

### System Conclusion

The Revert Lend system introduces a comprehensive decentralized lending protocol leveraging Uniswap v3 LP positions for collateral, underscored by a suite of smart contracts that facilitate a range of operations from asset management to automated strategies and risk mitigation. Its architecture combines innovation in liquidity provision with flexibility, allowing users to maximize their capital efficiency while ensuring security and adaptability. Through its integration with Uniswap v3 and the use of advanced features like flash loans and automated position management, Revert Lend sets a new benchmark for DeFi lending protocols, aiming to enhance liquidity utilization and user empowerment in the evolving landscape of decentralized finance.

### Time spent:
40 hours