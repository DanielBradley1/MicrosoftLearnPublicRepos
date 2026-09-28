<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# remoteDesktopSecurityConfiguration resource type

Namespace: microsoft.graph

Represents the configuration for the remoteDesktopSecurityConfiguration object on the servicePrincipal.

Use this configuration to enable the Microsoft Entra ID [Remote Desktop Services \(RDS\) authentication protocol](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-rdpbcgr/dc43f040-d75d-49a9-90c6-0c9999281136), for Microsoft Entra ID to authenticate users to [joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-directory-join) or [hybrid joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-hybrid-join) devices. The configuration also enables single sign-on \(SSO\) when RDP clients connect to a Microsoft Entra joined or Microsoft Entra hybrid joined device that is part of the **targetDeviceGroups** object.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-remotedesktopsecurityconfiguration?view=graph-rest-1.0) | [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) collection | Get a list of the [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-remotedesktopsecurityconfiguration?view=graph-rest-1.0) | [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) | Create a new [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) object on the servicePrincipal object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/remotedesktopsecurityconfiguration-get?view=graph-rest-1.0) | [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) | Read the properties and relationships of a [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) object on the servicePrincipal object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/remotedesktopsecurityconfiguration-update?view=graph-rest-1.0) | [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) | Update the properties of a [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) object on the servicePrincipal object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-remotedesktopsecurityconfiguration?view=graph-rest-1.0) | None | Delete a [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) object on a servicePrincipal object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the RDS security configuration. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isRemoteDesktopProtocolEnabled | Boolean | Determines if Microsoft Entra ID RDS authentication protocol for RDP is enabled. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| approvedClientApps | [approvedClientApp](https://learn.microsoft.com/en-us/graph/api/resources/approvedclientapp?view=graph-rest-1.0) collection | The collection of approved client apps that are associated with the RDS configuration. Supports `$expand`. |
| targetDeviceGroups | [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) collection | The collection of target device groups that are associated with the RDS security configuration that will be enabled for SSO when a client connects to the target device over RDP using the new Microsoft Entra ID RDS authentication protocol. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.remoteDesktopSecurityConfiguration",
  "id": "String (identifier)",
  "isRemoteDesktopProtocolEnabled": "Boolean"
}
```
