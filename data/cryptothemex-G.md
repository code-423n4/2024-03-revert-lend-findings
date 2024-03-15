### Gas Risk Issues
Already reported issues have been removed from report and only new issues are being reported. 

### [G-01]<a name="g-01"></a> `a = a + b` is more gas effective than `a += b` for state variables (excluding arrays and mappings)

This saves **16 gas per instance.**

*There are 10 instance(s) of this issue:*

```solidity
File: src/V3Oracle.sol

440:         fees0 += state.tokensOwed0;

441:         fees1 += state.tokensOwed1;

```



*GitHub* : [440](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L440), [441](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L441)

```solidity
File: src/transformers/LeverageTransformer.sol

62:             amount0 += amountOut;

74:             amount1 += amountOut;

153:             amount += amountOut;

162:             amount += amountOut;

```



*GitHub* : [62](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L62), [74](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L74), [153](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L153), [162](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L162)

```solidity
File: src/transformers/V3Utils.sol

319:                 targetAmount += amountOutDelta;

321:                 targetAmount += amount0;

336:                 targetAmount += amountOutDelta;

338:                 targetAmount += amount1;

```


*GitHub* : [319](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L319), [321](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L321), [336](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L336), [338](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L338)

### [G-02]<a name="g-02"></a> `array[index] += amount` is cheaper than `array[index] = array[index] + amount` (or related variants)

When updating a value in an array with arithmetic, using `array[index] += amount` is cheaper than `array[index] = array[index] + amount`.

This is because you avoid an additional `mload` when the array is stored in memory, and an `sload` when the array is stored in storage.

This can be applied for any arithmetic operation including `+=`, `-=`,`/=`,`*=`,`^=`,`&=`, `%=`, `<<=`,`>>=`, and `>>>=`.

This optimization can be particularly significant if the pattern occurs during a loop.

*Saves 28 gas for a storage array, 38 for a memory array*

*There are 2 instance(s) of this issue:*

```solidity
File: src/transformers/AutoCompound.sol

250:         positionBalances[tokenId][token] = positionBalances[tokenId][token] + amount;

270:         positionBalances[tokenId][token] = positionBalances[tokenId][token] - amount;

```


*GitHub* : [250](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L250), [270](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L270)

### [G-03]<a name="g-03"></a> Using bools for storage incurs overhead

Use uint256(1) and uint256(2) for true/false to avoid a Gwarmaccess (100 gas), and to avoid Gsset (20000 gas) when changing from ‘false’ to ‘true’, after having been ‘true’ in the past. See [source](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/58f635312aa21f947cae5f8578638a85aa2519f5/contracts/security/ReentrancyGuard.sol#L23-L27).

*There are 4 instance(s) of this issue:*

```solidity
File: src/V3Vault.sol

163:     mapping(address => bool) public transformerAllowList; // contracts allowed to transform positions (selected audited contracts e.g. V3Utils)

164:     mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; // owners permissions for other addresses to call transform on owners behalf (e.g. AutoRange contract)

```



*GitHub* : [163](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L163), [164](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L164)

```solidity
File: src/automators/Automator.sol

34:     mapping(address => bool) public operators;

35:     mapping(address => bool) public vaults;

```


*GitHub* : [34](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L34), [35](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L35)

### [G-04]<a name="g-04"></a> Use calldata instead of memory for function arguments that do not get mutated

When a function with a `memory` array is called externally, the `abi.decode()` step has to use a for-loop to copy each index of the `calldata` to the `memory` index. Each iteration of this for-loop costs at least 60 gas (i.e. `60 * <mem_array>.length`). Using `calldata` directly bypasses this loop. 

If the array is passed to an `internal` function which passes the array to another internal function where the array is modified and therefore `memory` is used in the `external` call, it's still more gas-efficient to use `calldata` when the `external` function uses modifiers, since the modifiers may prevent the internal functions from being called. Structs have the same overhead as an array of length one. 

 *Saves 60 gas per instance*

*There are 2 instance(s) of this issue:*

```solidity
File: src/transformers/V3Utils.sol

98:     function executeWithPermit(uint256 tokenId, Instructions memory instructions, uint8 v, bytes32 r, bytes32 s)

115:     function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {

```


*GitHub* : [98](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L98), [115](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L115)

### [G-05]<a name="g-05"></a> For Operations that will not overflow, you could use `unchecked`

*Saves 30-40 gas per instance*"

*There are 352 instance(s) of this issue:*

```solidity
File: src/InterestRateModel.sol

4: import "@openzeppelin/contracts/access/Ownable.sol";

6: import "./interfaces/IInterestRateModel.sol";

7: import "./interfaces/IErrors.sol";

12:     uint256 private constant Q96 = 2 ** 96;

13:     uint256 public constant YEAR_SECS = 31557600; // taking into account leap years

15:     uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10; // 10%

16:     uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%

50:         return debt * Q96 / (cash + debt);

67:             borrowRateX96 = (utilizationRateX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;

69:             uint256 normalRateX96 = (kinkX96 * multiplierPerSecondX96 / Q96) + baseRatePerSecondX96;

70:             uint256 excessUtilX96 = utilizationRateX96 - kinkX96;

71:             borrowRateX96 = (excessUtilX96 * jumpMultiplierPerSecondX96 / Q96) + normalRateX96;

74:         supplyRateX96 = utilizationRateX96 * borrowRateX96 / Q96;

95:         baseRatePerSecondX96 = baseRatePerYearX96 / YEAR_SECS;

96:         multiplierPerSecondX96 = multiplierPerYearX96 / YEAR_SECS;

97:         jumpMultiplierPerSecondX96 = jumpMultiplierPerYearX96 / YEAR_SECS;

```



*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L4), [6](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L6), [7](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L7), [12](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L12), [13](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L13), [15](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L15), [16](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L16), [50](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L50), [67](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L67), [69](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L69), [70](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L70), [71](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L71), [74](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L74), [95](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L95), [96](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L96), [97](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L97)

