<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/embeddinginput?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# embeddingInput resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A set of precomputed embedding vectors produced by a single embedding model for the request text. Provide one **embeddingInput** per model in the [textClassificationRequest](https://learn.microsoft.com/en-us/graph/api/resources/textclassificationrequest?view=graph-rest-beta) **embeddings** collection so the service can skip recomputing embeddings.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| chunkOffsets | [chunkOffsets](https://learn.microsoft.com/en-us/graph/api/resources/chunkoffsets?view=graph-rest-beta) | Optional offset metadata for the text chunks that produced this embedding data. The **starts** property is required when **chunkOffsets** is present. When **lengths** is also present, the decoded element counts must match and pair by index. |
| data | String | The embedding vectors the model produced for the text, encoded as a base64 string of little-endian 32-bit floats. Every vector the model emitted \(for example, one per text chunk\) is concatenated in order; each contributes exactly the modelType's embedding dimension worth of float components, so the decoded length must be a whole multiple of that dimension. |
| modelType | String | The embedding model identifier drawn from the service allow-list \(for example: text-embedding-3-small-512\). Unique \(case-insensitive\) within the embeddings collection; entries whose modelType is outside the allow-list are rejected with a 400. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.embeddingInput",
  "modelType": "String",
  "data": "String",
  "chunkOffsets": {
    "@odata.type": "microsoft.graph.chunkOffsets"
  }
}
```
