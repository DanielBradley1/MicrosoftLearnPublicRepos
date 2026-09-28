<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremetric?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsWorkFromAnywhereMetric resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics metric for work from anywhere report.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsWorkFromAnywhereMetrics](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsworkfromanywheremetric-list?view=graph-rest-1.0) | [userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremetric?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremetric?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsworkfromanywheremetric-get?view=graph-rest-1.0) | [userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremetric?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremetric?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsworkfromanywheremetric-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremetric?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremetric?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsworkfromanywheremetric-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremetric?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsworkfromanywheremetric-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremetric?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsWorkFromAnywhereMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremetric?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics work from anywhere metric. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| metricDevices | [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0) collection | The work from anywhere metric devices. Read-only. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsWorkFromAnywhereMetric",
  "id": "String (identifier)"
}
```
