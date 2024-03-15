## DOS due to blacklisted addresses
Tokens such as USDC which is supported by the protocol allow for address blacklisting. Add a check at the withdraw function to check whether the address to withdraw the shares to is blacklisted.
```@solidity
  function withdraw(uint256 assets, address receiver, address owner) external override returns (uint256) {
        (, uint256 shares) = _withdraw(receiver, owner, assets, false);
         return shares;
    }
```
[_withdraw](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L920-L952)

## No check whether `SetVault` is active
Autocompound transformer adjusts tokens which are in the vault via transform mode. The vault is set and or changed by the operator and can be in an active or inactive state. There is no check in the [AutoCompound](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoCompound.sol#L87-L96) and [AutoRange](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoRange.sol#L97-L104) transformers whether the vault is active or not. 

## DOS in `_removeTokenFromOwner`
When the length of token Indexes becomes larger iterating through the tokenIndexes may become costly and result in gas cost that is more than block gas limit leaving the removal of tokens from owner in a DOS state since token Ids are not deleted even after removal.
```@solidity
function _removeTokenFromOwner(address from, uint256 tokenId) internal {
        uint256 lastTokenIndex = ownedTokens[from].length - 1;
        uint256 tokenIndex = ownedTokensIndex[tokenId];
        
        //if array becomes large since its not deleted itll lead to DOS due to oog
        if (tokenIndex != lastTokenIndex) {
            uint256 lastTokenId = ownedTokens[from][lastTokenIndex];
            ownedTokens[from][tokenIndex] = lastTokenId;
            ownedTokensIndex[lastTokenId] = tokenIndex;
        }
        ownedTokens[from].pop();
        // Note that ownedTokensIndex[tokenId] is not deleted. There is no need to delete it - gas optimization
  
        delete tokenOwner[tokenId]; // Remove the token from the token owner mapping
    }
```
