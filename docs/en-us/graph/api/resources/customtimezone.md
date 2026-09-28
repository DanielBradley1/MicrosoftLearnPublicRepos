<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customtimezone?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# customTimeZone resource type

Namespace: microsoft.graph

Represents a time zone where the transition from standard to daylight saving time, or vice versa is not standard.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bias | Edm.Int32 | The time offset of the time zone from Coordinated Universal Time \(UTC\). This value is in minutes. Time zones that are ahead of UTC have a positive offset; time zones that are behind UTC have a negative offset. |
| daylightOffset | [daylightTimeZoneOffset](https://learn.microsoft.com/en-us/graph/api/resources/daylighttimezoneoffset?view=graph-rest-1.0) | Specifies when the time zone switches from standard time to daylight saving time. |
| name | string | The name of the custom time zone. |
| standardOffset | [standardTimeZoneOffset](https://learn.microsoft.com/en-us/graph/api/resources/standardtimezoneoffset?view=graph-rest-1.0) | Specifies when the time zone switches from daylight saving time to standard time. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "bias": "Int32",
  "daylightOffset": {"@odata.type": "microsoft.graph.daylightTimeZoneOffset"},
  "name": "string",
  "standardOffset": {"@odata.type": "microsoft.graph.standardTimeZoneOffset"}
}
```
