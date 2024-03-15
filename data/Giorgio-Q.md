## Ineffective deadline on decreaseLiquidity() 

##Links

https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1072-L1076

## Vulnerability details

Using block.timestamp as the deadline argument when interacting with the Uniswap NFT Position Manager renders the deadline ineffective and defeats its intended purpose.


## Impact 

Transaction may remain pending in the mempool, transactions can be maliciously executed at a later point, optmizing arbitrage on the MEV side.

## POC

[Here](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1072-L1076)

```solidity
      if (liquidity > 0) {
            nonfungiblePositionManager.decreaseLiquidity(
                INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp) 
            );
        }
```

We can see that block.timestamp is used as an argument, which will result in no deadline for the liquidity "swap".

## Mitigation route

Consider adding a parameter for the swap deadline.

## Use answer <= 0 instead answer < 0

## Link

https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Oracle.sol#L338

## Description

Under uncommon circumstances price feeds may return 0 which isn't desirable behavior, so it is best to add checks to avoid such conditions.

## Impact

The usage of 0 price is devastating to the protocol 

## POC

```
        if (updatedAt + feedConfig.maxFeedAge < block.timestamp || answer < 0) {
```

As we can see above, if 0 is returned it will be accepted, this is not desirable behavior

## Mitigation route

Do use `answer <= 0` instead