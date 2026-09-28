<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingengagement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# meetingEngagement resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains information associated with real-time participant interaction behaviors during a meeting, including reactions \(like, love, applause, etc.\), hand raises, camera toggles, and microphone mute/unmute events in an [attendanceRecord](https://learn.microsoft.com/en-us/graph/api/resources/attendancerecord?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| --- | --- | --- |
| `engagementType` | microsoft.graph.meetingEngagementType | The category of the engagement event. Required, non-nullable. |
| `engagementSubType` | String | The specific engagement action within the type \(e.g., `like`, `love`, `applause`, `laugh`, `surprised` for reactions; `raiseHand` for hand; `cameraOn` for camera; `unmute`, `mute` for microphone\). |
| `dateTime` | DateTimeOffset | The UTC date and time when the engagement event occurred, in ISO 8601 format. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "engagementType": "String(reaction, hand, camera, microphone, unknownFutureValue)",
    "engagementSubType": "String",
    "dateTime": "DateTimeOffset"
}  
```
