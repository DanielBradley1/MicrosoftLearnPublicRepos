<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecyclepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# agentIdentityLifecyclePolicy resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a lifecycle policy that governs the lifecycle of agent identities through compliance rules and enforcement actions.

Inherits from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta).

## Methods

For the list of operations, see the methods of the [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) base type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the policy was created. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |
| description | String | The description of the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |
| displayName | String | The display name of the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |
| enforcementAction | [microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyenforcementaction?view=graph-rest-beta) | The action taken when an agent identity governed by the policy becomes non-compliant. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |
| gracePeriodInDays | Int32 | The number of days after an identity becomes non-compliant before the enforcement action is applied. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |
| id | String | The unique identifier for the policy. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isEnabled | Boolean | Indicates whether the policy is enabled and actively evaluated. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the policy was last modified. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |
| notificationSchedule | [microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicynotificationsettings?view=graph-rest-beta) | The notification settings for the policy, including the offsets, in days after non-compliance, at which notifications are sent. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |
| policySource | [microsoft.graph.identityGovernance.lifecyclePolicySource](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-beta#lifecyclepolicysource-values) | Indicates whether the policy is system-managed \(a built-in default\) or created by an administrator. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). The possible values are: `userCreated`, `systemDefault`, `unknownFutureValue`. |
| scope | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-beta) | The set of agent identities that the policy applies to. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |
| versionNumber | Int32 | The version number of the policy, which increments each time the policy is updated. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| createdBy | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | The user or service principal that created the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |
| lastModifiedBy | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | The user or service principal that last modified the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |
| rules | [microsoft.graph.identityGovernance.lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta) collection | The collection of inline compliance rules evaluated for the policy. Rules are combined with AND logic. A maximum of 10 rules are allowed per policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |
| versions | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) collection | The collection of previous versions of the policy. Inherited from [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). |

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
  "gracePeriodInDays": "Integer",
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
  "versionNumber": "Integer"
}
```
