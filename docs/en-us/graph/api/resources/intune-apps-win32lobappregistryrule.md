<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappregistryrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# win32LobAppRegistryRule resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A complex type to store registry rule data for a Win32 LOB app.

Inherits from [win32LobAppRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprule?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ruleType | [win32LobAppRuleType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappruletype?view=graph-rest-1.0) | The rule type indicating the purpose of the rule. Inherited from [win32LobAppRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprule?view=graph-rest-1.0). The possible values are: `detection`, `requirement`. |
| check32BitOn64System | Boolean | A value indicating whether to search the 32-bit registry on 64-bit systems. |
| keyPath | String | The full path of the registry entry containing the value to detect. |
| valueName | String | The name of the registry value to detect. |
| operationType | [win32LobAppRegistryRuleOperationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappregistryruleoperationtype?view=graph-rest-1.0) | The registry operation type. The possible values are: `notConfigured`, `exists`, `doesNotExist`, `string`, `integer`, `version`. |
| operator | [win32LobAppRuleOperator](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappruleoperator?view=graph-rest-1.0) | The operator for registry detection. The possible values are: `notConfigured`, `equal`, `notEqual`, `greaterThan`, `greaterThanOrEqual`, `lessThan`, `lessThanOrEqual`. |
| comparisonValue | String | The registry comparison value. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppRegistryRule",
  "ruleType": "String",
  "check32BitOn64System": true,
  "keyPath": "String",
  "valueName": "String",
  "operationType": "String",
  "operator": "String",
  "comparisonValue": "String"
}
```
