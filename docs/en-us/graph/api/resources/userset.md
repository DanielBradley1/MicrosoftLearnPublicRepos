<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# userSet resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Used in the request, approval, and assignment review settings of an [access package assignment policy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-beta). It's an abstract base type inherited by the following resource types:

- [singleUser](https://learn.microsoft.com/en-us/graph/api/resources/singleuser?view=graph-rest-beta)
- [groupMembers](https://learn.microsoft.com/en-us/graph/api/resources/groupmembers?view=graph-rest-beta)
- [connectedOrganizationMembers](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganizationmembers?view=graph-rest-beta)
- [requestorManager](https://learn.microsoft.com/en-us/graph/api/resources/requestormanager?view=graph-rest-beta)
- [internalSponsors](https://learn.microsoft.com/en-us/graph/api/resources/internalsponsors?view=graph-rest-beta)
- [externalSponsors](https://learn.microsoft.com/en-us/graph/api/resources/externalsponsors?view=graph-rest-beta)
- [targetUserSponsors](https://learn.microsoft.com/en-us/graph/api/resources/targetusersponsors?view=graph-rest-beta)
- [targetAgentIdentitySponsorsOrOwners](https://learn.microsoft.com/en-us/graph/api/resources/targetagentidentitysponsorsorowners?view=graph-rest-beta)

In entitlement management, the derived types of this object are configured in the following properties and relationships:

- **escalationApprovers** property of [accessPackageDynamicApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagedynamicapprovalstage?view=graph-rest-beta)
- **primaryApprovers** property of [accessPackageDynamicApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagedynamicapprovalstage?view=graph-rest-beta)
- **escalationApprovers** property of [approvalStage](https://learn.microsoft.com/en-us/graph/api/resources/approvalstage?view=graph-rest-beta)
- **primaryApprovers** property of [approvalStage](https://learn.microsoft.com/en-us/graph/api/resources/approvalstage?view=graph-rest-beta)
- **reviewers** property of [assignmentReviewSettings](https://learn.microsoft.com/en-us/graph/api/resources/assignmentreviewsettings?view=graph-rest-beta)
- **allowedRequestors** property of [requestorSettings](https://learn.microsoft.com/en-us/graph/api/resources/requestorsettings?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isBackup | Boolean | For a user in an approval stage, this property indicates whether the user is a backup fallback approver. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type. A [userSet](https://learn.microsoft.com/en-us/graph/api/resources/userset?view=graph-rest-beta) is an abstract base class and so wouldn't be sent or received. Instead, one of the following `@odata.type` values representing the inherited types would be used:

- `#microsoft.graph.singleUser`
- `#microsoft.graph.groupMembers`
- `#microsoft.graph.connectedOrganizationMembers`
- `#microsoft.graph.requestorManager`
- `#microsoft.graph.internalSponsors`
- `#microsoft.graph.externalSponsors`

```json
{
  "@odata.type": "#microsoft.graph.userSet",
  "isBackup": false
}
```
