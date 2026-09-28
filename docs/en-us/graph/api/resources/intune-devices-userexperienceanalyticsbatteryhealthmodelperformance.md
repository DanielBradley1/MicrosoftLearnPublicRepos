<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsBatteryHealthModelPerformance resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics battery health model performance entity contains battery related information for all unique device models in their organization.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsBatteryHealthModelPerformances](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance-list?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance-get?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance-create.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance?view=graph-rest-beta) | Create a new [userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance?view=graph-rest-beta). |
| [Update userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance-update.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsBatteryHealthModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthmodelperformance?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics battery health model performance object. |
| activeDevices | Int32 | Number of active devices for that model. Valid values 0 to 2147483647 |
| model | String | The model name of the device. Deprecated in favor of DeviceModelName. |
| manufacturer | String | Name of the device manufacturer. Deprecated in favor of DeviceManufacturerName. |
| deviceModelName | String | The model name of the device. |
| deviceManufacturerName | String | The manufacturer name of the device. |
| averageMaxCapacityPercentage | Int32 | The mean of the maximum capacity for all devices of a given model. Maximum capacity measures the full charge vs. design capacity for a device’s batteries.. Valid values 0 to 2147483647 |
| averageEstimatedRuntimeInMinutes | Int32 | The mean of the estimated runtimes on full charge for all devices of a given model. Unit in minutes. Valid values 0 to 2147483647 |
| averageBatteryAgeInDays | Int32 | The mean of the battery age for all devices of a given model in a tenant. Unit in days. Valid values 0 to 2147483647 |
| meanFullBatteryDrainCount | Int32 | The mean of number of times the battery has been discharged an amount that equals 100% of its capacity for all devices of a given model in a tenant. Valid values 0 to 2147483647 |
| medianMaxCapacityPercentage | Int32 | The median of the maximum capacity for all devices of a given model. Maximum capacity measures the full charge vs. design capacity for a device’s batteries.. Valid values 0 to 2147483647 |
| medianEstimatedRuntimeInMinutes | Int32 | The median of the estimated runtimes on full charge for all devices of a given model. Unit in minutes. Valid values 0 to 2147483647 |
| medianFullBatteryDrainCount | Int32 | The median of number of times the battery has been discharged an amount that equals 100% of its capacity for all devices of a given model in a tenant. Valid values 0 to 2147483647 |
| modelBatteryHealthScore | Int32 | A weighted average of a model’s maximum capacity score and runtime estimate score. Values range from 0-100. Valid values 0 to 2147483647 |
| modelHealthStatus | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-beta) | The overall battery health status of a given model in a tenant. Possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsBatteryHealthModelPerformance",
  "id": "String (identifier)",
  "activeDevices": 1024,
  "model": "String",
  "manufacturer": "String",
  "deviceModelName": "String",
  "deviceManufacturerName": "String",
  "averageMaxCapacityPercentage": 1024,
  "averageEstimatedRuntimeInMinutes": 1024,
  "averageBatteryAgeInDays": 1024,
  "meanFullBatteryDrainCount": 1024,
  "medianMaxCapacityPercentage": 1024,
  "medianEstimatedRuntimeInMinutes": 1024,
  "medianFullBatteryDrainCount": 1024,
  "modelBatteryHealthScore": 1024,
  "modelHealthStatus": "String"
}
```
