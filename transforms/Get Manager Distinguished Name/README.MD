The Get Manager Distinguished Name Transform pulls the data stored in the identities managers attribute "Distinguished Name", which should be set up to import the identities distinguishedName from Active Directory. 

This way, the distinguishedName of a users manager will be populated in an identity attribute set up with this transform. 

Allowing this identity attribute to be set up with attribute sync to "manager" in Active Directory. 

Result: As a users manager is updated in IdentityNow, the users manager will also be updated in Active Directory automatically. If the user does not have a manager, this attribute will show as blank. 
