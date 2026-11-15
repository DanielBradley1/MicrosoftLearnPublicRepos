<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicylink?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# webFilteringPolicyLink resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the association between a [webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta) and a [filteringProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta).

Inherits from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicylink-list?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicylink?view=graph-rest-beta) collection | Get a list of the webFilteringPolicyLink objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicylink-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicylink?view=graph-rest-beta) | Read the properties and relationships of [microsoft.graph.networkaccess.webFilteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicylink?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicylink-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicylink?view=graph-rest-beta) | Update the properties of a webFilteringPolicyLink object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicylink-delete?view=graph-rest-beta) | None | Delete a webFilteringPolicyLink object. |
| [Get policy](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicylink-list-policy?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta) | Get the web filtering policy associated with the policy link. |
| [Add policy](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicylink-post-policy?view=graph-rest-beta) | None | Associate a web filtering policy with the policy link. |
| [Remove policy](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicylink-delete-policy?view=graph-rest-beta) | None | Remove a [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the policy link. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| state | [microsoft.graph.networkaccess.status](https://learn.microsoft.com/en-us/graph/api/resources/enums-networkaccess?view=graph-rest-beta#status-values) | The state of the policy link. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). The possible values are: `enabled`, `disabled`, `unknownFutureValue`. |
| version | String | The version of the policy link. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policy | [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta) | The web filtering policy associated with the filtering profile. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringPolicyLink",
  "id": "String (identifier)",
  "state": "String",
  "version": "String"
}
```
