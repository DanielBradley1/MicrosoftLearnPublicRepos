<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-session?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# session resource type

Namespace: microsoft.graph.callRecords

Represents a user-user communication or a user-meeting communication in the case of a conference call.

One session can be returned multiple times if the communication involves more than one service identity. For more information, see [call record API FAQ](https://learn.microsoft.com/en-us/graph/callrecords-api-faq).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List sessions](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-list-sessions?view=graph-rest-1.0) | [microsoft.graph.callRecords.session](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-session?view=graph-rest-1.0) collection | Retrieve the list of sessions associated with a [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callee | [microsoft.graph.callRecords.endpoint](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-endpoint?view=graph-rest-1.0) | Endpoint that answered the session. |
| caller | [microsoft.graph.callRecords.endpoint](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-endpoint?view=graph-rest-1.0) | Endpoint that initiated the session. |
| endDateTime | DateTimeOffset | UTC time when the last user left the session. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| failureInfo | [microsoft.graph.callRecords.failureInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-failureinfo?view=graph-rest-1.0) | Failure information associated with the session if the session failed. |
| id | string | Unique identifier for the session. Read-only. |
| isTest | Boolean | Specifies whether the session is a test. |
| modalities | microsoft.graph.callRecords.modality collection | List of modalities present in the session. The possible values are: `unknown`, `audio`, `video`, `videoBasedScreenSharing`, `data`, `screenSharing`, `unknownFutureValue`. |
| startDateTime | DateTimeOffset | UTC time when the first user joined the session. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| segments | [microsoft.graph.callRecords.segment](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-segment?view=graph-rest-1.0) collection | The list of segments involved in the session. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "callee": {"@odata.type": "microsoft.graph.callRecords.endpoint"},  
  "caller": {"@odata.type": "microsoft.graph.callRecords.endpoint"},
  "endDateTime": "String (timestamp)",
  "failureInfo": {"@odata.type": "microsoft.graph.callRecords.failureInfo"},
  "id": "String (identifier)",
  "isTest": "Boolean",
  "modalities": ["string"],
  "startDateTime": "String (timestamp)"
}
```
