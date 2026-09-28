<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/retrievalresponse -->
<!-- Sitemap-Last-Modified: 2026-08-14 -->

# retrievalResponse resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents results from a retrieval query.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `retrievalHits` | [retrievalHit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/retrievalhit) collection | A collection of the retrieval results. If empty, no relevant results were found. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.retrievalResponse",
  "retrievalHits": [
    {
      "@odata.type": "microsoft.graph.retrievalHit"
    }
  ]
}
```
