<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicylink?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-02-27 -->

# threatIntelligencePolicyLink resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Links a [threatIntelligencePolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicy?view=graph-rest-beta) to a [filteringProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta) in Global Secure Access. This link enables the threat intelligence capabilities to be applied to network traffic for the associated resource.

Inherits from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta).

## Methods

For supported API operations, see [filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the threat intelligence policy link. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| state | microsoft.graph.networkaccess.status | The operational state of the policy link that determines if the threat intelligence policy is actively applied to network traffic. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta).The possible values are: `enabled`, `disabled`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |
| version | String | The version of the policy link, used for tracking changes. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policy | [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta) | The threat intelligence policy associated with this link. The link connects the policy to filtering profiles, enabling the threat intelligence capabilities to be applied to network traffic. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.threatIntelligencePolicyLink",
  "id": "String (identifier)",
  "state": "String",
  "version": "String"
}
```
