<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappproductcoderule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# win32LobAppProductCodeRule resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A complex type to store the product code and version rule data for a Win32 LOB app. This rule is not supported as a requirement rule.

Inherits from [win32LobAppRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprule?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ruleType | [win32LobAppRuleType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappruletype?view=graph-rest-1.0) | The rule type indicating the purpose of the rule. Inherited from [win32LobAppRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprule?view=graph-rest-1.0). The possible values are: `detection`, `requirement`. |
| productCode | String | The product code of the app. |
| productVersionOperator | [win32LobAppRuleOperator](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappruleoperator?view=graph-rest-1.0) | The product version comparison operator. The possible values are: `notConfigured`, `equal`, `notEqual`, `greaterThan`, `greaterThanOrEqual`, `lessThan`, `lessThanOrEqual`. |
| productVersion | String | The product version comparison value. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppProductCodeRule",
  "ruleType": "String",
  "productCode": "String",
  "productVersionOperator": "String",
  "productVersion": "String"
}
```
