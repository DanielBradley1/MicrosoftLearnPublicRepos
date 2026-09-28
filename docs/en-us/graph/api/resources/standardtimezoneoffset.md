<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/standardtimezoneoffset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# standardTimeZoneOffset resource type

Namespace: microsoft.graph

Specifies when a time zone switches from daylight saving time to standard time.

For example, if a time zone is specified with the following properties:

- **dayOccurrence** is 3
- **dayOfWeek** is "Sunday"
- **month** is 10
- **time** is 02:00:00 \_ **year** is 0 That means the transition from daylight saving time to standard occurs at 2 AM on the third Sunday of October, every year.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dayOccurrence | Edm.Int32 | Represents the nth occurrence of the day of week that the transition from daylight saving time to standard time occurs. |
| dayOfWeek | dayOfWeek | Represents the day of the week when the transition from daylight saving time to standard time. |
| month | Edm.Int32 | Represents the month of the year when the transition from daylight saving time to standard time occurs. |
| time | Edm.TimeOfDay | Represents the time of day when the transition from daylight saving time to standard time occurs. |
| year | Edm.Int32 | Represents how frequently in terms of years the change from daylight saving time to standard time occurs. For example, a value of 0 means every year. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "dayOccurrence": "Int32",
  "dayOfWeek": "string",
  "month": "Int32",
  "time": "TimeOfDay",
  "year": "Int32"
}
```
