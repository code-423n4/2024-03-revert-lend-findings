### L-01: AutoRange incorrect maxAmountAdd calculation
Function `AutoRange.execute` currently calculates maxAmountAdd as follows:
```solidity
// max amount to add - removing max potential fees (if config.onlyFees - the have been removed already)
            state.maxAddAmount0 = config.onlyFees ? state.amount0 : state.amount0 * Q64 / (params.rewardX64 + Q64);
            state.maxAddAmount1 = config.onlyFees ? state.amount1 : state.amount1 * Q64 / (params.rewardX64 + Q64);
```
In case `onlyFees = False`, the maxAddAmount is calculated as `state.amount * (Q64)/ (rewardX64 + Q64)`, this is for `removing max potentials fees` (to keep enough token as fee for operator). However, this calculation is wrong for large `rewardX64`, since `rewardX64` reflect the percentage at which the reward is calculated, then the formula must be `1 - (rewardX64)/Q64`

So if `rewardX64` = 20%, then `maxAddAmount` should be 80%, but in fact, it's calculated as  `1/(1+0.2)` = 83.3%.