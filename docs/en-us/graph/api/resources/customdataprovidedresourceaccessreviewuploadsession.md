<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceaccessreviewuploadsession?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# customDataProvidedResourceAccessReviewUploadSession resource type

Namespace: microsoft.graph

Represents an upload session for access review scenarios on an [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). Use this type when uploading external access data for access reviews via the Bring Your Own Data \(BYOD\) flow.

Inherits from [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0).

## Methods

This derived type supports the same methods as the base [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) resource. For the list of supported operations, see the base type documentation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | DateTime when the upload session was created. Read-only. Supports `$orderby`. Inherited from [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0). |
| data | [microsoft.graph.customDataProvidedResourcePayloads.data](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-data?view=graph-rest-1.0) | An object containing the context for which this data is being uploaded. For access review upload sessions, this is of type [microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-accessreviewcontextdata?view=graph-rest-1.0). Inherited from [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0). |
| id | String | Unique identifier of the upload session. Read-only. Inherited from [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0). |
| isUploadDone | Boolean | Indicates if all the necessary files have been uploaded to this session. Inherited from [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0). |
| referenceId | String | The ID of the context for which data is being uploaded, for example, the access review instance ID. Supports `$filter (eq)`. Inherited from [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0). |
| stats | [customDataProvidedResourceUploadStats](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadstats?view=graph-rest-1.0) | Metadata about the files uploaded in this upload session thus far. Inherited from [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0). |
| status | customDataProvidedResourceUploadStatus | Status of the upload session. The possible values are: `active`, `complete`, `expired`, `unknownFutureValue`. Supports `$filter (eq)`. Inherited from [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| files | [customDataProvidedResourceFile](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcefile?view=graph-rest-1.0) collection | The files uploaded during this upload session. Supports `$expand` and `$expand` with nested `$filter` and `$orderby`. Inherited from [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession",
  "id": "String (identifier)",
  "status": "String",
  "isUploadDone": "Boolean",
  "stats": {
    "@odata.type": "microsoft.graph.customDataProvidedResourceUploadStats"
  },
  "createdDateTime": "String (timestamp)",
  "referenceId": "String",
  "data": {
    "@odata.type": "microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData"
  }
}
```
