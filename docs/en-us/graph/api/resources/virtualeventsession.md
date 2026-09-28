<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-04 -->

# virtualEventSession resource type

Namespace: microsoft.graph

Represents a session in a [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0).

Inherits from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualevent-list-sessions?view=graph-rest-1.0) | [virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession?view=graph-rest-1.0) collection | Get a list of all [virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession?view=graph-rest-1.0) objects under a virtual event. |
| [Get](https://learn.microsoft.com/en-us/graph/api/virtualeventsession-get?view=graph-rest-1.0) | [virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession?view=graph-rest-1.0) | Read the properties and relationships of a [virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowAttendeeToEnableCamera | Boolean | Indicates whether attendees can turn on their camera. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowAttendeeToEnableMic | Boolean | Indicates whether attendees can turn on their microphone. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowBreakoutRooms | Boolean | Indicates whether breakout rooms are enabled for the virtual event session. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowCopyingAndSharingMeetingContent | Boolean | Indicates whether the ability to copy and share meeting content is enabled for the virtual event session. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowedLobbyAdmitters | [allowedLobbyAdmitterRoles](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0#allowedlobbyadmitterroles-values) | Specifies the users who can admit from the lobby. The possible values are: `organizerAndCoOrganizersAndPresenters`, `organizerAndCoOrganizers`, `unknownFutureValue`. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowedPresenters | [onlineMeetingPresenters](#onlinemeetingpresenters-values) | Specifies who can be a presenter in a virtual event session. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowLiveShare | [meetingLiveShareOptions](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0#meetingliveshareoptions-values) | Indicates whether live share is enabled for the virtual event session. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowMeetingChat | [meetingChatMode](#meetingchatmode-values) | Specifies the mode of meeting chat. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowParticipantsToChangeName | Boolean | Specifies whether participants are allowed to rename themselves in an instance of the meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowPowerPointSharing | Boolean | Indicates whether PowerPoint live is enabled for the virtual event session. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowRecording | Boolean | Indicates whether recording is enabled for the virtual event session. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowTeamworkReactions | Boolean | Indicates whether Teams reactions are enabled for the virtual event session. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowTranscription | Boolean | Indicates whether transcription is enabled for the virtual event session. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowWhiteboard | Boolean | Indicates whether whiteboard is enabled for the virtual event session. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| anonymizeIdentityForRoles | onlineMeetingRole collection | Specifies whose identity is anonymized in the virtual event session. The possible values are: `attendee`. The `attendee` value can't be removed through a PATCH operation once added. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| audioConferencing | [audioConferencing](https://learn.microsoft.com/en-us/graph/api/resources/audioconferencing?view=graph-rest-1.0) | The phone access \(dial-in\) information for the virtual event session. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| capacity | Int32 | Represents the expected number of attendees for the virtual event session. |
| chatInfo | [chatInfo](https://learn.microsoft.com/en-us/graph/api/resources/chatinfo?view=graph-rest-1.0) | The chat information associated with the virtual event session. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| chatRestrictions | [chatRestrictions](https://learn.microsoft.com/en-us/graph/api/resources/chatrestrictions?view=graph-rest-1.0) | Specifies the configuration settings for meeting chat restrictions. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| cloudVideoInteropInfo | [cloudVideoInteropInfo](https://learn.microsoft.com/en-us/graph/api/resources/cloudvideointeropinfo?view=graph-rest-1.0) | Conferencing device integration settings for [Cloud Video Interop \(CVI\)](https://learn.microsoft.com/en-us/microsoftteams/cloud-video-interop). Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| endDateTime | [DateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The virtual event session end time. |
| expiryDateTime | DateTimeOffset | Indicates the date and time when the meeting resource expires. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| id | String | The unique identifier of the virtual event session. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| isEndToEndEncryptionEnabled | Boolean | Indicates whether end-to-end encryption \(E2EE\) is enabled for the virtual event session. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| isEntryExitAnnounced | Boolean | Indicates whether to announce when callers join or leave. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| joinInformation | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The join information of the virtual event session. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| joinMeetingIdSettings | [joinMeetingIdSettings](https://learn.microsoft.com/en-us/graph/api/resources/joinmeetingidsettings?view=graph-rest-1.0) | Specifies the **joinMeetingId**, the meeting passcode, and the requirement for the passcode. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| joinWebUrl | String | The join URL of the virtual event session. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| lobbyBypassSettings | [lobbyBypassSettings](https://learn.microsoft.com/en-us/graph/api/resources/lobbybypasssettings?view=graph-rest-1.0) | Specifies which participants can bypass the meeting lobby. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| meetingOptionsWebUrl | String | Provides the URL to the Teams meeting options page for the specified meeting. This link allows *only the organizer* to configure meeting settings. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| meetingSpokenLanguageTag | String | Specifies the spoken language used during the meeting for recording and transcription purposes. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| meetingType | [onlineMeetingType](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0#onlinemeetingtype-values) | The type of the online meeting. The possible values are: `adhoc`, `scheduled`, `recurring`, `broadcast`, `meetnow`, `unknownFutureValue`. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| recordAutomatically | Boolean | Indicates whether to record the virtual event session automatically. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| sensitivityLabelAssignment | [onlineMeetingSensitivityLabelAssignment](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingsensitivitylabelassignment?view=graph-rest-1.0) | Specifies the sensitivity label applied to the Teams meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| startDateTime | [DateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The virtual event session start time. |
| subject | String | The subject of the virtual event session. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| videoOnDemandWebUrl | String | The [URL of the video on demand \(VOD\)](https://learn.microsoft.com/en-us/microsoftteams/manage-vod-publishing) for Microsoft Teams events that allows webinar and town hall organizers to quickly publish and share event recordings. |
| videoTeleconferenceId | String | The video teleconferencing ID. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| watermarkProtection | [watermarkProtectionValues](https://learn.microsoft.com/en-us/graph/api/resources/watermarkprotectionvalues?view=graph-rest-1.0) | Specifies whether the client application should apply a watermark to a content type. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |

### onlineMeetingPresenters values

| Value | Description |
| --- | --- |
| everyone | Everyone is a presenter. Default. |
| organization | Everyone in organizer’s organization is a presenter. |
| roleIsPresenter | Only the participants whose role is presenter are presenters. |
| organizer | Only the organizer is a presenter. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### meetingChatMode values

| Value | Description |
| --- | --- |
| enabled | Meeting chat is enabled. |
| disabled | Meeting chat is disabled. |
| limited | Meeting chat is enabled but only during the meeting call. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### meetingChatHistoryDefaultMode values

| Value | Description |
| --- | --- |
| all | All meeting chat history is shared. |
| none | No meeting chat history is shared. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| attendanceReports | [meetingAttendanceReport](https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport?view=graph-rest-1.0) collection | Attendance reports of this virtual event session. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventSession",
  "allowAttendeeToEnableCamera": "Boolean",
  "allowAttendeeToEnableMic": "Boolean",
  "allowBreakoutRooms": "Boolean",
  "allowCopyingAndSharingMeetingContent": "Boolean",
  "allowedLobbyAdmitters": "String",
  "allowedPresenters": "String",
  "allowLiveShare": "String",
  "allowMeetingChat": "String",
  "allowParticipantsToChangeName": "Boolean",
  "allowPowerPointSharing": "Boolean",
  "allowTeamworkReactions": "Boolean",
  "allowWhiteboard": "Boolean",
  "audioConferencing": {"@odata.type": "microsoft.graph.audioConferencing"},
  "capacity": "Int32",
  "chatInfo": {"@odata.type": "microsoft.graph.chatInfo"},
  "chatRestrictions":{"@odata.type": "microsoft.graph.chatRestrictions"},
  "cloudVideoInteropInfo": {"@odata.type": "microsoft.graph.cloudVideoInteropInfo"},
  "endDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "expiryDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "isEndToEndEncryptionEnabled": "Boolean",
  "isEntryExitAnnounced": "Boolean",
  "joinInformation": {"@odata.type": "microsoft.graph.itemBody"},
  "joinMeetingIdSettings": {"@odata.type": "microsoft.graph.joinMeetingIdSettings"},
  "joinWebUrl": "String",
  "lobbyBypassSettings": {"@odata.type": "microsoft.graph.lobbyBypassSettings"},
  "meetingOptionsWebUrl": "String",
  "meetingSpokenLanguageTag": "String",
  "meetingType": "String",
  "recordAutomatically": "Boolean",
  "sensitivityLabelAssignment": {"@odata.type": "microsoft.graph.onlineMeetingSensitivityLabelAssignment"},
  "shareMeetingChatHistoryDefault": "String",
  "startDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "subject": "String",
  "videoOnDemandWebUrl": "String",
  "videoTeleconferenceId": "String",
  "watermarkProtection": {"@odata.type": "microsoft.graph.watermarkProtectionValues"}
}
```

## Related content

[List meetingAttendanceReports](https://learn.microsoft.com/en-us/graph/api/meetingattendancereport-list?view=graph-rest-1.0)
