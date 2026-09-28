<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmodelscores?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsModelScores resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics model scores entity consolidates the various Endpoint Analytics scores.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsModelScoreses](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsmodelscores-list?view=graph-rest-1.0) | [userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmodelscores?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmodelscores?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsmodelscores-get?view=graph-rest-1.0) | [userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmodelscores?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmodelscores?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsmodelscores-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmodelscores?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmodelscores?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsmodelscores-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmodelscores?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsmodelscores-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmodelscores?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsModelScores](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmodelscores?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics model score entry. Supports: $select, $OrderBy. Read-only. |
| model | String | The model name of the device. Supports: $select, $OrderBy. Read-only. |
| manufacturer | String | The manufacturer name of the device. Examples: Microsoft Corporation, HP, Lenovo. Supports: $select, $OrderBy. Read-only. |
| modelDeviceCount | Int64 | Indicates unique devices count of given model in a consolidated report. Supports: $select, $OrderBy. Read-only. Valid values -9.22337203685478E+18 to 9.22337203685478E+18 |
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
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsModelScores",
  "id": "String (identifier)",
  "model": "String",
  "manufacturer": "String",
  "modelDeviceCount": 1024,
  "endpointAnalyticsScore": "4.2",
  "startupPerformanceScore": "4.2",
  "appReliabilityScore": "4.2",
  "workFromAnywhereScore": "4.2",
  "batteryHealthScore": "4.2",
  "healthStatus": "String"
}
```
