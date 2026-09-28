<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approvalstep?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# approvalStep resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies a decision step in an [approval](https://learn.microsoft.com/en-us/graph/api/resources/approval?view=graph-rest-beta) in entitlement management and PIM.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/approval-list-steps?view=graph-rest-beta) | [approvalStep](https://learn.microsoft.com/en-us/graph/api/resources/approvalstep?view=graph-rest-beta) collection | List the **approvalStep** objects associated with an **approval** object in entitlement management and PIM. |
| [Get](https://learn.microsoft.com/en-us/graph/api/approvalstep-get?view=graph-rest-beta) | [approvalStep](https://learn.microsoft.com/en-us/graph/api/resources/approvalstep?view=graph-rest-beta) | Retrieve the properties of an **approvalStep** object in entitlement management and PIM. |
| [Update](https://learn.microsoft.com/en-us/graph/api/approvalstep-update?view=graph-rest-beta) | None | Apply approve or deny decision on an **approvalStep** object in entitlement management and PIM. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedToMe | Boolean | Indicates whether the step is assigned to the calling user to review. Read-only. |
| displayName | String | The label provided by the policy creator to identify an approval step. Read-only. |
| id | String | The identifier of the step associated with an approval object. Read-only. |
| justification | String | The justification associated with the approval step decision. |
| reviewResult | String | The result of this approval record. Possible values include: `NotReviewed`, `Approved`, `Denied`. |
| reviewedBy | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta) collection | The identifier of the reviewer. `00000000-0000-0000-0000-000000000000` if the assigned reviewer hasn't reviewed. Read-only. |
| reviewedDateTime | DateTimeOffset | The date and time when a decision was recorded. The date and time information uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| status | String | The step status. Possible values: `InProgress`, `Initializing`, `Completed`, `Expired`. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| approval | [approval](https://learn.microsoft.com/en-us/graph/api/resources/approval?view=graph-rest-beta) collection | The approval object for decisions associated with the `accessPackageAssignmentRequest` in entitlement management, the `roleAssignmentScheduleRequest` in PIM for Microsoft Entra roles, or the `assignmentScheduleRequest` in PIM for Groups. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
   "@odata.type":"#microsoft.graph.approvalStep",
   "id":"String (identifier)",
   "displayName":"String",
   "status":"String",
   "assignedToMe":true,
   "reviewedBy": [{"@odata.type": "microsoft.graph.userIdentity"}],
   "reviewedDateTime":"String (timestamp)",
   "reviewResult":"String",
   "justification":"String"
}
```
