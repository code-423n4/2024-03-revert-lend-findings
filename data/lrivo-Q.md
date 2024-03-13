# V3Vault allows the creation of useless loans with a 0-value collateral

As the documentation states, the `collateralFactor` of an LP pair is equal to the lower `collateralFactor` of the two assets inside the position.

So, if one of the two assets in the LP position happens to have a `collateralFactor` of 0, the `collateralFactor` of the whole loan will be 0 too.

`V3Vault::create()` and later `V3Vault::onERC721Received()` do not check if one of the two LP position's assets has a collateral factor of 0, thus allowing the creation of such useless loans.

## Impact

This does not affect the protocol in any major ways, but can potentially cause frustration and a waste of gas if users were to try taking a loan in those conditions.


## Recommended Mitigation

Add a check inside `V3Vault::create()` to assert that none of the LP's assets have a `collateralFactor` of 0 before creating the loan.