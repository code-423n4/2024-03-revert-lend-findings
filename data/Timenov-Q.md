# Revert Lend QA report by Timenov

## Summary

| |Issue|Instances|
|-|:-|:-:|
| I-01 | Emergency admin can have timelock. | 1 |
| I-02 | Event emits differ in contracts. | 4 |
| I-03 | Group validations with same error. | 1 |

### [I-01] Emergency admin can have timelock.
In `V3Oracle.sol` there is an address state variable `emergencyAdmin` which will be used for `address which can call special emergency actions without timelock`. However there is no validation if the `emergencyAdmin != owner`. There should be such validation, because as per the README the owner is `set to a Multisig and Timelock`. Having no such check, will allow the `emergencyAdmin` be set to a Timelock which will break protocol's documentation.

### [I-02] Event emits differ in contracts.
In all the contracts, first the changes are made and the the event is emitted. However in `Automator.sol`, first the events are emitted and then changes are done. Consider using the same flow in all contracts to achieve better code readability.

### [I-03] Group validations with same error.
In `Automator::setTWAPConfig` there are 2 validations in 2 if statements: `_TWAPSeconds < MIN_TWAP_SECONDS` and `_maxTWAPTickDifference > MAX_TWAP_TICK_DIFFERENCE`. They both revert with the same error `InvalidConfig`. Consider grouping them to have better code structure.