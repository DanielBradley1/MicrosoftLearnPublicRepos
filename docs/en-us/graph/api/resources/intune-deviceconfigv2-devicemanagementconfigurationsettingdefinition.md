<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# deviceManagementConfigurationSettingDefinition resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementConfigurationSettingDefinitions](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition-list?view=graph-rest-beta) | [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) objects. |
| [Get deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition-get?view=graph-rest-beta) | [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) object. |
| [Create deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition-create?view=graph-rest-beta) | [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) | Create a new [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) object. |
| [Delete deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). |
| [Update deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition-update?view=graph-rest-beta) | [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) | Update the properties of a [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) object. |
| [retrieveDeviceConfigurationAvailableOptions function](https://learn.microsoft.com/en-us/graph/api/api/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition-retrievedeviceconfigurationavailableoptions.md?view=graph-rest-beta) | [deviceConfigurationOption](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-deviceconfigurationoption.md?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicability | [deviceManagementConfigurationSettingApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingapplicability?view=graph-rest-beta) | Details which device setting is applicable on. Supports: $filters. |
| accessTypes | [deviceManagementConfigurationSettingAccessTypes](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingaccesstypes?view=graph-rest-beta) | Read/write access mode of the setting. The possible values are: `none`, `add`, `copy`, `delete`, `get`, `replace`, `execute`. |
| keywords | String collection | Tokens which to search settings on |
| infoUrls | String collection | List of links more info for the setting can be found at. |
| occurrence | [deviceManagementConfigurationSettingOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingoccurrence?view=graph-rest-beta) | Indicates whether the setting is required or not |
| baseUri | String | Base CSP Path |
| offsetUri | String | Offset CSP Path from Base |
| rootDefinitionId | String | Root setting definition id if the setting is a child setting. |
| categoryId | String | Specify category in which the setting is under. Support $filters. |
| settingUsage | [deviceManagementConfigurationSettingUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingusage?view=graph-rest-beta) | Indicate setting type for the setting. The possible values are: configuration, compliance, reusableSetting. Each setting usage has separate API end-point to call. The possible values are: `none`, `configuration`, `compliance`, `unknownFutureValue`, `inventory`. |
| uxBehavior | [deviceManagementConfigurationControlType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcontroltype?view=graph-rest-beta) | Setting control type representation in the UX. The possible values are: default, dropdown, smallTextBox, largeTextBox, toggle, multiheaderGrid, contextPane. The possible values are: `default`, `dropdown`, `smallTextBox`, `largeTextBox`, `toggle`, `multiheaderGrid`, `contextPane`, `unknownFutureValue`. |
| visibility | [deviceManagementConfigurationSettingVisibility](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingvisibility?view=graph-rest-beta) | Setting visibility scope to UX. The possible values are: none, settingsCatalog, template. The possible values are: `none`, `settingsCatalog`, `template`, `unknownFutureValue`, `inventoryCatalog`. |
| riskLevel | [deviceManagementConfigurationSettingRiskLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingrisklevel?view=graph-rest-beta) | Setting risklevel. The possible values are: low, medium, high. The possible values are: `low`, `medium`, `high`. |
| referredSettingInformationList | [deviceManagementConfigurationReferredSettingInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationreferredsettinginformation?view=graph-rest-beta) collection | List of referred setting information. |
| id | String | Identifier for item |
| description | String | Description of the setting. |
| helpText | String | Help text of the setting. Give more details of the setting. |
| name | String | Name of the item |
| displayName | String | Name of the setting. For example: Allow Toast. |
| version | String | Item Version |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSettingDefinition",
  "applicability": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingApplicability",
    "description": "String",
    "platform": "String",
    "deviceMode": "String",
    "technologies": "String"
  },
  "accessTypes": "String",
  "keywords": [
    "String"
  ],
  "infoUrls": [
    "String"
  ],
  "occurrence": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingOccurrence",
    "minDeviceOccurrence": 1024,
    "maxDeviceOccurrence": 1024
  },
  "baseUri": "String",
  "offsetUri": "String",
  "rootDefinitionId": "String",
  "categoryId": "String",
  "settingUsage": "String",
  "uxBehavior": "String",
  "visibility": "String",
  "riskLevel": "String",
  "referredSettingInformationList": [
    {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationReferredSettingInformation",
      "settingDefinitionId": "String"
    }
  ],
  "id": "String (identifier)",
  "description": "String",
  "helpText": "String",
  "name": "String",
  "displayName": "String",
  "version": "String"
}
```
