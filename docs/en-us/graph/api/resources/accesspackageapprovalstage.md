<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageApprovalStage resource type

Namespace: microsoft.graph

Used for the **stages** property of [accessPackageAssignmentApprovalSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentapprovalsettings?view=graph-rest-1.0) in an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0). Specifies the primary, fallback, and escalation approvers of each stage.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approverInformationVisibility | [approverInformationVisibility](#approverinformationvisibility-values) | Indicates whether approver information is visible to the requestor. The possible values are: `default`, `notVisible`, `visible`, `unknownFutureValue`. |
| durationBeforeAutomaticDenial | Duration | The number of days that a request can be pending a response before it is automatically denied. |
| durationBeforeEscalation | Duration | If escalation is required, the time a request can be pending a response from a primary approver. |
| escalationApprovers | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | If escalation is enabled and the primary approvers do not respond before the escalation time, the escalationApprovers are the users who are asked to approve requests. |
| fallbackEscalationApprovers | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | The subjects, typically users, who are the fallback escalation approvers. |
| fallbackPrimaryApprovers | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | The subjects, typically users, who are the fallback primary approvers. |
| isApproverJustificationRequired | Boolean | Indicates whether the approver is required to provide a justification for approving a request. |
| isEscalationEnabled | Boolean | If `true`, then one or more **escalationApprovers** are configured in this approval stage. |
| primaryApprovers | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | The subjects, typically users, who are asked to approve requests. A collection of [singleUser](https://learn.microsoft.com/en-us/graph/api/resources/singleuser?view=graph-rest-1.0), [groupMembers](https://learn.microsoft.com/en-us/graph/api/resources/groupmembers?view=graph-rest-1.0), [requestorManager](https://learn.microsoft.com/en-us/graph/api/resources/requestormanager?view=graph-rest-1.0), [internalSponsors](https://learn.microsoft.com/en-us/graph/api/resources/internalsponsors?view=graph-rest-1.0), [externalSponsors](https://learn.microsoft.com/en-us/graph/api/resources/externalsponsors?view=graph-rest-1.0), or [targetUserSponsors](https://learn.microsoft.com/en-us/graph/api/resources/targetusersponsors?view=graph-rest-1.0). |

### approverInformationVisibility values

| Member | Description |
| :--- | :--- |
| default | Use the default system setting for approver information visibility. |
| notVisible | Approver information is not visible to the requestor. |
| visible | Approver information is visible to the requestor. |
| unknownFutureValue | Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageApprovalStage",
  "approverInformationVisibility": "String",
  "durationBeforeAutomaticDenial": "String (duration)",
  "durationBeforeEscalation": "String (duration)",
  "escalationApprovers": [
    {
      "@odata.type": "microsoft.graph.singleUser"
    }
  ],
  "fallbackEscalationApprovers": [
    {
      "@odata.type": "microsoft.graph.singleUser"
    }
  ],
  "fallbackPrimaryApprovers": [
    {
      "@odata.type": "microsoft.graph.singleUser"
    }
  ],
  "isApproverJustificationRequired": "Boolean",
  "isEscalationEnabled": "Boolean",
  "primaryApprovers": [
    {
      "@odata.type": "microsoft.graph.singleUser"
    }
  ]
  
}
```
