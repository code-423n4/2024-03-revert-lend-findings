# Revert Lend CodeArena Review by Paul4912

Review Resources:

- [codebase](https://github.com/code-423n4/2024-03-revert-lend/tree/main)

## Table of Contents

- [Revert Lend CodeArena Review by Paul4912](#revert-lend-codearena-review-by-paul4912)
  - [Table of Contents](#table-of-contents)
  - [Review Summary](#review-summary)
  - [Scope](#scope)
  - [Critical Findings](#critical-findings)
  - [High Findings](#high-findings)
    - [1. High - Checking for collateral value limits is done even when decreasing debt shares](#1-high---checking-for-collateral-value-limits-is-done-even-when-decreasing-debt-shares)
      - [Technical Details](#technical-details)
      - [Impact](#impact)
      - [Recommendation](#recommendation)
  - [Medium Findings](#medium-findings)
  - [Low Findings](#low-findings)
    - [1. Low - No public function for converting assets to shares for debt](#1-low---no-public-function-for-converting-assets-to-shares-for-debt)
      - [Technical Details](#technical-details-1)
      - [Impact](#impact-1)
      - [Recommendation](#recommendation-1)
  - [Informational Findings](#informational-findings)
    - [1. Informational - Redundant line](#1-informational---redundant-line)
      - [Technical Details](#technical-details-2)
      - [Impact](#impact-2)
      - [Recommendation](#recommendation-2)
  - [Gas Optimisation Findings](#gas-optimisation-findings)

## Review Summary

Manual code review of contracts in scope trying to find flaws and potential improvements that are not picked up on last audit and automated tools. 

## Scope

src/V3Vault.sol
src/V3Oracle.sol
src/InterestRateModel.sol
src/automators/AutoExit.sol
src/automators/Automator.sol
src/transformers/AutoCompound.sol
src/transformers/AutoRange.sol
src/transformers/LeverageTransformer.sol
src/transformers/V3Utils.sol
src/utils/FlashloanLiquidator.sol
src/utils/Swapper.sol

## Critical Findings

None.

## High Findings

### 1. High - Checking for collateral value limits is done even when decreasing debt shares

Checking the if the max debt you can mint against a certain collateral should only be done when increasing debt shares. This is also written here:
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1204

#### Technical Details

When loan is getting repaid we still check it when we shouldn't.
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L997

When loan is getting liquidated we still check it when we shouldn't.
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1081

#### Impact
This would mean we cannot repay or liquidate loans when the debt limit is decreased past current levels. In the event we want to decrease a limit below what people have already borrowed, we would be unable to decrease it and allow users to repay at the same time. We would have to wait for repayments first and then decrease it. In catastrophic events such as depegging of assets we want to disable borrowing immediately and allow repayments. Users will be panic withdrawing their lent tokens and will need borrowers the ability to repay.

#### Recommendation

Remove the function call to check for the limit on _repay() and liquidate() functions

## Medium Findings

None

## Low Findings

### 1. Low - No public function for converting assets to shares for debt

When repay a loan, if you want to repay everything you need to provide exact amount of shares. Since theres no public function to get your total loan in shares form, only in assets form if a small rounding error persists in conversion could make function call fail.


#### Technical Details
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L973
This line will fail if input assets' conversion to shares has a rounding error. loans[tokenId].debtShares is stored in shares and converted to assets when displayed to user via loanInfo() in line 231. By converting to assets and then back to shares has a risk of inducing a rounding error which could make the value not exact. 


#### Impact
User would potentially have error whole repaying loan and require calling the mapping of loans directly to get correct shares amount. If mapping of loans is private will be a little harder.

#### Recommendation

Add a external function to return loan in shares similar to previewDeposit() in line 334. Or alternatively, modify logic in repay to account for overrepayments to be converted to exact. This allows users to repay all loan by simply inputing max int.

By doing this you can also make loans mapping private to save some gas.

## Informational Findings

### 1. Informational - Redundant line

https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L986
This line is redundant since if assets is equal to 0 we have nothing to repay. 

#### Technical Details

Whether isShare is true or false due to the if statement in line 964, assets should always be > 0 or this function has no reason to be called.

#### Impact
Informational.

#### Recommendation

Just throw an error if assets == 0. Makes the code more verbose. Don't want to run rest of code if assets == 0 anyway.

## Gas Optimisation Findings

https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L599
```isTransformMode ? msg.sender : owner```
If this is in transform mode we want to send to msg.sender. If not in transform mode the owner always has to be msg.sender otherwise transaction is unauthorized from line 561. So we always want to send to msg.sender regardless of transform mode. Line 595 can also be removed.

https://github.com/Paul4912/2024-03-revert-lend/blob/9b3b6304b176d23ee007c18f56c91cd699bf5b78/src/automators/AutoExit.sol#L124
This line can be removed since its covered by line 127. In the edge case params.liquidity and state.liquidity is both 0, Uniswap's nonfungibleposition manager will throw error anyway.



### Time spent:
20 hours