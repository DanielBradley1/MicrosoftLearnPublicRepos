<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/syntheticmediadetectioninfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# syntheticMediaDetectionInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the current synthetic media detection result attached to a [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-beta) in a call. Detection bots produce this object indirectly by invoking [reportSyntheticMedia](https://learn.microsoft.com/en-us/graph/api/participant-reportsyntheticmedia?view=graph-rest-beta). The service then surfaces it on the participant in roster updates and GET responses so all participants can react to the detection.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| detectionId | Guid | Unique identifier for the detection event. This property correlates with the `id` parameter that the detection bot passed to **reportSyntheticMedia**. |
| detectorBot | String | Identifier of the detection bot that produced this result. |
| isParticipantTrusted | Boolean | Set to `true` if the participant is classified as trusted or reliable \(for example, a known internal user\); otherwise, `false`. |
| syntheticConfidence | Double | Confidence score \(`0.0` to `1.0`\) that the participant's media is synthetic. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.syntheticMediaDetectionInfo",
  "detectionId": "Guid",
  "syntheticConfidence": "Double",
  "detectorBot": "String",
  "isParticipantTrusted": "Boolean"
}
```
