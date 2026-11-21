<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-invitationredemptionrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# invitationRedemptionRule resource type

Namespace: microsoft.graph.identityGovernance

Represents a lifecycle policy rule that requires a guest user to redeem their invitation within a specified period. This rule is supported only on guest lifecycle policies. Inherits from [microsoft.graph.identityGovernance.lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0).

## Methods

This resource has no standalone methods. Configure this rule inline in the **rules** collection when [creating a lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-post-lifecyclepolicies?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| gracePeriodInDays | Int32 | The optional grace period, in days, from the first detected rule violation. If omitted or set to `null`, the containing policy's grace period applies. Set to `0` for no additional grace period. Inherited from [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0). |
| id | String | The unique identifier for the rule. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| invitationRedemptionThresholdInDays | Int32 | The number of days in which the guest user must redeem their invitation, from 1 through 30. |
| isEnabled | Boolean | Indicates whether the rule is enabled. Inherited from [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.invitationRedemptionRule",
  "gracePeriodInDays": "Int32",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "invitationRedemptionThresholdInDays": "Int32"
}
```
