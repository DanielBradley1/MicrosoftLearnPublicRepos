<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/shiftavailability?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# shiftAvailability resource type

Namespace: microsoft.graph

Availability of the user to be scheduled for a [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) and its recurrence pattern.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| recurrence | [patternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0) | Specifies the pattern for recurrence |
| timeSlots | [timeRange](https://learn.microsoft.com/en-us/graph/api/resources/timerange?view=graph-rest-1.0) collection | The time slot\(s\) preferred by the user. |
| timeZone | String | Specifies the time zone for the indicated time. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "recurrence": {"@odata.type": "microsoft.graph.patternedRecurrence"},
  "timeSlots": [{"@odata.type": "microsoft.graph.timeRange"}],
  "timeZone": "String"
}
```