```solidity
File: src/V3Oracle.sol

4: import "v3-core/interfaces/IUniswapV3Factory.sol";

5: import "v3-core/interfaces/IUniswapV3Pool.sol";

7: import "v3-core/libraries/TickMath.sol";

9: import "v3-periphery/libraries/PoolAddress.sol";

10: import "v3-periphery/libraries/LiquidityAmounts.sol";

12: import "v3-periphery/interfaces/INonfungiblePositionManager.sol";

14: import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

15: import "@openzeppelin/contracts/access/Ownable.sol";

17: import "../lib/AggregatorV3Interface.sol";

19: import "./interfaces/IV3Oracle.sol";

20: import "./interfaces/IErrors.sol";

25:     uint16 public constant MIN_PRICE_DIFFERENCE = 200; //2%

27:     uint256 private constant Q96 = 2 ** 96;

28:     uint256 private constant Q128 = 2 ** 128;

37:         CHAINLINK_TWAP_VERIFY, // using chainlink for price and TWAP to verify

38:         TWAP_CHAINLINK_VERIFY, // using TWAP for price and chainlink to verify

39:         CHAINLINK, // using only chainlink directly

40:         TWAP // using TWAP directly

44:         AggregatorV3Interface feed; // chainlink feed

48:         IUniswapV3Pool pool; // reference pool

52:         uint16 maxDifference; // max price difference x10000

65:     uint16 public maxPoolPriceDifference = MIN_PRICE_DIFFERENCE; // max price difference between oracle derived price and pool price x10000

120:         value = (price0X96 * (amount0 + fees0) / Q96 + price1X96 * (amount1 + fees1) / Q96) * Q96 / priceTokenX96;

121:         feeValue = (price0X96 * fees0 / Q96 + price1X96 * fees1 / Q96) * Q96 / priceTokenX96;

122:         price0X96 = price0X96 * Q96 / priceTokenX96;

123:         price1X96 = price1X96 * Q96 / priceTokenX96;

129:         uint256 derivedPoolPriceX96 = price0X96 * Q96 / price1X96;

144:             ? (priceX96 - verifyPriceX96) * 10000 / priceX96

145:             : (verifyPriceX96 - priceX96) * 10000 / verifyPriceX96;

304:             chainlinkPriceX96 = (10 ** referenceTokenDecimals) * chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96

305:                 / (10 ** feedConfig.tokenDecimals);

338:         if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0) {

342:         return uint256(answer) * Q96 / (10 ** feedConfig.feedDecimals);

353:             poolTWAPPriceX96 = Q96 * Q96 / priceX96;

366:             secondsAgos[0] = 0; // from (before)

367:             secondsAgos[1] = twapSeconds; // from (before)

368:             (int56[] memory tickCumulatives,) = pool.observe(secondsAgos); // pool observe may fail when there is not enough history available (only use pool with enough history!)

369:             int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)));

440:         fees0 += state.tokensOwed0;

441:         fees1 += state.tokensOwed1;

463:             feeGrowth0 = feeGrowthInside0LastX128 - position.feeGrowthInside0LastX128;

464:             feeGrowth1 = feeGrowthInside1LastX128 - position.feeGrowthInside1LastX128;

486:                 feeGrowthInside0X128 = lowerFeeGrowthOutside0X128 - upperFeeGrowthOutside0X128;

487:                 feeGrowthInside1X128 = lowerFeeGrowthOutside1X128 - upperFeeGrowthOutside1X128;

489:                 feeGrowthInside0X128 = feeGrowthGlobal0X128 - lowerFeeGrowthOutside0X128 - upperFeeGrowthOutside0X128;

490:                 feeGrowthInside1X128 = feeGrowthGlobal1X128 - lowerFeeGrowthOutside1X128 - upperFeeGrowthOutside1X128;

492:                 feeGrowthInside0X128 = upperFeeGrowthOutside0X128 - lowerFeeGrowthOutside0X128;

493:                 feeGrowthInside1X128 = upperFeeGrowthOutside1X128 - lowerFeeGrowthOutside1X128;

```



*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L4), [5](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L5), [7](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L7), [9](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L9), [10](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L10), [12](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L12), [14](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L14), [15](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L15), [17](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L17), [19](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L19), [20](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L20), [25](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L25), [27](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L27), [28](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L28), [37](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L37), [38](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L38), [39](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L39), [40](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L40), [44](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L44), [48](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L48), [52](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L52), [65](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L65), [120](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L120), [121](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L121), [122](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L122), [123](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L123), [129](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L129), [144](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L144), [145](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L145), [304](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L304), [305](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L305), [338](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L338), [342](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L342), [353](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L353), [366](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L366), [367](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L367), [368](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L368), [369](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L369), [440](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L440), [441](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L441), [463](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L463), [464](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L464), [486](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L486), [487](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L487), [489](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L489), [490](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L490), [492](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L492), [493](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L493)

