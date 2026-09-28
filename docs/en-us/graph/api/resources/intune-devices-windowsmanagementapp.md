<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsManagementApp resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows management app entity.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get windowsManagementApp](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanagementapp-get?view=graph-rest-beta) | [windowsManagementApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapp?view=graph-rest-beta) | Read properties and relationships of the [windowsManagementApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapp?view=graph-rest-beta) object. |
| [Update windowsManagementApp](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanagementapp-update?view=graph-rest-beta) | [windowsManagementApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapp?view=graph-rest-beta) | Update the properties of a [windowsManagementApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapp?view=graph-rest-beta) object. |
| [setAsManagedInstaller action](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanagementapp-setasmanagedinstaller?view=graph-rest-beta) | None | Set the Managed Installer status for the caller tenant |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the Windows management app |
| availableVersion | String | Windows management app available version. |
| managedInstaller | [managedInstallerStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-managedinstallerstatus?view=graph-rest-beta) | Managed Installer Status. Possible values are: `disabled`, `enabled`. |
| managedInstallerConfiguredDateTime | String | Managed Installer Configured Date Time |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| healthStates | [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta) collection | The list of health states for installed Windows management app. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsManagementApp",
  "id": "String (identifier)",
  "availableVersion": "String",
  "managedInstaller": "String",
  "managedInstallerConfiguredDateTime": "String"
}
```
