<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# onlineMeeting resource type

Namespace: microsoft.graph

Contains information about a meeting, including the URL used to join a meeting, the attendees list, and the description.

Caution

Microsoft Graph online meeting APIs that support Microsoft Teams live events are deprecated and stopped returning data on September 30, 2024. New Microsoft Graph APIs will replace these APIs in spring of 2025. For more information, see [Retirement of Teams live events API on Microsoft Graph](https://devblogs.microsoft.com/microsoft365dev/deprecation-of-teams-live-events-api-on-microsoft-graph/).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/application-post-onlinemeetings?view=graph-rest-1.0) | [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) | Create an online meeting. |
| [Get](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-get?view=graph-rest-1.0) | [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) | Read the properties and relationships of an **onlineMeeting** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-update?view=graph-rest-1.0) | [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) | Update the properties of an **onlineMeeting** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-delete?view=graph-rest-1.0) | None | Delete an **onlineMeeting** object. |
| [Create or get](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-createorget?view=graph-rest-1.0) | [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) | Create an **onlineMeeting** object with a custom, external ID. If the meeting already exists, retrieve its properties. |
| [List transcripts](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-list-transcripts?view=graph-rest-1.0) | [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) collection | Retrieve the list of transcripts of an **onlineMeeting**. |
| [List recordings](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-list-recordings?view=graph-rest-1.0) | [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) collection | Retrieve the list of recordings of an **onlineMeeting**. |

Note

