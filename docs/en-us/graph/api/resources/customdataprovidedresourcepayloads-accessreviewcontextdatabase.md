<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-accessreviewcontextdatabase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# accessReviewContextDataBase resource type

Namespace: microsoft.graph.customDataProvidedResourcePayloads

Represents the abstract base for access review context data associated with an [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). Contains the access review definition and instance identifiers that link the uploaded data to a specific review. This is an abstract type from which the following types are derived.

- [accessReviewContextData](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-accessreviewcontextdata?view=graph-rest-1.0)
- [applyDecisionContextData](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-applydecisioncontextdata?view=graph-rest-1.0)

Inherits from [microsoft.graph.customDataProvidedResourcePayloads.data](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-data?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| reviewDefinitionId | String | The unique identifier of the access review definition that this data is associated with. |
| reviewInstanceId | String | The unique identifier of the access review instance that this data is associated with. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextDataBase",
  "reviewDefinitionId": "String",
  "reviewInstanceId": "String"
}
```
