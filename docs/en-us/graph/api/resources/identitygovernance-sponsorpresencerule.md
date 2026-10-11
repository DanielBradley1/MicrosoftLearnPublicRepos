<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-sponsorpresencerule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# sponsorPresenceRule resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a compliance rule that requires an identity to have at least a minimum number of sponsors to remain compliant with its [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta).

Inherits from [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta).

## Methods

For the list of operations, see the methods of the [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta) base type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the rule. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isEnabled | Boolean | Indicates whether the rule is enabled and evaluated as part of its policy. Inherited from [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta). |
| minimumSponsorCount | Int32 | The minimum number of sponsors that an identity must have to remain compliant with the rule. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.sponsorPresenceRule",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "minimumSponsorCount": "Integer"
}
```
