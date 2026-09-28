<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/searchalteration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# searchAlteration resource type

Namespace: microsoft.graph

Provides the details about the search alteration for spelling correction.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alteredHighlightedQueryString | String | Defines the altered highlighted query string with spelling correction. The annotation around the corrected segment is: `\\ue000, \\ue001`. |
| alteredQueryString | String | Defines the altered query string with spelling correction. |
| alteredQueryTokens | [alteredQueryToken](https://learn.microsoft.com/en-us/graph/api/resources/alteredquerytoken?view=graph-rest-1.0) collection | Represents changed segments related to an original user query. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "alteredHighlightedQueryString": "String",
  "alteredQueryString": "String",
  "alteredQueryTokens": [{"@odata.type": "microsoft.graph.alteredQueryToken"}]
}
```
