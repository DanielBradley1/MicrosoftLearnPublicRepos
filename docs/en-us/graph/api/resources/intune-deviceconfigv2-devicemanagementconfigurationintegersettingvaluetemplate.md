<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationintegersettingvaluetemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationIntegerSettingValueTemplate resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Integer Setting Value Template

Inherits from [deviceManagementConfigurationSimpleSettingValueTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsimplesettingvaluetemplate?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| settingValueTemplateId | String | Setting Value Template Id Inherited from [deviceManagementConfigurationSimpleSettingValueTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsimplesettingvaluetemplate?view=graph-rest-beta) |
| defaultValue | [deviceManagementConfigurationIntegerSettingValueDefaultTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationintegersettingvaluedefaulttemplate?view=graph-rest-beta) | Integer Setting Value Default Template. |
| recommendedValueDefinition | [deviceManagementConfigurationIntegerSettingValueDefinitionTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationintegersettingvaluedefinitiontemplate?view=graph-rest-beta) | Recommended value definition. |
| requiredValueDefinition | [deviceManagementConfigurationIntegerSettingValueDefinitionTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationintegersettingvaluedefinitiontemplate?view=graph-rest-beta) | Required value definition. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationIntegerSettingValueTemplate",
  "settingValueTemplateId": "String",
  "defaultValue": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationIntegerSettingValueConstantDefaultTemplate",
    "constantValue": 1024
  },
  "recommendedValueDefinition": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationIntegerSettingValueDefinitionTemplate",
    "minValue": 1024,
    "maxValue": 1024
  },
  "requiredValueDefinition": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationIntegerSettingValueDefinitionTemplate",
    "minValue": 1024,
    "maxValue": 1024
  }
}
```
