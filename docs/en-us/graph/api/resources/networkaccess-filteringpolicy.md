<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# filteringPolicy resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the specific traffic that is allowed or blocked through the Global Secure Access services for a [filtering profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta).

Inherits from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-filteringpolicies?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) collection | Get all filtering policies in the tenant to better understand what traffic is blocked or allowed. |
| [List policies for a filtering policy profile](https://learn.microsoft.com/en-us/graph/api/networkaccess-policylink-list-policy?view=graph-rest-beta) | [filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta) collection | Get the filtering policy resources from the policy profile. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringpolicy-post-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) | Create a new [microsoft.graph.networkaccess.filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) for defining traffic rules. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringpolicy-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) | Get a [microsoft.graph.networkaccess.filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) object to view its configuration. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringprofile-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) | Modify the properties of an existing [microsoft.graph.networkaccess.filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) to update its traffic rules. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringpolicylink-delete-policy?view=graph-rest-beta) | None | Delete a [microsoft.graph.networkaccess.filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) object. |
| [Delete policy for a filtering policy profile](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringprofile-delete-policies?view=graph-rest-beta) | None | Delete a [microsoft.graph.networkaccess.filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the filtering Policy was originally created. |
| description | String | A description of the filtering policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |
| id | String | The identifier for the filtering policy. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when a particular profile was last modified or updated. |
| name | String | The display name for the filtering policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policyRules | [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta) collection | The definition of the policy ruleset that makes up the core definition of a policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.filteringPolicy",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "version": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)"
}
```
