# Analysis Report for **Revert Lend**

![Alttext](https://private-user-images.githubusercontent.com/107410002/312376875-14644b24-7de5-4c41-bec8-60035e3d90d0.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTA1MTY1MDAsIm5iZiI6MTcxMDUxNjIwMCwicGF0aCI6Ii8xMDc0MTAwMDIvMzEyMzc2ODc1LTE0NjQ0YjI0LTdkZTUtNGM0MS1iZWM4LTYwMDM1ZTNkOTBkMC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMzE1JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDMxNVQxNTIzMjBaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0yZDAzYzM2YTZlODIwZmY1MmM0ODAzOTgxZjg3ZmIzNzYxMGY1MGVjMWZhNmFjNDFjN2RhMjk3MGU2MmViMzA4JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.rPebsdpjnks6fJd-oxpkcz44GjJzWF182ycKaWUtolI)

## Table of Contents

- [Approach](#approach)
- [Brief Overview](#brief-overview)
- [Scope and Architecture Overview](#scope-and-architecture-overview)
  - [Automators](#automators)
  - [Transformers](#Transformers)
  - [Utils](#Utils)
  - [Src](#Src)
- [Centralization Risks](#centralization-risks)
- [Systemic Risks](#systemic-risks)
- [Recommendations](#recommendations)
- [Security Researcher Logistics](#security-researcher-logistics)
- [Conclusion](#conclusion)
- [Resources](#resources)

## Approach

Started with a comprehensive analysis of the provided docs and whitepaper to understand protocol functionality and key points, ambiguities were discussed with the sponsors(devs), and possible risk areas were outlined.

Followed by a manual review of each contract in scope, testing function behavior, protocol logic against expectations, and working out potential attack vectors. Vulnerabilities related to dependencies and inheritances, were also assessed. Comparisons with similar protocols was also performed to identify recurring issues and evaluate fix effectiveness.

Finally, identified issues from the security review were compiled into a comprehensive audit report.

## Brief Overview

Revert Lend stands as a peer-to-pool lending platform, tailor-made for AMM Liquidity Providers , specifically within the Uniswap v3 ecosystem. It introduces an opportunity for users to secure ERC-20 token loans by using their Uniswap v3 liquidity provider positions as collateral. What seems to set this protocol apart is its capacity to allow Liquidity Providers to keep managing their capital actively within the Uniswap v3 pools, even while it serves as collateral. This functionality ensures that Liquidity Providers can continuously optimize and manage their positions to adapt to the fluctuating demands of the market, providing an uninterrupted liquidity provision experience.

## Scope and Architecture Overview

### **Automators**

---

### [Automator.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol)

This contract enables the automatic reinvestment of fees into liquidity positions with potential for swaps to optimize token ratios, all within a single transaction. Controlled by a Revert bot operator and capable of direct and vault-based position transformations, this contract keeps track of compounding actions, configuration adjustments, and token balance changes, providing a comprehensive tool for liquidity management. The system also facilitates the management of rewards and leftover balances, ensuring a seamless process for liquidity providers to maximize their yield through strategic reinvestment and position optimization.

#### Configuration and Management

- **Operators and Vaults**: It allows the contract owner to designate specific addresses as operators or vaults, enabling them to execute certain privileged actions within the contract's ecosystem.

- **Withdrawer**: A specific address that's authorized to withdraw accumulated fees or tokens from the contract. This role is typically reserved for the contract owner or a trusted entity.

- **TWAP Configuration**: The contract owner can set parameters related to Time Weighted Average Price (TWAP) calculations, including the observation period (`TWAPSeconds`) and the maximum allowable tick difference (`maxTWAPTickDifference`) to mitigate price manipulation risks.

#### TWAP Validation

- **Swap Validation**: Before performing swaps, the contract validates them against current market conditions and configured TWAP parameters to ensure they're executed within acceptable price ranges and slippage limits.

- **TWAP Calculation**: Utilizes Uniswap V3's `observe` function to calculate TWAP over a specified period, assisting in price verification and ensuring swaps don't deviate significantly from the market price.

#### Liquidity Management

- **Decrease Liquidity and Collect**: Allows for reducing a position's liquidity in a Uniswap V3 pool and collecting accrued fees. This operation can be crucial for automated strategies that adjust position sizes in response to market conditions.

#### Token and ETH Withdrawals

- **Balance Withdrawals**: The contract supports withdrawing ERC20 token balances and ETH, facilitating the management of accrued fees or rebalancing of assets.

- **WETH Handling**: Includes mechanisms for wrapping and unwrapping WETH (Wrapped ETH), allowing the contract to seamlessly handle ETH in operations requiring ERC20 tokens.

#### Access Control and Security

- **Operator and Vault Checks**: Enforces checks to ensure that only authorized operators can perform certain actions and that interactions with vaults are restricted to approved contracts.

- **Ownership Validation**: For operations involving Uniswap V3 positions or vault-held assets, the contract verifies that the caller owns the relevant NFT or vault asset.

#### Event Logging

- Logs significant administrative actions, such as changes to the operator list, vault list, withdrawer address, and TWAP configuration, aiding in transparency and auditability.

#### Error Handling

- Implements custom error messages for unauthorized access, invalid configurations, and operational failures, enhancing contract usability and debuggability.

#### Eth Handling

- **Receive Function**: Includes a fallback `receive` function to handle ETH, specifically for unwrapping WETH, ensuring that the contract can accept ETH refunds or payments as needed.

---

### [AutoExit.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol)

This contract introduces an innovative approach to managing Uniswap V3 positions, enabling automatic execution of limit or stop-loss orders based on specific market conditions. This functionality allows liquidity providers to either remove their liquidity position or swap it to the opposite token when the market reaches a predetermined tick, effectively serving as an automated risk management tool. Operated by a Revert controlled bot, the contract utilizes external swap routers to ensure optimized swap execution. Position owners must approve the AutoExit contract to manage their positions, which can be configured for automatic execution using the contract's `configToken` method. Once a position reaches its trigger tick, the operator can execute the pre-configured action, with the event details broadcasted for transparency.

#### Constructor

- Initializes the contract by setting up necessary parameters such as the Nonfungible Position Manager, operator, withdrawer, TWAP seconds, TWAP tick difference, and routers for external swaps.

#### Event Logging

- **`Executed`**: Logs when a position is executed, including details about the execution such as whether it was a swap or removal, the amounts returned, and the tokens involved.
- **`PositionConfigured`**: Logs the configuration of a position, detailing the active status, swap behavior, trigger ticks, slippage settings, and reward parameters.

#### Position Configuration

- **`PositionConfig` struct**: Defines the configuration for each position, including whether it's active, swap behaviors, trigger ticks for execution, slippage tolerances, whether only fees should be used for rewards, and the maximum reward percentage.
- **`configToken`**: Allows the owner of a Uniswap V3 position to configure how their position should be managed by the contract, including setting up the conditions for automated exit strategies.

#### Execution

- **`ExecuteParams` struct**: Contains parameters required for executing a position's configured strategy, including swap details, liquidity information, minimum amounts for removal, deadline, and reward percentage.
- **`execute`**: Can be called by an authorized operator to execute a position's exit strategy based on its configuration. It validates the position's state, performs necessary swaps or liquidity removal, applies configured rewards, and transfers the resulting assets back to the position owner. It also deactivates the position's configuration to prevent re-entrancy or duplication of execution.
  - The function performs checks to ensure it's only called when the market conditions meet the predefined triggers (ticks) and validates the swap against the current pool price and configured slippage.
  - It manages reward calculation based on whether the strategy involves swapping and whether only fees are considered for rewards.

#### Access Control and Security

- Enforces that only the position owner can configure a token and that only authorized operators can execute configured strategies, ensuring that positions are managed according to their owners' intentions and protected against unauthorized access.

#### TWAP Validation and Liquidity Management

- Inherits functionalities from the `Automator` contract for validating swaps against TWAP settings and managing liquidity in Uniswap V3 pools, ensuring that exit strategies are executed in line with market conditions and within acceptable price ranges.

---

### **Transformers**

---

### [LeverageTransformer.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol)

This contract provides functionalities for directly leveraging or deleveraging positions within a single transaction in the vault system, specifically it allows users to increase their position's leverage by borrowing a specified amount, swapping borrowed tokens to desired assets, and then adding those assets to their Uniswap V3 position. Conversely, it supports the reduction of leverage by removing liquidity from the position, optionally swapping assets back to the loan token, and repaying the borrowed amount.

#### Constructor

- Initializes the contract with references to the Nonfungible Position Manager and routers for swaps, enabling the leveraging functionalities.

#### Leverage Up

- **`leverageUp` Method**: Allows increasing the leverage of a Uniswap V3 position by borrowing additional assets (either token0 or token1 of the Uniswap V3 position), optionally swapping a portion of the borrowed asset to another, and adding both assets back as liquidity to the position.
  - Parameters include details about the amount to borrow, swap specifics (amounts in, minimum amounts out, swap data for 0x API calls), liquidity addition tolerances, and the recipient for any leftover tokens after adding liquidity.
  - This method calls external swap functionalities (through inherited `Swapper` functionalities) to execute any necessary swaps and interacts with a vault contract to manage the borrowing of assets.

#### Leverage Down

- **`leverageDown` Method**: Facilitates decreasing the leverage of a position by removing liquidity, optionally swapping some of the removed assets back to the borrowed asset type, and repaying the borrowed amount to the vault.
  - Parameters include the specifics of the liquidity to remove, swap details for converting assets back to the borrowed asset, minimum amounts expected from swaps, and the address to send any leftover tokens.
  - Similar to `leverageUp`, it uses the `Swapper` functionalities for executing swaps and interacts with a vault contract for the repayment of the borrowed assets.

#### Swap Integration

- Both leverage up and down functionalities rely on the `Swapper` contract's swap mechanisms to execute asset conversions through predefined swap routes, allowing for efficient market operations based on live swap data.

#### Vault Interaction

- Interacts with a vault contract (referenced as `IVault`) for borrowing and repaying assets. This integration allows the contract to leverage or deleverage positions based on external conditions and configurations.

#### Use Cases

- **Leverage Up**: Users can increase their exposure to price movements of a Uniswap V3 pool's underlying assets without adding more of their own capital, potentially amplifying returns (and risks).
- **Leverage Down**: Users can reduce their exposure to minimize risk or lock in profits without completely exiting their positions, providing flexibility in managing their investments.

#### Security Considerations

- The contract expects certain operations like borrowing and repaying to be executed through a trusted vault contract, which should implement adequate security measures to manage these financial operations safely.
- It includes checks to ensure swaps meet minimum output requirements and deadlines, protecting users from slippage and front-running.

---

### [AutoRange.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol)

This contract facilitates the automatic adjustment of Uniswap V3 positions' ranges via a controlled bot, aiming to optimize liquidity positions based on market movements. This contract enables operators to reconfigure the range of approved positions to maintain optimal placement within the Uniswap V3 pool. When a position is adjusted, a new position is created with settings mirroring the original, and the configuration is transferred to this new position. For positions housed within a Vault, the contract invokes a transform call to execute the range adjustment. Key features here include leveraging Uniswap's flash loans for liquidity adjustments and managing position configurations through struct mappings, ensuring operational flexibility and efficiency in liquidity management strategies.

#### Event Logging

- **`RangeChanged`**: Logs when a position's range has been successfully changed, capturing both the old and new token IDs.
- **`PositionConfigured`**: Logs the configuration of a position with details on tick limits, tick deltas for range adjustment, slippage parameters, and reward settings.

#### Constructor

- Initializes with references to Nonfungible Position Manager, operator, withdrawer, TWAP settings, routers, and additional configuration parameters for automated operations.

#### Position Configuration

- **`PositionConfig` Struct**: Holds configuration details for range adjustment of a position, including tick limits for triggering adjustments, tick deltas for new range boundaries, slippage tolerances for swaps, and reward calculation parameters.
- **`configToken` Function**: Allows users or designated vaults to configure how a position should automatically adjust its range based on the specified parameters.

#### Automated Range Adjustment

- **`executeWithVault` and `execute` Functions**: Executed by the designated operator, these functions adjust the range of a configured position when market conditions meet predefined triggers. The adjustment process can include swapping tokens to optimize position composition before adjusting the range.
  - When a position's range is adjusted, a new position is minted with the adjusted range, and the original position's configuration is transferred to the new position. If the position is held within a vault, the `transform` method is called to execute the range adjustment.
  - The process ensures that positions remain aligned with market conditions, potentially improving the position's profitability or reducing risk.

#### Swap Integration

- Utilizes the inherited `Swapper` functionalities to execute necessary swaps as part of the range adjustment process. This allows for efficient market operations and ensures that positions are adjusted with optimal asset composition.

#### Vault Interaction

- Supports interaction with vault contracts for positions held within vaults. This feature allows for seamless range adjustments of positions managed by vaults, extending the contract's utility to more complex DeFi strategies.

#### Security and Access Control

- Enforces strict access control, allowing only authorized operators or vaults to execute range adjustments. This prevents unauthorized modifications of positions and ensures that adjustments are made in the best interest of the position holders.

#### Reward Mechanism

- Incorporates a reward mechanism for the operator, calculated based on the configured parameters, incentivizing the maintenance and adjustment of positions to optimize performance.

---

### [AutoCompound.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol)

This contract enables automatic reinvestment of fees into liquidity positions with potential for swaps to optimize token ratios, all within a single transaction. Controlled by a Revert bot operator and capable of direct and vault-based position transformations, this contract integrates with Uniswap's INonfungiblePositionManager, supporting multicall for batch operations and safeguarded by a reentrancy guard. It keeps track of compounding actions, configuration adjustments, and token balance changes, providing a comprehensive tool for liquidity management. The system also facilitates the management of rewards and leftover balances, ensuring a seamless process for liquidity providers to maximize their yield through strategic reinvestment and position optimization.

#### Constructor

- Sets up the contract with necessary configurations, including references to the Nonfungible Position Manager and specified TWAP settings for swap validation.

#### Event Logging

- **`AutoCompounded`**: Logs details of the compounding action, including amounts added to the position, rewards generated, and tokens involved.
- **`RewardUpdated`**: Logs changes to the reward configuration initiated by the contract owner.
- **`BalanceAdded` / `BalanceRemoved` / `BalanceWithdrawn`**: Logs the management of token balances associated with positions, whether adding to the balance, removing from it, or withdrawing it to a specific address.

#### Position Balances Management

- Maintains a mapping of position token balances (`positionBalances`) to track the accumulated fees and rewards for each position. This allows for precise management of resources when compounding positions.

#### Compounding Functionality

- **`executeWithVault` / `execute` Functions**: Allow for the compounding of positions either directly or through a vault. These functions facilitate the collection of fees, optional swapping of tokens for optimal position alignment, and the addition of liquidity to the Uniswap V3 position.
  - Compounding can include fee collection, token swaps based on market conditions (validated through TWAP to prevent manipulation), and the reinvestment of tokens back into the position to increase its size.
  - The process is designed to optimize the position's value over time by reinvesting earnings and adjusting its composition according to predefined strategies.

#### Reward Mechanism

- Implements a reward mechanism to incentivize the operator's actions, with rewards calculated as a percentage of the fees generated from compounding actions. The total allowable reward percentage (`totalRewardX64`) is configurable by the contract owner, subject to a maximum limit.

#### Security and Access Control

- Includes non-reentrancy guards to prevent potential security vulnerabilities during execution of compounding actions.
- Enforces access control, allowing only authorized operators or vaults to initiate compounding actions, ensuring that positions are managed securely and according to their owners' preferences.

#### Withdrawal Functions

- **`withdrawLeftoverBalances`**: Enables position owners to withdraw any leftover tokens after compounding actions have been executed.
- **`withdrawBalances`**: Allows the contract's designated withdrawer to remove accumulated protocol fees from the contract.

#### Reward Configuration

- **`setReward`**: Allows the contract owner to adjust the reward percentage allocated to the protocol from compounding actions, providing flexibility in managing incentives for operators.

#### Utility Functions

- **`_checkApprovals`**: Ensures that the contract has the necessary approvals to manage the position's tokens, optimizing gas costs by setting max allowances where needed.

---

### [V3Utils.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol)

This contract provides a suite of utility functions to interact with Uniswap V3 positions, including complex operations like swap, mint, and liquidity management, without holding any ERC20 or NFT assets itself. It extends the Swapper contract for executing swaps and integrates with the Permit2 system for EIP-712 style token spending permissions. Key functionalities include executing pre-defined instructions on NFTs, such as changing liquidity ranges, compounding fees into liquidity, or withdrawing and swapping tokens, all within atomic transactions. It supports direct execution with or without EIP712 permits and leverages flash loans for liquidations. The contract operates in a completely ownerless and stateless manner, emphasizing flexibility and upgradability for Uniswap V3 position management.

#### Constructor

- Sets up essential components like the Nonfungible Position Manager, swap routers, and the Permit2 contract for permit-based operations.

#### Operations

- **Execute with Permit**: Allows operations on Uniswap V3 positions using EIP712 permits, facilitating actions without requiring upfront token approvals.
- **Execute**: Executes configured instructions on Uniswap V3 positions, supporting a range of operations including changing ranges, compounding fees, and withdrawing or collecting fees followed by swaps.
- **Swap**: Facilitates direct token swaps with slippage control, optionally handling wrapped ETH conversions.
- **Swap and Mint**: Performs token swaps (if necessary) and uses the output tokens to mint a new Uniswap V3 position, applying to both specified tokens and other tokens if configured.
- **Swap and Increase Liquidity**: Allows for token swaps and the addition of liquidity to an existing Uniswap V3 position, optimizing position value.
- Each operation can handle WETH wrapping/unwrapping if specified, accommodating strategies involving ETH.

#### Integration and Extensions

- Inherits `Swapper` for its swap capabilities, allowing efficient market operations and liquidity management.
- Implements `IERC721Receiver` to handle NFTs safely, facilitating operations on Uniswap V3 positions directly through transfers.
- Utilizes OpenZeppelin's `ReentrancyGuard` to prevent reentrancy attacks, ensuring the security of transactions.

#### Events

- Various events (`CompoundFees`, `ChangeRange`, `WithdrawAndCollectAndSwap`, etc.) are emitted to log significant actions performed on Uniswap V3 positions, aiding in transparency and traceability.

#### Flexibility and Security

- The contract offers high flexibility for Uniswap V3 position management, allowing users to configure detailed actions based on market conditions or strategic needs.
- Implements checks to ensure operations are authorized and secure, including validations for permits and NFT ownership.
- Designed to be ownerless and stateless, the contract focuses purely on executing operations without managing state, reducing the risk profile associated with holding assets.

#### Utility and Efficiency

- Through the use of permit signatures and direct NFT transfers, `V3Utils` minimizes the need for multiple transactions and approvals, streamlining operations for Uniswap V3 liquidity providers.
- Offers a platform for advanced strategies like automatic range adjustments or fee compounding, enhancing liquidity provision strategies on Uniswap V3.

---

### **Utils**

### [Swapper.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol)

Contract is designed to facilitate token swaps utilizing various decentralized exchange (DEX) protocols, including Uniswap V3 and 0x Exchange. It acts as an intermediary to execute trades with external routing based on pre-calculated swap instructions, ensuring slippage control through a minimum output amount parameter. Key features include integration with Uniswap V3's non-fungible position manager for liquidity management, support for WETH transactions, and the ability to interact with a universal router for executing complex trade strategies. The contract emits events for each swap, providing transparency over trade details such as input and output token addresses and amounts.
r

#### Swap Execution

- **Router Swap (`_routerSwap`)**: Facilitates token swaps using external routing protocols, employing off-chain calculated instructions. It involves slippage checks to ensure the minimum amount of output tokens (`amountOutMin`) is received. It supports integration with multiple routers like 0x Exchange Proxy and Uniswap's Universal Router.

- **Direct Pool Swap (`_poolSwap`)**: Executes swaps directly within a specified Uniswap V3 pool. It requires the contract to have available amounts of both participating tokens. Similar to router swaps, it includes slippage control to ensure the output meets a predefined minimum.

#### Swap Callback

- **Uniswap V3 Callback (`uniswapV3SwapCallback`)**: Required for participating in Uniswap V3 swaps, this callback function facilitates the transfer of the necessary input tokens to the Uniswap pool after a swap is initiated but before it's completed.

#### Swap Data Structures

- **ZeroxRouterData**: Contains information specific to executing swaps via the 0x Exchange Proxy, including the target address for token allowance and the data payload for the swap.
- **UniversalRouterData**: Designed for the Uniswap Universal Router, detailing commands and inputs for the swap, alongside a deadline for execution.

#### Support for Diverse DeFi Protocols

- Integrates with key components of the Uniswap V3 ecosystem, including the Non-Fungible Position Manager for managing liquidity positions and the WETH9 contract for handling wrapped ETH transactions.
- The contract is designed to be flexible, allowing for the addition of other protocols and routing mechanisms through external routers.

#### Event Logging

- **Swap Event**: Emits details of each swap transaction, including the input and output tokens, and the amounts involved. This aids in transparency and tracking of swap operations.

#### Error Handling and Security

- Extends a custom `IErrors` interface for consistent error management across various operations, enhancing the contract's robustness and ease of debugging.

---

### [FlashloanLiquidator.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol)

Contract builds on swapper's functionality and utilizing Uniswap V3's flash loans, enables atomic liquidation of loans alongside necessary token swaps. It integrates with V3 vault system to perform loan liquidations by acquiring assets through Uniswap V3 flash loans, swapping assets if necessary to meet liquidation requirements, and ensuring a minimum reward for the liquidator. This process is done within the `liquidate` function that orchestrates the flash loan, asset swaps, and loan liquidation in a single transaction. Upon completion, the contract settles the flash loan, returns any excess assets to the liquidator, and verifies that the liquidator's minimum reward condition is met, enhancing operational efficiency and security in liquidation scenarios.

The `FlashloanLiquidator` contract extends the `Swapper` contract to perform atomic liquidations of loans using Uniswap V3's flash loans. Here are its key functionalities:

#### Flash Loan Initiation for Liquidation

- **Liquidate Function**: Initiates the liquidation process for a specified loan. It first checks if the loan is eligible for liquidation by ensuring the liquidation cost is non-zero. It then determines the correct asset to flash borrow (based on the vault's asset) and initiates a flash loan from a Uniswap V3 pool to cover the liquidation cost.

#### Handling the Flash Loan Callback

- **Uniswap V3 Flash Callback**: Implements the `uniswapV3FlashCallback` function required for handling flash loans. This function is automatically called by the Uniswap V3 pool after issuing a flash loan. Within this callback, the contract:
  - Approves the vault to access the required asset amount for liquidation.
  - Calls the vault's `liquidate` function to perform the actual loan liquidation.
  - Executes necessary swaps via `_routerSwap` to convert any borrowed assets not in the form of the liquidation asset back into the liquidation asset.
  - Returns the borrowed amount plus fees back to the Uniswap pool.
  - Ensures that the operation yields at least the minimum required reward for the liquidator, failing which, the transaction is reverted.

#### Swap Execution

Leverages inherited functionalities from the `Swapper` contract to perform token swaps. This is utilized within the flash loan callback to manage assets post-liquidation:

- **Swaps for Asset Conversion**: After liquidation, if the received tokens are not in the desired asset form, the contract swaps these tokens back to the required asset using previously defined `_routerSwap` functionality.

#### Reward Distribution

- **Returning Leftover Tokens and Reward**: After fulfilling the flash loan and swap operations, any leftover tokens, including the liquidation reward, are transferred back to the liquidator. This includes:
  - Returning any remaining tokens that were swapped but not needed to repay the flash loan or exceed the liquidation cost.
  - Ensuring the liquidator receives a reward at least equal to the `minReward` specified, with the contract reverting if this condition is not met.

#### Error Handling and Security

- Inherits custom error handling from the `IErrors` interface and `Swapper` contract to manage operation-specific errors, such as swap failures or insufficient rewards from liquidation.

#### Constructor and State Variables

- Initializes with addresses for necessary components like the Nonfungible Position Manager, 0x Router, and Universal Router, required for swap operations and interacting with the Uniswap V3 ecosystem.

### **Src**

### [InterestRateModel.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol)

This contract offers a dynamic framework for calculating interest rates within athe Vault. It extends the Ownable contract, allowing for governance over crucial parameters affecting borrow and supply rates. This model incorporates a base rate, a multiplier effect based on utilization rates, and a kink point that transitions the interest rate calculation from a linear to a potentially exponential regime, accommodating rapid changes in utilization beyond certain thresholds.

The `InterestRateModel` contract, incorporating `Ownable` from OpenZeppelin alongside interfaces `IInterestRateModel` and `IErrors`, offers a dynamic framework for calculating both borrow and supply interest rates in a Vault, specifically designed for use within decentralized finance (DeFi) protocols. Here's an outline of its core functionalities and design:

#### Key Components

- **Interest Rate Calculation**: Utilizes a model that factors in the base rate, multiplier, and jump multiplier per year, alongside a "kink" utilization rate, to calculate interest rates. This model allows for the adjustment of interest rates based on the current utilization rate of the protocol, enhancing the flexibility and economic stability of lending operations.
- **Q96 Precision**: The contract employs fixed-point arithmetic with a factor of \(2^{96}\) (`Q96`) to maintain high precision in interest rate calculations without the need for floating-point numbers, which are not natively supported in Solidity.

- **Yearly Constants**: Defines constants like `YEAR_SECS` to account for the number of seconds in a year, considering leap years, facilitating the annualization of interest rates.

- **Configurable Parameters**: Allows the contract owner to set parameters such as the base rate, multiplier, jump multiplier, and kink utilization rate per year, each scaled by `Q96` for precision. These parameters determine how interest rates adjust with the protocol's utilization rate.

#### Events

- **SetValues**: Emitted when the interest rate model's parameters are updated, providing transparency and traceability for changes in the model's configuration.

#### Modifiers and Access Control:

- **onlyOwner**: Ensures that only the contract owner can update the interest rate model's parameters, securing the protocol against unauthorized modifications.

#### Core Methods:

- **getUtilizationRateX96**: Calculates the utilization rate given the current cash and debt within the protocol, returning a value scaled by `Q96`. This rate is crucial for determining how close the protocol is to being fully utilized, which in turn influences interest rates.

- **getRatesPerSecondX96**: Given the current cash and debt, calculates the borrow and supply rates per second, each scaled by `Q96`. The calculation considers whether the current utilization rate is above or below the "kink" point, applying different multipliers accordingly to derive the final rates.

- **setValues**: Allows the contract owner to update the model's parameters, including base rate, multipliers, and the kink utilization rate, each expressed on an annual basis and scaled by `Q96`. This method provides the flexibility to adjust the interest rate model in response to changing market conditions or economic policies.

#### Design Considerations:

- The contract is designed to be highly flexible, allowing for detailed customization of the interest rate model based on empirical data or economic strategy.
- Utilizes fixed-point arithmetic for precision and to accommodate Solidity's limitations regarding floating-point arithmetic.
- Emphasizes security and controlled access through the `onlyOwner` modifier, ensuring that adjustments to the model are deliberate and authorized.

---

### [V3Oracle.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol)

This contract integrates chainlink and Uniswap v3 TWAP oracles, providing a robust mechanism for determining the value of Uniswap v3 LP positions in a specified token. It features a fallback mode for enhanced security, addressing the need for accurate and reliable price information within DeFi applications. By harnessing both Chainlink's feeds for external market prices and Uniswap v3's time-weighted average prices (TWAP), it offers flexibility in price source selection through various operational modes. These **modes** allow for verification of price consistency across oracles, reducing the risk of price manipulation. The oracle supports configuration for multiple tokens, enabling customization of price verification thresholds and update intervals to ensure data relevancy and integrity. This hybrid approach aims to balance decentralized oracle resilience.

#### Key Features:

- **Multiple Oracle Modes**: Supports different modes of price data retrieval, including direct Chainlink feeds, TWAP from Uniswap V3, and hybrid modes that verify one source against another for added security.
- **Chainlink and Uniswap V3 Integration**: Seamlessly integrates with Chainlink for reliable off-chain price feeds and Uniswap V3 for on-chain TWAPs, providing flexibility and redundancy in price sourcing.
- **Emergency Fallback Mode**: Includes provisions for an emergency mode that can be activated by a designated admin, allowing for rapid response to adverse conditions like oracle manipulation or failure.

#### Configuration and Management:

- **Dynamic Oracle Configuration**: Offers the ability to dynamically configure oracle sources and parameters for each supported token, including feed addresses, maximum feed age, decimal precision, and mode of operation.
- **Token and Pool Configurations**: Supports setting up configurations for each token, including their corresponding Chainlink feeds and reference Uniswap V3 pools, making it adaptable to various token ecosystems.
- **Emergency Admin Controls**: Allows an emergency administrator to adjust oracle modes in response to critical situations, enhancing the protocol's resilience against external shocks or manipulations.

#### Functionality Highlights:

- **Position Value Calculation**: Can calculate the total value, fee value, and individual token prices of Uniswap V3 positions in a specified token, factoring in current liquidity, fees accrued, and prevailing market prices.
- **Price Verification**: Implements checks to ensure the derived pool price from oracle data does not deviate significantly from the actual pool price, serving as a safeguard against price manipulation.

#### Events and Updatability:

- **Config Update Events**: Emits events for critical updates, including token configurations and oracle mode changes, ensuring transparency and traceability.
- **Admin Functions**: Provides functions for the contract owner to update token configurations, oracle modes, and the emergency admin, facilitating ongoing maintenance and adaptation to changing market dynamics.

#### Design Considerations:

- The contract's design prioritizes security and data integrity by incorporating mechanisms to verify oracle data and enabling emergency interventions. It also demonstrates a flexible approach to oracle selection, allowing users to choose between or combine different data sources based on reliability, timeliness, and relevance to their specific needs.

---

### [V3Vault.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol)

The V3Vault contract utilizes Uniswap V3 LP positions as collateral within a framework that strictly adheres to the IERC4626 Vault Standard. It represents a seamless representation of ERC20 shares to denote participation in the lending pool, facilitating a singular ERC20 asset for both borrowing and lending operations. The architecture is deeply integrated with the Uniswap ecosystem, leveraging its Nonfungible Position Manager for efficient liquidity management and swaps. Incorporating a dynamic interest rate model and an oracle for accurate collateral assessment, it ensures competitive rates and secure collateralization. Moreover, it empowers administrators with extensive management capabilities, including adjustable limits and configurations, to adapt to evolving market conditions.

#### Key Features:

- **Lending and Borrowing**: Users can lend ERC20 tokens to earn interest or borrow against their Uniswap V3 LP positions.
- **ERC4626 Compliance**: Implements the ERC4626 standard for tokenized vaults, making the vault's shares tradable as ERC20 tokens.
- **Dynamic Interest Rates**: Utilizes an interest rate model to dynamically adjust lending and borrowing rates based on market conditions.
- **Collateral Management**: Supports multiple tokens as collateral, each configured with a collateral factor to determine its borrowing power.
- **Liquidation Mechanism**: Allows positions to be liquidated if they become undercollateralized, ensuring the system's stability.

#### Administrative Controls:

- **Reserve and Risk Management**: Includes mechanisms for managing reserves and setting risk parameters like collateral factors and liquidation penalties.
- **Token and Pool Configuration**: Enables the configuration of supported tokens and their Uniswap V3 pools for collateral valuation.
- **Emergency Functions**: Provides emergency administrative controls to respond to adverse market conditions or system vulnerabilities.

#### Core Mechanisms:

- **Position Management**: Facilitates the creation, transformation, and management of collateralized positions using Uniswap V3 LP tokens.
- **Interest Rate Adjustment**: Periodically recalculates interest rates for both lenders and borrowers to align with market dynamics.
- **Loan Health Checks**: Evaluates the health of loans to prevent undercollateralization and initiates liquidation if necessary.

#### User Interactions:

- **Deposits and Withdrawals**: Allows users to deposit ERC20 tokens to lend to the vault or withdraw their lent assets.
- **Borrowing and Repayment**: Users can borrow against their collateralized Uniswap V3 positions and repay their loans with flexibility.
- **Collateral Adjustment**: Offers functions to manage Uniswap V3 positions used as collateral, including adding liquidity or withdrawing it as part of loan management.

#### Safety Features:

- **Collateral Factor and Limits**: Each token's borrowing power is determined by its collateral factor, and global borrowing limits prevent excessive risk exposure.
- **Reserve Management**: Maintains financial reserves to cover potential losses from loan defaults or liquidations, with parameters to ensure sufficient coverage.

## Systemic Risks

- Possible issues with the ecosystem being on an L2 since the sequencer being down would cease all timing logics to now be faulty.
- Protocol uses secondary sources of pricing data for some pricing logic, but still 100 percent depends on this data, i.e if the query to `pool.observe()` is to to fail for any reason it's going to halt the system even if Chainlink's `latestRoundData()` is the primary source for that tx and vice versa.
- External dependencies from pragma oracle, inherited contracts, etc.
- Large approvals may not work with some ERC20 tokens which would fault the logic around `_checkApprovals()` for these tokens
- Incorrect implementations of supported EIPs, not following the CEI pattern and not using local variables for emitting packed storage variables.

## Centralization Risks

- An admin could just set any value for the twap via `Automator::setTWAPConfig()` efffectively affecting the priceof the token.
- An admin could set the reserve protection value very low and financially flaw the system
- An admin could maliciously [set the management reward system](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/transformers/AutoCompound.sol#L243-L247) and lower the reward to 0, essentially breaking the rewards logic since now it can't be reset to any value whatsoever due to the `<=` check.
- An admin could still maliciously withdraw the reserves after reducing the reserved protection section of these reserves.
- An admin could maliciously use `setMaxPoolPriceDifference()` to allow for the ingestion of faulty oracle data for innocent users by placing the acceptable max difference to be very high.

## Recommendations

- Enhance documentation quality, currently the code's natspec and protocol's provided docs, do not always align, for example in the docs.
- Improve protocol's testability, one thing to note about tests is that _there's always room for further refinement and improvement._, a few out of the box ideas need to also be attached to test cases, for example `V3Oracle._getReferencePoolPriceX96()` will show incorrect price for negative tick deltas, whcih would've been caught if these were considered during testing.
- To support the above, even fuzz and invariant tests could be further incorporated to help secure protocol.
- There seems to be a need to improve the naming conventions in some areas of protocol to ease user/developer experience while trying to use/understand protocol, for example the `MIN_PRICE_DIFFERENCE`is not the min price difference but actually the **min max price difference**, i.e looking at t[rying to set the max price difference](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L190-L196) we can see that it's checked to not be lower than our MIN_PRICE_DIFFERENCE.
- Two step variable and address updates should be implemented including zero address checks. A timelock can also be considered for the setter functions to give users time to react to protocol changes. Adding these fixes can help protect from mistakes and unexepected behaviour.
- Onboard more developers, cause multiple eyes checking out a protocol can be invaluable. More contributors can significantly reduce potential risks and oversights. Evidence of where this could come in handy can be gleaned from codebase typos. Drawing from the [broken windows theory](https://en.wikipedia.org/wiki/Broken_windows_theory), such lapses may signify underlying code imperfections.
- Re-enhance event monitoring, current implementation subtly suggests that event tracking isn't maximized. Instances where events are missing or seem arbitrarily embedded have been observed.

## Security Researcher Logistics

My attempt on reviewing the Codebase spanned over 60 hours distributed over 9 days:

- 2 hours dedicated to writing this analysis.
- 6 hours (first day) spent exploring the whole system (docs/whitepaper) to grasp the foundations before diving into it line by line
- 2 hours were allocated for discussions with sponsors on the private discord group regarding potential vulnerabilities.
- 2 hours over the course of the 8 days _(~15 minutes per day)_ was spent lurking in the public discord group to get more ideas based on questions other security researchers ask and explanation provided by sponsors
- The remaining time was spent on finding issues and writing the report for each of them.

## Conclusion

The codebase was a very great learning experience, though it was a pretty hard nut to crack, nonetheless during my review, I uncovered a few issues within the protocol and they need to be fixed. Recommended steps should be taken to protect the protocol from potential attacks. Timely audits and codebase cleanup for mitigations should also be conducted to keep the codebase fresh and up to date with evolving security times.

## Resources

- [Documentation](https://github.com/revert-finance/lend-whitepaper/blob/main/Revert_Lend-wp.pdf)
- [Website](https://revert.finance)
- [Audit Page](https://github.com/code-423n4/2024-03-revert-lend/)
- [Previous Audit Report](https://github.com/code-423n4/2024-03-revert-lend/blob/main/audits/HYDN_-_Revert_Finance_Vault_Audit_Report.docx.pdf)


### Time spent:
60 hours