# Low-Severity

## [L-01] Check address `to` for `address(0)` before transferring ethers (*Note: Instance missed by bot*)

It's indeed a good practice to check if the destination address (`to` address) is not the zero address before transferring `ethers`. This is to ensure that accidental transfers to the zero address do not occur, which could result in the loss of funds since transactions to the zero address are typically irreversible.

```solidity
File : src/automators/Automator.sol

123:   function withdrawETH(address to) external {
           if (msg.sender != withdrawer) {
               revert Unauthorized();
            }

        uint256 balance = address(this).balance;
        if (balance > 0) {
            (bool sent,) = to.call{value: balance}("");
            if (!sent) {
                revert EtherSendFailed();
            }

```
[123-133](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L123C4-L133C14)

# Non-critical

## [N-01] Do not use shadowed variable `owner` in `withdraw` function

This can lead to confusion when referencing the variable `owner` within the `withdraw` function because the parameter `owner` will take precedence over the inherited state variable `owner`. Shadowing can lead to bugs if the developer mistakenly references the wrong variable within the function. Shadowing can make the code less clear and readable.

```solidity
File : src/V3Vault.sol

372:     function withdraw(uint256 assets, address receiver, address owner) external override returns (uint256) {

```
[372](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L372)

## [N-02] Changing the visibility of functions from `public` to `external` when it's not intended to be called within the contract itself (*Note: Instances missed by bot*)

Declaring a function as `external` clearly communicates to developers that the function is intended to be called from outside the contract. This can improve code readability and reduce the risk of unintended internal calls.

### Changing the visibility of `getRatesPerSecondX96` function from `public` to `external`

```solidity
File : src/InterestRateModel.sol

58:    function getRatesPerSecondX96(uint256 cash, uint256 debt)
59:        public
           view
           override
           returns (uint256 borrowRateX96, uint256 supplyRateX96)
        {

```
[58-63](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L58C1-L63C6)

### Changing the visibility of `previewDeposit`, `previewMint`, `previewWithdraw` and `previewRedeem` functions from `public` to `external`

```solidity
File : src/V3Vault.sol

334:     function previewDeposit(uint256 assets) public view override returns (uint256) {

340:     function previewMint(uint256 shares) public view override returns (uint256) { 

346:     function previewWithdraw(uint256 assets) public view override returns (uint256) {   

352:     function previewRedeem(uint256 shares) public view override returns (uint256) {        

```
[334](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L334), [340](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L340), [346](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L346), [352](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L352)   

## [N-03] Typos (*Note: missed by bot*)

### `owner's` not `owners`

```diff
File : src/V3Vault.sol

-934:   // if caller has allowance for owners shares - may call withdraw
+934:   // if caller has allowance for owner's shares - may call withdraw

```
[934](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L934)