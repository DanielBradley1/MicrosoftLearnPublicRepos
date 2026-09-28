<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/openshiftitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-08 -->

# openShiftItem resource type

Namespace: microsoft.graph

Represents a single count of an [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0).

Inherits from [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activities | [shiftActivity](https://learn.microsoft.com/en-us/graph/api/resources/shiftactivity?view=graph-rest-1.0) collection | An incremental part of a shift that can cover details of when and where an employee is during their shift. For example, an assignment, a scheduled break, or lunch. Required. Inherited from [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0). |
| displayName | String | The shift label of the **openShift**. Inherited from [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0). |
| endDateTime | DateTimeOffset | The end date and time for the **openShift**. Required. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0). |
| notes | String | The shift notes for the **openShift**. Inherited from [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0). |
| openSlotCount | Int32 | Count of the number of slots for the given open shift. |
| startDateTime | DateTimeOffset | The start date and time for the **openShift**. Required. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0). |
| theme | scheduleEntityTheme | The color of the open shift. The possible values are: `white`, `blue`, `green`, `purple`, `pink`, `yellow`, `gray`, `darkBlue`, `darkGreen`, `darkPurple`, `darkPink`, `darkYellow`, `unknownFutureValue`, `darkRed`, `cranberry`, `darkOrange`, `bronze`, `peach`, `gold`, `lime`, `forest`, `lightGreen`, `jade`, `lightTeal`, `darkTeal`, `steel`, `skyBlue`, `blueGray`, `lavender`, `lilac`, `plum`, `magenta`, `darkBrown`, `beige`, `charcoal`, `silver`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `darkRed`, `cranberry`, `darkOrange`, `bronze`, `peach`, `gold`, `lime`, `forest`, `lightGreen`, `jade`, `lightTeal`, `darkTeal`, `steel`, `skyBlue`, `blueGray`, `lavender`, `lilac`, `plum`, `magenta`, `darkBrown`, `beige`, `charcoal`, `silver`. Inherited from [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.openShiftItem",
  "activities": [{"@odata.type": "microsoft.graph.shiftActivity"}],
  "displayName": "String",
  "endDateTime": "String (timestamp)",
  "notes": "String",
  "openSlotCount": "Int32",
  "startDateTime": "String (timestamp)",
  "theme": "String"
}
```
