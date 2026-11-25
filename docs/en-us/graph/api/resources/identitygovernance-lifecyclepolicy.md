<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# lifecyclePolicy resource type

Namespace: microsoft.graph.identityGovernance

Represents the abstract base type for lifecycle policies that govern identities by evaluating compliance rules and applying enforcement actions when an identity becomes non-compliant. A maximum of 10 policies are allowed per subject type per tenant.

You can't create instances of this abstract type directly. Instead, use one of the following derived types:

- [agentIdentityLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecyclepolicy?view=graph-rest-1.0)
- [guestLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-guestlifecyclepolicy?view=graph-rest-1.0)

Instances are differentiated by the **@odata.type** property.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-lifecyclepolicies?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) collection | Get lifecycle policies. |
| [Create](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-post-lifecyclepolicies?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) | Create a lifecycle policy of a concrete derived type. |
| [List versions](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-list-versions?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) collection | Get the read-only version history of a lifecycle policy. |
| [List lifecyclePolicies](https://learn.microsoft.com/en-us/graph/api/identitygovernance-deleteditemcontainer-list-lifecyclepolicies?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) collection | Get soft-deleted lifecycle policies. |
| [Get](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) | Read the properties and relationships of [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-update?view=graph-rest-1.0) | None | Update the properties of a lifecyclePolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-delete?view=graph-rest-1.0) | None | Delete a lifecyclePolicy object. |
| [lifecyclePolicy: restore](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-restore?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) | Restore a soft-deleted lifecyclePolicy object. |
| [Get report](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-list-report?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-1.0) | Read the latest processing report for the policy. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the policy was created. |
| description | String | The description of the policy. |
| displayName | String | The display name of the policy. |
| enforcementAction | [microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyenforcementaction?view=graph-rest-1.0) | The action taken when an identity governed by the policy becomes non-compliant. This is a polymorphic type; the possible types are [deleteOnlyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-deleteonlyenforcementaction?view=graph-rest-1.0), [disableOnlyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-disableonlyenforcementaction?view=graph-rest-1.0), and [disableThenDeleteEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-disablethendeleteenforcementaction?view=graph-rest-1.0). |
| gracePeriodInDays | Int32 | The number of days after an identity becomes non-compliant before the enforcement action is applied. |
| id | String | The unique identifier for the policy. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnabled | Boolean | Indicates whether the policy is enabled and actively evaluated. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the policy was last modified. |
| notificationSchedule | [microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicynotificationsettings?view=graph-rest-1.0) | The notification settings for the policy, including the offsets, in days after non-compliance, at which notifications are sent. |
| policySource | microsoft.graph.identityGovernance.lifecyclePolicySource | Indicates whether the policy is system-managed \(a built-in default\) or created by an administrator. The possible values are: `userCreated`, `systemDefault`, `unknownFutureValue`. |
| scope | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) | The set of subjects that the policy applies to. For example, use an [allExcludingGroupsSubjectSet](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-allexcludinggroupssubjectset?view=graph-rest-1.0) to exclude specific groups from evaluation. |
| versionNumber | Int32 | The version number of the policy, which increments each time the policy is updated. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| createdBy | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The user or service principal that created the policy. |
| lastModifiedBy | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The user or service principal that last modified the policy. |
| report | [microsoft.graph.identityGovernance.lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-1.0) | The latest processing report for the policy. |
| rules | [microsoft.graph.identityGovernance.lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0) collection | The collection of inline compliance rules evaluated for the policy. Rules are combined with AND logic. A maximum of 10 rules are allowed per policy. |
| versions | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) collection | The collection of previous versions of the policy. |

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
  "versionNumber": "Int32",
  "policySource": "String",
  "gracePeriodInDays": "Int32",
  "enforcementAction": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction"
  },
  "notificationSchedule": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings"
  }
}
```
