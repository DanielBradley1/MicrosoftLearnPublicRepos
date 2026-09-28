<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# call resource type

Namespace: microsoft.graph

The **call** resource is created when there's an incoming call for the application or the application creates a new outgoing call via a `POST` on `communications/calls`.

Calls can be set up as a peer-to-peer or as a group call. To create or join a group call, supply the `chatInfo` and `meetingInfo`. If these values aren't supplied, a new group call is created automatically. For an incoming call, record these values in a highly available store so that your application can rejoin the call if your application crashes.

Although the same identity can't be invited multiple times, it's possible for an application to join the same meeting multiple times. Each time the application wants to join a call, a separate identity must be provided in order for the clients to display them as different participants.

> **Note:** You can get the join URL from a meeting scheduled with Microsoft Teams. Extract the data from the URL as shown to populate `chatInfo` and `meetingInfo`.

```http
https://teams.microsoft.com/l/meetup-join/19%3ameeting_NTg0NmQ3NTctZDVkZC00YzRhLThmNmEtOGQ3M2E0ODdmZDZk%40thread.v2/0?context=%7b%22Tid%22%3a%2272f988bf-86f1-41af-91ab-2d7cd011db47%22%2c%22Oid%22%3a%224b444206-207c-42f8-92a6-e332b41c88a2%22%7d
```

Becomes:

```http
https://teams.microsoft.com/l/meetup-join/19:meeting_NTg0NmQ3NTctZDVkZC00YzRhLThmNmEtOGQ3M2E0ODdmZDZk@thread.v2/0?context={"Tid":"72f988bf-86f1-41af-91ab-2d7cd011db47","Oid":"4b444206-207c-42f8-92a6-e332b41c88a2"}
```

Note

The following known issues are associated with this resource:

