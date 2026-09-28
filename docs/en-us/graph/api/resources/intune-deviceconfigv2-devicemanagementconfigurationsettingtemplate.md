<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationSettingTemplate resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Setting Template

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementConfigurationSettingTemplates](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate-list?view=graph-rest-beta) | [deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate?view=graph-rest-beta) objects. |
| [Get deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate-get?view=graph-rest-beta) | [deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate?view=graph-rest-beta) object. |
| [Create deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate-create?view=graph-rest-beta) | [deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate?view=graph-rest-beta) | Create a new [deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate?view=graph-rest-beta) object. |
| [Delete deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate?view=graph-rest-beta). |
| [Update deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate-update?view=graph-rest-beta) | [deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate?view=graph-rest-beta) | Update the properties of a [deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of this setting template within the policy template which contains it. Automatically generated. |
| settingInstanceTemplate | [deviceManagementConfigurationSettingInstanceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinginstancetemplate?view=graph-rest-beta) | Setting Instance Template |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| settingDefinitions | [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) collection | List of related Setting Definitions |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSettingTemplate",
  "id": "String (identifier)",
  "settingInstanceTemplate": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationSimpleSettingInstanceTemplate",
    "settingInstanceTemplateId": "String",
    "settingDefinitionId": "String",
    "isRequired": true,
    "simpleSettingValueTemplate": {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationStringSettingValueTemplate",
      "settingValueTemplateId": "String",
      "defaultValue": {
        "@odata.type": "microsoft.graph.deviceManagementConfigurationStringSettingValueConstantDefaultTemplate",
        "constantValue": "String"
      }
    }
  }
}
```
