<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# callRecording resource type

Namespace: microsoft.graph

Represents a recording associated with an [online meeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) or an [ad hoc call](https://learn.microsoft.com/en-us/graph/api/resources/adhoccall?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-list-recordings?view=graph-rest-1.0) | [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) collection | Get the list of [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) objects associated with a scheduled [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/callrecording-get?view=graph-rest-1.0) | [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) | Get a [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) object associated with a scheduled [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/callrecording-get?view=graph-rest-1.0) | [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) | Get a [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) object associated with a meeting and an ad hoc call after the instance has ended. |
| [Get delta by organizer](https://learn.microsoft.com/en-us/graph/api/callrecording-delta?view=graph-rest-1.0) | [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) collection | Get a set of [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) resources that were added for [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) instances organized by the specified user. |
| [List recordings by organizer](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-getallrecordings?view=graph-rest-1.0) | [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) collection | Get the [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) objects for all the [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) instances organized by the specified user. |
| [Get recordings initiated by a specified user](https://learn.microsoft.com/en-us/graph/api/adhoccall-getallrecordings?view=graph-rest-1.0) | [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) collection | Get the [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) objects from [ad hoc call](https://learn.microsoft.com/en-us/graph/api/resources/adhoccall?view=graph-rest-1.0) instances that a specific user initiates. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callId | String | The unique identifier for the [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) that is related to this recording. Read-only. |
| content | Stream | The content of the recording. Read-only. |
| contentCorrelationId | String | The unique identifier that links the transcript with its corresponding recording. Read-only. |
| createdDateTime | DateTimeOffset | Date and time at which the recording was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| endDateTime | DateTimeOffset | Date and time at which the recording ends. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| id | String | The unique identifier for the recording. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| meetingId | String | The unique identifier of the **onlineMeeting** related to this recording. Read-only. |
| meetingOrganizer | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity information of the organizer of the **onlineMeeting** related to this recording. Read-only. |
| recordingContentUrl | String | The URL that can be used to access the content of the recording. Read-only. |

## Relationships

None.

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
  "recordingContentUrl": "String"
}
```
