https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L550C1-L603C1

The borrow function in the V3Vault.sol allows users to borrow assets from a lending pool associated by a tokenId.

Function breakdown

1. Permission Check and Mode Detection:

It first checks a isTransformMode boolean. 
It then updates some exchange rates and resets a daily debt increase limit.

2. Loan Object and Access Control:

It retrieves the Loan storage object associated with the tokenId.
It performs an access control check. Normally, only the owner or the lending pool itself can call this function for borrowing. However, in isTransformMode, a whitelisted address can also call it.

3. Borrowing Amount Conversion and Update

4. Daily Debt Increase Limit Check

5. Collateral and Health Check

6. Minimum Loan Size Check

7. Health Check

8. Transferring Borrowed Assets

9. Event Emission

Here is the issue, the borrow function updates exchange rates and resets daily debt increase limit before performing the access control checks therefore updating the rates will take place even for failed borrows but consuming gas while performing the update before reverting because of invalid tokenid. This could  also lead to a potential denial of service when a bad actor sends many invalid transactions updating the rates but failing hence slowing down the borrowing process of legitimate users.

The function should perform access control checks first before going ahead to consume gas to update the rates and reset the daily limit for transactions that will fail eventually.


Mitigation Strategies:


1. Nonce-based Rate Limiting:

Implement a functionality where users need to include a unique nonce with their borrow requests.
The contract keeps track of used nonces for each user. This prevents spamming from a single address while allowing legitimate users to submit multiple requests.

