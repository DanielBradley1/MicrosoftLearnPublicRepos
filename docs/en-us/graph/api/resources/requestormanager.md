<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/requestormanager?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# requestorManager resource type

Namespace: microsoft.graph

Used in the approval settings of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0).

It's a subtype of [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0), in which the `@odata.type` value `#microsoft.graph.requestorManager` indicates that a requesting user's manager is to be the approver. When creating an access package assignment policy approval stage with requestorManager, also include another approver, such as a single user or group member, in case the requesting user doesn't have a manager.

In entitlement management, this subtype can be configured in:

- **primaryApprovers** and **escalationApprovers** properties of [approvalStage](https://learn.microsoft.com/en-us/graph/api/resources/approvalstage?view=graph-rest-1.0) and [accessPackageDynamicApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagedynamicapprovalstage?view=graph-rest-1.0)
- **primaryApprovers**, **fallbackPrimaryApprovers**, **escalationApprovers**, and **fallbackEscalationApprovers** properties of [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0) for an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| managerLevel | Int32 | The hierarchical level of the manager with respect to the requestor. For example, the direct manager of a requestor would have a managerLevel of 1, while the manager of the requestor's manager would have a managerLevel of 2. Default value for managerLevel is 1. Possible values for this property range from 1 to 2. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.requestorManager",
  "managerLevel": "Integer"
}
```
