<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# targetDeviceGroup resource type

Namespace: microsoft.graph

Represents the group of devices configured for the remoteDesktopSecurityConfiguration object on the servicePrincipal. This configuration enables SSO using the Microsoft Entra ID [Remote Desktop Services \(RDS\) authentication protocol](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-rdpbcgr/dc43f040-d75d-49a9-90c6-0c9999281136), when Microsoft Entra ID authenticates a user to a [joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-directory-join) or [hybrid joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-hybrid-join) device that is a member of the targetDeviceGroup.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/remotedesktopsecurityconfiguration-list-targetdevicegroups?view=graph-rest-1.0) | [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) collection | Get a list of the [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) objects and their properties for the [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) object on the servicePrincipal. |
| [Create](https://learn.microsoft.com/en-us/graph/api/remotedesktopsecurityconfiguration-post-targetdevicegroups?view=graph-rest-1.0) | [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) | Create a new [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) object for the [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) object on the servicePrincipal. |
| [Get](https://learn.microsoft.com/en-us/graph/api/targetdevicegroup-get?view=graph-rest-1.0) | [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) | Read the properties and relationships of a [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) object for the [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) on a servicePrincipal. |
| [Update](https://learn.microsoft.com/en-us/graph/api/targetdevicegroup-update?view=graph-rest-1.0) | [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) | Update the properties of a [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) object for the [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) on the servicePrincipal. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/remotedesktopsecurityconfiguration-delete-targetdevicegroups?view=graph-rest-1.0) | None | Delete a [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) object for the [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) on the servicePrincipal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name for the target device group. |
| id | String | Object identifier of the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.targetDeviceGroup",
  "id": "String (identifier)",
  "displayName": "String"
}
```
