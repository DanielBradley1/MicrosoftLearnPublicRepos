<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/watermarkprotectionvalues?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# watermarkProtectionValues resource type

Namespace: microsoft.graph

Indicates that a watermark is enabled for this particular meeting. Any clients that don't support watermarks will have a restricted \(audio-only\) experience in the meeting.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabledForContentSharing | Boolean | Indicates whether to apply a watermark to any shared content. |
| isEnabledForVideo | Boolean | Indicates whether to apply a watermark to everyone's video feed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.watermarkProtectionValues",
  "isEnabledForContentSharing": "Boolean",
  "isEnabledForVideo": "Boolean"
}
```
