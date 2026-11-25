<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-guestlifecyclepolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# guestLifecyclePolicy resource type

Namespace: microsoft.graph.identityGovernance

Represents a lifecycle policy that governs guest users in an organization. Inherits from [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0).

## Methods

This resource is part of a polymorphic collection managed by the [lifecyclePolicy resource](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) base type. Operations are performed through the base type endpoints.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the policy was created. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| description | String | The description of the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| displayName | String | The display name of the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| enforcementAction | [microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyenforcementaction?view=graph-rest-1.0) | The action applied when a guest user governed by the policy becomes noncompliant. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| gracePeriodInDays | Int32 | The number of days before the enforcement action is applied. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| id | String | The unique identifier for the policy. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnabled | Boolean | Indicates whether the policy is enabled. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the policy was last modified. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| notificationSchedule | [microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicynotificationsettings?view=graph-rest-1.0) | The notification schedule for noncompliant guest users. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| policySource | microsoft.graph.identityGovernance.lifecyclePolicySource | Indicates whether the policy is system-managed or user-created. The possible values are: `userCreated`, `systemDefault`, `unknownFutureValue`. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| scope | [microsoft.graph.subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) | The guest users included in the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| versionNumber | Int32 | The version number of the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| createdBy | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The user or service principal that created the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| lastModifiedBy | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The user or service principal that last modified the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| report | [microsoft.graph.identityGovernance.lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-1.0) | The latest processing report for the policy. |
| rules | [microsoft.graph.identityGovernance.lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0) collection | The compliance rules evaluated by the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| versions | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) collection | The previous versions of the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.guestLifecyclePolicy",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "enforcementAction": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction"
  },
  "gracePeriodInDays": "Int32",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "lastModifiedDateTime": "String (timestamp)",
  "notificationSchedule": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings"
  },
  "policySource": "String",
  "scope": {
    "@odata.type": "microsoft.graph.subjectSet"
  },
  "versionNumber": "Int32"
}
```
