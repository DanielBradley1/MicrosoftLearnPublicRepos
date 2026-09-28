<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsregressionsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsRegressionSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics Regression Summary.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get userExperienceAnalyticsRegressionSummary](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsregressionsummary-get?view=graph-rest-beta) | [userExperienceAnalyticsRegressionSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsregressionsummary?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsRegressionSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsregressionsummary?view=graph-rest-beta) object. |
| [Update userExperienceAnalyticsRegressionSummary](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsregressionsummary-update.md?view=graph-rest-beta) | [userExperienceAnalyticsRegressionSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsregressionsummary?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsRegressionSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsregressionsummary?view=graph-rest-beta) object. |
| [summarizeDeviceRegressionPerformance function](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsregressionsummary-summarizedeviceregressionperformance?view=graph-rest-beta) | [userExperienceAnalyticsRegressionSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsregressionsummary?view=graph-rest-beta) | Not yet documented |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics regression summary. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| modelRegression | [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-beta) collection | The metric values for the user experience analytics model regression. |
| manufacturerRegression | [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-beta) collection | The metric values for the user experience analytics Manufacturer regression. |
| operatingSystemRegression | [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-beta) collection | The metric values for the user experience analytics operating system regression. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsRegressionSummary",
  "id": "String (identifier)"
}
```
