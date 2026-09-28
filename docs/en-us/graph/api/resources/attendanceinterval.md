<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attendanceinterval?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# attendanceInterval resource type

Namespace: microsoft.graph

Contains information associated with an attendance interval in an [attendanceRecord](https://learn.microsoft.com/en-us/graph/api/resources/attendancerecord?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| durationInSeconds | Int32 | Duration of the meeting interval in seconds; that is, the difference between **joinDateTime** and **leaveDateTime**. |
| joinDateTime | DateTime | The time the attendee joined in UTC. |
| leaveDateTime | DateTime | The time the attendee left in UTC. |

Tip

When data is lacking, the value of **joinDateTime** or **leaveDateTime** will be set to `null`, and the value of **durationInSeconds** will be set to `0` in the response body of the [Get meetingAttendanceReport](https://learn.microsoft.com/en-us/graph/api/meetingattendancereport-get?view=graph-rest-v1.0&preserve-view=true) method.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "durationInSeconds": "Int32",
    "joinDateTime": "String (timestamp)",
    "leaveDateTime": "String (timestamp)"
}
```
