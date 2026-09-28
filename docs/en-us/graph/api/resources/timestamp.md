<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timestamp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# timeStamp resource type

Namespace: microsoft.graph

Date and time information for a point in time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| date | Date | The date portion of the timestamp. |
| time | TimeOfDay | The time portion of the timestamp. |
| timeZone | String | The timezone portion of the timestamp, which is one of the 24 longitudinal areas in the world. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "date": "String (timestamp)",
  "time": "String (timestamp)",
  "timeZone": "string"
}
```
