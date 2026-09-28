<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsimplesettinginstance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationSimpleSettingInstance resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Simple setting instance

Inherits from [deviceManagementConfigurationSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettinginstance?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| settingDefinitionId | String | Setting Definition Id Inherited from [deviceManagementConfigurationSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettinginstance?view=graph-rest-beta) |
| settingInstanceTemplateReference | [deviceManagementConfigurationSettingInstanceTemplateReference](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettinginstancetemplatereference?view=graph-rest-beta) | Setting Instance Template Reference Inherited from [deviceManagementConfigurationSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettinginstance?view=graph-rest-beta) |
| simpleSettingValue | [deviceManagementConfigurationSimpleSettingValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsimplesettingvalue?view=graph-rest-beta) | Simple setting instance value |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance",
  "settingDefinitionId": "String",
  "settingInstanceTemplateReference": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
    "settingInstanceTemplateId": "String"
  },
  "simpleSettingValue": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationStringSettingValue",
    "settingValueTemplateReference": {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
      "settingValueTemplateId": "String",
      "useTemplateDefault": true
    },
    "value": "String"
  }
}
```
