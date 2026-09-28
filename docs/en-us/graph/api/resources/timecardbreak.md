<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timecardbreak?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# timeCardBreak resource type

Namespace: microsoft.graph

Represents a specific [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) break.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| breakId | String | ID of the **timeCardBreak**. |
| end | [timeCardEvent](https://learn.microsoft.com/en-us/graph/api/resources/timecardevent?view=graph-rest-1.0) | The start event of the **timeCardBreak**. |
| notes | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Notes about the **timeCardBreak**. |
| start | [timeCardEvent](https://learn.microsoft.com/en-us/graph/api/resources/timecardevent?view=graph-rest-1.0) | The start event of the **timeCardBreak**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.timeCardBreak",
  "breakId": "String",
  "start": {
    "@odata.type": "microsoft.graph.timeCardEvent"
  },
  "end": {
    "@odata.type": "microsoft.graph.timeCardEvent"
  },
  "notes": {
    "@odata.type": "microsoft.graph.itemBody"
  }
}
```
