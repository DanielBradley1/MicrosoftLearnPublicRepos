<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetrichistory?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsMetricHistory resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics metric history.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsMetricHistories](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsmetrichistory-list?view=graph-rest-1.0) | [userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetrichistory?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetrichistory?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsmetrichistory-get?view=graph-rest-1.0) | [userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetrichistory?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetrichistory?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsmetrichistory-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetrichistory?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetrichistory?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsmetrichistory-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetrichistory?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsmetrichistory-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetrichistory?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsMetricHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetrichistory?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics metric history. |
| deviceId | String | The Intune device id of the device. |
| metricDateTime | DateTimeOffset | The metric date time. The value cannot be modified and is automatically populated when the metric is created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Returned by default. |
| metricType | String | The user experience analytics metric type. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| userExperienceAnalyticsMetric | [userExperienceAnalyticsMetric](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmetric?view=graph-rest-1.0) | User experience analytics metric. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsMetricHistory",
  "id": "String (identifier)",
  "deviceId": "String",
  "metricDateTime": "String (timestamp)",
  "metricType": "String"
}
```
