<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationSettingDefinition resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Not yet documented

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementConfigurationSettingDefinitions](https://learn.microsoft.com/en-us/graph/api/intune-mam-devicemanagementconfigurationsettingdefinition-list?view=graph-rest-beta) | [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) objects. |
| [Get deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-mam-devicemanagementconfigurationsettingdefinition-get?view=graph-rest-beta) | [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) object. |
| [Create deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-mam-devicemanagementconfigurationsettingdefinition-create?view=graph-rest-beta) | [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) | Create a new [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) object. |
| [Delete deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-mam-devicemanagementconfigurationsettingdefinition-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). |
| [Update deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-mam-devicemanagementconfigurationsettingdefinition-update?view=graph-rest-beta) | [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) | Update the properties of a [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicability | [deviceManagementConfigurationSettingApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingapplicability?view=graph-rest-beta) | Details which device setting is applicable on |
| accessTypes | [deviceManagementConfigurationSettingAccessTypes](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingaccesstypes?view=graph-rest-beta) | Read/write access mode of the setting. The possible values are: `none`, `add`, `copy`, `delete`, `get`, `replace`, `execute`. |
| keywords | String collection | Tokens which to search settings on |
| infoUrls | String collection | List of links more info for the setting can be found at |
| occurrence | [deviceManagementConfigurationSettingOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingoccurrence?view=graph-rest-beta) | Indicates whether the setting is required or not |
| baseUri | String | Base CSP Path |
| offsetUri | String | Offset CSP Path from Base |
| rootDefinitionId | String | Root setting definition if the setting is a child setting. |
| categoryId | String | Specifies the area group under which the setting is configured in a specified configuration service provider \(CSP\) |
| settingUsage | [deviceManagementConfigurationSettingUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingusage?view=graph-rest-beta) | Setting type, for example, configuration and compliance. The possible values are: `none`, `configuration`, `compliance`. |
| uxBehavior | [deviceManagementConfigurationControlType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationcontroltype?view=graph-rest-beta) | Setting control type representation in the UX. The possible values are: `default`, `dropdown`, `smallTextBox`, `largeTextBox`, `toggle`, `multiheaderGrid`, `contextPane`. |
| visibility | [deviceManagementConfigurationSettingVisibility](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingvisibility?view=graph-rest-beta) | Setting visibility scope to UX. The possible values are: `none`, `settingsCatalog`, `template`. |
| referredSettingInformationList | [deviceManagementConfigurationReferredSettingInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationreferredsettinginformation?view=graph-rest-beta) collection | List of referred setting information. |
| id | String | Identifier for item |
| description | String | Description of the item |
| helpText | String | Help text of the item |
| name | String | Name of the item |
| displayName | String | Display name of the item |
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
