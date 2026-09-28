<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappuninstallpowershellscript?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-12 -->

# win32LobAppUninstallPowerShellScript resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A representation of a PowerShell script that is used to uninstall a Win32 app on an end-user device managed by Intune.

Inherits from [win32LobAppScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappscript?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List win32LobAppUninstallPowerShellScripts](https://learn.microsoft.com/en-us/graph/api/intune-apps-win32lobappuninstallpowershellscript-list?view=graph-rest-beta) | [win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappuninstallpowershellscript?view=graph-rest-beta) collection | List properties and relationships of the [win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappuninstallpowershellscript?view=graph-rest-beta) objects. |
| [Get win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/intune-apps-win32lobappuninstallpowershellscript-get?view=graph-rest-beta) | [win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappuninstallpowershellscript?view=graph-rest-beta) | Read properties and relationships of the [win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappuninstallpowershellscript?view=graph-rest-beta) object. |
| [Create win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/intune-apps-win32lobappuninstallpowershellscript-create?view=graph-rest-beta) | [win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappuninstallpowershellscript?view=graph-rest-beta) | Create a new [win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappuninstallpowershellscript?view=graph-rest-beta) object. |
| [Delete win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/intune-apps-win32lobappuninstallpowershellscript-delete?view=graph-rest-beta) | None | Deletes a [win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappuninstallpowershellscript?view=graph-rest-beta). |
| [Update win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/intune-apps-win32lobappuninstallpowershellscript-update?view=graph-rest-beta) | [win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappuninstallpowershellscript?view=graph-rest-beta) | Update the properties of a [win32LobAppUninstallPowerShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappuninstallpowershellscript?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the script associated with a mobileLobApp entity. This property is read-only. Inherited from [mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta) |
| displayName | String | The display name for the script. Inherited from [mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta) |
| content | String | The content of the script. This is a Base64-encoded representation of the script's original content. The content has a maximum size limit of 100KB. Inherited from [mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta) |
| state | [mobileAppContentScriptState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscriptstate?view=graph-rest-beta) | Indicates the state of the script upload. Possible values are commitPending, commitSuccess, and commitFailed. This property is read-only. Inherited from [mobileAppContentScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscript?view=graph-rest-beta). Possible values are: `commitPending`, `commitSuccess`, `commitFailed`, `unknownFutureValue`. |
| enforceSignatureCheck | Boolean | Indicates whether or not to enforce a signature check when running the script. When TRUE, the script cannot be run without enforcing a signature check. When FALSE, no signature check will be enforced when running the script. Default value is FALSE. Inherited from [win32LobAppScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappscript?view=graph-rest-beta) |
| runAs32Bit | Boolean | Indicates whether the script will run as 32-bit or 64-bit. When TRUE, the script will run as 32-bit. When FALSE, the script will run as 64-bit. Default value is FALSE. Inherited from [win32LobAppScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappscript?view=graph-rest-beta) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppUninstallPowerShellScript",
  "id": "String (identifier)",
  "displayName": "String",
  "content": "String",
  "state": "String",
  "enforceSignatureCheck": true,
  "runAs32Bit": true
}
```
