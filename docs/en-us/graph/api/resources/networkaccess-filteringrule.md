<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-27 -->

# filteringRule resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents a rule that filters traffic in Global Secure Access.

Base type of [fqdnFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-fqdnfilteringrule?view=graph-rest-beta), [urlDestinationFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-urldestinationfilteringrule?view=graph-rest-beta), and [webCategoryFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategoryfilteringrule?view=graph-rest-beta).

Inherits from [policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringrule-list?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta) collection | Get a list of the object types that are derived from **filteringRule**. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringrule-post?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta) | Create a new object type that is derived from **filteringRule**. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringrule-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta) | Get the properties and relationships of an object type that is derived from **filteringRule**. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringrule-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta) | Update the properties of an object type that is derived from **filteringRule**. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringrule-delete?view=graph-rest-beta) | None | Delete an object type that is derived from **filteringRule**. |
| [Get web category by URL](https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-getwebcategorybyurl?view=graph-rest-beta) | [microsoft.graph.networkaccess.webCategory](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategory?view=graph-rest-beta) | Check the web category of a given Uniform Resource Locator \(URL\). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| destinations | [microsoft.graph.networkaccess.ruleDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ruledestination?view=graph-rest-beta) collection | Possible destinations and types of destinations accessed by the user in accordance with the network filtering policy, such as IP addresses and FQDNs/URLs. |
| id | String | A unique ID for the rule. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). |
| name | String | The display name of the rule. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). |
| ruleType | microsoft.graph.networkaccess.networkDestinationType | The rule types that specify the basis for filtering. The possible values are: `url`, `fqdn`, `ipAddress`, `ipRange`, `ipSubnet`, and `webCategory`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.filteringRule",
  "destinations": [{"@odata.type": "microsoft.graph.networkaccess.webCategory"}],
  "id": "String (identifier)",
  "name": "String",
  "ruleType": "String"
}
```
