<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsnotautopilotreadydevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsNotAutopilotReadyDevice resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics Device not windows autopilot ready.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsNotAutopilotReadyDevices](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsnotautopilotreadydevice-list?view=graph-rest-beta) | [userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsnotautopilotreadydevice?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsnotautopilotreadydevice?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsnotautopilotreadydevice-get?view=graph-rest-beta) | [userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsnotautopilotreadydevice?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsnotautopilotreadydevice?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsnotautopilotreadydevice-create.md?view=graph-rest-beta) | [userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsnotautopilotreadydevice?view=graph-rest-beta) | Create a new [userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsnotautopilotreadydevice?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsnotautopilotreadydevice-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsnotautopilotreadydevice?view=graph-rest-beta). |
| [Update userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsnotautopilotreadydevice-update.md?view=graph-rest-beta) | [userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsnotautopilotreadydevice?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsNotAutopilotReadyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsnotautopilotreadydevice?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics intune device. |
| deviceName | String | The intune device's name. |
| serialNumber | String | The intune device's serial number. |
| manufacturer | String | The intune device's manufacturer. |
| model | String | The intune device's model. |
| managedBy | String | The intune device's managed by. |
| autoPilotRegistered | Boolean | The intune device's autopilotRegistered. |
| autoPilotProfileAssigned | Boolean | The intune device's autopilotProfileAssigned. |
| azureAdRegistered | Boolean | The intune device's azureAdRegistered. |
| azureAdJoinType | String | The intune device's azure Ad joinType. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsNotAutopilotReadyDevice",
  "id": "String (identifier)",
  "deviceName": "String",
  "serialNumber": "String",
  "manufacturer": "String",
  "model": "String",
  "managedBy": "String",
  "autoPilotRegistered": true,
  "autoPilotProfileAssigned": true,
  "azureAdRegistered": true,
  "azureAdJoinType": "String"
}
```
