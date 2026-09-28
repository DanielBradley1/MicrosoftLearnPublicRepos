<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-deviceappmanagement?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceAppManagement resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Singleton entity that acts as a container for all device and app management functionality.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/intune-unlock-deviceappmanagement-get?view=graph-rest-1.0) | [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-deviceappmanagement?view=graph-rest-1.0) | Read properties and relationships of the [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-deviceappmanagement?view=graph-rest-1.0) object. |
| [Update deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/intune-unlock-deviceappmanagement-update?view=graph-rest-1.0) | [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-deviceappmanagement?view=graph-rest-1.0) | Update the properties of a [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-deviceappmanagement?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| wdacSupplementalPolicies | [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-1.0) collection | The collection of Windows Defender Application Control Supplemental Policies. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAppManagement",
  "id": "String (identifier)"
}
```
