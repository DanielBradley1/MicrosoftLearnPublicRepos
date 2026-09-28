<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# subjectSet resource type

Namespace: microsoft.graph

A shared object that is used in entitlement management access package assignment policies, role management policies, and lifecycle workflows through the **scope** property of the [triggerAndScopeBasedConditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-triggerandscopebasedconditions?view=graph-rest-1.0) resource.

- In entitlement management, used in the request, approval, and assignment review settings of an access package assignment policy.
- In role management policies, used in the approval settings that are defined in rules for role management policies.
- In lifecycle workflows, used to configure the users that are in the scope of a workflow.

This object is an abstract base type from which the following resources are derived:

| Resource | Feature | Description |
| --- | --- | --- |
| [attributeRuleMembers](https://learn.microsoft.com/en-us/graph/api/resources/attributerulemembers?view=graph-rest-1.0) | Entitlement Management | Represents members of a connected organization in an access package assignment policy. |
| [connectedOrganizationMembers](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganizationmembers?view=graph-rest-1.0) | Entitlement Management | Represents members of a connected organization in an access package assignment policy. |
| [externalSponsors](https://learn.microsoft.com/en-us/graph/api/resources/externalsponsors?view=graph-rest-1.0) | Entitlement Management | Represents user's connected organization external sponsors for access package assignments. |
| [groupBasedSubjectSet](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-groupbasedsubjectset?view=graph-rest-1.0) | Lifecycle Workflows | Represents the group that is the scope of a lifecycle workflow. |
| [groupMembers](https://learn.microsoft.com/en-us/graph/api/resources/groupmembers?view=graph-rest-1.0) | Entitlement Management | Represents a collection of users part of a group in the tenant who are allowed as requestor, approver, or reviewer. |
| [internalSponsors](https://learn.microsoft.com/en-us/graph/api/resources/internalsponsors?view=graph-rest-1.0) | Entitlement Management | Represents user's connected organization internal sponsors as the approver for access package assignments. |
| [requestorManager](https://learn.microsoft.com/en-us/graph/api/resources/requestormanager?view=graph-rest-1.0) | Entitlement Management | Represents the manager of the requestor as approver for access package assignments. |
| [ruleBasedSubjectSet](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-rulebasedsubjectset?view=graph-rest-1.0) | Lifecycle Workflows | Represents the rules to define the subjects for the scope of a lifecycle workflow. |
| [singleServicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/singleserviceprincipal?view=graph-rest-1.0) | Entitlement Management | Represents a specific service principal in the tenant who will be allowed as a requestor, approver, or reviewer. |
| [singleUser](https://learn.microsoft.com/en-us/graph/api/resources/singleuser?view=graph-rest-1.0) | Entitlement Management | Represents a single user as approver to access packages. |
| [targetAgentIdentitySponsorsOrOwners](https://learn.microsoft.com/en-us/graph/api/resources/targetagentidentitysponsorsorowners?view=graph-rest-1.0) | Entitlement Management | Represents the sponsors or owners of a specific agent identity. |
| [targetApplicationOwners](https://learn.microsoft.com/en-us/graph/api/resources/targetapplicationowners?view=graph-rest-1.0) | Entitlement Management | Represents the application owners who can request an access package on behalf of that application. |
| [targetManager](https://learn.microsoft.com/en-us/graph/api/resources/targetmanager?view=graph-rest-1.0) | Entitlement Management | Represents the manager of a user who can request an access package on behalf of that user. |
| [targetUserSponsors](https://learn.microsoft.com/en-us/graph/api/resources/targetusersponsors?view=graph-rest-1.0) | Entitlement Management | Represents another user in the tenant who can approve an access package on behalf of a user. |

In entitlement management, this object is configured in the following properties and relationships:

- **escalationApprovers** property of [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0)
- **fallbackEscalationApprovers** property of [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0)
- **fallbackPrimaryApprovers** property of [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0)
- **primaryApprovers** property of [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0)

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.subjectSet"
}
```
