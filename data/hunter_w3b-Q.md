### L-1. In the `V3Oracle::getValue()` function, the `priceTokenX96` variable is calculated based on the `token` parameter passed to the function. However, when calculating the `value` and `feeValue` variables, the `priceTokenX96` variable is used regardless of whether the `token` parameter is `token0`, `token1`, or neither of them. This can lead to incorrect calculations of `value` and `feeValue` if the `token` parameter is not one of the tokens in the Uniswap V3 pool.

https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L95-L131

```solidity
    function getValue(uint256 tokenId, address token)
        external
        view
        override
        returns (uint256 value, uint256 feeValue, uint256 price0X96, uint256 price1X96)
    {
        (address token0, address token1, uint24 fee,, uint256 amount0, uint256 amount1, uint256 fees0, uint256 fees1) =
            getPositionBreakdown(tokenId);

        uint256 cachedChainlinkReferencePriceX96;

        (price0X96, cachedChainlinkReferencePriceX96) =
            _getReferenceTokenPriceX96(token0, cachedChainlinkReferencePriceX96);
        (price1X96, cachedChainlinkReferencePriceX96) =
            _getReferenceTokenPriceX96(token1, cachedChainlinkReferencePriceX96);

        uint256 priceTokenX96;
        if (token0 == token) {
            priceTokenX96 = price0X96;
        } else if (token1 == token) {
            priceTokenX96 = price1X96;
        } else {
            (priceTokenX96,) = _getReferenceTokenPriceX96(token, cachedChainlinkReferencePriceX96);
        }

        value = (price0X96 * (amount0 + fees0) / Q96 + price1X96 * (amount1 + fees1) / Q96) * Q96 / priceTokenX96;
        feeValue = (price0X96 * fees0 / Q96 + price1X96 * fees1 / Q96) * Q96 / priceTokenX96;
        price0X96 = price0X96 * Q96 / priceTokenX96;
        price1X96 = price1X96 * Q96 / priceTokenX96;

        // checks derived pool price for price manipulation attacks
        // this prevents manipulations of pool to get distorted proportions of collateral tokens - for borrowing
        // when a pool is in this state, liquidations will be disabled - but arbitrageurs (or liquidator himself)
        // will move price back to reasonable range and enable liquidation
        uint256 derivedPoolPriceX96 = price0X96 * Q96 / price1X96;
        _checkPoolPrice(token0, token1, fee, derivedPoolPriceX96);
    }
```

To fix this issue, the `priceTokenX96` variable should only be calculated if the `token` parameter is one of the tokens in the pool. Otherwise, the `price0X96` and `price1X96` variables should be used directly to calculate the `value` and `feeValue` variables.

### L-2. In the `_checkPoolPrice()` function, the `derivedPoolPriceX96` variable is calculated as `price0X96 * Q96 / price1X96`, which represents the price of `token1` in terms of `token0`. However, the `_getReferencePoolPriceX96()` function returns the price of `token0` in terms of `token1`. This means that the `_checkPoolPrice()` function is comparing two prices that are not directly comparable.

https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L133-L138

```solidity
    function _checkPoolPrice(address token0, address token1, uint24 fee, uint256 derivedPoolPriceX96) internal view {
        IUniswapV3Pool pool = _getPool(token0, token1, fee);
        uint256 priceX96 = _getReferencePoolPriceX96(pool, 0);
        _requireMaxDifference(priceX96, derivedPoolPriceX96, maxPoolPriceDifference);
    }
```

To fix this issue, the `derivedPoolPriceX96` variable should be calculated as `price1X96 * Q96 / price0X96`, which represents the price of `token0` in terms of `token1`. This will make it directly comparable to the price returned by the `_getReferencePoolPriceX96()` function.

### L-3. In the `_getReferencePoolPriceX96()` function, the `secondsAgos` array is initialized with the values `0` and `twapSeconds`, which represent the time periods for calculating the TWAP price. However, the `observe()` function of the Uniswap V3 pool contract expects the `secondsAgos` array to be sorted in ascending order. In this case, if `twapSeconds` is greater than `0`, the array is not sorted in ascending order, which can cause the `observe()` function to fail.

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
            (int56[] memory tickCumulatives,) = pool.observe(secondsAgos); // pool observe may fail when there is not enough history available (only use pool with enough history!)
            int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)));
            sqrtPriceX96 = TickMath.getSqrtRatioAtTick(tick);
        }

        return FullMath.mulDiv(sqrtPriceX96, sqrtPriceX96, Q96);
    }
