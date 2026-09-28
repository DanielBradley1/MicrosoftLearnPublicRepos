<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappfilesystemrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# win32LobAppFileSystemRule resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A complex type to store file or folder rule data for a Win32 LOB app.

Inherits from [win32LobAppRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprule?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ruleType | [win32LobAppRuleType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappruletype?view=graph-rest-1.0) | The rule type indicating the purpose of the rule. Inherited from [win32LobAppRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprule?view=graph-rest-1.0). The possible values are: `detection`, `requirement`. |
| path | String | The file or folder path to look up. |
| fileOrFolderName | String | The file or folder name to look up. |
| check32BitOn64System | Boolean | A value indicating whether to expand environment variables in the 32-bit context on 64-bit systems. |
| operationType | [win32LobAppFileSystemOperationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappfilesystemoperationtype?view=graph-rest-1.0) | The file system operation type. The possible values are: `notConfigured`, `exists`, `modifiedDate`, `createdDate`, `version`, `sizeInMB`. |
| operator | [win32LobAppRuleOperator](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappruleoperator?view=graph-rest-1.0) | The operator for file or folder detection. The possible values are: `notConfigured`, `equal`, `notEqual`, `greaterThan`, `greaterThanOrEqual`, `lessThan`, `lessThanOrEqual`. |
| comparisonValue | String | The file or folder comparison value. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppFileSystemRule",
  "ruleType": "String",
  "path": "String",
  "fileOrFolderName": "String",
  "check32BitOn64System": true,
  "operationType": "String",
  "operator": "String",
  "comparisonValue": "String"
}
```
