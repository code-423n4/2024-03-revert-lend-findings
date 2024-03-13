# [L-01] Unsafe Casting
https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Oracle.sol#L342C24-L342C30
There are also other instances where it is casted from uint to int 

## Recomendation 
Use OZ safeCasting while casting

# [L-02] Natspec comment might not be giving out the exact intended behavior in`AutoCompound::execute()`  

The comment->
`Can only be called only from configured operator account, or vault via transform`
```
 if (!operators[msg.sender] && !vaults[msg.sender]) {
            revert Unauthorized();
        }
```
## Recommendation 
Edit the comments telling the intended behavior
# [NC -01] Code structure not suggested
Refer to the solidity docs for the code structure