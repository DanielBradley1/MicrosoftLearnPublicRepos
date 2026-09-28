<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# customDataProvidedResourceUploadSession resource type

Namespace: microsoft.graph

Represents an upload session created on an [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). This is an abstract type from which the following type is derived.

- [customDataProvidedResourceAccessReviewUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceaccessreviewuploadsession?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

For more information, see [Include custom data provided resource in the catalog for catalog user Access Reviews](https://learn.microsoft.com/en-us/entra/id-governance/custom-data-resource-access-reviews).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/accesspackageresource-post-uploadsessions?view=graph-rest-1.0) | [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) | Create a new object type that is derived from **customDataProvidedResourceUploadSession**. |
| [List](https://learn.microsoft.com/en-us/graph/api/accesspackageresource-list-uploadsessions?view=graph-rest-1.0) | [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) collection | Get a list of objects that are derived from **customDataProvidedResourceUploadSession** and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/customdataprovidedresourceuploadsession-get?view=graph-rest-1.0) | [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) | Read the properties and relationships of an object type that is derived from **customDataProvidedResourceUploadSession**. |
| [Upload file](https://learn.microsoft.com/en-us/graph/api/customdataprovidedresourceuploadsession-uploadfile?view=graph-rest-1.0) | [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) | Upload a file to an object that is derived from **customDataProvidedResourceUploadSession**. |
| [Update](https://learn.microsoft.com/en-us/graph/api/customdataprovidedresourceuploadsession-update?view=graph-rest-1.0) | [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) | Update the properties of an object type that is derived from **customDataProvidedResourceUploadSession**. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/accesspackageresource-delete-uploadsessions?view=graph-rest-1.0) | None | Delete an object type that is derived from **customDataProvidedResourceUploadSession**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | DateTime when the upload session was created. Read-only. Supports `$orderby`. |
| data | [microsoft.graph.customDataProvidedResourcePayloads.data](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-data?view=graph-rest-1.0) | An object containing the context for which this data is being uploaded. |
| id | String | Unique identifier of the upload session. Read-only. |
| isUploadDone | Boolean | Indicates if all the necessary files have been uploaded to this session. |
| referenceId | String | The ID of the context for which data is being uploaded, for example, the Access Review instance ID. Supports `$filter (eq)`. |
| stats | [customDataProvidedResourceUploadStats](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadstats?view=graph-rest-1.0) | Metadata about the files uploaded in this upload session thus far. |
| status | customDataProvidedResourceUploadStatus | Status of the upload session. The possible values are: `active`, `complete`, `expired`, `unknownFutureValue`. Supports `$filter (eq)`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| files | [customDataProvidedResourceFile](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcefile?view=graph-rest-1.0) collection | The files uploaded during this upload session. Supports `$expand` and `$expand` with nested `$filter` and `$orderby`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customDataProvidedResourceUploadSession",
  "id": "String (identifier)",
  "status": "String",
  "isUploadDone": "Boolean",
  "stats": {
    "@odata.type": "microsoft.graph.customDataProvidedResourceUploadStats"
  },
  "createdDateTime": "String (timestamp)",
  "referenceId": "String",
  "data": {
    "@odata.type": "microsoft.graph.customDataProvidedResourcePayloads.data"
  }
}
```
