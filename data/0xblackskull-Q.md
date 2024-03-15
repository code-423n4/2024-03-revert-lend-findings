### If `totalRewardX64` set to 0 then there is no way to set new value
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L243-L247
```
function setReward(uint64 _totalRewardX64) external onlyOwner {
        //@audit-qa 
        require(_totalRewardX64 <= totalRewardX64, ">totalRewardX64");
        totalRewardX64 = _totalRewardX64;
        emit RewardUpdated(msg.sender, _totalRewardX64);
    }
```
Mitigation:  add require statement 
```
require(_totalRewardX64 != 0);
```

### Need emit event in `else` block
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1150-L1165
```
function _updateGlobalInterest()
        internal
        returns (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96)
    {
        // only needs to be updated once per block (when needed)
        if (block.timestamp > lastExchangeRateUpdate) {
            (newDebtExchangeRateX96, newLendExchangeRateX96) = _calculateGlobalInterest();
            lastDebtExchangeRateX96 = newDebtExchangeRateX96;
            lastLendExchangeRateX96 = newLendExchangeRateX96;
            lastExchangeRateUpdate = block.timestamp;
            emit ExchangeRateUpdate(newDebtExchangeRateX96, newLendExchangeRateX96);
        } else {
            newDebtExchangeRateX96 = lastDebtExchangeRateX96;
            newLendExchangeRateX96 = lastLendExchangeRateX96;
            //@audit missing event, ExchangeRateUpdate(newDebtExchangeRateX96, newLendExchangeRateX96)
        }
    }
```

### operator address is not EOA checked
According to Additional Context on C4 page, `Operators (which are EOA used by bots to call actions in Automator contracts)`
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L69-L72
```
function setOperator(address _operator, bool _active) public onlyOwner {
        emit OperatorChanged(_operator, _active);
        operators[_operator] = _active;
    }
```

### should check tokens length must be more then 0
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L104-L117
```
 function withdrawBalances(address[] calldata tokens, address to) external virtual {
        if (msg.sender != withdrawer) {
            revert Unauthorized();
        }
        uint256 i;
        uint256 count = tokens.length;
        for (; i < count; ++i) {
            uint256 balance = IERC20(tokens[i]).balanceOf(address(this));
            if (balance > 0) {
                _transferToken(to, IERC20(tokens[i]), balance, true);
            }
        }
    }
```

### `maxDifference` and `maxDifference` are in int16 but it should be in int24  becoz `twapTick` and `twapTick` are in int24
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L166-L177
```
    function _hasMaxTWAPTickDifference(IUniswapV3Pool pool, uint32 twapPeriod, int24 currentTick, uint16 maxDifference)
        internal
        view
        returns (bool)
    {
        (int24 twapTick, bool twapOk) = _getTWAPTick(pool, twapPeriod);
        if (twapOk) {
            return twapTick - twapTick >= -int16(maxDifference) && twapTick - currentTick <= int16(maxDifference);
        } else {
            return false;
        }
    }
```

### config.onlyFees and !config.onlyFees can be remove for more simplifies and stabilizes the code 
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L112-L117
```
 if (
	config.onlyFees && params.rewardX64 > config.maxRewardX64 || 
	!config.onlyFees && params.rewardX64 > config.maxRewardX64
	) {
		revert ExceedsMaxReward();
    }
```
and we can also rewrite by 
```
if (params.rewardX64 > config.maxRewardX64 ) {
            revert ExceedsMaxReward();
        }
```

### No need of second `if` statement for balance check
https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/FlashloanLiquidator.sol#L101-L107
```
uint256 balance = data.asset.balanceOf(address(this));
            if (balance < data.minReward) {
                revert NotEnoughReward();
            }
            if (balance > 0) { //@audit-remove this check
                SafeERC20.safeTransfer(data.asset, data.liquidator, balance);
            }
```
balance is already check in first `if` statement, so just remove second `if`  and transfer the balance
```
uint256 balance = data.asset.balanceOf(address(this));
            if (balance < data.minReward) {
                revert NotEnoughReward();
            }
                SafeERC20.safeTransfer(data.asset, data.liquidator, balance);
        
```

