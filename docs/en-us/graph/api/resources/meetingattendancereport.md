<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# meetingAttendanceReport resource type

Namespace: microsoft.graph

Contains information associated with a meeting attendance report for an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) or a [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0).

Meeting attendance reports are online meeting artifacts. For details, see [Online meeting artifacts and permissions](https://learn.microsoft.com/en-us/graph/cloud-communications-online-meeting-artifacts).

The policies that apply to the [Teams attendance report](https://support.microsoft.com/office/manage-meeting-attendance-reports-in-microsoft-teams-ae7cf170-530c-47d3-84c1-3aedac74d310) also extend to Microsoft Graph, which means the same rules and retention periods, including a one-year retention policy from the meeting date, apply to the **meetingAttendanceReport** scenarios.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/meetingattendancereport-list?view=graph-rest-1.0) | [meetingAttendanceReport](https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport?view=graph-rest-1.0) collection | Get a list of [meetingAttendanceReport](https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/meetingattendancereport-get?view=graph-rest-1.0) | [meetingAttendanceReport](https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport?view=graph-rest-1.0) | Read the properties and relationships of a [meetingAttendanceReport](https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| externalEventInformation | [virtualEventExternalInformation](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventexternalinformation?view=graph-rest-1.0) collection | The external information of a virtual event. Returned only for event organizers or coorganizers. Read-only. |
| id | String | Unique identifier for the attendance report. Read-only. |
| meetingEndDateTime | DateTimeOffset | UTC time when the meeting ended. Read-only. |
| meetingStartDateTime | DateTimeOffset | UTC time when the meeting started. Read-only. |
| totalParticipantCount | Int32 | Total number of participants. Read-only. |

## Relationships

| Relationship | Type | Description |
| --- | --- | --- |
| attendanceRecords | [attendanceRecord](https://learn.microsoft.com/en-us/graph/api/resources/attendancerecord?view=graph-rest-1.0) collection | List of attendance records of an attendance report. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.meetingAttendanceReport",
  "externalEventInformation": [{"@odata.type": "microsoft.graph.virtualEventExternalInformation"}],
  "id": "String(identifier)",
  "meetingEndDateTime": "String (timestamp)",
  "meetingStartDateTime": "String (timestamp)",
  "totalParticipantCount": "Int32"
}
```
