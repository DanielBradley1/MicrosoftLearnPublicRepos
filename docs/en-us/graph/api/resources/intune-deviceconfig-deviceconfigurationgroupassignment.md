<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceConfigurationGroupAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device configuration group assignment.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceConfigurationGroupAssignments](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationgroupassignment-list?view=graph-rest-beta) | [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta) collection | List properties and relationships of the [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta) objects. |
| [Get deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationgroupassignment-get?view=graph-rest-beta) | [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta) | Read properties and relationships of the [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta) object. |
| [Create deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationgroupassignment-create?view=graph-rest-beta) | [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta) | Create a new [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta) object. |
| [Delete deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationgroupassignment-delete?view=graph-rest-beta) | None | Deletes a [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta). |
| [Update deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationgroupassignment-update?view=graph-rest-beta) | [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta) | Update the properties of a [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| targetGroupId | String | The Id of the AAD group we are targeting the device configuration to. |
| excludeGroup | Boolean | Indicates if this group is should be excluded. Defaults that the group should be included |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| deviceConfiguration | [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) | The navigation link to the Device Configuration being targeted. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceConfigurationGroupAssignment",
  "id": "String (identifier)",
  "targetGroupId": "String",
  "excludeGroup": true
}
```
