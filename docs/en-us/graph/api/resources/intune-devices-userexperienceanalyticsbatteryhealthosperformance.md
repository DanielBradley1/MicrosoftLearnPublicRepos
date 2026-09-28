<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthosperformance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsBatteryHealthOsPerformance resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics battery health os performance entity contains battery related information for all operating system versions in their organization.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsBatteryHealthOsPerformances](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthosperformance-list?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthosperformance?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthosperformance?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthosperformance-get?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthosperformance?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthosperformance?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthosperformance-create.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthosperformance?view=graph-rest-beta) | Create a new [userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthosperformance?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthosperformance-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthosperformance?view=graph-rest-beta). |
| [Update userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthosperformance-update.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthosperformance?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsBatteryHealthOsPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthosperformance?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics battery health os performance object. |
| activeDevices | Int32 | Number of active devices for that os version. Valid values 0 to 2147483647 |
| osVersion | String | Version of the operating system. |
| osBuildNumber | String | Build number of the operating system. |
| averageMaxCapacityPercentage | Int32 | The mean of the maximum capacity for all devices running a particular operating system version. Maximum capacity measures the full charge vs. design capacity for a device’s batteries.. Valid values 0 to 2147483647 |
| averageEstimatedRuntimeInMinutes | Int32 | The mean of the estimated runtimes on full charge for all devices running a particular operating system version. Unit in minutes. Valid values 0 to 2147483647 |
| averageBatteryAgeInDays | Int32 | The mean of the battery age for all devices running a particular operating system version in a tenant. Unit in days. Valid values 0 to 2147483647 |
| meanFullBatteryDrainCount | Int32 | The mean of number of times the battery has been discharged an amount that equals 100% of its capacity for all devices running a particular operating system version in a tenant. Valid values 0 to 2147483647 |
| medianMaxCapacityPercentage | Int32 | The median of the maximum capacity for all devices running a particular operating system version. Maximum capacity measures the full charge vs. design capacity for a device’s batteries.. Valid values 0 to 2147483647 |
| medianEstimatedRuntimeInMinutes | Int32 | The median of the estimated runtimes on full charge for all devices running a particular operating system version. Unit in minutes. Valid values 0 to 2147483647 |
| medianFullBatteryDrainCount | Int32 | The median of number of times the battery has been discharged an amount that equals 100% of its capacity for all devices running a particular operating system version in a tenant. Valid values 0 to 2147483647 |
| osBatteryHealthScore | Int32 | A weighted average of battery health score across all devices running a particular operating system version. Values range from 0-100. Valid values 0 to 2147483647 |
| osHealthStatus | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-beta) | The overall battery health status of a given os version in a tenant. Possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsBatteryHealthOsPerformance",
  "id": "String (identifier)",
  "activeDevices": 1024,
  "osVersion": "String",
  "osBuildNumber": "String",
  "averageMaxCapacityPercentage": 1024,
  "averageEstimatedRuntimeInMinutes": 1024,
  "averageBatteryAgeInDays": 1024,
  "meanFullBatteryDrainCount": 1024,
  "medianMaxCapacityPercentage": 1024,
  "medianEstimatedRuntimeInMinutes": 1024,
  "medianFullBatteryDrainCount": 1024,
  "osBatteryHealthScore": 1024,
  "osHealthStatus": "String"
}
```
