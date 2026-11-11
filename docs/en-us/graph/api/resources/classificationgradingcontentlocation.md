<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/classificationgradingcontentlocation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-10 -->

# classificationGradingContentLocation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a classification grading match with surrounding document context. In a [classificationGradingJobResponse](https://learn.microsoft.com/en-us/graph/api/resources/classificationgradingjobresponse?view=graph-rest-beta), eligible matches at `result.classification[].matches[]` use this type.

Inherits from `sensitiveContentLocation` and adds **contextText** for eligible partial-document grading matches with accepted caller-supplied embeddings. This includes final pattern-match and retained AI-refined detections, but not Exact Data Match detections. The shared base type and ordinary classification responses are unchanged.

Context text can contain sensitive document content. Use it only for authorized grading and don't write it to diagnostic logs.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| confidence | Int32 | The match confidence level. Inherited from `sensitiveContentLocation`. |
| contextText | String | The complete match and surrounding text, clipped to document boundaries. The default context is up to 100 characters on each side. Read-only, nullable, and omitted when unavailable. |
| evidences | [sensitiveContentEvidence](https://learn.microsoft.com/en-us/graph/api/resources/sensitivecontentevidence?view=graph-rest-beta) collection | Evidence associated with the match. Inherited from `sensitiveContentLocation`. |
| idMatch | String | The matched identifier text. Inherited from `sensitiveContentLocation`. |
| length | Int32 | The match length in the normalized classified text, not in **contextText**. Inherited from `sensitiveContentLocation`. |
| offset | Int32 | The match's start position in the normalized classified text, not in **contextText**. Inherited from `sensitiveContentLocation`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.classificationGradingContentLocation",
  "confidence": "Integer",
  "evidences": [
    {
      "@odata.type": "microsoft.graph.sensitiveContentEvidence"
    }
  ],
  "idMatch": "String",
  "length": "Integer",
  "offset": "Integer",
  "contextText": "String"
}
```
