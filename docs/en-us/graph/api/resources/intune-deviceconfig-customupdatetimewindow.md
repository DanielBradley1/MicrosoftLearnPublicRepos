<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-customupdatetimewindow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# customUpdateTimeWindow resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Custom update time window

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| startDay | [dayOfWeek](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-dayofweek?view=graph-rest-beta) | Start day of the time window. Possible values are: `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday`. |
| endDay | [dayOfWeek](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-dayofweek?view=graph-rest-beta) | End day of the time window. Possible values are: `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday`. |
| startTime | TimeOfDay | Start time of the time window |
| endTime | TimeOfDay | End time of the time window |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.customUpdateTimeWindow",
  "startDay": "String",
  "endDay": "String",
  "startTime": "String (time of day)",
  "endTime": "String (time of day)"
}
```
