<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingengagement?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# meetingEngagement resource type

Namespace: microsoft.graph

Contains information associated with real-time participant interaction behaviors during a meeting, including reactions, hand raises, camera toggles, and microphone mute and unmute events. Returned by the **engagements** property of the [attendanceRecord](https://learn.microsoft.com/en-us/graph/api/resources/attendancerecord?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dateTime | DateTimeOffset | The date and time when the engagement event occurred. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2026 is `2026-01-01T00:00:00Z`. |
| engagementSubType | String | The specific engagement action within the engagement type. The possible values are: `like`, `love`, `applause`, `laugh`, `surprised` for `reaction`; `raiseHand` for `hand`; `cameraOn`, `cameraOff` for `camera`; and `mute`, `unmute` for `microphone`. |
| engagementType | meetingEngagementType | The category of the engagement event. The possible values are: `reaction`, `hand`, `camera`, `microphone`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.meetingEngagement",
  "dateTime": "String (timestamp)",
  "engagementSubType": "String",
  "engagementType": "String"
}
```
