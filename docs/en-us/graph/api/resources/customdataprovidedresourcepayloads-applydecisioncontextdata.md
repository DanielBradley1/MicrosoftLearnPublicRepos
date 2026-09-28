<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-applydecisioncontextdata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# applyDecisionContextData resource type

Namespace: microsoft.graph.customDataProvidedResourcePayloads

Represents context data for the callback sent when batch apply decisions are triggered for an [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) in an access review. Contains the access review definition and instance identifiers so the callback receiver can correlate the batch apply result back to the specific review that initiated the operation.

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
  "@odata.type": "#microsoft.graph.customDataProvidedResourcePayloads.applyDecisionContextData",
  "reviewDefinitionId": "String",
  "reviewInstanceId": "String"
}
```
