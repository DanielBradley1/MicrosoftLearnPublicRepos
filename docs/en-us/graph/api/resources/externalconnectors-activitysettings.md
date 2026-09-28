<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-activitysettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# activitySettings resource type

Namespace: microsoft.graph.externalConnectors

Collects configurable settings related to activities involving connector content.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| urlToItemResolvers | [microsoft.graph.externalConnectors.urlToItemResolverBase](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-urltoitemresolverbase?view=graph-rest-1.0) collection | Specifies configurations to identify an **externalItem** based on a shared URL. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalConnectors.activitySettings",
  "urlToItemResolvers": [
    {
      "@odata.type": "microsoft.graph.externalConnectors.urlToItemResolverBase"
    }
  ]
}
```
