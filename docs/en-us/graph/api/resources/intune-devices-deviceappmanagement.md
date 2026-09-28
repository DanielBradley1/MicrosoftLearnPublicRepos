<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceappmanagement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceAppManagement resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Singleton entity that acts as a container for all device app management functionality.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/intune-devices-deviceappmanagement-get?view=graph-rest-beta) | [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceappmanagement?view=graph-rest-beta) | Read properties and relationships of the [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceappmanagement?view=graph-rest-beta) object. |
| [Update deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/intune-devices-deviceappmanagement-update?view=graph-rest-beta) | [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceappmanagement?view=graph-rest-beta) | Update the properties of a [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceappmanagement?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| windowsManagementApp | [windowsManagementApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapp?view=graph-rest-beta) | Windows management app. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAppManagement",
  "id": "String (identifier)"
}
```
