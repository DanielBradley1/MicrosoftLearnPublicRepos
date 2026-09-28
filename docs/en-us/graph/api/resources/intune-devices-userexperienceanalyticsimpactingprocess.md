<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsimpactingprocess?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsImpactingProcess resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics top impacting process entity.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsImpactingProcesses](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsimpactingprocess-list?view=graph-rest-beta) | [userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsimpactingprocess?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsimpactingprocess?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsimpactingprocess-get?view=graph-rest-beta) | [userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsimpactingprocess?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsimpactingprocess?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsimpactingprocess-create.md?view=graph-rest-beta) | [userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsimpactingprocess?view=graph-rest-beta) | Create a new [userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsimpactingprocess?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsimpactingprocess-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsimpactingprocess?view=graph-rest-beta). |
| [Update userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsimpactingprocess-update.md?view=graph-rest-beta) | [userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsimpactingprocess?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsImpactingProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsimpactingprocess?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics top impacting process entity. |
| deviceId | String | The unique identifier of the impacted device. |
| category | String | The category of impacting process. |
| processName | String | The process name. |
| description | String | The description of process. |
| publisher | String | The publisher of the process. |
| impactValue | Double | The impact value of the process. Valid values 0 to 1.79769313486232E+308 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsImpactingProcess",
  "id": "String (identifier)",
  "deviceId": "String",
  "category": "String",
  "processName": "String",
  "description": "String",
  "publisher": "String",
  "impactValue": "4.2"
}
```