- A bearer token is required for the `Authorization` header for all the methods listed in the previous table. For details about how to get the `token` for the `Authorization` header, see [Get access on behalf of a user](https://learn.microsoft.com/en-us/graph/auth-v2-user?tabs=http#3-request-an-access-token).
- The expiry time for online meetings is set to 60 days after the meeting's start or end time. If the meeting is updated or activated before it expires, the expiry time will be extended by another 60 days.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowAttendeeToEnableCamera | Boolean | Indicates whether attendees can turn on their camera. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowAttendeeToEnableMic | Boolean | Indicates whether attendees can turn on their microphone. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowBreakoutRooms | Boolean | Indicates whether breakout rooms are enabled for the meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowCopyingAndSharingMeetingContent | Boolean | Indicates whether the ability to copy and share meeting content is enabled for the meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowedLobbyAdmitters | [allowedLobbyAdmitterRoles](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0#allowedlobbyadmitterroles-values) | Specifies the users who can admit from the lobby. The possible values are: `organizerAndCoOrganizersAndPresenters`, `organizerAndCoOrganizers`, `unknownFutureValue`. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowedPresenters | [onlineMeetingPresenters](#onlinemeetingpresenters-values) | Specifies who can be a presenter in a meeting. Possible values are listed in the following table. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowLiveShare | [meetingLiveShareOptions](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0#meetingliveshareoptions-values) | Indicates whether live share is enabled for the meeting. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowMeetingChat | [meetingChatMode](#meetingchatmode-values) | Specifies the mode of meeting chat. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowParticipantsToChangeName | Boolean | Specifies if participants are allowed to rename themselves in an instance of the meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowPowerPointSharing | Boolean | Indicates whether PowerPoint live is enabled for the meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowTeamworkReactions | Boolean | Indicates whether Teams reactions are enabled for the meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowRecording | Boolean | Indicates whether recording is enabled for the meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowTeamworkReactions | Boolean | Indicates whether Teams reactions are enabled for the meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowTranscription | Boolean | Indicates whether transcription is enabled for the meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| allowWhiteboard | Boolean | Indicates whether whiteboard is enabled for the meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| audioConferencing | [audioConferencing](https://learn.microsoft.com/en-us/graph/api/resources/audioconferencing?view=graph-rest-1.0) | The phone access \(dial-in\) information for an online meeting. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| chatInfo | [chatInfo](https://learn.microsoft.com/en-us/graph/api/resources/chatinfo?view=graph-rest-1.0) | The chat information associated with this online meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| chatRestrictions | [chatRestrictions](https://learn.microsoft.com/en-us/graph/api/resources/chatrestrictions?view=graph-rest-1.0) | Specifies the configuration settings for meeting chat restrictions. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| cloudVideoInteropInfo | [cloudVideoInteropInfo](https://learn.microsoft.com/en-us/graph/api/resources/cloudvideointeropinfo?view=graph-rest-1.0) | Conferencing device integration settings for [Cloud Video Interop \(CVI\)](https://learn.microsoft.com/en-us/microsoftteams/cloud-video-interop). Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| creationDateTime | DateTime | The meeting creation time in UTC. Read-only. |
| endDateTime | DateTime | The meeting end time in UTC. Required when you create an online meeting. |
| expiryDateTime | DateTimeOffset | Indicates the date and time when the meeting resource expires. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| externalId | String | The external ID that is a custom identifier. Optional. |
| id | String | The default ID associated with the online meeting. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| isEndToEndEncryptionEnabled | Boolean | Indicates whether end-to-end encryption \(E2EE\) is enabled for the online meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| isEntryExitAnnounced | Boolean | Indicates whether to announce when callers join or leave. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| joinInformation | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The join information in the language and locale variant specified in the `Accept-Language` request HTTP header. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| joinMeetingIdSettings | [joinMeetingIdSettings](https://learn.microsoft.com/en-us/graph/api/resources/joinmeetingidsettings?view=graph-rest-1.0) | Specifies the **joinMeetingId**, the meeting passcode, and the requirement for the passcode. Once an **onlineMeeting** is created, the **joinMeetingIdSettings** can't be modified. To make any changes to this property, the meeting needs to be canceled and a new one needs to be created. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| joinWebUrl | String | The join URL of the online meeting. The format of the URL may change; therefore, users shouldn't rely on any information extracted from parsing the URL. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| lobbyBypassSettings | [lobbyBypassSettings](https://learn.microsoft.com/en-us/graph/api/resources/lobbybypasssettings?view=graph-rest-1.0) | Specifies which participants can bypass the meeting lobby. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| meetingOptionsWebUrl | String | Provides the URL to the Teams meeting options page for the specified meeting. This link allows *only the organizer* to configure meeting settings. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| meetingSpokenLanguageTag | String | Specifies the spoken language used during the meeting for recording and transcription purposes. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| meetingTemplateId | String | The ID of the [meeting template](https://learn.microsoft.com/en-us/microsoftteams/create-custom-meeting-template). |
| meetingType | [onlineMeetingType](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0#onlinemeetingtype-values) | The type of the online meeting. The possible values are: `adhoc`, `scheduled`, `recurring`, `broadcast`, `meetnow`, `unknownFutureValue`. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| participants | [meetingParticipants](https://learn.microsoft.com/en-us/graph/api/resources/meetingparticipants?view=graph-rest-1.0) | The participants associated with the online meeting, including the organizer and the attendees. |
| recordAutomatically | Boolean | Indicates whether to record the meeting automatically. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| sensitivityLabelAssignment | [onlineMeetingSensitivityLabelAssignment](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingsensitivitylabelassignment?view=graph-rest-1.0) | Specifies the sensitivity label applied to the Teams meeting. |
| shareMeetingChatHistoryDefault | [meetingChatHistoryDefaultMode](#meetingchathistorydefaultmode-values) | Specifies whether meeting chat history is shared with participants. The possible values are: `all`, `none`, `unknownFutureValue`. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| startDateTime | DateTime | The meeting start time in UTC. |
| subject | String | The subject of the online meeting. Required when you create an online meeting. |
| videoTeleconferenceId | String | The video teleconferencing ID. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| watermarkProtection | [watermarkProtectionValues](https://learn.microsoft.com/en-us/graph/api/resources/watermarkprotectionvalues?view=graph-rest-1.0) | Specifies whether the client application should apply a watermark a content type. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| attendeeReport \(deprecated\) | Stream | The content stream of the attendee report of a [Microsoft Teams live event](https://learn.microsoft.com/en-us/microsoftteams/teams-live-events/what-are-teams-live-events). Read-only. |
| broadcastSettings \(deprecated\) | [broadcastMeetingSettings](https://learn.microsoft.com/en-us/graph/api/resources/broadcastmeetingsettings?view=graph-rest-1.0) | Settings related to a live event. |
| isBroadcast \(deprecated\) | Boolean | Indicates whether this meeting is a [Teams live event](https://learn.microsoft.com/en-us/microsoftteams/teams-live-events/what-are-teams-live-events). |

### onlineMeetingPresenters values

| Value | Description |
| --- | --- |
| everyone | Everyone is a presenter. Default. |
| organization | Everyone in organizer’s organization is a presenter. |
| roleIsPresenter | Only the participants whose role is presenter are presenters. |
| organizer | Only the organizer is a presenter. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

Tip

When creating or updating an online meeting with **allowedPresenters** set to `roleIsPresenter`, include a full list of **attendees** with the specified attendees' **role** set to `presenter` in the request body.

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
| --- | --- | --- |
| attendanceReports | [meetingAttendanceReport](https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport?view=graph-rest-1.0) collection | The attendance reports of an online meeting. Read-only. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). |
| recordings | [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) collection | The recordings of an online meeting. Read-only. |
| transcripts | [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) collection | The transcripts of an online meeting. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
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
  "allowRecording": "Boolean",
  "allowTeamworkReactions": "Boolean",
  "allowTranscription": "Boolean",
  "allowWhiteboard": "Boolean",
  "attendeeReport": "Stream",
  "audioConferencing": {"@odata.type": "microsoft.graph.audioConferencing"},
  "broadcastSettings": {"@odata.type": "microsoft.graph.broadcastMeetingSettings"},
  "chatInfo": {"@odata.type": "microsoft.graph.chatInfo"},
  "chatRestrictions": {"@odata.type": "microsoft.graph.chatRestrictions"},
  "cloudVideoInteropInfo": {"@odata.type": "microsoft.graph.cloudVideoInteropInfo"},
  "creationDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "expiryDateTime": "String (timestamp)",
  "externalId": "String",
  "id": "String (identifier)",
  "isBroadcast": "Boolean",
  "isEndToEndEncryptionEnabled": "Boolean",
  "isEntryExitAnnounced": "Boolean",
  "joinInformation": {"@odata.type": "microsoft.graph.itemBody"},
  "joinMeetingIdSettings": {"@odata.type": "microsoft.graph.joinMeetingIdSettings"},
  "joinWebUrl": "String",
  "lobbyBypassSettings": {"@odata.type": "microsoft.graph.lobbyBypassSettings"},
  "meetingOptionsWebUrl": "String",
  "meetingSpokenLanguageTag": "String",
  "meetingTemplateId": "String",
  "meetingType": "String",
  "participants": {"@odata.type": "microsoft.graph.meetingParticipants"},
  "recordAutomatically": "Boolean",
  "sensitivityLabelAssignment": {"@odata.type": "microsoft.graph.onlineMeetingSensitivityLabelAssignment"},
  "shareMeetingChatHistoryDefault": "String",
  "startDateTime": "String (timestamp)",
  "subject": "String",
  "videoTeleconferenceId": "String",
  "watermarkProtection": "String"
}
```
