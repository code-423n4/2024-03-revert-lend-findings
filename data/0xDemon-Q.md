## **[L-01] Unsafe downcast may overflow**

When a type is downcast to a smaller type, the higher order bits are discarded, resulting in the application of a modulo operation to the original value.

If the downcasted value is large enough, this may result in an overflow that will not revert.

```solidity
            instructions.feeAmount0 == type(uint128).max
                ? type(uint128).max
                : (amount0 + instructions.feeAmount0).toUint128(),
            instructions.feeAmount1 == type(uint128).max
                ? type(uint128).max
                : (amount1 + instructions.feeAmount1).toUint128()
```

*Github : [133 - 138](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/V3Utils.sol#L133-L138)*

## [L-02] Low level call to arbitrary address may lead to gas grieffing attack

If the destination address is a contract that has a fallback function then this can cause very large gas usage or if the destination address is a malicious actor who deliberately carries out gas grieffing.

```solidity
        uint256 balance = address(this).balance;
        if (balance > 0) {
            (bool sent,) = to.call{value: balance}("");
            if (!sent) {
                revert EtherSendFailed();
            }
```

*Github : [128 - 133](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/automators/Automator.sol#L128-L133)*