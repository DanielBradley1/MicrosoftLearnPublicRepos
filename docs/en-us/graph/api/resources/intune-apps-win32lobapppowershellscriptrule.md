<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapppowershellscriptrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# win32LobAppPowerShellScriptRule resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A complex type to store the PowerShell script rule data for a Win32 LOB app.

Inherits from [win32LobAppRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprule?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ruleType | [win32LobAppRuleType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappruletype?view=graph-rest-1.0) | The rule type indicating the purpose of the rule. Inherited from [win32LobAppRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprule?view=graph-rest-1.0). The possible values are: `detection`, `requirement`. |
| displayName | String | The display name for the rule. Do not specify this value if the rule is used for detection. |
| enforceSignatureCheck | Boolean | A value indicating whether a signature check is enforced. |
| runAs32Bit | Boolean | A value indicating whether the script should run as 32-bit. |
| runAsAccount | [runAsAccountType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-runasaccounttype?view=graph-rest-1.0) | The execution context of the script. Do not specify this value if the rule is used for detection. Script detection rules will run in the same context as the associated app install context. The possible values are: `system`, `user`. |
| scriptContent | String | The base64-encoded script content. |
| operationType | [win32LobAppPowerShellScriptRuleOperationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapppowershellscriptruleoperationtype?view=graph-rest-1.0) | The script output comparison operation type. Use NotConfigured \(the default value\) if the rule is used for detection. The possible values are: `notConfigured`, `string`, `dateTime`, `integer`, `float`, `version`, `boolean`. |
| operator | [win32LobAppRuleOperator](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappruleoperator?view=graph-rest-1.0) | The script output operator. Use NotConfigured \(the default value\) if the rule is used for detection. The possible values are: `notConfigured`, `equal`, `notEqual`, `greaterThan`, `greaterThanOrEqual`, `lessThan`, `lessThanOrEqual`. |
| comparisonValue | String | The script output comparison value. Do not specify a value if the rule is used for detection. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppPowerShellScriptRule",
  "ruleType": "String",
  "displayName": "String",
  "enforceSignatureCheck": true,
  "runAs32Bit": true,
  "runAsAccount": "String",
  "scriptContent": "String",
  "operationType": "String",
  "operator": "String",
  "comparisonValue": "String"
}
```
