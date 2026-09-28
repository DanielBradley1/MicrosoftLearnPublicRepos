<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/searchhitscontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# searchHitsContainer resource type

Namespace: microsoft.graph

Represent the list of search results.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hits | [searchHit](https://learn.microsoft.com/en-us/graph/api/resources/searchhit?view=graph-rest-1.0) collection | A collection of the search results. |
| moreResultsAvailable | Boolean | Provides information if more results are available. Based on this information, you can adjust the **from** and **size** properties of the [searchRequest](https://learn.microsoft.com/en-us/graph/api/resources/searchrequest?view=graph-rest-1.0) accordingly. |
| total | Int32 | The total number of results. Note this isn't the number of results on the page, but the total number of results satisfying the query. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "hits": [{"@odata.type": "microsoft.graph.searchHit"}],
  "moreResultsAvailable": true,
  "total": 1024
}
```
