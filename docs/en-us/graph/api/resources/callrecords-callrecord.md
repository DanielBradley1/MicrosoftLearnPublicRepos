<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-29 -->

# callRecord resource type

Namespace: microsoft.graph.callRecords

Represents a single peer-to-peer call or a group call between multiple participants, sometimes referred to as an online meeting. A call record is created after a call or meeting ends.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/callrecords-cloudcommunications-list-callrecords?view=graph-rest-1.0) | [microsoft.graph.callRecords.callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0) collection | Get the list of [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-get?view=graph-rest-1.0) | [microsoft.graph.callRecords.callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0) | Read properties and relationships of callRecord object. |
| [List PSTN calls](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getpstncalls?view=graph-rest-1.0) | [microsoft.graph.callRecords.pstnCallLogRow collection](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstncalllogrow?view=graph-rest-1.0) | List **pstnCallLogRow** objects in a call record. |
| [List direct routing calls](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getdirectroutingcalls?view=graph-rest-1.0) | [microsoft.graph.callRecords.directRoutingLogRow collection](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-directroutinglogrow?view=graph-rest-1.0) | List **directRoutingLogRow** objects for a call record. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTimeOffset | UTC time when the last user left the call. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| id | String | Unique identifier for the call record. Read-only. |
| joinWebUrl | String | Meeting URL associated to the call. May not be available for a peerToPeer call record type. |
| lastModifiedDateTime | DateTimeOffset | UTC time when the call record was created. The DatetimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| modalities | modality collection | List of all the modalities used in the call. The possible values are: `unknown`, `audio`, `video`, `videoBasedScreenSharing`, `data`, `screenSharing`, `unknownFutureValue`. |
| startDateTime | DateTimeOffset | UTC time when the first user joined the call. The DatetimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| type | callType | Indicates the type of the call. The possible values are: `unknown`, `groupCall`, `peerToPeer`, `unknownFutureValue`. |
| version | Int64 | Monotonically increasing version of the call record. Higher version call records with the same id includes additional data compared to the lower version. |
| organizer \(deprecated\) | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The organizing party's identity. The **organizer** property is deprecated and will stop returning data on June 30, 2026. Going forward, use the **organizer\_v2** relationship. |
| participants \(deprecated\) | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) collection | List of distinct identities involved in the call. Limited to 130 entries. The **participants** property is deprecated and will stop returning data on June 30, 2026. Going forward, use the **participants\_v2** relationship. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| organizer\_v2 | [microsoft.graph.callRecords.organizer](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-organizer?view=graph-rest-1.0) | Identity of the organizer of the call. This relationship is expanded by default in **callRecord** methods. |
| participants\_v2 | [microsoft.graph.callRecords.participant](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participant?view=graph-rest-1.0) collection | List of distinct participants in the call. |
| sessions | [microsoft.graph.callRecords.session](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-session?view=graph-rest-1.0) collection | List of sessions involved in the call. Peer-to-peer calls typically only have one session, whereas group calls typically have at least one session per participant. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "endDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "joinWebUrl": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "modalities": ["string"],
  "organizer": {"@odata.type": "microsoft.graph.identitySet"},
  "participants": [{"@odata.type": "microsoft.graph.identitySet"}],
  "startDateTime": "String (timestamp)",
  "type": "String",
  "version": "Int64"
}
```
