## L-01 Lack of minAmount parameter 

In `execute()` function of `AutoCompound.sol` and `AutoRange.sol` minAmount parameters are missing in the `NPM.IncreaseLiquidity()` and `NPM.mint()` external calls.

**Line of code:** 
- [AutoRange.sol:198-210](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoRange.sol#L198-L210)
- [AutoCompound.sol:163-167](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoCompound.sol#L163-L167)

### Impact
- Due to MEV sandwich attacks, users may end up losing value by providing more tokens than needed (or buying liquidity at a premium price at the expense of MEV Attacker).

### Mitigation
- Allow users to provide a minimum amount (or define their slippage tolerance) for these transactions


## L-02 Deadline defined as block.timestamp

In `Liquidate()` function of `V3Vault.sol` there is a call to NPM for `decreaseLiquidity()` with block.timestamp as the deadline parameter, which is ineffective.

Refer to this [issue](https://github.com/code-423n4/2022-12-backed-findings/issues/64) on how this can be exploited.

**Line of code:** 
- [V3Vault.sol:735](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L735)
- [V3Vault.sol:1066](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1066)

### Mitigation
- Allow users to provide a deadline parameter in the `liquidate()` function.