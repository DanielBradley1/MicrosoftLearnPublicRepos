<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-urldestinationfilteringrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# urlDestinationFilteringRule resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines a URL filtering rule, enabling administrators to manage granular access to specific destinations on the internet.

Inherits from [microsoft.graph.networkaccess.filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see [filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| destinations | [microsoft.graph.networkaccess.ruleDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ruledestination?view=graph-rest-beta) collection | The list of potential destinations and destination types that the user may access, including fully qualified domain names \(FQDNs\), uniform resource locators \(URLs\), and web categories, within the context of a network filtering policy. Inherited from [microsoft.graph.networkaccess.filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta). |
| id | String | The unique identifier for the **urlDestinationFilteringRule**. Inherited from [microsoft.graph.networkaccess.filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta). |
| name | String | Display name. Inherited from [microsoft.graph.networkaccess.filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta). |
| ruleType | microsoft.graph.networkaccess.networkDestinationType | The network destination type used by a filtering rule. Supports a subset of the values for **networkDestinationType**. The possible values are: `url`, `fqdn`, `webCategory`, `unknownFutureValue`. Inherited from [microsoft.graph.networkaccess.filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.urlDestinationFilteringRule",
  "destinations": [{"@odata.type": "microsoft.graph.networkaccess.ruleDestination"}],
  "id": "String (identifier)",
  "name": "String",
  "ruleType": "String"
}
```
