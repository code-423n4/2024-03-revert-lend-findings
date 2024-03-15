https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L561
 
 This conditional statement must be executed in the first line of the function body and immediately after the function is called. Because the first point is that checking it depends only on the function caller and the input parameters, and the second point is that if this condition is not met, it is not necessary to calculate and execute the calculations and functions that are executed in the current state before the condition. And gas consumption is saved. This strategy aligns with the principle of "guard statements," which are used to quickly exit a function if certain conditions are not met, thereby avoiding the execution of subsequent, potentially unnecessary code.
 
 =================================================================
 
 https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L788

## Summary : missing "is contract" method in function

## Vulnerability Detail
onwer can set any kind of address ad transformer even an EOA.

# Tool used

Manual Review

## Recommendation
 use below  function and revert if there is no code in input transformer address
 pragma solidity ^0.8.0;


    function isContract(address _address) public view returns (bool) {
        uint32 size;
        assembly {
            size := extcodesize(_address)
        }
        return (size > 0);
    }

