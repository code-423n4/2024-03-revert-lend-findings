# Custom errors and revert statement was only introduced in Solidity version 0.8.4 but contracts use ^0.8.0

## Description
The `revert-error` pattern cannot be implemented until the introduction of custom error and revert statements in Solidity version `0.8.4`. These contracts will not compile in Solidity versions 0.8.0, 0.8.1, 0.8.2, and 0.8.3.

Here's an example of `revert-error` pattern.
```solidity
if(msg.sender != owner) revert Unauthorized;
```
Reference: https://soliditylang.org/blog/2021/04/21/solidity-0.8.4-release-announcement/

## Mitigation
Fixate to a newer version of not older than 0.8.4 but be mindful of the newer versions' issues as well.