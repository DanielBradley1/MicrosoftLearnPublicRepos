<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-periodicattestationrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# periodicAttestationRule resource type

Namespace: microsoft.graph.identityGovernance

Represents a compliance rule that requires an identity to be attested within a specified interval to remain compliant with its [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0).

Inherits from [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0).

## Methods

For the list of operations, see the methods of the [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0) base type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attestationIntervalInDays | Int32 | The number of days within which an identity must be attested to remain compliant with the rule. |
| gracePeriodInDays | Int32 | The optional grace period, in days, from the first detected rule violation. If omitted or set to `null`, the containing policy's grace period applies. Set to `0` for no additional grace period. Inherited from [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0). |
| id | String | The unique identifier for the rule. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnabled | Boolean | Indicates whether the rule is enabled and evaluated as part of its policy. Inherited from [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.periodicAttestationRule",
  "gracePeriodInDays": "Int32",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "attestationIntervalInDays": "Int32"
}
```
