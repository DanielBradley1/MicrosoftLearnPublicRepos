<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsMetric resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics metric contains the score and units of a metric of a user experience anlaytics category.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsMetrics](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsmetric-list?view=graph-rest-1.0) | [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsmetric-get?view=graph-rest-1.0) | [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsmetric-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsmetric-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsmetric-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics metric. |
| value | Double | The value of the user experience analytics metric. |
| unit | String | The unit of the user experience analytics metric. Examples: none, percentage, count, seconds, score. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsMetric",
  "id": "String (identifier)",
  "value": "4.2",
  "unit": "String"
}
```
