<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceConfigurationAssignment resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The device configuration assignment entity assigns an AAD group to a specific device configuration.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceConfigurationAssignments](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationassignment-list?view=graph-rest-1.0) | [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0) collection | List properties and relationships of the [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0) objects. |
| [Get deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationassignment-get?view=graph-rest-1.0) | [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0) | Read properties and relationships of the [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0) object. |
| [Create deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationassignment-create?view=graph-rest-1.0) | [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0) | Create a new [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0) object. |
| [Delete deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationassignment-delete?view=graph-rest-1.0) | None | Deletes a [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0). |
| [Update deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationassignment-update?view=graph-rest-1.0) | [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0) | Update the properties of a [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key of the assignment. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-1.0) | The assignment target for the device configuration. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceConfigurationAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "targetType": "String",
    "entraObjectId": "String"
  }
}
```