```solidity
File: src/V3Vault.sol

4: import "v3-core/interfaces/IUniswapV3Factory.sol";

5: import "v3-core/interfaces/IUniswapV3Pool.sol";

6: import "v3-core/libraries/TickMath.sol";

7: import "v3-core/libraries/FixedPoint128.sol";

9: import "v3-periphery/libraries/LiquidityAmounts.sol";

10: import "v3-periphery/interfaces/INonfungiblePositionManager.sol";

12: import "@openzeppelin/contracts/utils/math/Math.sol";

13: import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

14: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

15: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";

16: import "@openzeppelin/contracts/access/Ownable.sol";

17: import "@openzeppelin/contracts/utils/math/SafeCast.sol";

18: import "@openzeppelin/contracts/utils/Multicall.sol";

20: import "permit2/interfaces/IPermit2.sol";

22: import "./interfaces/IVault.sol";

23: import "./interfaces/IV3Oracle.sol";

24: import "./interfaces/IInterestRateModel.sol";

25: import "./interfaces/IErrors.sol";

33:     uint256 private constant Q32 = 2 ** 32;

34:     uint256 private constant Q96 = 2 ** 96;

36:     uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%

38:     uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%

39:     uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%

41:     uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%

43:     uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%

44:     uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%

70:     event Add(uint256 indexed tokenId, address owner, uint256 oldTokenId); // when a token is added replacing another token - oldTokenId > 0

90:     ); // shows exactly how liquidation amounts were divided

110:         uint32 collateralFactorX32; // how much this token is valued as collateral

111:         uint32 collateralValueLimitFactorX32; // how much asset equivalent may be lent out given this collateral

112:         uint192 totalDebtShares; // how much debt shares are theoretically backed by this collateral

154:     mapping(uint256 => Loan) public loans; // tokenID -> loan mapping

157:     mapping(address => uint256[]) private ownedTokens; // Mapping from owner address to list of owned token IDs

158:     mapping(uint256 => uint256) private ownedTokensIndex; // Mapping from token ID to index of the owner tokens list (for removal without loop)

159:     mapping(uint256 => address) private tokenOwner; // Mapping from token ID to owner

161:     uint256 private transformedTokenId = 0; // transient storage (when available in dencun)

163:     mapping(address => bool) public transformerAllowList; // contracts allowed to transform positions (selected audited contracts e.g. V3Utils)

164:     mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; // owners permissions for other addresses to call transform on owners behalf (e.g. AutoRange contract)

307:             return globalLendLimit - value;

318:             return _convertToShares(globalLendLimit - value, lendExchangeRateX96, Math.Rounding.Down);

567:         uint256 loanDebtShares = loan.debtShares + shares;

569:         debtSharesTotal += shares;

577:             dailyDebtIncreaseLimitLeft -= assets;

581:             tokenId, newDebtExchangeRateX96, newLendExchangeRateX96, loanDebtShares - shares, loanDebtShares

636:             params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),

637:             params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)

731:         debtSharesTotal -= debtShares;

769:             _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up) * reserveProtectionFactorX32 / Q32;

771:         uint256 unprotected = reserves > protected ? reserves - protected : 0;

913:             dailyLendIncreaseLimitLeft -= assets;

949:         dailyLendIncreaseLimitLeft += assets;

990:         uint256 loanDebtShares = loan.debtShares - shares;

992:         debtSharesTotal -= shares;

995:         dailyDebtIncreaseLimitLeft += assets;

998:             tokenId, newDebtExchangeRateX96, newLendExchangeRateX96, loanDebtShares + shares, loanDebtShares

1027:         reserves = balance + debt > lent ? balance + debt - lent : 0;

1028:         available = balance > reserves ? balance - reserves : 0;

1054:                 fees0 = uint128(liquidationValue * fees0 / feeValue);

1055:                 fees1 = uint128(liquidationValue * fees1 / feeValue);

1060:                 liquidity = uint128((liquidationValue - feeValue) * liquidity / (fullValue - feeValue));

1100:         uint256 maxPenaltyValue = debt * (Q32 + MAX_LIQUIDATION_PENALTY_X32) / Q32;

1105:             uint256 startLiquidationValue = debt * fullValue / collateralValue;

1107:                 (Q96 - ((fullValue - maxPenaltyValue) * Q96 / (startLiquidationValue - maxPenaltyValue)));

1109:                 + (MAX_LIQUIDATION_PENALTY_X32 - MIN_LIQUIDATION_PENALTY_X32) * penaltyFractionX96 / Q96;

1111:             liquidationValue = debt * (Q32 + penaltyX32) / Q32;

1116:             uint256 penaltyValue = fullValue * (Q32 - MAX_LIQUIDATION_PENALTY_X32) / Q32;

1118:             reserveCost = debt - penaltyValue;

1132:             missing = reserveCost - reserves;

1137:             newLendExchangeRateX96 = (totalLent - missing) * newLendExchangeRateX96 / totalLent;

1181:         supplyRateX96 = supplyRateX96.mulDiv(Q32 - reserveFactorX32, Q32);

1188:                 + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;

1190:                 + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;

1217:                 tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);

1218:                 tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);

1220:                 tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares);

1221:                 tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);

1230:                             > lentAssets * collateralValueLimitFactorX32 / Q32

1238:                             > lentAssets * collateralValueLimitFactorX32 / Q32

1248:         uint256 time = block.timestamp / 1 days;

1260:         uint256 time = block.timestamp / 1 days;

1304:         uint256 lastTokenIndex = ownedTokens[from].length - 1;

1313:         delete tokenOwner[tokenId]; // Remove the token from the token owner mapping

```



*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L5), [6](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L6), [7](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L7), [9](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L9), [10](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L10), [12](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L12), [13](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L13), [14](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L14), [15](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L15), [16](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L16), [17](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L17), [18](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L18), [20](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L20), [22](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L22), [23](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L23), [24](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L24), [25](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L25), [33](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L33), [34](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L34), [36](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L36), [38](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L38), [39](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L39), [41](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L41), [43](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L43), [44](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L44), [70](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L70), [90](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L90), [110](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L110), [111](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L111), [112](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L112), [154](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L154), [157](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L157), [158](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L158), [159](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L159), [161](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L161), [163](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L163), [164](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L164), [307](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L307), [318](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L318), [567](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L567), [569](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L569), [577](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L577), [581](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L581), [636](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L636), [637](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L637), [731](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L731), [769](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L769), [771](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L771), [913](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L913), [949](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L949), [990](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L990), [992](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L992), [995](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L995), [998](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L998), [1027](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1027), [1028](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1028), [1054](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1054), [1055](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1055), [1060](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1060), [1100](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1100), [1105](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1105), [1107](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1107), [1109](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1109), [1111](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1111), [1116](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1116), [1118](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1118), [1132](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1132), [1137](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1137), [1181](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1181), [1188](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1188), [1190](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1190), [1217](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1217), [1218](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1218), [1220](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1220), [1221](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1221), [1230](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1230), [1238](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1238), [1248](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1248), [1260](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1260), [1304](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1304), [1313](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L1313)

