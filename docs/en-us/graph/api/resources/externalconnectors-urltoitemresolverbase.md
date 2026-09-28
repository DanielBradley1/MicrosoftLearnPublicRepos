<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-urltoitemresolverbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# urlToItemResolverBase resource type

Namespace: microsoft.graph.externalConnectors

Defines the rules for resolving a URL to the ID of an [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| priority | Int32 | The priority which defines the sequence in which the urlToItemResolverBase instances are evaluated. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalConnectors.urlToItemResolverBase",
  "priority": "Integer"
}
```

## Related content

Types that inherit from the [urlToItemResolverBase](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-urltoitemresolverbase?view=graph-rest-1.0) abstract base type.

- [itemIdResolver](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-itemidresolver?view=graph-rest-1.0)
