<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsimplesettingcollectioninstancetemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationSimpleSettingCollectionInstanceTemplate resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Simple Setting Collection Instance Template

Inherits from [deviceManagementConfigurationSettingInstanceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinginstancetemplate?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| settingInstanceTemplateId | String | Setting Instance Template Id Inherited from [deviceManagementConfigurationSettingInstanceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinginstancetemplate?view=graph-rest-beta) |
| settingDefinitionId | String | Setting Definition Id Inherited from [deviceManagementConfigurationSettingInstanceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinginstancetemplate?view=graph-rest-beta) |
| isRequired | Boolean | Indicates if a policy must specify this setting. Inherited from [deviceManagementConfigurationSettingInstanceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinginstancetemplate?view=graph-rest-beta) |
| simpleSettingCollectionValueTemplate | [deviceManagementConfigurationSimpleSettingValueTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsimplesettingvaluetemplate?view=graph-rest-beta) collection | Simple Setting Collection Value Template |
| allowUnmanagedValues | Boolean | Linked policy may append values which are not present in the template. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSimpleSettingCollectionInstanceTemplate",
  "settingInstanceTemplateId": "String",
  "settingDefinitionId": "String",
  "isRequired": true,
  "simpleSettingCollectionValueTemplate": [
    {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationStringSettingValueTemplate",
      "settingValueTemplateId": "String",
      "defaultValue": {
        "@odata.type": "microsoft.graph.deviceManagementConfigurationStringSettingValueConstantDefaultTemplate",
        "constantValue": "String"
      }
    }
  ],
  "allowUnmanagedValues": true
}
```