```solidity
File: src/automators/AutoExit.sol

4: import "./Automator.sol";

45:         bool isActive; // if position is active

50:         int24 token0TriggerTick; // when tick is below this one

51:         int24 token1TriggerTick; // when tick is equal or above this one

53:         uint64 token0SlippageX64; // when token 0 is swapped to token 1

54:         uint64 token1SlippageX64; // when token 1 is swapped to token 0

55:         bool onlyFees; // if only fees maybe used for protocol reward

56:         uint64 maxRewardX64; // max allowed reward percentage of fees or full position

64:         uint256 tokenId; // tokenid to process

65:         bytes swapData; // if its a swap order - must include swap data

66:         uint128 liquidity; // liquidity the calculations are based on

67:         uint256 amountRemoveMin0; // min amount to be removed from liquidity

68:         uint256 amountRemoveMin1; // min amount to be removed from liquidity

69:         uint256 deadline; // for uniswap operations - operator promises fair value

70:         uint64 rewardX64; // which reward will be used for protocol, can be max configured amount (considering onlyFees)

155:                 state.amount0 -= state.feeAmount0 * params.rewardX64 / Q64;

156:                 state.amount1 -= state.feeAmount1 * params.rewardX64 / Q64;

181:             state.amount0 = state.isAbove ? state.amount0 + state.amountOutDelta : state.amount0 - state.amountInDelta;

182:             state.amount1 = state.isAbove ? state.amount1 - state.amountInDelta : state.amount1 + state.amountOutDelta;

187:                     state.amount0 -= state.amount0 * params.rewardX64 / Q64;

189:                     state.amount1 -= state.amount1 * params.rewardX64 / Q64;

194:             state.amount0 -= (config.onlyFees ? state.feeAmount0 : state.amount0) * params.rewardX64 / Q64;

195:             state.amount1 -= (config.onlyFees ? state.feeAmount1 : state.amount1) * params.rewardX64 / Q64;

```



*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L4), [45](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L45), [50](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L50), [51](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L51), [53](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L53), [54](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L54), [55](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L55), [56](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L56), [64](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L64), [65](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L65), [66](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L66), [67](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L67), [68](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L68), [69](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L69), [70](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L70), [155](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L155), [156](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L156), [181](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L181), [182](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L182), [187](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L187), [189](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L189), [194](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L194), [195](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L195)

```solidity
File: src/automators/Automator.sol

4: import "@openzeppelin/contracts/access/Ownable.sol";

5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

6: import "@openzeppelin/contracts/utils/math/SafeCast.sol";

8: import "v3-core/interfaces/IUniswapV3Factory.sol";

9: import "v3-core/interfaces/IUniswapV3Pool.sol";

10: import "v3-core/libraries/TickMath.sol";

11: import "v3-core/libraries/FullMath.sol";

13: import "v3-periphery/interfaces/INonfungiblePositionManager.sol";

15: import "../../lib/IWETH9.sol";

16: import "../utils/Swapper.sol";

17: import "../interfaces/IVault.sol";

20:     uint256 internal constant Q64 = 2 ** 64;

21:     uint256 internal constant Q96 = 2 ** 96;

23:     uint32 public constant MIN_TWAP_SECONDS = 60; // 1 minute

24:     uint32 public constant MAX_TWAP_TICK_DIFFERENCE = 200; // 2%

111:         for (; i < count; ++i) {

158:             amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), priceX96, Q96 * Q64);

160:             amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), Q96, priceX96 * Q64);

173:             return twapTick - currentTick >= -int16(maxDifference) && twapTick - currentTick <= int16(maxDifference);

182:         secondsAgos[0] = 0; // from (before)

183:         secondsAgos[1] = twapPeriod; // from (before)

187:             return (int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapPeriod))), true);

213:         feeAmount0 = amount0 - feeAmount0;

214:         feeAmount1 = amount1 - feeAmount1;

```



*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L4), [5](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L5), [6](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L6), [8](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L8), [9](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L9), [10](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L10), [11](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L11), [13](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L13), [15](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L15), [16](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L16), [17](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L17), [20](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L20), [21](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L21), [23](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L23), [24](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L24), [111](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L111), [158](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L158), [160](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L160), [173](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L173), [182](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L182), [183](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L183), [187](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L187), [213](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L213), [214](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L214)

```solidity
File: src/transformers/AutoCompound.sol

4: import "@openzeppelin/contracts/security/ReentrancyGuard.sol";

5: import "@openzeppelin/contracts/utils/Multicall.sol";

6: import "@openzeppelin/contracts/utils/math/SafeMath.sol";

8: import "v3-periphery/interfaces/INonfungiblePositionManager.sol";

10: import "../automators/Automator.sol";

47:     uint64 public constant MAX_REWARD_X64 = uint64(Q64 / 50); // 2%

48:     uint64 public totalRewardX64 = MAX_REWARD_X64; // 2%

119:         state.amount0 = state.amount0 + positionBalances[params.tokenId][state.token0];

120:         state.amount1 = state.amount1 + positionBalances[params.tokenId][state.token1];

148:                         params.swap0To1 ? state.amount0 - state.amountInDelta : state.amount0 + state.amountOutDelta;

150:                         params.swap0To1 ? state.amount1 + state.amountOutDelta : state.amount1 - state.amountInDelta;

156:             state.maxAddAmount0 = state.amount0 * Q64 / (rewardX64 + Q64);

157:             state.maxAddAmount1 = state.amount1 * Q64 / (rewardX64 + Q64);

170:                 state.amount0Fees = state.compounded0 * rewardX64 / Q64;

171:                 state.amount1Fees = state.compounded1 * rewardX64 / Q64;

175:             _setBalance(params.tokenId, state.token0, state.amount0 - state.compounded0 - state.amount0Fees);

176:             _setBalance(params.tokenId, state.token1, state.amount1 - state.compounded1 - state.amount1Fees);

233:         for (; i < count; ++i) {

250:         positionBalances[tokenId][token] = positionBalances[tokenId][token] + amount;

259:                 emit BalanceAdded(tokenId, token, amount - currentBalance);

261:                 emit BalanceRemoved(tokenId, token, currentBalance - amount);

270:         positionBalances[tokenId][token] = positionBalances[tokenId][token] - amount;

```



