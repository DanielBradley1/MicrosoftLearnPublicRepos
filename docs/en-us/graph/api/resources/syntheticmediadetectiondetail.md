<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/syntheticmediadetectiondetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# syntheticMediaDetectionDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents one individual detection result produced by a synthetic media detection model for a single time segment of media. A [reportSyntheticMedia](https://learn.microsoft.com/en-us/graph/api/participant-reportsyntheticmedia?view=graph-rest-beta) request can contain a collection of these details \(for example, one per model or per segment\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| confidence | Double | Confidence score for this specific detection, expressed as a value between `0.0` and `1.0`. |
| modality | contentModality | Type of media to be analyzed. The possible values are: `audio`, `video`, `image`, `text`, `multimodal`, `unknownFutureValue`. |
| modelName | String | Name of the detection model used \(for example, `DeepfakeDetector-v2`, `VoiceAuthenticator-v1`\). |
| modelTasks | String collection | Detection tasks that the model performed. This value is free-form text. The bot can specify any task names that describe its analysis. Common examples include `faceSwap`, `lipSync`, and `voiceClone`. |
| segment | [mediaSegment](https://learn.microsoft.com/en-us/graph/api/resources/mediasegment?view=graph-rest-beta) | Time segment of the media that was analyzed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.syntheticMediaDetectionDetail",
  "modelName": "String",
  "modality": "String",
  "modelTasks": [
    "String"
  ],
  "segment": {
    "@odata.type": "microsoft.graph.mediaSegment"
  },
  "confidence": "Double"
}
```
