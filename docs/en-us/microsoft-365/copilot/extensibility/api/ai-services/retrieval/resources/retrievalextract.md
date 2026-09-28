<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/retrievalextract -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# retrievalExtract resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a single extract within the list of retrieval extracts.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `relevanceScore` | Float | The cosine similarity between the text extract and the `queryString`, normalized to the 0-1 range. A `retrievalExtract` can be returned without a relevance score. |
| `text` | String | The text extract received. |

| Property | Type | Description |
| :--- | :--- | :--- |
| `pageNumbers` | Int32 collection | The collection of page numbers that the extract is on. The API returns this property only when `includeThumbnails` is true in the initial request. |
| `relevanceScore` | Float | The cosine similarity between the text extract and the `queryString`, normalized to the 0-1 range. A `retrievalExtract` can be returned without a relevance score. |
| `text` | String | The text extract received. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.retrievalExtract",
  "text": "String",
  "relevanceScore": "Float"
}
```

```json
{
  "@odata.type": "#microsoft.graph.retrievalExtract",
  "text": "String",
  "relevanceScore": "Float",
  "pageNumbers": [
    "Integer"
  ]
}
```
