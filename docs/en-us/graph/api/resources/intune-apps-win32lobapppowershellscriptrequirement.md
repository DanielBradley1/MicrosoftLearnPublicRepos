<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapppowershellscriptrequirement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# win32LobAppPowerShellScriptRequirement resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains PowerShell script properties to detect a Win32 App

Inherits from [win32LobAppRequirement](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprequirement?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| operator | [win32LobAppDetectionOperator](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappdetectionoperator?view=graph-rest-beta) | The operator for detection Inherited from [win32LobAppRequirement](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprequirement?view=graph-rest-beta). Possible values are: `notConfigured`, `equal`, `notEqual`, `greaterThan`, `greaterThanOrEqual`, `lessThan`, `lessThanOrEqual`. |
| detectionValue | String | The detection value Inherited from [win32LobAppRequirement](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprequirement?view=graph-rest-beta) |
| displayName | String | The unique display name for this rule |
| enforceSignatureCheck | Boolean | A value indicating whether signature check is enforced |
| runAs32Bit | Boolean | A value indicating whether this script should run as 32-bit |
| runAsAccount | [runAsAccountType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-runasaccounttype?view=graph-rest-beta) | Indicates the type of execution context the script runs in. Possible values are: `system`, `user`. |
| scriptContent | String | The base64 encoded script content to detect Win32 Line of Business \(LoB\) app |
| detectionType | [win32LobAppPowerShellScriptDetectionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapppowershellscriptdetectiontype?view=graph-rest-beta) | The detection type for script output. Possible values are: `notConfigured`, `string`, `dateTime`, `integer`, `float`, `version`, `boolean`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppPowerShellScriptRequirement",
  "operator": "String",
  "detectionValue": "String",
  "displayName": "String",
  "enforceSignatureCheck": true,
  "runAs32Bit": true,
  "runAsAccount": "String",
  "scriptContent": "String",
  "detectionType": "String"
}
```
