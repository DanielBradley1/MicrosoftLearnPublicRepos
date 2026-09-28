<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-12 -->

# contentModel resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an AI model used to process documents in SharePoint document libraries. It can either classify documents, or extract metadata from the documents. Some content models set content types to present the classification results.

The extracted metadata is added to columns in the document library. Columns are created when a content model is applied.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/contentmodel-get?view=graph-rest-beta) | [contentModel](https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta) | Read the properties and relationships of a **contentModel** object. |
| [Get applied drives](https://learn.microsoft.com/en-us/graph/api/contentmodel-getapplieddrives?view=graph-rest-beta) | [contentModelUsage](https://learn.microsoft.com/en-us/graph/api/resources/contentmodelusage?view=graph-rest-beta) collection | List all the [contentModelUsage](https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta) information related to an applied **contentModel**. |
| [Get by name](https://learn.microsoft.com/en-us/graph/api/contentmodel-getbyname?view=graph-rest-beta) | [contentModel](https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta) | Read the properties and relationships of a **contentModel** object by its model name. |
| [Add to drive](https://learn.microsoft.com/en-us/graph/api/contentmodel-addtodrive?view=graph-rest-beta) | [contentModelUsage](https://learn.microsoft.com/en-us/graph/api/resources/contentmodelusage?view=graph-rest-beta) | Automatically process new documents in the library. |
| [Remove from drive](https://learn.microsoft.com/en-us/graph/api/contentmodel-removefromdrive?view=graph-rest-beta) | None | Remove the **contentModel** from the document library. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user, device, or applicationthat created the item. Read-only. |
| createdDateTime | DateTimeOffset | Date and time of item creation. Read-only. |
| id | String | The ID of the content model. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user, device, or application that modified the item. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time of item last modification. Read-only. |
| modelType | contentModelType | The type of the **contentModel**. The possible values are: `teachingMethod`, `layoutMethod`, `freeformSelectionMethod`, `prebuiltContractModel`, `prebuiltInvoiceModel`, `prebuiltReceiptModel`, `unknownFutureValue`. |
| name | String | The name of the **contentModel**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.contentModel",
  "id": "String (identifier)",
  "name": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "modelType": "String"
}
```
