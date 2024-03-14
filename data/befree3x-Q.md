# QA reports

## Low

### [L-1] Missing checks on `V3Vault::setEmergencyAdmin` allowing owner to set the emergency admin as himself


**Vulnerability Details**


An emergency is defined by the protocol to be able to execute certain critical operations without timelock, for example:
- Set an oracle mode
- Set different protocol limit factors, e.g. the global limit of lent or deb amounts


However, it's possible for the owner to accidentally (or not) make himself as an emergency admin.


```javascript


function setEmergencyAdmin(address admin) external onlyOwner {
@>      emergencyAdmin = admin; // missing check here
       emit SetEmergencyAdmin(admin);
   }


```


**Impact**

If the emergency admin is also the owner, the protocol becomes entirely centralized. Although the current implementation allows all administrative actions to be done by the owner, an emergency admin can help to execute certain administrative actions in the absence of the owner.


**Tools Used**

Manual review.

**Recommended Mitigation Steps**

The following change can be used to update the `setEmergencyAdmin` function in both files `V3Vault.sol` and `V3Oracle.sol`

```diff

function setEmergencyAdmin(address admin) external onlyOwner {
+       if(admin == owner()) {
+           revert Unauthorized();
+       }
       emergencyAdmin = admin;
       emit SetEmergencyAdmin(admin);
}

```

The following test case can be added to the files `V3Vault.t.sol` and `V3Oracle.t.sol` as well:

- On `V3Vault.t.sol`, add this test:
  
```javascript

function testEmergencyAdminCanNotBeOwner() external {
       vm.expectRevert(IErrors.Unauthorized.selector);
       vault.setEmergencyAdmin(address(this));
}

```

- On `V3Oracle.t.sol`, add this test:

```javascript

function testEmergencyAdminCanNotBeOwner() external {
       vm.expectRevert(IErrors.Unauthorized.selector);
       oracle.setEmergencyAdmin(address(this));
}

```