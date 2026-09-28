<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencerule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# threatIntelligenceRule resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a rule that defines how to evaluate and respond to specific threat intelligence matches in network traffic through Global Secure Access. These rules determine what action to take when traffic matches specified threat intelligence criteria.

Inherits from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencepolicy-list-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.threatIntelligenceRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencerule?view=graph-rest-beta) collection | Get a list of the threatIntelligencePolicyRule objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencepolicy-post-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta) | Create a new threatIntelligencePolicyRule object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencerule-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.threatIntelligenceRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencerule?view=graph-rest-beta) | Read the properties and relationships of a threatIntelligenceRule object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencerule-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.threatIntelligenceRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencerule?view=graph-rest-beta) | Update the properties of a threatIntelligenceRule object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencerule-delete?view=graph-rest-beta) | None | Delete a threatIntelligenceRule object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.networkaccess.threatIntelligenceAction | The action to take when network traffic matches this rule's conditions. The possible values are: `allow`, `block`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |
| description | String | A description of the threat intelligence rule. Supports `$filter` \(`eq`\). |
| id | String | The unique identifier for the threat intelligence rule. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` \(`eq`\). |
| matchingConditions | [microsoft.graph.networkaccess.threatIntelligenceMatchingConditions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencematchingconditions?view=graph-rest-beta) | Conditions that define what network traffic should be evaluated by this rule. |
| name | String | The display name of the threat intelligence rule. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). Supports `$filter` \(`eq`\). |
| priority | Int64 | The priority of the rule which determines the order of rule evaluation. Lower values indicate higher priority. Supports `$filter` \(`eq`\). |
| settings | [microsoft.graph.networkaccess.threatIntelligenceRuleSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencerulesettings?view=graph-rest-beta) | Settings that define how the threat intelligence rule operates and is enforced. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.threatIntelligenceRule",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "action": "String",
  "priority": "Integer",
  "settings": {
    "@odata.type": "microsoft.graph.networkaccess.threatIntelligenceRuleSettings"
  },
  "matchingConditions": {
    "@odata.type": "microsoft.graph.networkaccess.threatIntelligenceMatchingConditions"
  }
}
```
