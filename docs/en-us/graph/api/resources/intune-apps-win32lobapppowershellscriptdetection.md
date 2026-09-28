<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapppowershellscriptdetection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# win32LobAppPowerShellScriptDetection resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains PowerShell script properties to detect a Win32 App

Inherits from [win32LobAppDetection](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappdetection?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enforceSignatureCheck | Boolean | A value indicating whether signature check is enforced |
| runAs32Bit | Boolean | A value indicating whether this script should run as 32-bit |
| scriptContent | String | The base64 encoded script content to detect Win32 Line of Business \(LoB\) app |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppPowerShellScriptDetection",
  "enforceSignatureCheck": true,
  "runAs32Bit": true,
  "scriptContent": "String"
}
```
