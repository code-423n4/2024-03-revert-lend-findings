## [L-01] repay() function can be front-run with repaying dust

Anyone can repay any loan. So when an original loan owner wishes to repay the whole debt by specifying the attributes of the `repay()`, the transaction could be front-run by an attacker where he repays the exact amount so that the `loan.debtShares` decrements by 1. This way the debt owner's transaction gets reverted due to the below condition.

```solidity
File: src/V3Vault.sol

973: if (shares > currentShares) {
            revert RepayExceedsDebt();
        }
```

### Recommendation:
The fix should be the following: If the debt/loan owner specifies too high amount, and the above condition is hit, the shares/assets values should be recalculated, like this:

```solidity
973: if (shares > currentShares) {
         shares = currentShares
         assets = _convertToAssets(shares, newDebtExchangeRateX96, Math.Rounding.Up);
     }
```
This way would protect the loan/debt owners from unnecessarily repeated transaction and hence save them gas.

*GitHub* : [973](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/V3Vault.sol#L973)

## [L-02] Uniswap positions minted to V3Vault are stuck
Using the `NonfungiblePositionManager` directly a user could potentially mint a position directly to V3Vault by having V3Vault as the receiver when calling `NonfungiblePositionManager.mint()`.

Since NonfungiblePositionManager doesn’t use `safeMint()` this would just transfer the token and liquidity to V3Vault without calling `V3Vault.onERC721Received()`, thus the liquidity would be lost.

### Recommendation
Consider adding a rescue function callable by owner that can transfer any accidentally minted tokens out of the contract. This could check that V3Vault is the owner of the token but has `loans[tokenId].owner == address(0)` to prevent misuse.