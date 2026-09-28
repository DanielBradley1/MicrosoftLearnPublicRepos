<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# userExperienceAnalyticsCategory resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics category entity contains the scores and insights for the various metrics of a category.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticscategory-get?view=graph-rest-1.0) | [userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory?view=graph-rest-1.0) object. |
| [Update userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticscategory-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics category. Read-only. |
| overallScore | Int32 | The overall score of the user experience analytics category. |
| totalDevices | Int32 | The total device count of the user experience analytics category. |
| insights | [userExperienceAnalyticsInsight](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsinsight?view=graph-rest-1.0) collection | The insights for the category. Read-only. |
| state | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The current health state of the user experience analytics category. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| metricValues | [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-1.0) collection | The metric values for the user experience analytics category. Read-only. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsCategory",
  "id": "String (identifier)",
  "overallScore": 1024,
  "totalDevices": 1024,
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
  "state": "String"
}
```
