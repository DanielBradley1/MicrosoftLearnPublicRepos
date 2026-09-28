<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timeperiod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-07 -->

# timePeriod resource type

Namespace: microsoft.graph

Contains the start and end date time for a time period.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTimeOffset | The date time of the end of the time period. |
| startDateTime | DateTimeOffset | The date time of the start of the time period. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.timePeriod",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)"
}
```
