<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approvalstage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# approvalStage resource type

Namespace: microsoft.graph

In entitlement management, used for the **approvalStages** property of approval settings in the **requestApprovalSettings** property of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0). Specifies the primary, fallback, and escalation approvers of each stage.

In PIM, defines the settings of the approval stages in a [unifiedRoleManagementPolicyApprovalRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyapprovalrule?view=graph-rest-1.0) object. Specifies the primary and escalation approvers of each stage and whether approvals and escalations are required.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/approval-list-stages?view=graph-rest-1.0) | [approvalStage](https://learn.microsoft.com/en-us/graph/api/resources/approvalstage?view=graph-rest-1.0) collection | List the **approvalStage** objects associated with an **approval** object in entitlement management and PIM. |
| [Get](https://learn.microsoft.com/en-us/graph/api/approvalstage-get?view=graph-rest-1.0) | [approvalStage](https://learn.microsoft.com/en-us/graph/api/resources/approvalstage?view=graph-rest-1.0) | Retrieve the properties of an **approvalStage** object in entitlement management and PIM. |
| [Update](https://learn.microsoft.com/en-us/graph/api/approvalstage-update?view=graph-rest-1.0) | None | Apply approve or deny decision on an **approvalStage** object in entitlement management and PIM. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedToMe | Boolean | Indicates whether the stage is assigned to the calling user to review. Read-only. |
| displayName | String | The label provided by the policy creator to identify an approval stage. Read-only. |
| id | String | The identifier of the stage associated with an approval object. Read-only. |
| justification | String | The justification associated with the approval stage decision. |
| reviewResult | String | The result of this approval record. Possible values include: `NotReviewed`, `Approved`, `Denied`. |
| reviewedBy | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | The identifier of the reviewer. `00000000-0000-0000-0000-000000000000` if the assigned reviewer hasn't reviewed. Read-only. |
| reviewedDateTime | DateTimeOffset | The date and time when a decision was recorded. The date and time information uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| status | String | The stage status. Possible values: `InProgress`, `Initializing`, `Completed`, `Expired`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.approvalStage",
  "assignedToMe": "Boolean",
  "displayName": "String",
  "id": "String (identifier)",
  "justification": "String",
  "reviewedBy": {
    "@odata.type": "microsoft.graph.identity"
  },
  "reviewedDateTime": "String (timestamp)",
  "reviewResult": "String",
  "status": "String"
}
```
