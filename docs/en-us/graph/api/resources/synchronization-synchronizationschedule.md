<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschedule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# synchronizationSchedule resource type

Namespace: microsoft.graph

Defines the schedule \(**schedule** property\) used to run a [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expiration | DateTimeOffset | Date and time when this job expires. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| interval | Duration | The interval between synchronization iterations. The value is represented in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format for durations. For example, `P1M` represents a period of one month and `PT1M` represents a period of one minute. |
| state | synchronizationScheduleState | The possible values are: `Active`, `Disabled`, `Paused`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "expiration": "String (timestamp)",
  "interval": "String (duration)",
  "state": "String"
}
```
