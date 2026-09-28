<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsinsight?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsInsight resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics insight is the recomendation to improve the user experience analytics score.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userExperienceAnalyticsMetricId | String | The unique identifier of the user experience analytics metric. |
| insightId | String | The unique identifier of the user experience analytics insight. |
| values | [userExperienceAnalyticsInsightValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsinsightvalue?view=graph-rest-1.0) collection | The value of the user experience analytics insight. |
| severity | [userExperienceAnalyticsInsightSeverity](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsinsightseverity?view=graph-rest-1.0) | The severity of the user experience analytics insight. The possible values are: none, informational, warning, error. None by default. The possible values are: `none`, `informational`, `warning`, `error`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsInsight",
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
```
