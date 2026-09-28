<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicescores?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsDeviceScores resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics device scores entity consolidates the various Endpoint Analytics scores.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsDeviceScoreses](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdevicescores-list?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicescores?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicescores?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdevicescores-get?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicescores?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicescores?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicescores-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicescores?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicescores?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicescores-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicescores?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicescores-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicescores?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsDeviceScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicescores?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics device score entry. Supports: $select, $OrderBy. Read-only. |
| deviceName | String | The name of the device. Supports: $select, $OrderBy. Read-only. |
| model | String | The model name of the device. Supports: $select, $OrderBy. Read-only. |
| manufacturer | String | The manufacturer name of the device. Examples: Microsoft Corporation, HP, Lenovo. Supports: $select, $OrderBy. Read-only. |
| endpointAnalyticsScore | Double | Indicates a weighted average of the various scores. Valid values range from 0-100. Value -1 means associated score is unavailable. A higher score indicates a healthier device. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| startupPerformanceScore | Double | Indicates a weighted average of boot score and logon score used for measuring startup performance. Valid values range from 0-100. Value -1 means associated score is unavailable. A higher score indicates a healthier device. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| appReliabilityScore | Double | Indicates a score calculated from application health data to indicate when a device is having problems running one or more applications. Valid values range from 0-100. Value -1 means associated score is unavailable. A higher score indicates a healthier device. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| workFromAnywhereScore | Double | Indicates a weighted score of the work from anywhere on a device level. Valid values range from 0-100. Value -1 means associated score is unavailable. A higher score indicates a healthier device. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| batteryHealthScore | Double | Indicates a calulated score indicating the health of the device's battery. Valid values range from 0-100. Value -1 means associated score is unavailable. A higher score indicates a healthier device. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| healthStatus | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The health status of the device. The possible values are: unknown, insufficientData, needsAttention, meetingGoals. Unknown by default. Supports: $filter, $select, $OrderBy. Read-only. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsDeviceScores",
  "id": "String (identifier)",
  "deviceName": "String",
  "model": "String",
  "manufacturer": "String",
  "endpointAnalyticsScore": "4.2",
  "startupPerformanceScore": "4.2",
  "appReliabilityScore": "4.2",
  "workFromAnywhereScore": "4.2",
  "batteryHealthScore": "4.2",
  "healthStatus": "String"
}
```
