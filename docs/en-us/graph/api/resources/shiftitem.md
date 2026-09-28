<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-08 -->

# shiftItem resource type

Namespace: microsoft.graph

Represents a version of a [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| --- | --- | --- |
| activities | [shiftActivity](https://learn.microsoft.com/en-us/graph/api/resources/shiftactivity?view=graph-rest-1.0) collection | An incremental part of a shift which can cover details of when and where an employee is during their shift. For example, an assignment or a scheduled break or lunch. Required. |
| displayName | string | The shift label of the `shiftItem`. |
| endDateTime | DateTimeOffset | The end date and time for the `shiftItem`. Required. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| notes | string | The shift notes for the `shiftItem`. |
| startDateTime | DateTimeOffset | The start date and time for the `shiftItem`. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Required. |
| theme | scheduleEntityTheme | The color of the shift. The possible values are: `white`, `blue`, `green`, `purple`, `pink`, `yellow`, `gray`, `darkBlue`, `darkGreen`, `darkPurple`, `darkPink`, `darkYellow`, `unknownFutureValue`, `darkRed`, `cranberry`, `darkOrange`, `bronze`, `peach`, `gold`, `lime`, `forest`, `lightGreen`, `jade`, `lightTeal`, `darkTeal`, `steel`, `skyBlue`, `blueGray`, `lavender`, `lilac`, `plum`, `magenta`, `darkBrown`, `beige`, `charcoal`, `silver`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `darkRed`, `cranberry`, `darkOrange`, `bronze`, `peach`, `gold`, `lime`, `forest`, `lightGreen`, `jade`, `lightTeal`, `darkTeal`, `steel`, `skyBlue`, `blueGray`, `lavender`, `lilac`, `plum`, `magenta`, `darkBrown`, `beige`, `charcoal`, `silver`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "notes": "String",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "theme": "String",
  "activities": [{"@odata.type": "microsoft.graph.shiftActivity"}]
}
```
