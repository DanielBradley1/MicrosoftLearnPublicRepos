<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-itemidresolver?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# itemIdResolver resource type

Namespace: microsoft.graph.externalConnectors

Defines the rules for resolving a URL to the ID of an [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0).

Inherits from [urlToItemResolverBase](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-urltoitemresolverbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| itemId | String | Pattern that specifies how to form the ID of the external item that the URL represents. The named groups from the regular expression in **urlPattern** within the [urlMatchInfo](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-urlmatchinfo?view=graph-rest-1.0) can be referenced by inserting the group name inside curly brackets. |
| priority | Int32 | Priority of each urlToItemResolverBase instance. Inherited from [urlToItemResolverBase](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-urltoitemresolverbase?view=graph-rest-1.0). |
| urlMatchInfo | [microsoft.graph.externalConnectors.urlMatchInfo](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-urlmatchinfo?view=graph-rest-1.0) | Configurations to match and resolve URL. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalConnectors.itemIdResolver",
  "itemId": "String",  
  "priority": "Integer",
  "urlMatchInfo": {
    "@odata.type": "microsoft.graph.externalConnectors.urlMatchInfo"
  }
}
```
