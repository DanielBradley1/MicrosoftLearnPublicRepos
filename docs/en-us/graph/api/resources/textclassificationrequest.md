<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/textclassificationrequest?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-31 -->

# textClassificationRequest resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a request to classify text for sensitive information types. Optionally include caller-supplied precomputed [embeddingInput](https://learn.microsoft.com/en-us/graph/api/resources/embeddinginput?view=graph-rest-beta) values so the service can skip recomputing embeddings for the text.

A **textClassificationRequest** is submitted to the **classifyText** action of the **dataClassificationService** resource.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentMetaData | [classificationRequestContentMetaData](https://learn.microsoft.com/en-us/graph/api/resources/classificationrequestcontentmetadata?view=graph-rest-beta) | Metadata that describes the content being classified. |
| embeddings | [embeddingInput](https://learn.microsoft.com/en-us/graph/api/resources/embeddinginput?view=graph-rest-beta) collection | Optional caller-supplied precomputed embeddings for the text, so the service can skip recomputing them. Embeddings for models outside the allow-list are rejected with a 400. |
| fileExtension | String | The file extension of the content being classified. |
| id | String | The unique identifier for the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| matchTolerancesToInclude | [mlClassificationMatchTolerance](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#mlclassificationmatchtolerance-values) | The match tolerance levels to include in the classification results. The possible values are: `exact`, `near`. |
| scopesToRun | [sensitiveTypeScope](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#sensitivetypescope-values) | The document scopes over which to run classification. The possible values are: `fullDocument`, `partialDocument`. |
| sensitiveTypeIds | String collection | The identifiers of the sensitive information types to evaluate against the text. |
| text | String | The text to classify. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.textClassificationRequest",
  "id": "String (identifier)",
  "text": "String",
  "embeddings": [
    {
      "@odata.type": "microsoft.graph.embeddingInput",
      "modelType": "String",
      "data": "String",
      "chunkOffsets": {
        "@odata.type": "microsoft.graph.chunkOffsets",
        "starts": "String",
        "lengths": "String"
      }
    }
  ],
  "fileExtension": "String",
  "sensitiveTypeIds": [
    "String"
  ],
  "scopesToRun": "String",
  "matchTolerancesToInclude": "String",
  "contentMetaData": {
    "@odata.type": "microsoft.graph.classificationRequestContentMetaData",
    "sourceId": "String",
    "workloadType": "String"
  }
}
```
