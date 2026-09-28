<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# threatIntelligencePolicy resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a policy that defines how threat intelligence is evaluated and enforced in network access decisions through Global Secure Access. This policy type allows you to apply security controls based on known threats and malicious destinations.

Inherits from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-threatintelligencepolicies?view=graph-rest-beta) | [microsoft.graph.networkaccess.threatIntelligencePolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicy?view=graph-rest-beta) collection | Get a list of the threatIntelligencePolicy objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-post-threatintelligencepolicies?view=graph-rest-beta) | [microsoft.graph.networkaccess.threatIntelligencePolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicy?view=graph-rest-beta) | Create a new threatIntelligencePolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencepolicy-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.threatIntelligencePolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicy?view=graph-rest-beta) | Read the properties and relationships of a threatIntelligencePolicy object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencepolicy-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.threatIntelligencePolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicy?view=graph-rest-beta) | Update the properties of a threatIntelligencePolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-delete-threatintelligencepolicies?view=graph-rest-beta) | None | Delete a threatIntelligencePolicy object. |
| [List policyRules](https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencepolicy-list-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta) collection | Get a list of the rules associated with this threat intelligence policy. |
| [Create policyRule](https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencepolicy-post-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta) | Create a new policyRule object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description of the threat intelligence policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). Supports `$filter` \(`eq`\). |
| id | String | The unique identifier for the threat intelligence policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` \(`eq`\). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the policy was last modified. |
| name | String | The display name of the threat intelligence policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). Supports `$filter` \(`eq`\). |
| settings | [microsoft.graph.networkaccess.threatIntelligencePolicySettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicysettings?view=graph-rest-beta) | Settings that define how the threat intelligence policy operates and evaluates threats. |
| version | String | The version of the policy, used for tracking changes. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policyRules | [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta) collection | The collection of rules that define how the threat intelligence policy is applied. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.threatIntelligencePolicy",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "version": "String",
  "kind": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "settings": {
    "@odata.type": "microsoft.graph.networkaccess.threatIntelligencePolicySettings"
  }
}
```
