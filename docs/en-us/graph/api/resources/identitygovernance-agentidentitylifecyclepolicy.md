<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecyclepolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# agentIdentityLifecyclePolicy resource type

Namespace: microsoft.graph.identityGovernance

Represents a lifecycle policy that governs the lifecycle of agent identities through compliance rules and enforcement actions.

Inherits from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0).

## Methods

For the list of operations, see the methods of the [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) base type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the policy was created. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| description | String | The description of the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| displayName | String | The display name of the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| enforcementAction | [microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyenforcementaction?view=graph-rest-1.0) | The action taken when an agent identity governed by the policy becomes non-compliant. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| gracePeriodInDays | Int32 | The number of days after an identity becomes non-compliant before the enforcement action is applied. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| id | String | The unique identifier for the policy. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnabled | Boolean | Indicates whether the policy is enabled and actively evaluated. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the policy was last modified. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| notificationSchedule | [microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicynotificationsettings?view=graph-rest-1.0) | The notification settings for the policy, including the offsets, in days after non-compliance, at which notifications are sent. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| policySource | microsoft.graph.identityGovernance.lifecyclePolicySource | Indicates whether the policy is system-managed \(a built-in default\) or created by an administrator. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). The possible values are: `userCreated`, `systemDefault`, `unknownFutureValue`. |
| scope | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) | The set of agent identities that the policy applies to. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| versionNumber | Int32 | The version number of the policy, which increments each time the policy is updated. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| createdBy | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The user or service principal that created the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| lastModifiedBy | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The user or service principal that last modified the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| report | [microsoft.graph.identityGovernance.lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-1.0) | The latest processing report for the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| rules | [microsoft.graph.identityGovernance.lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0) collection | The collection of inline compliance rules evaluated for the policy. Rules are combined with AND logic. A maximum of 10 rules are allowed per policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |
| versions | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) collection | The collection of previous versions of the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.agentIdentityLifecyclePolicy",
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
