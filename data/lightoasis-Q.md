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

## 2. Reentrancy issue in V3Vault.create()


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


