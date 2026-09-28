<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescriptruleerror?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceComplianceScriptRuleError resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Inherits from [deviceComplianceScriptError](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescripterror?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | [code](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-code?view=graph-rest-beta) | Error code. Inherited from [deviceComplianceScriptError](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescripterror?view=graph-rest-beta). Possible values are: `none`, `jsonFileInvalid`, `jsonFileMissing`, `jsonFileTooLarge`, `rulesMissing`, `duplicateRules`, `tooManyRulesSpecified`, `operatorMissing`, `operatorNotSupported`, `datatypeMissing`, `datatypeNotSupported`, `operatorDataTypeCombinationNotSupported`, `moreInfoUriMissing`, `moreInfoUriInvalid`, `moreInfoUriTooLarge`, `descriptionMissing`, `descriptionInvalid`, `descriptionTooLarge`, `titleMissing`, `titleInvalid`, `titleTooLarge`, `operandMissing`, `operandInvalid`, `operandTooLarge`, `settingNameMissing`, `settingNameInvalid`, `settingNameTooLarge`, `englishLocaleMissing`, `duplicateLocales`, `unrecognizedLocale`, `unknown`, `remediationStringsMissing`. |
| deviceComplianceScriptRulesValidationError | [deviceComplianceScriptRulesValidationError](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescriptrulesvalidationerror?view=graph-rest-beta) | Error code. Inherited from [deviceComplianceScriptError](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescripterror?view=graph-rest-beta). Possible values are: `none`, `jsonFileInvalid`, `jsonFileMissing`, `jsonFileTooLarge`, `rulesMissing`, `duplicateRules`, `tooManyRulesSpecified`, `operatorMissing`, `operatorNotSupported`, `datatypeMissing`, `datatypeNotSupported`, `operatorDataTypeCombinationNotSupported`, `moreInfoUriMissing`, `moreInfoUriInvalid`, `moreInfoUriTooLarge`, `descriptionMissing`, `descriptionInvalid`, `descriptionTooLarge`, `titleMissing`, `titleInvalid`, `titleTooLarge`, `operandMissing`, `operandInvalid`, `operandTooLarge`, `settingNameMissing`, `settingNameInvalid`, `settingNameTooLarge`, `englishLocaleMissing`, `duplicateLocales`, `unrecognizedLocale`, `unknown`, `remediationStringsMissing`. |
| message | String | Error message. Inherited from [deviceComplianceScriptError](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescripterror?view=graph-rest-beta) |
| settingName | String | Setting name for the rule with error. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceComplianceScriptRuleError",
  "code": "String",
  "deviceComplianceScriptRulesValidationError": "String",
  "message": "String",
  "settingName": "String"
}
```
