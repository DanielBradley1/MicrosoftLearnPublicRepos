<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-unmanageddevicediscoverytask?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# unmanagedDeviceDiscoveryTask resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This task derived type represents a list of unmanaged devices discovered in the network.

Inherits from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List unmanagedDeviceDiscoveryTasks](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-unmanageddevicediscoverytask-list?view=graph-rest-beta) | [unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-unmanageddevicediscoverytask?view=graph-rest-beta) collection | List properties and relationships of the [unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-unmanageddevicediscoverytask?view=graph-rest-beta) objects. |
| [Get unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-unmanageddevicediscoverytask-get?view=graph-rest-beta) | [unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-unmanageddevicediscoverytask?view=graph-rest-beta) | Read properties and relationships of the [unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-unmanageddevicediscoverytask?view=graph-rest-beta) object. |
| [Create unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-unmanageddevicediscoverytask-create?view=graph-rest-beta) | [unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-unmanageddevicediscoverytask?view=graph-rest-beta) | Create a new [unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-unmanageddevicediscoverytask?view=graph-rest-beta) object. |
| [Delete unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-unmanageddevicediscoverytask-delete?view=graph-rest-beta) | None | Deletes a [unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-unmanageddevicediscoverytask?view=graph-rest-beta). |
| [Update unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-unmanageddevicediscoverytask-update?view=graph-rest-beta) | [unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-unmanageddevicediscoverytask?view=graph-rest-beta) | Update the properties of a [unmanagedDeviceDiscoveryTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-unmanageddevicediscoverytask?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The entity key. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| displayName | String | The name. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| description | String | The description. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The created date. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| dueDateTime | DateTimeOffset | The due date. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| category | [deviceAppManagementTaskCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskcategory?view=graph-rest-beta) | The category. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta). Possible values are: `unknown`, `advancedThreatProtection`. |
| priority | [deviceAppManagementTaskPriority](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskpriority?view=graph-rest-beta) | The priority. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta). Possible values are: `none`, `high`, `low`. |
| creator | String | The email address of the creator. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| creatorNotes | String | Notes from the creator. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| assignedTo | String | The name or email of the admin this task is assigned to. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| status | [deviceAppManagementTaskStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskstatus?view=graph-rest-beta) | The status. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta). Possible values are: `unknown`, `pending`, `active`, `completed`, `rejected`. |
| unmanagedDevices | [unmanagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-unmanageddevice?view=graph-rest-beta) collection | Unmanaged devices discovered in the network. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.unmanagedDeviceDiscoveryTask",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "dueDateTime": "String (timestamp)",
  "category": "String",
  "priority": "String",
  "creator": "String",
  "creatorNotes": "String",
  "assignedTo": "String",
  "status": "String",
  "unmanagedDevices": [
    {
      "@odata.type": "microsoft.graph.unmanagedDevice",
      "os": "String",
      "osVersion": "String",
      "ipAddress": "String",
      "deviceName": "String",
      "macAddress": "String",
      "domain": "String",
      "manufacturer": "String",
      "model": "String",
      "location": "String",
      "lastLoggedOnUser": "String",
      "lastSeenDateTime": "String (timestamp)"
    }
  ]
}
```
