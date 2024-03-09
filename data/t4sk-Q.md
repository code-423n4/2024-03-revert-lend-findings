# Lock solidity version
```
// SPDX-License-Identifier: BUSL-1.1
pragma solidity ^0.8.0;
```

# V3Oracle._requireMaxDifference incorrect comparison

```solidity
        if (differenceX10000 >= maxDifferenceX10000) {
            revert PriceDifferenceExceeded();
        }
```

`maxDifferencex1000` is max allowed price difference

Here the code will revert when the price difference is exactly equal to the max allowed difference.

Inequality should be changed to `differenceX10000 > maxDifferenceX10000`

https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L147

https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L200