<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicy resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the abstract base type for lifecycle policies that govern identities by evaluating compliance rules and applying enforcement actions when an identity becomes non-compliant. A maximum of 10 policies are allowed per subject type per tenant.

You can't create instances of this abstract type directly. Instead, use the following derived type:

- [agentIdentityLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecyclepolicy?view=graph-rest-beta)

Instances are differentiated by the **@odata.type** property.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-get?view=graph-rest-beta) | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) | Read the properties and relationships of [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) object. |
| [Update lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-update?view=graph-rest-beta) | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) | Update the properties of a lifecyclePolicy object. |
| [Delete lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-delete?view=graph-rest-beta) | None | Delete a lifecyclePolicy object. |
| [lifecyclePolicy: restore](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-restore?view=graph-rest-beta) | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) | Restore a soft-deleted lifecyclePolicy object. |
| [List rules](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-list-rules?view=graph-rest-beta) | [microsoft.graph.identityGovernance.lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta) collection | Get the compliance rules defined on the policy. |
| [Evaluate impact](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-impact?view=graph-rest-beta) | [lifecyclePolicyImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyimpactsummary?view=graph-rest-beta) collection | Evaluate the impact of the policy during a specified period. |
| [Get report](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-list-report?view=graph-rest-beta) | [lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-beta) | Read the latest processing report for the policy. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the policy was created. |
| description | String | The description of the policy. |
| displayName | String | The display name of the policy. |
| enforcementAction | [microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyenforcementaction?view=graph-rest-beta) | The action taken when an identity governed by the policy becomes non-compliant. This is a polymorphic type; the possible types are [deleteOnlyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-deleteonlyenforcementaction?view=graph-rest-beta), [disableOnlyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-disableonlyenforcementaction?view=graph-rest-beta), and [disableThenDeleteEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-disablethendeleteenforcementaction?view=graph-rest-beta). |
| gracePeriodInDays | Int32 | The number of days after an identity becomes non-compliant before the enforcement action is applied. |
| id | String | The unique identifier for the policy. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isEnabled | Boolean | Indicates whether the policy is enabled and actively evaluated. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the policy was last modified. |
| notificationSchedule | [microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicynotificationsettings?view=graph-rest-beta) | The notification settings for the policy, including the offsets, in days after non-compliance, at which notifications are sent. |
| policySource | [microsoft.graph.identityGovernance.lifecyclePolicySource](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-beta#lifecyclepolicysource-values) | Indicates whether the policy is system-managed \(a built-in default\) or created by an administrator. The possible values are: `userCreated`, `systemDefault`, `unknownFutureValue`. |
| scope | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-beta) | The set of subjects that the policy applies to. For example, use an [allExcludingGroupsSubjectSet](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-allexcludinggroupssubjectset?view=graph-rest-beta) to exclude specific groups from evaluation. |
| versionNumber | Int32 | The version number of the policy, which increments each time the policy is updated. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| createdBy | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | The user or service principal that created the policy. |
| lastModifiedBy | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | The user or service principal that last modified the policy. |
| report | [microsoft.graph.identityGovernance.lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-beta) | The latest processing report for the policy. |
| rules | [microsoft.graph.identityGovernance.lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta) collection | The collection of inline compliance rules evaluated for the policy. Rules are combined with AND logic. A maximum of 10 rules are allowed per policy. |
| versions | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) collection | The collection of previous versions of the policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicy",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "isEnabled": "Boolean",
  "lastModifiedDateTime": "String (timestamp)",
  "scope": {
    "@odata.type": "microsoft.graph.subjectSet"
  },
  "versionNumber": "Integer",
  "policySource": "String",
  "gracePeriodInDays": "Integer",
  "enforcementAction": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction"
  },
  "notificationSchedule": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings"
  }
}
```
