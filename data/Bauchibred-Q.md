# QA Report for Revert Lend

## Table of Contents

| Issue ID                                                                                                                                     | Description                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| [QA-01](#qa-01-min_twap_seconds-is-too-low-and-an-avenue-to-ingest-manipulated-prices)                                                       | `MIN_TWAP_SECONDS` is too low and an avenue to ingest manipulated prices                                                       |
| [QA-02](#qa-02-unhandled-chainlink-revert-would-halt-core-functionalities)                                                                   | Unhandled Chainlink revert would halt core functionalities                                                                     |
| [QA-03](#qa-03-_checkapprovals-should-be-reimplemented-to-count-for-the-allowance-depleting)                                                 | `_checkApprovals` should be reimplemented to count for the allowance depleting                                                 |
| [QA-04](#qa-04-setters-should-always-have-equality-checkers)                                                                                 | Setters should always have equality checkers                                                                                   |
| [QA-05](#qa-05-allow-totalrewardx64-to-be-set-higher-via-autocompound-setreward)                                                             | Allow `totalRewardX64` to be set higher via `AutoCompound.setReward()`                                                         |
| [QA-06](#qa-06-pricing-logic-shouldnt-be-unavailable-in-any-case-or-atleast-the-provider-of-the-secondary-source-should-not-halt-the-system) | Pricing logic shouldn't be unavailable in any case or at least the provider of the secondary source should not halt the system |
| [QA-07](#qa-07-introduce-better-naming-conventions)                                                                                          | Introduce better naming conventions                                                                                            |
| [QA-08](#qa-08-introduce-a-contract-existence-check-before-a-low-level-call-to-send-eth)                                                     | Introduce a contract existence check before a low level call to send ETH                                                       |
| [QA-09](#qa-09-safeincreaseallowance-has-been-deprecated)                                                                                    | `safeIncreaseAllowance` has been deprecated                                                                                    |

## QA-01 `MIN_TWAP_SECONDS` is too low and an avenue to ingest manipulated prices

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/automators/Automator.sol#L86-L98

```solidity
    function setTWAPConfig(uint16 _maxTWAPTickDifference, uint32 _TWAPSeconds) public onlyOwner {
        if (_TWAPSeconds < MIN_TWAP_SECONDS) {
            revert InvalidConfig();
        }
        if (_maxTWAPTickDifference > MAX_TWAP_TICK_DIFFERENCE) {
            revert InvalidConfig();
        }
        emit TWAPConfigChanged(_TWAPSeconds, _maxTWAPTickDifference);
        TWAPSeconds = _TWAPSeconds;
        maxTWAPTickDifference = _maxTWAPTickDifference;
    }

```

One can see that the accepted TWAP seconds could be as low as 60 seconds which is just a minute and one could say is even same with a spot price, this is cause the timeframe is too short and still allows for manipulatable prices.

### Impact

Since `MIN_TWAP_SECONDS` is very low, then this might lead to protocol ingesting manipulated prices

### Recommended Mitigation Steps

Have the `MIN_TWAP_SECONDS` value be within the 10-30 minutes range.

## QA-02 Unhandled Chainlink revert would halt core functionalities

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L331-L349

```solidity

    function _getChainlinkPriceX96(address token) internal view returns (uint256) {
        if (token == chainlinkReferenceToken) {
            return Q96;
        }

        TokenConfig memory feedConfig = feedConfigs[token];
    //@audit
        // if stale data - revert
        (, int256 answer,, uint256 updatedAt,) = feedConfig.feed.latestRoundData();
        if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0) {
            revert ChainlinkPriceError();
        }

        return uint256(answer) * Q96 / (10 ** feedConfig.feedDecimals);
    }
```

One can see that all pricing logic that requires us to query chainlink at the end of the calls on the `_getChainlinkPriceX96()`, i.e three out of the 5 accepted pricing modes require the call to this function not to revert.

But evidently, we can see that this call lacks error handling for the potential failure of `feedConfig.feed.latestRoundData()`, note that Chainlink pricefeeds could revert due to whatever reason, i.e say maintenance or maybe the Chainlink team decide to change the underlying address. Now this omission of not considering thiks call failing would lead to systemic issues, since calls to this would now revert halting any action that requires this call to succeed.

### Impact

A revert of the entire operation that requires querying the Chainlink pricing logic, This limitation poses a significant risk, since all three pricing modes that use the Chainlink mode either as a primary or secondary source would now revert.

### Recommended Mitigation Steps

Wrap the `feedConfig.feed.latestRoundData()` call in a try-catch block, even if it's only for the pricing logic that use Chainlink as a secondary sourceand then handle the error (e.g., revert with a specific message or use an alternative pricing method) and also apply other chainlink safety integration checks from here: https://medium.com/cyfrin/chainlink-oracle-defi-attacks-93b6cb6541bf

## QA-03 `_checkApprovals` should be reimplemented to count for the allowance depleting

### Proof of Concept

The function `_checkApprovals` is designed to only set approvals if the current allowance is zero. This is a one-time setup meant to minimize gas costs associated with setting allowances for token transfers.

```solidity
function _checkApprovals(address token0, address token1) internal {
    uint256 allowance0 = IERC20(token0).allowance(address(this), address(nonfungiblePositionManager));
    if (allowance0 == 0) {
        SafeERC20.safeApprove(IERC20(token0), address(nonfungiblePositionManager), type(uint256).max);
    }
    uint256 allowance1 = IERC20(token1).allowance(address(this), address(nonfungiblePositionManager));
    if (allowance1 == 0) {
        SafeERC20.safeApprove(IERC20(token1), address(nonfungiblePositionManager), type(uint256).max);
    }
}
```

While setting the allowance to `type(uint256).max` reduces the need for repeated approvals (and thus saves gas), it neglects the scenario where the allowance might be fully utilized. In typical use cases, reaching `type(uint256).max` would require an unrealistic volume of transactions. However, it does not account for potential bugs, exploits, or changes in contract logic that could deplete this allowance unexpectedly.

### Impact

The current implementation of the `_checkApprovals` function sets the token allowance to `type(uint256).max` for the `nonfungiblePositionManager` contract, intending to save on gas costs for future transactions. However, this approach introduces a vulnerability where, once the `type(uint256).max` allowance is exhausted, there would be no mechanism in place to renew the approval. This could lead to a situation where the smart contract is unable to perform operations requiring token transfers on behalf of users, effectively freezing any functionality dependent on these approvals.

### Recommended Mitigation Steps

Instead of only checking for an allowance of zero, implement a mechanism to check if the allowance is below a certain threshold and, if so, replenish it.

## QA-04 Setters should always have equality checkers

### Proof of Concept

Use this search prompt code: [https://github.com/search?q=repo%3Acode-423n4%2F2024-03-revert-lend%20function%20set&type=code](https://github.com/search?q=repo%3Acode-423n4%2F2024-03-revert-lend%20function%20set&type=code)

Evidently we can see that multiple setter functions exist in scope, with them not having any check that the new accepted value is not equal to the previously stored value.

For e.g [setReward()](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/transformers/AutoCompound.sol#L243-L247) cehcks that the new value is "<=" where as it should only check "<" leading to an unnecessary update of totalRewardX64 if `_totalRewardX64 is already == totalRewardX64`.

```solidity
    function setReward(uint64 _totalRewardX64) external onlyOwner {
        require(_totalRewardX64 <= totalRewardX64, ">totalRewardX64");
        totalRewardX64 = _totalRewardX64;
        emit RewardUpdated(msg.sender, _totalRewardX64);
    }
```

Another example would be the below that does not implement any checks whatsoever:

```
 function setWithdrawer(address _withdrawer) public onlyOwner {
 emit WithdrawerChanged(_withdrawer);
withdrawer = _withdrawer;
}
```

And so on.

### Impact

Unnecessary code execution

### Recommended Mitigation Steps

Introduce equality checkers for setter functions

## QA-05 Allow `totalRewardX64` to be set higher via `AutoCompound.setReward()`

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/transformers/AutoCompound.sol#L243-L247

```solidity
    function setReward(uint64 _totalRewardX64) external onlyOwner {
        require(_totalRewardX64 <= totalRewardX64, ">totalRewardX64");
        totalRewardX64 = _totalRewardX64;
        emit RewardUpdated(msg.sender, _totalRewardX64);
    }
```

This function is used to set the reward value, keep in mind that there are no checks for e.g that the provided `_totalRewardX64 != 0`, now if this value gets set to 0 it can never be changed cause as implemented in code it can only be lower in value

### Impact

Low since this requires admin mistake, but the whole rewards logic could be broken

### Recommended Mitigation Steps

Allow this value to be reset to atleast an accepted max.

## QA-06 Pricing logic shouldn't be unavailable in any case or atleast the provider of the secondary source should not halt the system

### Proof of Concept

The relevant code segment attempts to calculate TWAP using the `pool.observe` function with two time points, 'now' and 'now - twapSeconds'. This method is prone to failure if the pool does not have enough historical data to cover the requested time span, a scenario not uncommon for newer or less active pools, i.e

```solidity
    function _getReferencePoolPriceX96(IUniswapV3Pool pool, uint32 twapSeconds) internal view returns (uint256) {
        uint160 sqrtPriceX96;
        // if twap seconds set to 0 just use pool price
        if (twapSeconds == 0) {
            (sqrtPriceX96,,,,,,) = pool.slot0();
        } else {
            uint32[] memory secondsAgos = new uint32[](2);
            secondsAgos[0] = 0; // from (before)
            secondsAgos[1] = twapSeconds; // from (before)
            //@audit-issue pool.observe could fail due to lack of history.
            (int56[] memory tickCumulatives,) = pool.observe(secondsAgos); // pool observe may fail when there is not enough history available (only use pool with enough history!)
            int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)));
            sqrtPriceX96 = TickMath.getSqrtRatioAtTick(tick);
        }

        return FullMath.mulDiv(sqrtPriceX96, sqrtPriceX96, Q96);
    }

```

Now the lack of error handling for the potential failure of `pool.observe` due to insufficient historical data. This omission would lead to systemic issues, particularly in financial systems that rely on continuous access to accurate pricing data for operational stability.

### Impact

The method `_getReferencePoolPriceX96` within the `V3Oracle` contract is designed to calculate the reference price from a Uniswap V3 pool, either directly from the latest slot price or through a Time-Weighted Average Price (TWAP) if a `twapSeconds` parameter is specified. An identified issue arises when the `pool.observe` function is called for TWAP calculation: if there is insufficient historical data within the specified `twapSeconds`, the call to `pool.observe` could fail, leading to a revert of the entire operation. This limitation poses a significant risk, since all three pricing modes that use the TWAP mode either as a primary or secondary source would now revert.

### Recommended Mitigation Steps

Wrap the `pool.observe` call in a try-catch block, even if it's only for the pricing logic that use TWAP as a secondary source.

    ```solidity
    try pool.observe(secondsAgos) returns (int56[] memory tickCumulatives,) {
        int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)));
        sqrtPriceX96 = TickMath.getSqrtRatioAtTick(tick);
    } catch {
        // Handle the error (e.g., revert with a specific message or use an alternative pricing method)
    }
    ```

## QA-07 Introduce better naming conventions

### Proof of Concept

Take a look at (https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L25-L28) we can see that this is used to declare the `MIN_PRICE_DIFFERENCE` as 2%, issue is that this value is actually the min max price difference, i.e looking at https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L183-L191

```solidity
    function setMaxPoolPriceDifference(uint16 _maxPoolPriceDifference) external onlyOwner {
        if (_maxPoolPriceDifference < MIN_PRICE_DIFFERENCE) {
            revert InvalidConfig();
        }
        maxPoolPriceDifference = _maxPoolPriceDifference;
        emit SetMaxPoolPriceDifference(_maxPoolPriceDifference);
    }
```

We can see that whenever setting the max pool price difference, it's checked to not be lower than our MIN_PRICE_DIFFERENCE

### Impact

Confusion in naming conventions leading to hard time of users/developers understanding code.

### Recommended Mitigation Steps

Consider renaming the vcariable and take into acount that it's the minimum max difference between the prices.

## QA-08 Introduce a contract existence check before a low level call to send ETH

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/automators/Automator.sol#L125-L138

```solidity
    function withdrawETH(address to) external {
        if (msg.sender != withdrawer) {
            revert Unauthorized();
        }

        uint256 balance = address(this).balance;
        if (balance > 0) {
            //@audit QA low level call
            (bool sent,) = to.call{value: balance}("");
            if (!sent) {
                revert EtherSendFailed();
            }
        }
    }
```

Now consider this minimal contract as a POC

```solidity


// SPDX-License-Identifier: MIT
pragma solidity ^0.8.21;
import "hardhat/console.sol";
contract test {
constructor() {
bytes memory txData*; (bool success,) = payable(address(0)).call{ value: 0 }(txData*); console.log("success",success);
}
}
```

One can see that the even as we used an invalid address, 0x0, the call still comes back successful, whereas it shouldn't.

### Recommedned Mitigation Steps

Introduce a contract existence check before transferring eth.

## QA-09 safeIncreaseAllowance has been deprecated

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/transformers/LeverageTransformer.sol#L75-L80

```solidity
            amount1 += amountOut;
        }
//@todo QA safeIncreaseAllowance has been deprecated
        SafeERC20.safeIncreaseAllowance(IERC20(token0), address(nonfungiblePositionManager), amount0);
        SafeERC20.safeIncreaseAllowance(IERC20(token1), address(nonfungiblePositionManager), amount1);

```

### Impact

Usage of deprecated functions.

### Recommended Mitigation Steps

Do not use deprecated functions
