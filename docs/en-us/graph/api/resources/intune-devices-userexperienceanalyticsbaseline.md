<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbaseline?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsBaseline resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics baseline entity contains baseline values against which to compare the user experience analytics scores.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsBaselines](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbaseline-list?view=graph-rest-1.0) | [userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbaseline?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbaseline?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbaseline-get?view=graph-rest-1.0) | [userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbaseline?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbaseline?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbaseline-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbaseline?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbaseline?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbaseline-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbaseline?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbaseline-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbaseline?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsBaseline](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbaseline?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics baseline. |
| displayName | String | The name of the baseline. |
| overallScore | Int32 | The overall score of the user experience analytics baseline. |
| isBuiltIn | Boolean | When TRUE, indicates the current baseline is the commercial median baseline. When FALSE, indicates it is a custom baseline. FALSE by default. |
| createdDateTime | DateTimeOffset | The date the custom baseline was created. The value cannot be modified and is automatically populated when the baseline is created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Returned by default. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| deviceBootPerformanceMetrics | [userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory?view=graph-rest-1.0) | The scores and insights for the device boot performance metrics. |
| bestPracticesMetrics | [userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory?view=graph-rest-1.0) | The scores and insights for the best practices metrics. |
| rebootAnalyticsMetrics | [userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory?view=graph-rest-1.0) | The scores and insights for the reboot analytics metrics. |
| resourcePerformanceMetrics | [userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory?view=graph-rest-1.0) | The scores and insights for the resource performance metrics. |
| appHealthMetrics | [userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory?view=graph-rest-1.0) | The scores and insights for the application health metrics. |
| workFromAnywhereMetrics | [userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory?view=graph-rest-1.0) | The scores and insights for the work from anywhere metrics. |
| batteryHealthMetrics | [userExperienceAnalyticsCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticscategory?view=graph-rest-1.0) | The scores and insights for the battery health metrics. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsBaseline",
  "id": "String (identifier)",
  "displayName": "String",
  "overallScore": 1024,
  "isBuiltIn": true,
  "createdDateTime": "String (timestamp)"
}
```
