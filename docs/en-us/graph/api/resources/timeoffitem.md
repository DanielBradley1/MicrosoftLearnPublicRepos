<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timeoffitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-08 -->

# timeOffItem resource type

Namespace: microsoft.graph

Represents a version of the [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| --- | --- | --- |
| endDateTime | DateTimeOffset | The end date and time for the `timeOffItem`. Required. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| startDateTime | DateTimeOffset | The start date and time for the `timeOffItem`. Required. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| theme | scheduleEntityTheme | The color of the time off. The possible values are: `white`, `blue`, `green`, `purple`, `pink`, `yellow`, `gray`, `darkBlue`, `darkGreen`, `darkPurple`, `darkPink`, `darkYellow`, `unknownFutureValue`, `darkRed`, `cranberry`, `darkOrange`, `bronze`, `peach`, `gold`, `lime`, `forest`, `lightGreen`, `jade`, `lightTeal`, `darkTeal`, `steel`, `skyBlue`, `blueGray`, `lavender`, `lilac`, `plum`, `magenta`, `darkBrown`, `beige`, `charcoal`, `silver`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `darkRed`, `cranberry`, `darkOrange`, `bronze`, `peach`, `gold`, `lime`, `forest`, `lightGreen`, `jade`, `lightTeal`, `darkTeal`, `steel`, `skyBlue`, `blueGray`, `lavender`, `lilac`, `plum`, `magenta`, `darkBrown`, `beige`, `charcoal`, `silver`. |
| timeOffReasonId | string | ID of the `timeOffReason` for this `timeOffItem`. Required. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "timeOffReasonId": "String",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "theme": "pink"
}
```