```

To fix this issue, the `secondsAgos` array should be initialized with the values `twapSeconds` and `0`, which will ensure that it is sorted in ascending order.

### L-4. In the `setTokenConfig()` function, the `TokenConfig` struct is initialized with the `pool` parameter passed to the function. However, the `pool` parameter is not validated to ensure that it is a valid Uniswap V3 pool contract. This can allow an attacker to pass a malicious contract as the `pool` parameter, which can lead to unexpected behavior or security vulnerabilities.

```solidity
    function setTokenConfig(
        address token,
        AggregatorV3Interface feed,
        uint32 maxFeedAge,
        IUniswapV3Pool pool,
        uint32 twapSeconds,
        Mode mode,
        uint16 maxDifference
    ) external onlyOwner {
        // can not be unset
        if (mode == Mode.NOT_SET) {
            revert InvalidConfig();
        }

        uint8 feedDecimals = feed.decimals();
        uint8 tokenDecimals = IERC20Metadata(token).decimals();

        TokenConfig memory config;

        if (token != referenceToken) {
            if (maxDifference < MIN_PRICE_DIFFERENCE) {
                revert InvalidConfig();
            }

            address token0 = pool.token0();
            address token1 = pool.token1();
            if (!(token0 == token && token1 == referenceToken || token0 == referenceToken && token1 == token)) {
                revert InvalidPool();
            }
            bool isToken0 = token0 == token;
            config = TokenConfig(
                feed, maxFeedAge, feedDecimals, tokenDecimals, pool, isToken0, twapSeconds, mode, maxDifference
            );
        } else {
            config = TokenConfig(
                feed, maxFeedAge, feedDecimals, tokenDecimals, IUniswapV3Pool(address(0)), false, 0, Mode.CHAINLINK, 0
            );
        }

        feedConfigs[token] = config;

        emit TokenConfigUpdated(token, config);
        emit OracleModeUpdated(token, mode);
    }
```

To fix this issue, the `pool` parameter should be validated to ensure that it is a valid Uniswap V3 pool contract before initializing the `TokenConfig` struct. One way to do this is to use the `IUniswapV3Pool(address).factory()` function to retrieve the Uniswap V3 factory contract associated with the pool, and then check if the factory contract is the expected contract.

### L-5. In the `setTokenConfig()` function, the `maxDifference` parameter is validated to ensure that it is not less than `MIN_PRICE_DIFFERENCE`. However, this validation is only performed if the `token` parameter is not the reference token. This means that if the reference token is being configured, the `maxDifference` parameter can be set to any value, even if it is less than `MIN_PRICE_DIFFERENCE`.

```solidity
    function setTokenConfig(
        address token,
        AggregatorV3Interface feed,
        uint32 maxFeedAge,
        IUniswapV3Pool pool,
        uint32 twapSeconds,
        Mode mode,
        uint16 maxDifference
    ) external onlyOwner {
        // can not be unset
        if (mode == Mode.NOT_SET) {
            revert InvalidConfig();
        }

        uint8 feedDecimals = feed.decimals();
        uint8 tokenDecimals = IERC20Metadata(token).decimals();

        TokenConfig memory config;

        if (token != referenceToken) {
            if (maxDifference < MIN_PRICE_DIFFERENCE) {
                revert InvalidConfig();
            }

            address token0 = pool.token0();
            address token1 = pool.token1();
            if (!(token0 == token && token1 == referenceToken || token0 == referenceToken && token1 == token)) {
                revert InvalidPool();
            }
            bool isToken0 = token0 == token;
            config = TokenConfig(
                feed, maxFeedAge, feedDecimals, tokenDecimals, pool, isToken0, twapSeconds, mode, maxDifference
            );
        } else {
            config = TokenConfig(
                feed, maxFeedAge, feedDecimals, tokenDecimals, IUniswapV3Pool(address(0)), false, 0, Mode.CHAINLINK, 0
            );
        }

        feedConfigs[token] = config;

        emit TokenConfigUpdated(token, config);
        emit OracleModeUpdated(token, mode);
    }
```

To fix this issue, the `maxDifference` parameter should be validated regardless of whether the `token` parameter is the reference token or not. The validation should ensure that the `maxDifference` parameter is not less than `MIN_PRICE_DIFFERENCE` for all tokens.
