<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsessionrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# customDataProvidedResourceUploadSessionRequest resource type

Namespace: microsoft.graph

The request object used to create a [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| data | [microsoft.graph.customDataProvidedResourcePayloads.data](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-data?view=graph-rest-1.0) | An object containing the context for which this data is being uploaded. For access review upload sessions, use [microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-accessreviewcontextdata?view=graph-rest-1.0). Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customDataProvidedResourceUploadSessionRequest",
  "data": {
    "@odata.type": "microsoft.graph.customDataProvidedResourcePayloads.data"
  }
}
```
