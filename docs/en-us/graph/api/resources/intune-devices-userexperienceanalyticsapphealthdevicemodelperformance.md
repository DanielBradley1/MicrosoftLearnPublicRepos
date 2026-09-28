<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsAppHealthDeviceModelPerformance resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics device model performance entity contains device model performance details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsAppHealthDeviceModelPerformances](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance-list?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance-get?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsAppHealthDeviceModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdevicemodelperformance?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics device model performance object. Supports: $select, $OrderBy. Read-only. |
| deviceModel | String | The model name of the device. Supports: $select, $OrderBy. Read-only. |
| deviceManufacturer | String | The manufacturer name of the device. Supports: $select, $OrderBy. Read-only. |
| activeDeviceCount | Int32 | The number of active devices for the model. Valid values 0 to 2147483647. Supports: $filter, $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| meanTimeToFailureInMinutes | Int32 | The mean time to failure for the application in minutes. Valid values 0 to 2147483647. Supports: $filter, $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| modelAppHealthScore | Double | The application health score of the device model. Valid values 0 to 100. Supports: $filter, $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| modelAppHealthStatus | String | The overall app health status of the device model. |
| healthStatus | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The health state of the user experience analytics model. The possible values are: unknown, insufficientData, needsAttention, meetingGoals. Unknown by default. Supports: $filter, $select, $OrderBy. Read-only. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsAppHealthDeviceModelPerformance",
  "id": "String (identifier)",
  "deviceModel": "String",
  "deviceManufacturer": "String",
  "activeDeviceCount": 1024,
  "meanTimeToFailureInMinutes": 1024,
  "modelAppHealthScore": "4.2",
  "modelAppHealthStatus": "String",
  "healthStatus": "String"
}
```
