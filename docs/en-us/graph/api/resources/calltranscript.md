<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# callTranscript resource type

Namespace: microsoft.graph

Represents a transcript associated with an [online meeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) and [ad hoc calls](https://learn.microsoft.com/en-us/graph/api/resources/adhoccall?view=graph-rest-1.0).

Note

For more information on access to transcripts through this API, see [Tenant administrator controls for transcript access](https://learn.microsoft.com/en-us/graph/api/calltranscript-get?view=graph-rest-1.0#tenant-administrator-controls-for-transcript-access).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List transcripts](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-list-transcripts?view=graph-rest-1.0) | [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) collection | Get the list of [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) objects associated with an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0). |
| [Get transcript](https://learn.microsoft.com/en-us/graph/api/calltranscript-get?view=graph-rest-1.0) | [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) | Get a [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) object associated with an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0). |
| [Get delta by organizer](https://learn.microsoft.com/en-us/graph/api/calltranscript-delta?view=graph-rest-1.0) | [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) collection | Get a set of [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) resources that were added for [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) instances organized by the specified user. |
| [List transcripts by organizer](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-getalltranscripts?view=graph-rest-1.0) | [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) collection | Get the [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) objects for all the [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) instances organized by the specified user. |
| [Get transcripts initiated by a specified user](https://learn.microsoft.com/en-us/graph/api/adhoccall-getalltranscripts?view=graph-rest-1.0) | [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) collection | Get all [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) objects from [ad hoc call](https://learn.microsoft.com/en-us/graph/api/resources/adhoccall?view=graph-rest-1.0) instances that a specific user initiates. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callId | String | The unique identifier for the [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) that is related to this transcript. Read-only. |
| content | Stream | The content of the transcript. Read-only. |
| contentCorrelationId | String | The unique identifier that links the transcript with its corresponding recording. Read-only. |
| createdDateTime | DateTimeOffset | Date and time at which the transcript was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| endDateTime | DateTimeOffset | Date and time at which the transcription ends. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| id | String | The unique identifier for the transcript. Read-only. |
| meetingId | String | The unique identifier of the online meeting related to this transcript. Read-only. |
| meetingOrganizer | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity information of the organizer of the **onlineMeeting** related to this transcript. Read-only. |
| metadataContent | Stream | The time-aligned metadata of the utterances in the transcript. Read-only. |
| transcriptContentUrl | String | The URL that can be used to access the content of the transcript. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "callId": "String",
  "content": "Stream",
  "contentCorrelationId": "String",
  "createdDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "meetingId": "String",
  "meetingOrganizer": {"@odata.type": "microsoft.graph.identitySet"},
  "metadataContent": "Stream",
  "transcriptContentUrl": "String"
}
```
