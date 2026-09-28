<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timeclocksettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# timeClockSettings resource type

Namespace: microsoft.graph

Represents timeclock settings for a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvedLocation | [geoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/geocoordinates?view=graph-rest-1.0) | The approved location of the **timeClock**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.timeClockSettings",
  "approvedLocation": {
    "@odata.type": "microsoft.graph.geoCoordinates"
  }
}
```
