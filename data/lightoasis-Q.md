## 1. There are no max and min values for the reserve factor.

The reserve factor is the percentage difference between debt and lend interest. There are currently no max and min values for the reserve factor. This could impact the borrowers and the lenders it is set too high or too low.
[V3Vault.sol#L838](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L838)
```
    function setReserveFactor(uint32 _reserveFactorX32) external onlyOwner {
        reserveFactorX32 = _reserveFactorX32;
        emit SetReserveFactor(_reserveFactorX32);
    }
```

## Tools Used
Manual Review

## Recommended Mitigation Steps
Consider implementing max and min values for the reserve factor. These values shouldn't be exceeded when setting the reserve factor.


## 2. Protocol mints less shares than intended.

The vulnerability is similar to [kelp #62](https://github.com/code-423n4/2023-11-kelp-findings/issues/62) where less tokens than intended were minted because the asset's price was higher after transferring the user's deposited amount before minting.

Transferring before minting will result in less shares for the users.
This is because the amount of shares to mint to the user is calculated with the asset the user deposited, thereby increasing the price of the asset and resulting in less shares.

```
    function _deposit(address receiver, uint256 amount, bool isShare, bytes memory permitData)
        internal
        returns (uint256 assets, uint256 shares)
    {
        (, uint256 newLendExchangeRateX96) = _updateGlobalInterest();

        _resetDailyLendIncreaseLimit(newLendExchangeRateX96, false);

        if (isShare) {
            shares = amount;
            assets = _convertToAssets(shares, newLendExchangeRateX96, Math.Rounding.Up);
        } else {
            assets = amount;
            shares = _convertToShares(assets, newLendExchangeRateX96, Math.Rounding.Down);
        }

        if (permitData.length > 0) {
            (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
                abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
            permit2.permitTransferFrom(
                permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
            );
        } else {
            // fails if not enough token approved
@>            SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
        }

@>        _mint(receiver, shares);
        ...
}
```

## Tools Used
Manual Review

## Recommended Mitigation Steps
Transfer tokens in the end:
```
    function _deposit(address receiver, uint256 amount, bool isShare, bytes memory permitData)
        internal
        returns (uint256 assets, uint256 shares)
    {
        (, uint256 newLendExchangeRateX96) = _updateGlobalInterest();

        _resetDailyLendIncreaseLimit(newLendExchangeRateX96, false);

        if (isShare) {
            shares = amount;
            assets = _convertToAssets(shares, newLendExchangeRateX96, Math.Rounding.Up);
        } else {
            assets = amount;
            shares = _convertToShares(assets, newLendExchangeRateX96, Math.Rounding.Down);
        }

+        _mint(receiver, shares);
        if (permitData.length > 0) {
            (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
                abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
            permit2.permitTransferFrom(
                permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
            );
        } else {
            // fails if not enough token approved
            SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
        }

-        _mint(receiver, shares);

        if (totalSupply() > globalLendLimit) {
            revert GlobalLendLimit();
        }

        if (assets > dailyLendIncreaseLimitLeft) {
            revert DailyLendIncreaseLimit();
        } else {
            dailyLendIncreaseLimitLeft -= assets;
        }

        emit Deposit(msg.sender, receiver, assets, shares);
    }

```

## 3. Reentrancy issue in V3Vault.create()


### Vulnerability details
### Bug Description

In create, a token transfer is triggered without a reentrancy guard in place which can lead to exploits. The function also doesn't follow CEI (Checks and Effects Interaction pattern) which means to make neccessary checks and update the contract's state before makinng any external calls. The function in it's current implementation is vulnerabile to reentrancy attacks. 
[V3Vault.sol#L401C36-L401C52](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L401C36-L401C52)

```
    function create(uint256 tokenId, address recipient) external override {
        nonfungiblePositionManager.safeTransferFrom(msg.sender, address(this), tokenId, abi.encode(recipient));
    }
```

## Impact
Theft of funds through reentrancy exploits. The lack of a reentrancy guard and necessary state updates before the external call leaves the function open to reentrancy attacks which can lead to a theft of funds.

## Recommended Mitigation
Consider Implementing a reentrancy guard on the create function.