*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L4), [5](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L5), [6](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L6), [8](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L8), [10](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L10), [47](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L47), [48](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L48), [119](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L119), [120](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L120), [148](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L148), [150](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L150), [156](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L156), [157](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L157), [170](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L170), [171](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L171), [175](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L175), [176](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L176), [233](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L233), [250](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L250), [259](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L259), [261](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L261), [270](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L270)

```solidity
File: src/transformers/AutoRange.sol

4: import "../automators/Automator.sol";

39:         int32 lowerTickLimit; // if negative also in-range positions may be adjusted / if 0 out of range positions may be adjusted

40:         int32 upperTickLimit; // if negative also in-range positions may be adjusted / if 0 out of range positions may be adjusted

41:         int32 lowerTickDelta; // this amount is added to current tick (floored to tickspacing) to define lowerTick of new position

42:         int32 upperTickDelta; // this amount is added to current tick (floored to tickspacing) to define upperTick of new position

43:         uint64 token0SlippageX64; // max price difference from current pool price for swap / Q64 for token0

44:         uint64 token1SlippageX64; // max price difference from current pool price for swap / Q64 for token1

45:         bool onlyFees; // if only fees maybe used for protocol reward

46:         uint64 maxRewardX64; // max allowed reward percentage of fees or full position

56:         uint256 amountIn; // if this is set to 0 no swap happens

58:         uint128 liquidity; // liquidity the calculations are based on

59:         uint256 amountRemoveMin0; // min amount to be removed from liquidity

60:         uint256 amountRemoveMin1; // min amount to be removed from liquidity

61:         uint256 deadline; // for uniswap operations - operator promises fair value

62:         uint64 rewardX64; // which reward will be used for protocol, can be max configured amount (considering onlyFees)

143:             state.protocolReward0 = state.feeAmount0 * params.rewardX64 / Q64;

144:             state.protocolReward1 = state.feeAmount1 * params.rewardX64 / Q64;

145:             state.amount0 -= state.protocolReward0;

146:             state.amount1 -= state.protocolReward1;

167:             state.currentTick < state.tickLower - config.lowerTickLimit

168:                 || state.currentTick >= state.tickUpper + config.upperTickLimit

171:             int24 baseTick = state.currentTick - (((state.currentTick % tickSpacing) + tickSpacing) % tickSpacing);

175:                 baseTick + config.lowerTickDelta == state.tickLower

176:                     && baseTick + config.upperTickDelta == state.tickUpper

191:             state.amount0 = params.swap0To1 ? state.amount0 - state.amountInDelta : state.amount0 + state.amountOutDelta;

192:             state.amount1 = params.swap0To1 ? state.amount1 + state.amountOutDelta : state.amount1 - state.amountInDelta;

195:             state.maxAddAmount0 = config.onlyFees ? state.amount0 : state.amount0 * Q64 / (params.rewardX64 + Q64);

196:             state.maxAddAmount1 = config.onlyFees ? state.amount1 : state.amount1 * Q64 / (params.rewardX64 + Q64);

202:                 SafeCast.toInt24(baseTick + config.lowerTickDelta), // reverts if out of valid range

203:                 SafeCast.toInt24(baseTick + config.upperTickDelta), // reverts if out of valid range

208:                 address(this), // is sent to real recipient aftwards

236:                 state.protocolReward0 = state.amountAdded0 * params.rewardX64 / Q64;

237:                 state.protocolReward1 = state.amountAdded1 * params.rewardX64 / Q64;

238:                 state.amount0 -= state.protocolReward0;

239:                 state.amount1 -= state.protocolReward1;

243:             if (state.amount0 - state.amountAdded0 > 0) {

244:                 _transferToken(state.realOwner, IERC20(state.token0), state.amount0 - state.amountAdded0, true);

246:             if (state.amount1 - state.amountAdded1 > 0) {

247:                 _transferToken(state.realOwner, IERC20(state.token1), state.amount1 - state.amountAdded1, true);

```



*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L4), [39](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L39), [40](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L40), [41](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L41), [42](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L42), [43](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L43), [44](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L44), [45](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L45), [46](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L46), [56](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L56), [58](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L58), [59](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L59), [60](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L60), [61](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L61), [62](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L62), [143](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L143), [144](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L144), [145](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L145), [146](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L146), [167](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L167), [168](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L168), [171](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L171), [175](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L175), [176](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L176), [191](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L191), [192](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L192), [195](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L195), [196](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L196), [202](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L202), [203](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L203), [208](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L208), [236](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L236), [237](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L237), [238](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L238), [239](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L239), [243](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L243), [244](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L244), [246](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L246), [247](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L247)

