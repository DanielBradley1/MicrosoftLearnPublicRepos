<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptdailyschedule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceHealthScriptDailySchedule resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device health script daily schedule.

Inherits from [deviceHealthScriptTimeSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscripttimeschedule?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| interval | Int32 | The x value of every x hours for hourly schedule, every x days for Daily Schedule, every x weeks for weekly schedule, every x months for Monthly Schedule. Valid values 1 to 23 Inherited from [deviceHealthScriptRunSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptrunschedule?view=graph-rest-beta) |
| useUtc | Boolean | Indicate if the time is Utc or client local time. Inherited from [deviceHealthScriptTimeSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscripttimeschedule?view=graph-rest-beta) |
| time | TimeOfDay | At what time the script is scheduled to run. This collection can contain a maximum of 20 elements. Inherited from [deviceHealthScriptTimeSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscripttimeschedule?view=graph-rest-beta) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceHealthScriptDailySchedule",
  "interval": 1024,
  "useUtc": true,
  "time": "String (time of day)"
}
```
