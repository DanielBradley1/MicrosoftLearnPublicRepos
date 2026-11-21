<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-sponsorpresencerule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# sponsorPresenceRule resource type

Namespace: microsoft.graph.identityGovernance

Represents a compliance rule that requires an identity to have at least a minimum number of sponsors to remain compliant with its [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0).

Inherits from [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0).

## Methods

For the list of operations, see the methods of the [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0) base type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| gracePeriodInDays | Int32 | The optional grace period, in days, from the first detected rule violation. If omitted or set to `null`, the containing policy's grace period applies. Set to `0` for no additional grace period. Inherited from [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0). |
| id | String | The unique identifier for the rule. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnabled | Boolean | Indicates whether the rule is enabled and evaluated as part of its policy. Inherited from [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0). |
| minimumSponsorCount | Int32 | The minimum number of sponsors that an identity must have to remain compliant with the rule. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.sponsorPresenceRule",
  "gracePeriodInDays": "Int32",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "minimumSponsorCount": "Int32"
}
```
