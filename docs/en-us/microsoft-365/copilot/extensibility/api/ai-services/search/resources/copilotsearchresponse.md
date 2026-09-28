<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/search/resources/copilotsearchresponse -->
<!-- Sitemap-Last-Modified: 2025-10-20 -->

# copilotSearchResponse resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents results from a search query.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `totalCount` | Int32 | Total number of search results available for the query. |
| `searchHits` | [copilotSearchHit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/search/resources/copilotsearchhit) collection | Array of search result objects ordered by relevance. If empty, no relevant results were found. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotSearchResponse",
  "totalCount": "Int32",
  "searchHits": [
    {
      "@odata.type": "microsoft.graph.copilotSearchHit"
    }
  ]
}
```
