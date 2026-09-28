<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-user?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# user resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List users](https://learn.microsoft.com/en-us/graph/api/intune-devices-user-list?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-user?view=graph-rest-1.0) collection | List properties and relationships of the [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-user?view=graph-rest-1.0) objects. |
| [Get user](https://learn.microsoft.com/en-us/graph/api/intune-devices-user-get?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-user?view=graph-rest-1.0) | Read properties and relationships of the [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-user?view=graph-rest-1.0) object. |
| [Create user](https://learn.microsoft.com/en-us/graph/api/intune-devices-user-create?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-user?view=graph-rest-1.0) | Create a new [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-user?view=graph-rest-1.0) object. |
| [Delete user](https://learn.microsoft.com/en-us/graph/api/intune-devices-user-delete?view=graph-rest-1.0) | None | Deletes a [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-user?view=graph-rest-1.0). |
| [Update user](https://learn.microsoft.com/en-us/graph/api/intune-devices-user-update?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-user?view=graph-rest-1.0) | Update the properties of a [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-user?view=graph-rest-1.0) object. |
| [removeAllDevicesFromManagement action](https://learn.microsoft.com/en-us/graph/api/intune-devices-user-removealldevicesfrommanagement?view=graph-rest-1.0) | None | Retire all devices from management for this user |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the user. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| managedDevices | [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-1.0) collection | The managed devices associated with the user. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.user",
  "id": "String (identifier)"
}
```
