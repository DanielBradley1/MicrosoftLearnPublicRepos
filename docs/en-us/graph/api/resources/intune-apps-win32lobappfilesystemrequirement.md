<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappfilesystemrequirement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# win32LobAppFileSystemRequirement resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains file or folder path to detect a Win32 App

Inherits from [win32LobAppRequirement](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprequirement?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| operator | [win32LobAppDetectionOperator](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappdetectionoperator?view=graph-rest-beta) | The operator for detection Inherited from [win32LobAppRequirement](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprequirement?view=graph-rest-beta). Possible values are: `notConfigured`, `equal`, `notEqual`, `greaterThan`, `greaterThanOrEqual`, `lessThan`, `lessThanOrEqual`. |
| detectionValue | String | The detection value Inherited from [win32LobAppRequirement](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprequirement?view=graph-rest-beta) |
| path | String | The file or folder path to detect Win32 Line of Business \(LoB\) app |
| fileOrFolderName | String | The file or folder name to detect Win32 Line of Business \(LoB\) app |
| check32BitOn64System | Boolean | A value indicating whether this file or folder is for checking 32-bit app on 64-bit system |
| detectionType | [win32LobAppFileSystemDetectionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappfilesystemdetectiontype?view=graph-rest-beta) | The file system detection type. Possible values are: `notConfigured`, `exists`, `modifiedDate`, `createdDate`, `version`, `sizeInMB`, `doesNotExist`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppFileSystemRequirement",
  "operator": "String",
  "detectionValue": "String",
  "path": "String",
  "fileOrFolderName": "String",
  "check32BitOn64System": true,
  "detectionType": "String"
}
```
