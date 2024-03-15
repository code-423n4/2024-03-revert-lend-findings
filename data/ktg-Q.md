### L-01: AutoRange incorrect maxAmountAdd calculation
Function `AutoRange.execute` currently calculates maxAmountAdd as follows:
```solidity
// max amount to add - removing max potential fees (if config.onlyFees - the have been removed already)
            state.maxAddAmount0 = config.onlyFees ? state.amount0 : state.amount0 * Q64 / (params.rewardX64 + Q64);
            state.maxAddAmount1 = config.onlyFees ? state.amount1 : state.amount1 * Q64 / (params.rewardX64 + Q64);
```
In case `onlyFees = False`, the maxAddAmount is calculated as `state.amount * (Q64)/ (rewardX64 + Q64)`, this is for `removing max potentials fees` (to keep enough token as fee for operator). However, this calculation is wrong for large `rewardX64`, since `rewardX64` reflect the percentage at which the reward is calculated, then the formula must be `1 - (rewardX64)/Q64`

So if `rewardX64` = 20%, then `maxAddAmount` should be 80%, but in fact, it's calculated as  `1/(1+0.2)` = 83.3%.

### L-02: AutoExit does not work with Revert Lend position
`AutoExit` does not work with Revert Lend position, function `configToken` will revert if `msg.sender` is not the owner:
```solidity
address owner = nonfungiblePositionManager.ownerOf(tokenId);
        if (owner != msg.sender) {
            revert Unauthorized();
        }
```
So after transferring NFT to Revert Lend Vault, `AutoExit` cannot be used.
Function `execute` also allow only `operator` to call, not `vault`:
```solidity
function execute(ExecuteParams calldata params) external {
        if (!operators[msg.sender]) {
            revert Unauthorized();
        }
...
``` 


### L-03: `Automator.setVault` should check if the vault has the same NonfungiblePositionManager with the automator
```solidity
function setVault(address _vault, bool _active) public onlyOwner {
        emit VaultChanged(_vault, _active);
        vaults[_vault] = _active;
    }
```
Function `setVault` does not check if `_vault` having the same `nonfungiblePositionManager` with the contract.
If they don't match, then incorrect operations might be applied on user positions, since function `configToken` does not differentiate which `vault` the tokenId associated with:
```solidity
function configToken(uint256 tokenId, address vault, PositionConfig calldata config) external {
        _validateOwner(tokenId, vault);

        // lower tick must be always below or equal to upper tick - if they are equal - range adjustment is deactivated
        if (config.lowerTickDelta > config.upperTickDelta) {
            revert InvalidConfig();
        }
```

### L-04: Approval is not cleared in `AutoCompound`
Function `execute` of `AutoCompound` approves `nonfungiblePositionManager` max amount and then doesn't reset it:
```
if (state.maxAddAmount0 > 0 || state.maxAddAmount1 > 0) {
                _checkApprovals(state.token0, state.token1);

function _checkApprovals(address token0, address token1) internal {
        // approve tokens once if not yet approved - to save gas during compounds
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
### L-05: Users cannot withdraw their tokens after they burn their Uniswap Position
The `positionBalances` current track left over tokens based on `tokenId` in Uniswap Pool. This mean if the burn their nft, they cannot get left over tokens in AutoCompound back:
```solidity
function withdrawLeftoverBalances(uint256 tokenId, address to) external nonReentrant {
        address owner = nonfungiblePositionManager.ownerOf(tokenId);
        if (vaults[owner]) {
            owner = IVault(owner).ownerOf(tokenId);
        }
        if (owner != msg.sender) {
            revert Unauthorized();
        }
```
Even if the user burn their nft, they should be able to withdraw their tokens in AutoRange, therefore, the variables `positionBalances` should track balances based on the actual address of the owner instead of `tokenId`


### L-06: V3Oracle.maxPoolPriceDifference is limited to uint16 value
`maxPoolPriceDifference` is used in function `_requireMaxDifference` to check if there is too much difference in prices:
```solidity
function _requireMaxDifference(uint256 priceX96, uint256 verifyPriceX96, uint256 maxDifferenceX10000)
        internal
        pure
    {
        uint256 differenceX10000 = priceX96 > verifyPriceX96
            ? (priceX96 - verifyPriceX96) * 10000 / priceX96
            : (verifyPriceX96 - priceX96) * 10000 / verifyPriceX96;
        // if too big difference - revert
        if (differenceX10000 >= maxDifferenceX10000) {
            revert PriceDifferenceExceeded();
        }
    }
```
The function accepts `maxDifferenceX10000` as `uint256` but its max value is 2**16-1 = 65535, which means the maximum difference is about 650 percent.