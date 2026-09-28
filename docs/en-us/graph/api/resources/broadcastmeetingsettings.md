<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/broadcastmeetingsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# broadcastMeetingSettings resource type

Namespace: microsoft.graph

Represents settings related to a [live event](https://learn.microsoft.com/en-us/microsoftteams/teams-live-events/what-are-teams-live-events) in Microsoft Teams.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| allowedAudience | [broadcastMeetingAudience](#broadcastmeetingaudience-values) | Defines who can join the Teams live event. Possible values are listed in the following table. |
| captions | [broadcastMeetingCaptionSettings](https://learn.microsoft.com/en-us/graph/api/resources/broadcastmeetingcaptionsettings?view=graph-rest-1.0) | Caption settings of a Teams live event. |
| isRecordingEnabled | Boolean | Indicates whether recording is enabled for this Teams live event. Default value is `false`. |
| isAttendeeReportEnabled | Boolean | Indicates whether attendee report is enabled for this Teams live event. Default value is `false`. |
| isQuestionAndAnswerEnabled | Boolean | Indicates whether Q&A is enabled for this Teams live event. Default value is `false`. |
| isVideoOnDemandEnabled | Boolean | Indicates whether video on demand is enabled for this Teams live event. Default value is `false`. |

### broadcastMeetingAudience values

| Value | Description |
| --- | --- |
| everyone | This Teams live event is open to anyone. This is the default value. |
| organization | Everyone in your org can join this Teams live event. |
| roleIsAttendee | Only the specified people can join this Teams live event. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.broadcastMeetingSettings",
  "allowedAudience": "everyone | organization | roleIsAttendee | unknownFutureValue",
  "captions": {
    "@odata.type": "microsoft.graph.broadcastMeetingCaptionSettings"
  },
  "isAttendeeReportEnabled": "Boolean",
  "isQuestionAndAnswerEnabled": "Boolean",
  "isRecordingEnabled": "Boolean",
  "isVideoOnDemandEnabled": "Boolean"
}
```
