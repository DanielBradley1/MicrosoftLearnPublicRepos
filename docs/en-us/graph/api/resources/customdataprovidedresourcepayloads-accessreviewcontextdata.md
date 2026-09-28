<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-accessreviewcontextdata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# accessReviewContextData resource type

Namespace: microsoft.graph.customDataProvidedResourcePayloads

Represents context data for access review upload session scenarios associated with an [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). This type is used as the **data** payload when creating a [customDataProvidedResourceAccessReviewUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceaccessreviewuploadsession?view=graph-rest-1.0) to specify which access review the uploaded data is for.

Inherits from [microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextDataBase](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-accessreviewcontextdatabase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| reviewDefinitionId | String | The unique identifier of the access review definition that this data is associated with. Inherited from [microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextDataBase](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-accessreviewcontextdatabase?view=graph-rest-1.0). |
| reviewInstanceId | String | The unique identifier of the access review instance that this data is associated with. Inherited from [microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextDataBase](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-accessreviewcontextdatabase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData",
  "reviewDefinitionId": "String",
  "reviewInstanceId": "String"
}
```