```solidity
File: src/transformers/LeverageTransformer.sol

4: import "@openzeppelin/contracts/utils/math/SafeCast.sol";

5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

7: import "../utils/Swapper.sol";

8: import "../interfaces/IVault.sol";

25:         bytes swapData0; // encoded data from 0x api call (address,bytes) - allowanceTarget,data

29:         bytes swapData1; // encoded data from 0x api call (address,bytes) - allowanceTarget,data

59:                 amount1 -= amountIn;

61:             amount -= amountIn;

62:             amount0 += amountOut;

71:                 amount0 -= amountIn;

73:             amount -= amountIn;

74:             amount1 += amountOut;

88:             SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0 - added0);

91:             SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1 - added1);

111:         bytes swapData0; // encoded data from 0x api call (address,bytes) - allowanceTarget,data

115:         bytes swapData1; // encoded data from 0x api call (address,bytes) - allowanceTarget,data

139:             params.feeAmount0 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount0 + params.feeAmount0),

140:             params.feeAmount1 == type(uint128).max ? type(uint128).max : SafeCast.toUint128(amount1 + params.feeAmount1)

152:             amount0 -= amountIn;

153:             amount += amountOut;

161:             amount1 -= amountIn;

162:             amount += amountOut;

```



*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L4), [5](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L5), [7](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L7), [8](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L8), [25](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L25), [29](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L29), [59](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L59), [61](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L61), [62](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L62), [71](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L71), [73](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L73), [74](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L74), [88](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L88), [91](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L91), [111](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L111), [115](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L115), [139](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L139), [140](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L140), [152](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L152), [153](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L153), [161](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L161), [162](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/LeverageTransformer.sol#L162)

```solidity
File: src/transformers/V3Utils.sol

4: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";

5: import "@openzeppelin/contracts/utils/math/SafeCast.sol";

7: import "permit2/interfaces/IPermit2.sol";

9: import "../utils/Swapper.sol";

60:         bytes swapData0; // encoded data from 0x api call (address,bytes) - allowanceTarget,data

65:         bytes swapData1; // encoded data from 0x api call (address,bytes) - allowanceTarget,data

135:                 : (amount0 + instructions.feeAmount0).toUint128(),

138:                 : (amount1 + instructions.feeAmount1).toUint128()

317:                     _transferToken(instructions.recipient, IERC20(token0), amount0 - amountInDelta, instructions.unwrap);

319:                 targetAmount += amountOutDelta;

321:                 targetAmount += amount0;

334:                     _transferToken(instructions.recipient, IERC20(token1), amount1 - amountInDelta, instructions.unwrap);

336:                 targetAmount += amountOutDelta;

338:                 targetAmount += amount1;

387:         address recipient; // recipient of tokenOut and leftover tokenIn (if any leftover)

389:         bool unwrap; // if tokenIn or tokenOut is WETH - unwrap

390:         bytes permitData; // if permit2 signatures are used - set this

425:         uint256 leftOver = params.amountIn - amountInDelta;

441:         address recipient; // recipient of leftover tokens

442:         address recipientNFT; // recipient of nft

485:                 params.amountIn0 + params.amountIn1,

496:                 params.amountIn0 + params.amountIn1

509:         address recipient; // recipient of leftover tokens

548:                 params.amountIn0 + params.amountIn1,

559:                 params.amountIn0 + params.amountIn1

619:             transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed0);

623:             transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.needed1);

627:             transferDetails[state.i++] = ISignatureTransfer.SignatureTransferDetails(address(this), state.neededOther);

635:             if (token0.balanceOf(address(this)) - state.balanceBefore0 != state.needed0) {

636:                 revert TransferError(); // reverts for fee-on-transfer tokens

640:             if (token1.balanceOf(address(this)) - state.balanceBefore1 != state.needed1) {

641:                 revert TransferError(); // reverts for fee-on-transfer tokens

645:             if (otherToken.balanceOf(address(this)) - state.balanceBeforeOther != state.neededOther) {

646:                 revert TransferError(); // reverts for fee-on-transfer tokens

691:             needed0 = amount0 - amountAdded0;

694:             needed1 = amount1 - amountAdded1;

700:             neededOther = amountOther - amountAddedOther;

721:             address(this), // is sent to real recipient aftwards

792:             total0 = params.amount0 - amountInDelta;

793:             total1 = params.amount1 + amountOutDelta;

803:             total1 = params.amount1 - amountInDelta;

804:             total0 = params.amount0 + amountOutDelta;

816:             total0 = params.amount0 + amountOutDelta0;

817:             total1 = params.amount1 + amountOutDelta1;

820:             uint256 leftOver = params.amountIn0 + params.amountIn1 - amountInDelta0 - amountInDelta1;

851:         uint256 left0 = total0 - added0;

852:         uint256 left1 = total1 - added1;

905:         if (balanceAfter0 - balanceBefore0 != amount0) {

908:         if (balanceAfter1 - balanceBefore1 != amount1) {

```



*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L4), [5](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L5), [7](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L7), [9](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L9), [60](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L60), [65](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L65), [135](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L135), [138](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L138), [317](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L317), [319](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L319), [321](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L321), [334](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L334), [336](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L336), [338](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L338), [387](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L387), [389](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L389), [390](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L390), [425](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L425), [441](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L441), [442](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L442), [485](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L485), [496](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L496), [509](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L509), [548](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L548), [559](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L559), [619](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L619), [623](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L623), [627](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L627), [635](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L635), [636](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L636), [640](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L640), [641](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L641), [645](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L645), [646](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L646), [691](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L691), [694](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L694), [700](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L700), [721](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L721), [792](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L792), [793](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L793), [803](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L803), [804](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L804), [816](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L816), [817](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L817), [820](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L820), [851](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L851), [852](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L852), [905](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L905), [908](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L908)

```solidity
File: src/utils/FlashloanLiquidator.sol

4: import "v3-core/interfaces/IUniswapV3Pool.sol";

5: import "v3-core/interfaces/callback/IUniswapV3FlashCallback.sol";

7: import "../interfaces/IVault.sol";

8: import "./Swapper.sol";

29:         uint256 tokenId; // loan to liquidate

30:         uint256 debtShares; // debt shares calculation is based on

31:         IVault vault; // vault where the loan is

32:         IUniswapV3Pool flashLoanPool; // pool which is used for flashloan - may not be used in the swaps below

33:         uint256 amount0In; // how much of token0 to swap to asset (0 if no swap should be done)

34:         bytes swapData0; // swap data for token0 swap

35:         uint256 amount1In; // how much of token1 to swap to asset (0 if no swap should be done)

36:         bytes swapData1; // swap data for token1 swap

37:         uint256 minReward; // min reward amount (works as a global slippage control for complete operation)

85:         SafeERC20.safeTransfer(data.asset, msg.sender, data.liquidationCost + (fee0 + fee1));

```



