<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# participant resource type

Namespace: microsoft.graph

Represents a participant in a [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List participant](https://learn.microsoft.com/en-us/graph/api/participant-get?view=graph-rest-1.0) | [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-1.0) | Retrieve a list of **participant** objects in the call. |
| [Get participant](https://learn.microsoft.com/en-us/graph/api/participant-get?view=graph-rest-1.0) | [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-1.0) | Read properties of the **participant** object. |
| [Delete participant](https://learn.microsoft.com/en-us/graph/api/participant-delete?view=graph-rest-1.0) | None | Delete a participant in a call. |
| [Invite](https://learn.microsoft.com/en-us/graph/api/participant-invite?view=graph-rest-1.0) | [inviteParticipantsOperation](https://learn.microsoft.com/en-us/graph/api/resources/inviteparticipantsoperation?view=graph-rest-1.0) | Invite a participant to the call. |
| [Mute participant](https://learn.microsoft.com/en-us/graph/api/participant-mute?view=graph-rest-1.0) | [muteParticipantOperation](https://learn.microsoft.com/en-us/graph/api/resources/muteparticipantoperation?view=graph-rest-1.0) | Mute a participant in a call. |
| [Start hold music](https://learn.microsoft.com/en-us/graph/api/participant-startholdmusic?view=graph-rest-1.0) | [startHoldMusicOperation](https://learn.microsoft.com/en-us/graph/api/resources/startholdmusicoperation?view=graph-rest-1.0) | Place a participant on hold while playing music on the background. |
| [Stop hold music](https://learn.microsoft.com/en-us/graph/api/participant-stopholdmusic?view=graph-rest-1.0) | [stopHoldMusicOperation](https://learn.microsoft.com/en-us/graph/api/resources/stopholdmusicoperation?view=graph-rest-1.0) | Reincorporate a participant previously put on hold to the call. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The participant ID. |
| info | [participantInfo](https://learn.microsoft.com/en-us/graph/api/resources/participantinfo?view=graph-rest-1.0) | Information about the participant. |
| isInLobby | Boolean | `true` if the participant is in lobby. |
| isMuted | Boolean | `true` if the participant is muted \(client or server muted\). |
| mediaStreams | [mediaStream](https://learn.microsoft.com/en-us/graph/api/resources/mediastream?view=graph-rest-1.0) collection | The list of media streams. |
| metadata | String | A blob of data provided by the participant in the roster. |
| recordingInfo | [recordingInfo](https://learn.microsoft.com/en-us/graph/api/resources/recordinginfo?view=graph-rest-1.0) | Information about whether the participant has recording capability. |
| removedState | [removedState](https://learn.microsoft.com/en-us/graph/api/resources/removedstate?view=graph-rest-1.0) | Indicates the reason why the **participant** was removed from the roster. |
| restrictedExperience | [onlineMeetingRestricted](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingrestricted?view=graph-rest-1.0) | Indicates the reason or reasons media content from this participant is restricted. |
| rosterSequenceNumber | Int64 | Indicates the roster sequence number in which the **participant** was last updated. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "info": {"@odata.type": "#microsoft.graph.participantInfo"},
  "isInLobby": "Boolean",
  "isMuted": "Boolean",
  "mediaStreams": [ { "@odata.type": "#microsoft.graph.mediaStream" } ],
  "metadata": "String",
  "recordingInfo": { "@odata.type": "#microsoft.graph.recordingInfo" },
  "removedState": { "@odata.type": "#microsoft.graph.removedState" },
  "restrictedExperience": { "@odata.type": "#microsoft.graph.onlineMeetingRestricted" },
  "rosterSequenceNumber": "Int64"
}
```