- [Webhook message processing exception: System.Security.Cryptography.CryptographicException](https://learn.microsoft.com/en-us/graph/known-issues#communication-calling-sdk-webhook-message-processing-exception-systemsecuritycryptographycryptographicexception)
- [Support for multi-endpoint use case in delta roster notification mode is missing](https://learn.microsoft.com/en-us/graph/known-issues#communication-calling-sdk-support-for-multi-endpoint-use-case-in-delta-roster-notification-mode-is-missing)
- [Inconsistent recorded participant number shown on teams client when bot grouping is enabled](https://learn.microsoft.com/en-us/graph/known-issues#communications-calling-sdk-inconsistent-recorded-participant-number-shown-on-teams-client-when-bot-grouping-is-enabled)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/application-post-calls?view=graph-rest-1.0) | [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) | Create **call** enables your bot to create a new outgoing peer-to-peer or group call, or join an existing meeting. |
| [Get](https://learn.microsoft.com/en-us/graph/api/call-get?view=graph-rest-1.0) | [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) | Read properties of the **call** object. |
| [Delete/hang up](https://learn.microsoft.com/en-us/graph/api/call-delete?view=graph-rest-1.0) | None | Delete or Hang-up an active **call**. |
| [Keep alive](https://learn.microsoft.com/en-us/graph/api/call-keepalive?view=graph-rest-1.0) | None | Ensure that the call remains active. |
| **Call handling** |  |  |
| [Answer](https://learn.microsoft.com/en-us/graph/api/call-answer?view=graph-rest-1.0) | None | Answer an incoming call. |
| [Reject](https://learn.microsoft.com/en-us/graph/api/call-reject?view=graph-rest-1.0) | None | Reject an incoming call. |
| [Redirect](https://learn.microsoft.com/en-us/graph/api/call-redirect?view=graph-rest-1.0) | None | Redirect an incoming call. |
| [Transfer](https://learn.microsoft.com/en-us/graph/api/call-transfer?view=graph-rest-1.0) | None | Transfer a call |
| **Group calls** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/call-list-participants?view=graph-rest-1.0) | [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-1.0) collection | Get a participant object collection. |
| [Invite participants](https://learn.microsoft.com/en-us/graph/api/participant-invite?view=graph-rest-1.0) | [commsOperation](https://learn.microsoft.com/en-us/graph/api/resources/commsoperation?view=graph-rest-1.0) | Invite participants to the active call. |
| [Mute participant](https://learn.microsoft.com/en-us/graph/api/participant-mute?view=graph-rest-1.0) | [muteParticipantOperation](https://learn.microsoft.com/en-us/graph/api/resources/muteparticipantoperation?view=graph-rest-1.0) | Mute a participant in the group call. |
| [Create](https://learn.microsoft.com/en-us/graph/api/call-post-audioroutinggroups?view=graph-rest-1.0) | [audioRoutingGroup](https://learn.microsoft.com/en-us/graph/api/resources/audioroutinggroup?view=graph-rest-1.0) | Create a new **audioRoutingGroup** by posting to the audioRoutingGroups collection. |
| [List audio routing groups](https://learn.microsoft.com/en-us/graph/api/call-list-audioroutinggroups?view=graph-rest-1.0) | [audioRoutingGroup](https://learn.microsoft.com/en-us/graph/api/resources/audioroutinggroup?view=graph-rest-1.0) collection | Get an **audioRoutingGroup** object collection. |
| [Add large gallery view](https://learn.microsoft.com/en-us/graph/api/call-addlargegalleryview?view=graph-rest-1.0) | [addLargeGalleryViewOperation](https://learn.microsoft.com/en-us/graph/api/resources/addlargegalleryviewoperation?view=graph-rest-1.0) | Add the large gallery view to a call. |
| **Interactive-voice-response** |  |  |
| [Play prompt](https://learn.microsoft.com/en-us/graph/api/call-playprompt?view=graph-rest-1.0) | [playPromptOperation](https://learn.microsoft.com/en-us/graph/api/resources/playpromptoperation?view=graph-rest-1.0) | Play prompt in the call. |
| [Record response](https://learn.microsoft.com/en-us/graph/api/call-record?view=graph-rest-1.0) | [recordOperation](https://learn.microsoft.com/en-us/graph/api/resources/recordoperation?view=graph-rest-1.0) | Records a short audio response from the caller. |
| [Cancel media processing](https://learn.microsoft.com/en-us/graph/api/call-cancelmediaprocessing?view=graph-rest-1.0) | [commsOperation](https://learn.microsoft.com/en-us/graph/api/resources/commsoperation?view=graph-rest-1.0) | Cancel media processing. |
| [Subscribe to tone](https://learn.microsoft.com/en-us/graph/api/call-subscribetotone?view=graph-rest-1.0) | [commsOperation](https://learn.microsoft.com/en-us/graph/api/resources/commsoperation?view=graph-rest-1.0) | Subscribe to DTMF tones. |
| [Send DTMF tone](https://learn.microsoft.com/en-us/graph/api/call-senddtmftones?view=graph-rest-1.0) | [commsOperation](https://learn.microsoft.com/en-us/graph/api/resources/commsoperation?view=graph-rest-1.0) | Send DTMF tones in a call. |
| **Self participant operations** |  |  |
| [Mute application](https://learn.microsoft.com/en-us/graph/api/call-mute?view=graph-rest-1.0) | [muteParticipantOperation](https://learn.microsoft.com/en-us/graph/api/resources/muteparticipantoperation?view=graph-rest-1.0) | Mute self in the call. |
| [Unmute application](https://learn.microsoft.com/en-us/graph/api/call-unmute?view=graph-rest-1.0) | [unmuteParticipantOperation](https://learn.microsoft.com/en-us/graph/api/resources/unmuteparticipantoperation?view=graph-rest-1.0) | Unmute self in the call. |
| [Change screen sharing role](https://learn.microsoft.com/en-us/graph/api/call-changescreensharingrole?view=graph-rest-1.0) | None | Start and stop sharing screen in the call. |
| **Recording Operations** |  |  |
| [Update recording status](https://learn.microsoft.com/en-us/graph/api/call-updaterecordingstatus?view=graph-rest-1.0) | [updateRecordingStatusOperation](https://learn.microsoft.com/en-us/graph/api/resources/updaterecordingstatusoperation?view=graph-rest-1.0) | Updates the recording status. |
| **Logging operations** |  |  |
| [Log teleconference device quality data](https://learn.microsoft.com/en-us/graph/api/call-logteleconferencedevicequality?view=graph-rest-1.0) | [teleconferenceDeviceQuality](https://learn.microsoft.com/en-us/graph/api/resources/teleconferencedevicequality?view=graph-rest-1.0) | Log video teleconferencing device quality data. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callbackUri | String | The callback URL on which callbacks are delivered. Must be an HTTPS URL. |
| callChainId | String | A unique identifier for all the participant calls in a conference or a unique identifier for two participant calls in a P2P call. This identifier must be copied over from `Microsoft.Graph.Call.CallChainId`. |
| callOptions | [outgoingCallOptions](https://learn.microsoft.com/en-us/graph/api/resources/outgoingcalloptions?view=graph-rest-1.0) | Contains the optional features for the call. |
| callRoutes | [callRoute](https://learn.microsoft.com/en-us/graph/api/resources/callroute?view=graph-rest-1.0) collection | The routing information on how the call was retargeted. Read-only. |
| chatInfo | [chatInfo](https://learn.microsoft.com/en-us/graph/api/resources/chatinfo?view=graph-rest-1.0) | The chat information. Required information for joining a meeting. |
| direction | callDirection | The direction of the call. The possible values are `incoming` or `outgoing`. Read-only. |
| id | String | The unique identifier for the call. Read-only. |
| incomingContext | [incomingContext](https://learn.microsoft.com/en-us/graph/api/resources/incomingcontext?view=graph-rest-1.0) | Call context associated with an incoming call. |
| mediaConfig | [appHostedMediaConfig](https://learn.microsoft.com/en-us/graph/api/resources/apphostedmediaconfig?view=graph-rest-1.0) or [serviceHostedMediaConfig](https://learn.microsoft.com/en-us/graph/api/resources/servicehostedmediaconfig?view=graph-rest-1.0) | The media configuration. Required. |
| mediaState | [callMediaState](https://learn.microsoft.com/en-us/graph/api/resources/callmediastate?view=graph-rest-1.0) | Read-only. The call media state. |
| meetingInfo | [organizerMeetingInfo](https://learn.microsoft.com/en-us/graph/api/resources/organizermeetinginfo?view=graph-rest-1.0), [tokenMeetingInfo](https://learn.microsoft.com/en-us/graph/api/resources/tokenmeetinginfo?view=graph-rest-1.0), or [joinMeetingIdMeetingInfo](https://learn.microsoft.com/en-us/graph/api/resources/joinmeetingidmeetinginfo?view=graph-rest-1.0) | The meeting information. Required information for meeting scenarios. |
| myParticipantId | String | Read-only. |
| requestedModalities | modality collection | The list of requested modalities. The possible values are: `unknown`, `audio`, `video`, `videoBasedScreenSharing`, `data`. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | The result information. For example, the result can hold termination reason. Read-only. |
| source | [participantInfo](https://learn.microsoft.com/en-us/graph/api/resources/participantinfo?view=graph-rest-1.0) | The originator of the call. |
| state | callState | The call state. The possible values are: `incoming`, `establishing`, `ringing`, `established`, `hold`, `transferring`, `transferAccepted`, `redirecting`, `terminating`, `terminated`. Read-only. |
| subject | String | The subject of the conversation. |
| targets | [invitationParticipantInfo](https://learn.microsoft.com/en-us/graph/api/resources/participantinfo?view=graph-rest-1.0) collection | The targets of the call. Required information for creating peer to peer call. |
| toneInfo | [toneInfo](https://learn.microsoft.com/en-us/graph/api/resources/toneinfo?view=graph-rest-1.0) | Read-only. |
| transcription | [callTranscriptionInfo](https://learn.microsoft.com/en-us/graph/api/resources/calltranscriptioninfo?view=graph-rest-1.0) | The transcription information for the call. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| contentSharingSessions | [contentSharingSession](https://learn.microsoft.com/en-us/graph/api/resources/contentsharingsession?view=graph-rest-1.0) collection | Read-only. Nullable. |
| operations | [commsOperation](https://learn.microsoft.com/en-us/graph/api/resources/commsoperation?view=graph-rest-1.0) collection | Read-only. Nullable. |
| participants | [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-1.0) collection | Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "callbackUri": "String",
  "callChainId": "String",
  "callOptions": {"@odata.type": "#microsoft.graph.outgoingCallOptions"},
  "chatInfo": {"@odata.type": "#microsoft.graph.chatInfo"},
  "contentSharingSessions": [{ "@odata.type": "microsoft.graph.contentSharingSession" }],
  "direction": "String",
  "id": "String (identifier)",
  "mediaConfig": {"@odata.type": "#microsoft.graph.mediaConfig"},
  "mediaState": {"@odata.type": "#microsoft.graph.callMediaState"},
  "meetingInfo": {"@odata.type": "#microsoft.graph.meetingInfo"},
  "myParticipantId": "String",
  "requestedModalities": ["String"],
  "resultInfo": {"@odata.type": "#microsoft.graph.resultInfo"},
  "source": {"@odata.type": "#microsoft.graph.participantInfo"},
  "state": "String",
  "subject": "String",
  "targets": [{"@odata.type": "#microsoft.graph.invitationParticipantInfo"}],
  "toneInfo": {"@odata.type": "#microsoft.graph.toneInfo"},
  "transcription": {"@odata.type": "#microsoft.graph.callTranscriptionInfo"},
}
```
