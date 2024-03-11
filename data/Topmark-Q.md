### Report 1:
#### No KinkX96 Boundary Validation
As noted from the code provided below in the InterestRateModel contract, it can be noted that `kinkX96` is set without any form of validation like the other variables, this would allow owner to unfairly set value that could break protocol functionality, this should be corrected by setting boundaries for this state update
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L98
```solidity
 function setValues(
        uint256 baseRatePerYearX96,
        uint256 multiplierPerYearX96,
        uint256 jumpMultiplierPerYearX96,
        uint256 _kinkX96
    ) public onlyOwner {
        if (
            baseRatePerYearX96 > MAX_BASE_RATE_X96 || multiplierPerYearX96 > MAX_MULTIPLIER_X96
                || jumpMultiplierPerYearX96 > MAX_MULTIPLIER_X96
        ) {
            revert InvalidConfig();
        }

        baseRatePerSecondX96 = baseRatePerYearX96 / YEAR_SECS;
        multiplierPerSecondX96 = multiplierPerYearX96 / YEAR_SECS;
        jumpMultiplierPerSecondX96 = jumpMultiplierPerYearX96 / YEAR_SECS;
>>>        kinkX96 = _kinkX96;

        emit SetValues(baseRatePerYearX96, multiplierPerYearX96, jumpMultiplierPerYearX96, _kinkX96);
    }
```
###  Report 2:
