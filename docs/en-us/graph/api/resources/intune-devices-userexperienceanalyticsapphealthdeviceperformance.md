<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# userExperienceAnalyticsAppHealthDevicePerformance resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics device performance entity contains device performance details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsAppHealthDevicePerformances](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthdeviceperformance-list?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformance?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformance?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthdeviceperformance-get?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformance?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformance?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthdeviceperformance-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformance?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformance?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthdeviceperformance-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformance?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthdeviceperformance-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformance?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsAppHealthDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformance?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics device performance object. Supports: $select, $OrderBy. Read-only. |
| deviceModel | String | The model name of the device. Supports: $select, $OrderBy. Read-only. |
| deviceManufacturer | String | The manufacturer name of the device. Supports: $select, $OrderBy. Read-only. |
| appCrashCount | Int32 | The number of application crashes for the device. Valid values 0 to 2147483647. Supports: $filter, $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| crashedAppCount | Int32 | The number of distinct application crashes for the device. Valid values 0 to 2147483647. Supports: $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| appHangCount | Int32 | The number of application hangs for the device. Valid values 0 to 2147483647. Supports: $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| processedDateTime | DateTimeOffset | The date and time when the statistics were last computed. The value cannot be modified and is automatically populated when the statistics are computed. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2022 would look like this: '2022-01-01T00:00:00Z'. Returned by default. Read-only. |
| meanTimeToFailureInMinutes | Int32 | The mean time to failure for the application in minutes. Valid values 0 to 2147483647. Supports: $filter, $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| deviceAppHealthScore | Double | The application health score of the device. Valid values 0 to 100. Supports: $filter, $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| deviceAppHealthStatus | String | The overall app health status of the device. |
| healthStatus | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The health state of the user experience analytics device. The possible values are: unknown, insufficientData, needsAttention, meetingGoals. Unknown by default. Supports: $filter, $select, $OrderBy. Read-only. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |
| deviceId | String | The Intune device id of the device. Supports: $select, $OrderBy. Read-only. |
| deviceDisplayName | String | The name of the device. Supports: $select, $OrderBy. Read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsAppHealthDevicePerformance",
  "id": "String (identifier)",
  "deviceModel": "String",
  "deviceManufacturer": "String",
  "appCrashCount": 1024,
  "crashedAppCount": 1024,
  "appHangCount": 1024,
  "processedDateTime": "String (timestamp)",
  "meanTimeToFailureInMinutes": 1024,
  "deviceAppHealthScore": "4.2",
  "deviceAppHealthStatus": "String",
  "healthStatus": "String",
  "deviceId": "String",
  "deviceDisplayName": "String"
}
```
