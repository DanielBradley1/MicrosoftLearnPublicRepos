<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/adhoccall?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# adhocCall resource type

Namespace: microsoft.graph

Represents an ad hoc call, including PSTN calls, one-to-one calls, and group calls. Use this resource to manage call recordings and transcripts through the Microsoft Graph communications API.

This resource supports subscribing to [change notifications](https://learn.microsoft.com/en-us/graph/change-notifications-overview).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get all recordings](https://learn.microsoft.com/en-us/graph/api/adhoccall-getallrecordings?view=graph-rest-1.0) | [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) collection | Get the [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) objects from [ad hoc call](https://learn.microsoft.com/en-us/graph/api/resources/adhoccall?view=graph-rest-1.0) instances that a specific user initiates. |
| [Get all transcripts](https://learn.microsoft.com/en-us/graph/api/adhoccall-getalltranscripts?view=graph-rest-1.0) | [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) collection | Get all [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) objects from [ad hoc call](https://learn.microsoft.com/en-us/graph/api/resources/adhoccall?view=graph-rest-1.0) instances that a specific user initiates. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTime | The meeting end time in UTC. Required when an ad hoc call is ended. |
| id | String | The unique identifier for the call, including PSTN, 1:1, and group calls. Read-only. |
| startDateTime | DateTime | The meeting start time in UTC. Required when the call is started. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| recordings | [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) collection | The recordings of a call. Read-only. |
| transcripts | [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) collection | The transcripts of a call. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.adhocCall",
  "id": "String (identifier)"
}
```

## Related content

- [Change notifications for Microsoft Teams resources](https://learn.microsoft.com/en-us/graph/teams-change-notification-in-microsoft-teams-overview)
- [Get change notifications for transcripts and recordings using Microsoft Graph](https://learn.microsoft.com/en-us/graph/teams-changenotifications-callrecording-and-calltranscript)
- [callRecording resource type](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0)
- [callTranscript resource type](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0)
