<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsoverview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# userExperienceAnalyticsOverview resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics overview entity contains the overall score and the scores and insights of every metric of all categories.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get userExperienceAnalyticsOverview](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsoverview-get?view=graph-rest-1.0) | [userExperienceAnalyticsOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsoverview?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsoverview?view=graph-rest-1.0) object. |
| [Update userExperienceAnalyticsOverview](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsoverview-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsoverview?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsoverview?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics overview. Supports: $select, $OrderBy. Read-only. |
| overallScore | Int32 | The user experience analytics overall score. |
| deviceBootPerformanceOverallScore | Int32 | The user experience analytics device boot performance overall score. |
| bestPracticesOverallScore | Int32 | The user experience analytics best practices overall score. |
| workFromAnywhereOverallScore | Int32 | The user experience analytics Work From Anywhere overall score. |
| appHealthOverallScore | Int32 | The user experience analytics app health overall score. |
| resourcePerformanceOverallScore | Int32 | The user experience analytics resource performance overall score. |
| batteryHealthOverallScore | Int32 | The user experience analytics battery health overall score. |
| insights | [userExperienceAnalyticsInsight](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsinsight?view=graph-rest-1.0) collection | The user experience analytics insights. Read-only. |
| state | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The current health state of the user experience analytics overview. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |
| deviceBootPerformanceHealthState | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The current health state of the user experience analytics 'BootPerformance' category. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |
| bestPracticesHealthState | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The current health state of the user experience analytics 'BestPractices' category. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |
| workFromAnywhereHealthState | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The current health state of the user experience analytics 'WorkFromAnywhere' category. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |
| appHealthState | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The current health state of the user experience analytics 'BestPractices' category. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |
| resourcePerformanceHealthState | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The current health state of the user experience analytics 'ResourcePerformance' category. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |
| batteryHealthState | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The current health state of the user experience analytics 'BatteryHealth' category. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsOverview",
  "id": "String (identifier)",
  "overallScore": 1024,
  "deviceBootPerformanceOverallScore": 1024,
  "bestPracticesOverallScore": 1024,
  "workFromAnywhereOverallScore": 1024,
  "appHealthOverallScore": 1024,
  "resourcePerformanceOverallScore": 1024,
  "batteryHealthOverallScore": 1024,
  "insights": [
    {
      "@odata.type": "microsoft.graph.userExperienceAnalyticsInsight",
      "userExperienceAnalyticsMetricId": "String",
      "insightId": "String",
      "values": [
        {
          "@odata.type": "microsoft.graph.insightValueDouble",
          "value": "4.2"
        }
      ],
      "severity": "String"
    }
  ],
  "state": "String",
  "deviceBootPerformanceHealthState": "String",
  "bestPracticesHealthState": "String",
  "workFromAnywhereHealthState": "String",
  "appHealthState": "String",
  "resourcePerformanceHealthState": "String",
  "batteryHealthState": "String"
}
```
