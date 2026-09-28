<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-segment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# segment resource type

Namespace: microsoft.graph.callRecords

Represents a portion of a User-User communication or a User-Meeting communication in the case of a Conference call. A typical VOIP call has one segment per session. In certain scenarios, such as PSTN calls, there are multiple segments per session due to additional server-to-server communication required to connect the call.

## Methods

No methods exist to directly access segments. Use the [Get callRecord](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-get?view=graph-rest-1.0) API with `$expand=sessions($expand=segments)` or the [List session](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-list-sessions?view=graph-rest-1.0) API with `$expand=segments` to get the segments for a [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callee | [microsoft.graph.callRecords.endpoint](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-endpoint?view=graph-rest-1.0) | Endpoint that answered this segment. |
| caller | [microsoft.graph.callRecords.endpoint](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-endpoint?view=graph-rest-1.0) | Endpoint that initiated this segment. |
| endDateTime | DateTimeOffset | UTC time when the segment ended. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| failureInfo | [microsoft.graph.callRecords.failureInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-failureinfo?view=graph-rest-1.0) | Failure information associated with the segment if it failed. |
| id | String | Unique identifier for the segment. Read-only. |
| media | [microsoft.graph.callRecords.media](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-media?view=graph-rest-1.0) collection | Media associated with this segment. |
| startDateTime | DateTimeOffset | UTC time when the segment started. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "callee": {"@odata.type": "microsoft.graph.callRecords.endpoint"},
  "caller": {"@odata.type": "microsoft.graph.callRecords.endpoint"},
  "endDateTime": "String (timestamp)",
  "failureInfo": {"@odata.type": "microsoft.graph.callRecords.failureInfo"},
  "id": "String (identifier)",
  "media": [{"@odata.type": "microsoft.graph.callRecords.media"}],
  "startDateTime": "String (timestamp)"
}
```
