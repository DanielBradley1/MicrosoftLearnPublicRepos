<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationstringsettingvaluedefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# deviceManagementConfigurationStringSettingValueDefinition resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

String constraints

Inherits from [deviceManagementConfigurationSettingValueDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingvaluedefinition?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| format | [deviceManagementConfigurationStringFormat](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationstringformat?view=graph-rest-beta) | Pre-defined format of the string. The possible values are: `none`, `email`, `guid`, `ip`, `base64`, `url`, `version`, `xml`, `date`, `time`, `binary`, `regEx`, `json`, `dateTime`, `surfaceHub`, `bashScript`, `unknownFutureValue`. |
| inputValidationSchema | String | Regular expression or any xml or json schema that the input string should match |
| maximumLength | Int64 | Maximum length of string. Valid values 0 to 87516 |
| minimumLength | Int64 | Minimum length of string. Valid values 0 to 87516 |
| isSecret | Boolean | Specifies whether the setting needs to be treated as a secret. Settings marked as yes will be encrypted in transit and at rest and will be displayed as asterisks when represented in the UX. |
| fileTypes | String collection | Supported file types for this setting. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationStringSettingValueDefinition",
  "format": "String",
  "inputValidationSchema": "String",
  "maximumLength": 1024,
  "minimumLength": 1024,
  "isSecret": true,
  "fileTypes": [
    "String"
  ]
}
```
