<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescriptvalidationresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceComplianceScriptValidationResult resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| rules | [deviceComplianceScriptRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescriptrule?view=graph-rest-beta) collection | Parsed rules from json. |
| scriptErrors | [deviceComplianceScriptError](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescripterror?view=graph-rest-beta) collection | Errors in json for the script. |
| ruleErrors | [deviceComplianceScriptRuleError](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescriptruleerror?view=graph-rest-beta) collection | Errors in json for the script for rules. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceComplianceScriptValidationResult",
  "rules": [
    {
      "@odata.type": "microsoft.graph.deviceComplianceScriptRule",
      "settingName": "String",
      "operator": "String",
      "deviceComplianceScriptRulOperator": "String",
      "dataType": "String",
      "deviceComplianceScriptRuleDataType": "String",
      "operand": "String"
    }
  ],
  "scriptErrors": [
    {
      "@odata.type": "microsoft.graph.deviceComplianceScriptError",
      "code": "String",
      "deviceComplianceScriptRulesValidationError": "String",
      "message": "String"
    }
  ],
  "ruleErrors": [
    {
      "@odata.type": "microsoft.graph.deviceComplianceScriptRuleError",
      "code": "String",
      "deviceComplianceScriptRulesValidationError": "String",
      "message": "String",
      "settingName": "String"
    }
  ]
}
```
