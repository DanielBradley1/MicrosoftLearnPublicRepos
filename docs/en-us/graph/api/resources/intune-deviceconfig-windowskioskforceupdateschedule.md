<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskforceupdateschedule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsKioskForceUpdateSchedule resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows 10 force update schedule for Kiosk devices.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| startDateTime | DateTimeOffset | The start time for the force restart. |
| recurrence | [windows10AppsUpdateRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10appsupdaterecurrence?view=graph-rest-beta) | Recurrence schedule. Possible values are: `none`, `daily`, `weekly`, `monthly`. |
| dayofWeek | [dayOfWeek](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-dayofweek?view=graph-rest-beta) | Day of week. Possible values are: `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday`. |
| dayofMonth | Int32 | Day of month. Valid values 1 to 31 |
| runImmediatelyIfAfterStartDateTime | Boolean | If true, runs the task immediately if StartDateTime is in the past, else, runs at the next recurrence. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsKioskForceUpdateSchedule",
  "startDateTime": "String (timestamp)",
  "recurrence": "String",
  "dayofWeek": "String",
  "dayofMonth": 1024,
  "runImmediatelyIfAfterStartDateTime": true
}
```
