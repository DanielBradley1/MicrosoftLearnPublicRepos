<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timecardentry?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# timeCardEntry resource type

Namespace: microsoft.graph

Represents a specific [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) entry.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| breaks | [timeCardBreak](https://learn.microsoft.com/en-us/graph/api/resources/timecardbreak?view=graph-rest-1.0) collection | The clock-in event of the **timeCard**. |
| clockInEvent | [timeCardEvent](https://learn.microsoft.com/en-us/graph/api/resources/timecardevent?view=graph-rest-1.0) | The clock-out event of the **timeCard**. |
| clockOutEvent | [timeCardEvent](https://learn.microsoft.com/en-us/graph/api/resources/timecardevent?view=graph-rest-1.0) | The list of breaks associated with the **timeCard**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.timeCardEntry",
  "clockInEvent": {
    "@odata.type": "microsoft.graph.timeCardEvent"
  },
  "clockOutEvent": {
    "@odata.type": "microsoft.graph.timeCardEvent"
  },
  "breaks": [
    {
      "@odata.type": "microsoft.graph.timeCardBreak"
    }
  ]
}
```
