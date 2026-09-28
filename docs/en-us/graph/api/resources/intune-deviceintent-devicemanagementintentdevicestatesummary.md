<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestatesummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementIntentDeviceStateSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that represents device state summary for an intent

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceManagementIntentDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicestatesummary-get?view=graph-rest-beta) | [deviceManagementIntentDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestatesummary?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementIntentDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestatesummary?view=graph-rest-beta) object. |
| [Update deviceManagementIntentDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicestatesummary-update?view=graph-rest-beta) | [deviceManagementIntentDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestatesummary?view=graph-rest-beta) | Update the properties of a [deviceManagementIntentDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestatesummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID |
| conflictCount | Int32 | Number of devices in conflict |
| errorCount | Int32 | Number of error devices |
| failedCount | Int32 | Number of failed devices |
| notApplicableCount | Int32 | Number of not applicable devices |
| notApplicablePlatformCount | Int32 | Number of not applicable devices due to mismatch platform and policy |
| successCount | Int32 | Number of succeeded devices |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementIntentDeviceStateSummary",
  "id": "String (identifier)",
  "conflictCount": 1024,
  "errorCount": 1024,
  "failedCount": 1024,
  "notApplicableCount": 1024,
  "notApplicablePlatformCount": 1024,
  "successCount": 1024
}
```
