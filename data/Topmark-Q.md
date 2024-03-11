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
#### Contradictory Derivation of Lent in V3Vault contract
As noted from the pointer in the code provided below, lent was first derived using totalSupply() and Math.Rounding.Up, however on the other hand in the lendInfo() function, lend amount was derived using balanceOf(account) and Math.Rounding.Down, which is contradictory to each other
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L213
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L221
```solidity
  function vaultInfo()
        external
        view
        override
        returns (
            uint256 debt,
            uint256 lent,
            uint256 balance,
            uint256 available,
            uint256 reserves,
            uint256 debtExchangeRateX96,
            uint256 lendExchangeRateX96
        )
    {
        (debtExchangeRateX96, lendExchangeRateX96) = _calculateGlobalInterest();
        (balance, available, reserves) = _getAvailableBalance(debtExchangeRateX96, lendExchangeRateX96);

        debt = _convertToAssets(debtSharesTotal, debtExchangeRateX96, Math.Rounding.Up);
>>>        lent = _convertToAssets(totalSupply(), lendExchangeRateX96, Math.Rounding.Up);
    }

    /// @notice Retrieves lending information for a specified account.
    /// @param account The address of the account for which lending info is requested.
    /// @return amount Amount of lent assets for the account
    function lendInfo(address account) external view override returns (uint256 amount) {
        (, uint256 newLendExchangeRateX96) = _calculateGlobalInterest();
>>>        amount = _convertToAssets(balanceOf(account), newLendExchangeRateX96, Math.Rounding.Down);
    }
```
