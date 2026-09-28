<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsBatteryHealthDevicePerformance resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics battery health device performance entity contains device level battery information.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsBatteryHealthDevicePerformances](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance-list?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance-get?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance-create.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance?view=graph-rest-beta) | Create a new [userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance?view=graph-rest-beta). |
| [Update userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance-update.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsBatteryHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceperformance?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics battery health device performance object. |
| deviceId | String | The unique identifier of the device, Intune DeviceID. |
| deviceName | String | Device friendly name. |
| model | String | The model name of the device. Deprecated in favor of DeviceModelName. |
| manufacturer | String | The manufacturer name of the device. Deprecated in favor of DeviceManufacturerName. |
| deviceModelName | String | The model name of the device. |
| deviceManufacturerName | String | The manufacturer name of the device. |
| maxCapacityPercentage | Int32 | Ratio of current capacity and design capacity of the battery with the lowest capacity. Unit in percentage and values range from 0-100. Valid values 0 to 2147483647 |
| estimatedRuntimeInMinutes | Int32 | The estimated runtime of the device when the battery is fully charged. Unit in minutes. Valid values 0 to 2147483647 |
| batteryAgeInDays | Int32 | Estimated battery age. Unit in days. Valid values 0 to 2147483647 |
| fullBatteryDrainCount | Int32 | Number of times the battery has been discharged an amount that equals 100% of its capacity, but not necessarily by discharging it from 100% to 0%. Valid values 0 to 2147483647 |
| deviceBatteryCount | Int32 | Number of batteries in a user device. Valid values 0 to 2147483647 |
| deviceBatteriesDetails | [userExperienceAnalyticsDeviceBatteryDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicebatterydetail?view=graph-rest-beta) collection | Properties \(maxCapacity and cycleCount\) related to all batteries of the device. |
| deviceBatteryTags | String collection | Tags for computed information on how battery on the device is behaving. E.g. newbattery, batterycapacityred, designcapacityzero, etc. |
| deviceBatteryHealthScore | Int32 | A weighted average of a device’s maximum capacity score and runtime estimate score. Values range from 0-100. Valid values 0 to 2147483647 |
| healthStatus | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-beta) | The overall battery health status of the device. Possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsBatteryHealthDevicePerformance",
  "id": "String (identifier)",
  "deviceId": "String",
  "deviceName": "String",
  "model": "String",
  "manufacturer": "String",
  "deviceModelName": "String",
  "deviceManufacturerName": "String",
  "maxCapacityPercentage": 1024,
  "estimatedRuntimeInMinutes": 1024,
  "batteryAgeInDays": 1024,
  "fullBatteryDrainCount": 1024,
  "deviceBatteryCount": 1024,
  "deviceBatteriesDetails": [
    {
      "@odata.type": "microsoft.graph.userExperienceAnalyticsDeviceBatteryDetail",
      "batteryId": "String",
      "maxCapacityPercentage": 1024,
      "fullBatteryDrainCount": 1024
    }
  ],
  "deviceBatteryTags": [
    "String"
  ],
  "deviceBatteryHealthScore": 1024,
  "healthStatus": "String"
}
```
