# Analysis Report for Revert Lend

![](https://private-user-images.githubusercontent.com/107410002/312376875-14644b24-7de5-4c41-bec8-60035e3d90d0.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTAzMTk4MDcsIm5iZiI6MTcxMDMxOTUwNywicGF0aCI6Ii8xMDc0MTAwMDIvMzEyMzc2ODc1LTE0NjQ0YjI0LTdkZTUtNGM0MS1iZWM4LTYwMDM1ZTNkOTBkMC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMzEzJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDMxM1QwODQ1MDdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1lMTgxNTVlODI3OGQ4OTAwMGJhMDE5ZWNlNjE2YjkxNWM1NThlOTQyYmU3NmZjYmQ3YmM3Y2Y2NGIyNjk3YzdlJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.A-Hy9Zrn96i2p0yKASQQDaBIgLpBwqCbmHfZ3fXjdWQ)

## Table of Contents

- [Approach](#approach)
- [Brief Overview](#brief-overview)
- [Scope and Architecture Overview](#scope-and-architecture-overview)
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

### Utils

- [Swapper.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol)
  Contract is designed to facilitate token swaps utilizing various decentralized exchange (DEX) protocols, including Uniswap V3 and 0x Exchange. It acts as an intermediary to execute trades with external routing based on pre-calculated swap instructions, ensuring slippage control through a minimum output amount parameter. Key features include integration with Uniswap V3's non-fungible position manager for liquidity management, support for WETH transactions, and the ability to interact with a universal router for executing complex trade strategies. The contract emits events for each swap, providing transparency over trade details such as input and output token addresses and amounts.
- [FlashloanLiquidator.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol)
  Contract builds on swapper's functionality and utilizing Uniswap V3's flash loans, enables atomic liquidation of loans alongside necessary token swaps. It integrates with V3 vault system to perform loan liquidations by acquiring assets through Uniswap V3 flash loans, swapping assets if necessary to meet liquidation requirements, and ensuring a minimum reward for the liquidator. This process is done within the `liquidate` function that orchestrates the flash loan, asset swaps, and loan liquidation in a single transaction. Upon completion, the contract settles the flash loan, returns any excess assets to the liquidator, and verifies that the liquidator's minimum reward condition is met, enhancing operational efficiency and security in liquidation scenarios.

### Automators

- [Automator.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol)
  This contract enables the automatic reinvestment of fees into liquidity positions with potential for swaps to optimize token ratios, all within a single transaction. Controlled by a Revert bot operator and capable of direct and vault-based position transformations, this contract keeps track of compounding actions, configuration adjustments, and token balance changes, providing a comprehensive tool for liquidity management. The system also facilitates the management of rewards and leftover balances, ensuring a seamless process for liquidity providers to maximize their yield through strategic reinvestment and position optimization.
- [AutoExit.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol)
  This contract introduces an innovative approach to managing Uniswap V3 positions, enabling automatic execution of limit or stop-loss orders based on specific market conditions. This functionality allows liquidity providers to either remove their liquidity position or swap it to the opposite token when the market reaches a predetermined tick, effectively serving as an automated risk management tool. Operated by a Revert controlled bot, the contract utilizes external swap routers to ensure optimized swap execution. Position owners must approve the AutoExit contract to manage their positions, which can be configured for automatic execution using the contract's `configToken` method. Once a position reaches its trigger tick, the operator can execute the pre-configured action, with the event details broadcasted for transparency.

### Transformers

- [LeverageTransformer.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/LeverageTransformer.sol)
  This contract provides functionalities for directly leveraging or deleveraging positions within a single transaction in the vault system, specifically it allows users to increase their position's leverage by borrowing a specified amount, swapping borrowed tokens to desired assets, and then adding those assets to their Uniswap V3 position. Conversely, it supports the reduction of leverage by removing liquidity from the position, optionally swapping assets back to the loan token, and repaying the borrowed amount.
- [AutoRange.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol)
  This contract facilitates the automatic adjustment of Uniswap V3 positions' ranges via a controlled bot, aiming to optimize liquidity positions based on market movements. This contract enables operators to reconfigure the range of approved positions to maintain optimal placement within the Uniswap V3 pool. When a position is adjusted, a new position is created with settings mirroring the original, and the configuration is transferred to this new position. For positions housed within a Vault, the contract invokes a transform call to execute the range adjustment. Key features here include leveraging Uniswap's flash loans for liquidity adjustments and managing position configurations through struct mappings, ensuring operational flexibility and efficiency in liquidity management strategies.
- [AutoCompound.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol)
  This contract enables automatic reinvestment of fees into liquidity positions with potential for swaps to optimize token ratios, all within a single transaction. Controlled by a Revert bot operator and capable of direct and vault-based position transformations, this contract integrates with Uniswap's INonfungiblePositionManager, supporting multicall for batch operations and safeguarded by a reentrancy guard. It keeps track of compounding actions, configuration adjustments, and token balance changes, providing a comprehensive tool for liquidity management. The system also facilitates the management of rewards and leftover balances, ensuring a seamless process for liquidity providers to maximize their yield through strategic reinvestment and position optimization.
- [V3Utils.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/V3Utils.sol)
  This contract provides a suite of utility functions to interact with Uniswap V3 positions, including complex operations like swap, mint, and liquidity management, without holding any ERC20 or NFT assets itself. It extends the Swapper contract for executing swaps and integrates with the Permit2 system for EIP-712 style token spending permissions. Key functionalities include executing pre-defined instructions on NFTs, such as changing liquidity ranges, compounding fees into liquidity, or withdrawing and swapping tokens, all within atomic transactions. It supports direct execution with or without EIP712 permits and leverages flash loans for liquidations. The contract operates in a completely ownerless and stateless manner, emphasizing flexibility and upgradability for Uniswap V3 position management.

### Src

- [InterestRateModel.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol)
  This contract offers a dynamic framework for calculating interest rates within athe Vault. It extends the Ownable contract, allowing for governance over crucial parameters affecting borrow and supply rates. This model incorporates a base rate, a multiplier effect based on utilization rates, and a kink point that transitions the interest rate calculation from a linear to a potentially exponential regime, accommodating rapid changes in utilization beyond certain thresholds.
- [V3Oracle.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol)
  This contract integrates chainlink and Uniswap v3 TWAP oracles, providing a robust mechanism for determining the value of Uniswap v3 LP positions in a specified token. It features a fallback mode for enhanced security, addressing the need for accurate and reliable price information within DeFi applications. By harnessing both Chainlink's feeds for external market prices and Uniswap v3's time-weighted average prices (TWAP), it offers flexibility in price source selection through various operational modes. These **modes** allow for verification of price consistency across oracles, reducing the risk of price manipulation. The oracle supports configuration for multiple tokens, enabling customization of price verification thresholds and update intervals to ensure data relevancy and integrity. This hybrid approach aims to balance decentralized oracle resilience.
- [V3Vault.sol](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol)
  The V3Vault contract utilizes Uniswap V3 LP positions as collateral within a framework that strictly adheres to the IERC4626 Vault Standard. It represents a seamless representation of ERC20 shares to denote participation in the lending pool, facilitating a singular ERC20 asset for both borrowing and lending operations. The architecture is deeply integrated with the Uniswap ecosystem, leveraging its Nonfungible Position Manager for efficient liquidity management and swaps. Incorporating a dynamic interest rate model and an oracle for accurate collateral assessment, it ensures competitive rates and secure collateralization. Moreover, it empowers administrators with extensive management capabilities, including adjustable limits and configurations, to adapt to evolving market conditions.

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
060 hours