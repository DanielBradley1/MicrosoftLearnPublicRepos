<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approvedclientapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# approvedClientApp resource type

Namespace: microsoft.graph

Represents an approved client application that can connect to remote desktops using the [Remote Desktop Services \(RDS\)](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) authentication protocol.

Represents the approved client apps configured for the [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) object on the service principal. This configuration along with [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) enables Single Sign on \(SSO\) using the Microsoft Entra ID [Remote Desktop Services \(RDS\) authentication protocol](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-rdpbcgr/dc43f040-d75d-49a9-90c6-0c9999281136), when Microsoft Entra ID authenticates a user to a [joined](https://learn.microsoft.com/en-us/entra/identity/devices/concept-directory-join) or [hybrid joined](https://learn.microsoft.com/en-us/entra/identity/devices/concept-hybrid-join) device that is a member of the target device group.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/remotedesktopsecurityconfiguration-list-approvedclientapps?view=graph-rest-1.0) | [approvedClientApp](https://learn.microsoft.com/en-us/graph/api/resources/approvedclientapp?view=graph-rest-1.0) collection | Get a list of the [approvedClientApp](https://learn.microsoft.com/en-us/graph/api/resources/approvedclientapp?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/remotedesktopsecurityconfiguration-post-approvedclientapps?view=graph-rest-1.0) | [approvedClientApp](https://learn.microsoft.com/en-us/graph/api/resources/approvedclientapp?view=graph-rest-1.0) | Create a new [approvedClientApp](https://learn.microsoft.com/en-us/graph/api/resources/approvedclientapp?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/approvedclientapp-get?view=graph-rest-1.0) | [approvedClientApp](https://learn.microsoft.com/en-us/graph/api/resources/approvedclientapp?view=graph-rest-1.0) | Read the properties and relationships of an [approvedClientApp](https://learn.microsoft.com/en-us/graph/api/resources/approvedclientapp?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/approvedclientapp-update?view=graph-rest-1.0) | [approvedClientApp](https://learn.microsoft.com/en-us/graph/api/resources/approvedclientapp?view=graph-rest-1.0) | Update the properties of an [approvedClientApp](https://learn.microsoft.com/en-us/graph/api/resources/approvedclientapp?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/remotedesktopsecurityconfiguration-delete-approvedclientapps?view=graph-rest-1.0) | None | Delete an [approvedClientApp](https://learn.microsoft.com/en-us/graph/api/resources/approvedclientapp?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the approved client application. |
| id | String | The unique identifier for the approved client application. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.approvedClientApp",
  "id": "String (identifier)",
  "displayName": "String"
}
```