*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L4), [5](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L5), [7](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L7), [8](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L8), [29](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L29), [30](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L30), [31](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L31), [32](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L32), [33](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L33), [34](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L34), [35](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L35), [36](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L36), [37](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L37), [85](https://github.com/code-423n4/2024-03-revert-lend/src/utils/FlashloanLiquidator.sol#L85)

```solidity
File: src/utils/Swapper.sol

4: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

6: import "v3-core/interfaces/callback/IUniswapV3SwapCallback.sol";

7: import "v3-core/interfaces/IUniswapV3Pool.sol";

8: import "v3-core/libraries/TickMath.sol";

10: import "v3-periphery/interfaces/INonfungiblePositionManager.sol";

12: import "../../lib/IWETH9.sol";

13: import "../../lib/IUniversalRouter.sol";

14: import "../interfaces/IErrors.sol";

107:             amountInDelta = balanceInBefore - balanceInAfter;

108:             amountOutDelta = balanceOutAfter - balanceOutBefore;

138:                 (params.swap0For1 ? TickMath.MIN_SQRT_RATIO + 1 : TickMath.MAX_SQRT_RATIO - 1),

146:             amountOutDelta = params.swap0For1 ? uint256(-amount1Delta) : uint256(-amount0Delta);

157:         require(amount0Delta > 0 || amount1Delta > 0); // swaps entirely within 0-liquidity regions are not supported

```


*GitHub* : [4](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L4), [6](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L6), [7](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L7), [8](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L8), [10](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L10), [12](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L12), [13](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L13), [14](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L14), [107](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L107), [108](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L108), [138](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L138), [146](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L146), [157](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L157)

### [G-06]<a name="g-06"></a> Use Custom Errors instead of Revert Strings to save Gas

Custom errors are available from solidity version 0.8.4. Custom errors save [**~50 gas**](https://gist.github.com/IllIllI000/ad1bd0d29a0101b25e57c293b4b0c746) each time they're hit by [avoiding having to allocate and store the revert string](https://blog.soliditylang.org/2021/04/21/custom-errors/#errors-in-depth). Not defining the strings also save deployment gas

Additionally, custom errors can be used inside and outside of contracts (including interfaces and libraries).

Source: <https://blog.soliditylang.org/2021/04/21/custom-errors/>:

> Starting from [Solidity v0.8.4](https://github.com/ethereum/solidity/releases/tag/v0.8.4), there is a convenient and gas-efficient way to explain to users why an operation failed through the use of custom errors. Until now, you could already use strings to give more information about failures (e.g., `revert("Insufficient funds.");`), but they are rather expensive, especially when it comes to deploy cost, and it is difficult to use dynamic information in them.

Consider replacing **all revert strings** with custom errors in the solution, and particularly those that have multiple occurrences:

*There are 2 instance(s) of this issue:*

```solidity
File: src/transformers/AutoCompound.sol

244:         require(_totalRewardX64 <= totalRewardX64, ">totalRewardX64");

269:         require(amount <= balance, "amount>balance");

```


*GitHub* : [244](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L244), [269](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L269)

### [G-07]<a name="g-07"></a> Using `private` rather than `public`, saves gas

If needed, the values can be read from the verified contract source code, or if there are multiple values there can be a single getter function that [returns a tuple](https://github.com/code-423n4/2022-08-frax/blob/90f55a9ce4e25bceed3a74290b854341d8de6afa/src/contracts/FraxlendPair.sol#L156-L178) of the values of all currently-public constants. Saves **3406-3606 gas** in deployment gas due to the compiler not having to create non-payable getter functions for deployment calldata, not having to store the bytes of the value outside of where it's used, and not adding another entry to the method ID table

*There are 66 instance(s) of this issue:*

```solidity
File: src/InterestRateModel.sol

13:     uint256 public constant YEAR_SECS = 31557600; // taking into account leap years

15:     uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10; // 10%

16:     uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%

23:     uint256 public multiplierPerSecondX96;

24:     uint256 public baseRatePerSecondX96;

25:     uint256 public jumpMultiplierPerSecondX96;

26:     uint256 public kinkX96;

```



*GitHub* : [13](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L13), [15](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L15), [16](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L16), [23](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L23), [24](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L24), [25](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L25), [26](https://github.com/code-423n4/2024-03-revert-lend/src/InterestRateModel.sol#L26)

```solidity
File: src/V3Oracle.sol

25:     uint16 public constant MIN_PRICE_DIFFERENCE = 200; //2%

56:     mapping(address => TokenConfig) public feedConfigs;

58:     address public immutable factory;

59:     INonfungiblePositionManager public immutable nonfungiblePositionManager;

62:     address public immutable referenceToken;

63:     uint8 public immutable referenceTokenDecimals;

65:     uint16 public maxPoolPriceDifference = MIN_PRICE_DIFFERENCE; // max price difference between oracle derived price and pool price x10000

68:     address public immutable chainlinkReferenceToken;

71:     address public emergencyAdmin;

```



*GitHub* : [25](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L25), [56](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L56), [58](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L58), [59](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L59), [62](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L62), [63](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L63), [65](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L65), [68](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L68), [71](https://github.com/code-423n4/2024-03-revert-lend/src/V3Oracle.sol#L71)

```solidity
File: src/V3Vault.sol

36:     uint32 public constant MAX_COLLATERAL_FACTOR_X32 = uint32(Q32 * 90 / 100); // 90%

38:     uint32 public constant MIN_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 2 / 100); // 2%

39:     uint32 public constant MAX_LIQUIDATION_PENALTY_X32 = uint32(Q32 * 10 / 100); // 10%

41:     uint32 public constant MIN_RESERVE_PROTECTION_FACTOR_X32 = uint32(Q32 / 100); //1%

43:     uint32 public constant MAX_DAILY_LEND_INCREASE_X32 = uint32(Q32 / 10); //10%

44:     uint32 public constant MAX_DAILY_DEBT_INCREASE_X32 = uint32(Q32 / 10); //10%

47:     INonfungiblePositionManager public immutable nonfungiblePositionManager;

50:     IUniswapV3Factory public immutable factory;

53:     IInterestRateModel public immutable interestRateModel;

56:     IV3Oracle public immutable oracle;

59:     IPermit2 public immutable permit2;

62:     address public immutable override asset;

115:     mapping(address => TokenConfig) public tokenConfigs;

118:     uint32 public reserveFactorX32 = 0;

121:     uint32 public reserveProtectionFactorX32 = MIN_RESERVE_PROTECTION_FACTOR_X32;

124:     uint256 public debtSharesTotal = 0;

127:     uint256 public lastExchangeRateUpdate = 0;

128:     uint256 public lastDebtExchangeRateX96 = Q96;

129:     uint256 public lastLendExchangeRateX96 = Q96;

131:     uint256 public globalDebtLimit = 0;

132:     uint256 public globalLendLimit = 0;

135:     uint256 public minLoanSize = 0;

138:     uint256 public dailyLendIncreaseLimitMin = 0;

139:     uint256 public dailyLendIncreaseLimitLeft = 0;

140:     uint256 public dailyLendIncreaseLimitLastReset = 0;

143:     uint256 public dailyDebtIncreaseLimitMin = 0;

144:     uint256 public dailyDebtIncreaseLimitLeft = 0;

145:     uint256 public dailyDebtIncreaseLimitLastReset = 0;

154:     mapping(uint256 => Loan) public loans; // tokenID -> loan mapping

163:     mapping(address => bool) public transformerAllowList; // contracts allowed to transform positions (selected audited contracts e.g. V3Utils)

164:     mapping(address => mapping(uint256 => mapping(address => bool))) public transformApprovals; // owners permissions for other addresses to call transform on owners behalf (e.g. AutoRange contract)

167:     address public emergencyAdmin;

```



*GitHub* : [36](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L36), [38](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L38), [39](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L39), [41](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L41), [43](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L43), [44](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L44), [47](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L47), [50](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L50), [53](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L53), [56](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L56), [59](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L59), [62](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L62), [115](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L115), [118](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L118), [121](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L121), [124](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L124), [127](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L127), [128](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L128), [129](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L129), [131](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L131), [132](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L132), [135](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L135), [138](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L138), [139](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L139), [140](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L140), [143](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L143), [144](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L144), [145](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L145), [154](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L154), [163](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L163), [164](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L164), [167](https://github.com/code-423n4/2024-03-revert-lend/src/V3Vault.sol#L167)

```solidity
File: src/automators/AutoExit.sol

60:     mapping(uint256 => PositionConfig) public positionConfigs;

```



*GitHub* : [60](https://github.com/code-423n4/2024-03-revert-lend/src/automators/AutoExit.sol#L60)

```solidity
File: src/automators/Automator.sol

23:     uint32 public constant MIN_TWAP_SECONDS = 60; // 1 minute

24:     uint32 public constant MAX_TWAP_TICK_DIFFERENCE = 200; // 2%

34:     mapping(address => bool) public operators;

35:     mapping(address => bool) public vaults;

37:     address public withdrawer;

38:     uint32 public TWAPSeconds;

39:     uint16 public maxTWAPTickDifference;

```



*GitHub* : [23](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L23), [24](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L24), [34](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L34), [35](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L35), [37](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L37), [38](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L38), [39](https://github.com/code-423n4/2024-03-revert-lend/src/automators/Automator.sol#L39)

```solidity
File: src/transformers/AutoCompound.sol

45:     mapping(uint256 => mapping(address => uint256)) public positionBalances;

47:     uint64 public constant MAX_REWARD_X64 = uint64(Q64 / 50); // 2%

48:     uint64 public totalRewardX64 = MAX_REWARD_X64; // 2%

```



*GitHub* : [45](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L45), [47](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L47), [48](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoCompound.sol#L48)

```solidity
File: src/transformers/AutoRange.sol

50:     mapping(uint256 => PositionConfig) public positionConfigs;

```



*GitHub* : [50](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/AutoRange.sol#L50)

```solidity
File: src/transformers/V3Utils.sol

19:     IPermit2 public immutable permit2;

```



*GitHub* : [19](https://github.com/code-423n4/2024-03-revert-lend/src/transformers/V3Utils.sol#L19)

```solidity
File: src/utils/Swapper.sol

21:     IWETH9 public immutable weth;

23:     address public immutable factory;

26:     INonfungiblePositionManager public immutable nonfungiblePositionManager;

29:     address public immutable zeroxRouter;

32:     address public immutable universalRouter;

```


*GitHub* : [21](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L21), [23](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L23), [26](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L26), [29](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L29), [32](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L32)

### [G-08]<a name="g-08"></a> WETH address definition can be use directly

WETH is a wrap Ether contract with a specific address in the Ethereum network, giving the option to define it may cause false recognition, it is healthier to define it directly.

    Advantages of defining a specific contract directly:
    
    It saves gas,
    Prevents incorrect argument definition,
    Prevents execution on a different chain and re-signature issues,
    WETH Address : 0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2

*There are 1 instance(s) of this issue:*

```solidity
File: src/utils/Swapper.sol

21:     IWETH9 public immutable weth;

```


*GitHub* : [21](https://github.com/code-423n4/2024-03-revert-lend/src/utils/Swapper.sol#L21)
