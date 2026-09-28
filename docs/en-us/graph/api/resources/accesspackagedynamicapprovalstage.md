<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagedynamicapprovalstage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-02 -->

# accessPackageDynamicApprovalStage resource type

Namespace: microsoft.graph

Specifies a decision stage in a dynamic [approval](https://learn.microsoft.com/en-us/graph/api/resources/approval?view=graph-rest-1.0) in entitlement management.

Inherits from [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| durationBeforeAutomaticDenial | Duration | The number of days that a request can be pending a response before it is automatically denied. Inherited from [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0). |
| durationBeforeEscalation | Duration | If escalation is required, the time a request can be pending a response from a primary approver. Inherited from [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0). |
| escalationApprovers | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | If escalation is enabled and the primary approvers do not respond before the escalation time, the escalationApprovers are the users who will be asked to approve requests. Inherited from [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0). |
| fallbackEscalationApprovers | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | The subjects, typically users, who are the fallback escalation approvers. Inherited from [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0). |
| fallbackPrimaryApprovers | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | The subjects, typically users, who are the fallback primary approvers. Inherited from [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0). |
| isApproverJustificationRequired | Boolean | Indicates whether the approver must provide justification for their response. Inherited from [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0). |
| isEscalationEnabled | Boolean | Indicates whether escalation if enabled. Inherited from [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0). |
| primaryApprovers | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | The primary approvers of this stage. Inherited from [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageDynamicApprovalStage",
  "durationBeforeAutomaticDenial": "String (duration)",
  "isApproverJustificationRequired": "Boolean",
  "isEscalationEnabled": "Boolean",
  "durationBeforeEscalation": "String (duration)",
  "primaryApprovers": [
    {
      "@odata.type": "microsoft.graph.identityGovernance.ruleBasedSubjectSet"
    }
  ],
  "fallbackPrimaryApprovers": [
    {
      "@odata.type": "microsoft.graph.identityGovernance.ruleBasedSubjectSet"
    }
  ],
  "escalationApprovers": [
    {
      "@odata.type": "microsoft.graph.identityGovernance.ruleBasedSubjectSet"
    }
  ],
  "fallbackEscalationApprovers": [
    {
      "@odata.type": "microsoft.graph.identityGovernance.ruleBasedSubjectSet"
    }
  ]
}
```
