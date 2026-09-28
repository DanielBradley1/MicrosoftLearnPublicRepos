<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/searchquery?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-08 -->

# searchQuery resource type

Namespace: microsoft.graph

Represents a search query that contains search terms and optional filters.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| queryString | String | The search query containing the search terms. Required. |
| queryTemplate | String | Provides a way to decorate the query string. Supports both KQL and query variables. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "queryString": "String",
  "queryTemplate": "String"
}
```
