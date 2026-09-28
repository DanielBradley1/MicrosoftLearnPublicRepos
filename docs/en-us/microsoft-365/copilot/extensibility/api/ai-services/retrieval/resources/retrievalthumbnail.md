<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/retrievalthumbnail -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# retrievalThumbnail resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a thumbnail associated with a [retrievalHit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/retrievalhit).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `content` | String | The Base64 representation of the thumbnail. |
| `mediaType` | String | The media type for proper interpretation of the Base64 content. |
| `pageNumber` | Int32 | The numeric page number the thumbnail represents. Use this property to associate the page numbers returned in individual extracts to the appropriate thumbnail. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.retrievalThumbnail",
  "content": "String",
  "mediaType": "String",
  "pageNumber": "Integer"
}
```
