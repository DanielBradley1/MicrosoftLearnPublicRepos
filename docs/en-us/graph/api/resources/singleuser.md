<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/singleuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# singleUser resource type

Namespace: microsoft.graph

Used in the request, approval, and assignment review settings of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0). The `@odata.type` value `#microsoft.graph.singleUser` indicates that this userSet identifies a specific user in the tenant who is allowed as a requestor, approver, or reviewer.

In entitlement management, this subtype can be configured in:

- **allowedRequestors** property of [accessPackageAssignmentRequestorSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestorsettings?view=graph-rest-1.0)
- **primaryApprovers** and **escalationApprovers** properties of [approvalStage](https://learn.microsoft.com/en-us/graph/api/resources/approvalstage?view=graph-rest-1.0) and [accessPackageDynamicApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagedynamicapprovalstage?view=graph-rest-1.0)
- **primaryApprovers**, **fallbackPrimaryApprovers**, **escalationApprovers**, and **fallbackEscalationApprovers** properties of [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0)
- **reviewers** property of [accessPackageAssignmentReviewSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentreviewsettings?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The name of the user in Microsoft Entra ID. Read-only. |
| userId | String | The ID of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) in Microsoft Entra ID. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.singleUser",
  "userId": "String",
  "description": "String"
}
```
