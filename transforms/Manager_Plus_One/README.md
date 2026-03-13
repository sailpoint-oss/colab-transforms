Knowing the Identity's Manager's Manager can be useful.  Adding the Manager's Manager name can be completed by setting up an Identity Profile Attribute Mapping using Manager_Plus_One.json.

Manager_Plus_One will look at the Identity record for the Identity's manager, and will return the manager field.

Attribute Mapping:
- name: Manager Plus One (technical name: managerPlusOne)
- source: Use your authoritative source (ex. Workday)
- attribute: Use any attribute (ex. MANAGER_ID)
- transform: Manager_Plus_One


********************************************************************************************************
*** Items below require a source to be setup using the Identity Security Cloud Governance Connector ****
********************************************************************************************************

With Adaptive Approval, it is possible to setup an Approval Policy that requires the Manager's Manager to approve.  For this to work, three new Identity Profile Attribute Mappings will need to be created.  Recommendation is to apply these attributes one at a time, Identity errors could occur if they are applied at the same time.  

Attribute Mapping to get ISC Native Identity for the Identity: 
- name: ISC ID (technical name: iscId)
- source: Identity Security Cloud Governance Connector source
- attribute: id

Attribute Mapping to get ISC Native Identity for the Identity's manager:
- name: Manager ISC ID (technical name: managerIscId)
- source: Use your authoritative source (ex. Workday)
- attribute: Use any attribute (ex. FILENUMBER)
- transform: Manager-ISC_ID

Attribute Mapping to get ISC Native Identity for the Identity's manager's manager:
- name: Manager Plus One ISC ID (technical name: managerPlusOneIscId)
- source: Use your authoritative source (ex. Workday)
- attribute: Use any attribute (ex. MANAGER_ID)
- transform: Manager_Plus_One-ISC_ID

Once the attributes are populated, create a Workflow
1. Trigger: Access Request Submitted
2. Action: Get Identity
   a. variable: $.trigger.requestedFor.id
3. Action: Approval Policy
   a. Approval Type: Multi-Step
   b. Approval Schema: Either Serial or Parallel
   c. Add Reviewers:
    - Category: Identity (Other)
    - Choose Variable: $.getIdentity.attributes.managerPlusOneIscId
4. Operator: End Step - Success

Assign approval workflow to access items.
