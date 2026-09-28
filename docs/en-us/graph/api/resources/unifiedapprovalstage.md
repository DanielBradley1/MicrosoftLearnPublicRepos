<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedapprovalstage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedApprovalStage resource type

Namespace: microsoft.graph

Defines the settings of the approval stages in a [unifiedRoleManagementPolicyApprovalRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyapprovalrule?view=graph-rest-1.0) object. Specifies the primary and escalation approvers of each stage and whether approvals and escalations are required.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvalStageTimeOutInDays | Int32 | The number of days that a request can be pending a response before it is automatically denied. |
| escalationApprovers | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | The escalation approvers for this stage when the primary approvers don't respond. |
| escalationTimeInMinutes | Int32 | The time a request can be pending a response from a primary approver before it can be escalated to the escalation approvers. |
| isApproverJustificationRequired | Boolean | Indicates whether the approver must provide justification for their reponse. |
| isEscalationEnabled | Boolean | Indicates whether escalation if enabled. |
| primaryApprovers | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | The primary approvers of this stage. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedApprovalStage",
  "approvalStageTimeOutInDays": "Integer",
  "isApproverJustificationRequired": "Boolean",
  "escalationTimeInMinutes": "Integer",
  "primaryApprovers": [
    {
      "@odata.type": "microsoft.graph.singleUser"
    }
  ],
  "isEscalationEnabled": "Boolean",
  "escalationApprovers": [
    {
      "@odata.type": "microsoft.graph.singleUser"
    }
  ]
}
```
