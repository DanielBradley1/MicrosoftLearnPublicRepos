<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationSettingGroupCollectionDefinition resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Inherits from [deviceManagementConfigurationSettingGroupDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupdefinition?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementConfigurationSettingGroupCollectionDefinitions](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition-list?view=graph-rest-beta) | [deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition?view=graph-rest-beta) objects. |
| [Get deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition-get?view=graph-rest-beta) | [deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition?view=graph-rest-beta) object. |
| [Create deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition-create?view=graph-rest-beta) | [deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition?view=graph-rest-beta) | Create a new [deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition?view=graph-rest-beta) object. |
| [Delete deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition?view=graph-rest-beta). |
| [Update deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition-update?view=graph-rest-beta) | [deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition?view=graph-rest-beta) | Update the properties of a [deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicability | [deviceManagementConfigurationSettingApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingapplicability?view=graph-rest-beta) | Details which device setting is applicable on. Supports: $filters. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| accessTypes | [deviceManagementConfigurationSettingAccessTypes](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingaccesstypes?view=graph-rest-beta) | Read/write access mode of the setting Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `none`, `add`, `copy`, `delete`, `get`, `replace`, `execute`. |
| keywords | String collection | Tokens which to search settings on Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| infoUrls | String collection | List of links more info for the setting can be found at. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| occurrence | [deviceManagementConfigurationSettingOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingoccurrence?view=graph-rest-beta) | Indicates whether the setting is required or not Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| baseUri | String | Base CSP Path Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| offsetUri | String | Offset CSP Path from Base Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| rootDefinitionId | String | Root setting definition id if the setting is a child setting. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| categoryId | String | Specify category in which the setting is under. Support $filters. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| settingUsage | [deviceManagementConfigurationSettingUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingusage?view=graph-rest-beta) | Indicate setting type for the setting. The possible values are: configuration, compliance, reusableSetting. Each setting usage has separate API end-point to call. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `none`, `configuration`, `compliance`, `unknownFutureValue`, `inventory`. |
| uxBehavior | [deviceManagementConfigurationControlType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcontroltype?view=graph-rest-beta) | Setting control type representation in the UX. The possible values are: default, dropdown, smallTextBox, largeTextBox, toggle, multiheaderGrid, contextPane. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `default`, `dropdown`, `smallTextBox`, `largeTextBox`, `toggle`, `multiheaderGrid`, `contextPane`, `unknownFutureValue`. |
| visibility | [deviceManagementConfigurationSettingVisibility](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingvisibility?view=graph-rest-beta) | Setting visibility scope to UX. The possible values are: none, settingsCatalog, template. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `none`, `settingsCatalog`, `template`, `unknownFutureValue`, `inventoryCatalog`. |
| riskLevel | [deviceManagementConfigurationSettingRiskLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingrisklevel?view=graph-rest-beta) | Setting risklevel. The possible values are: low, medium, high Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `low`, `medium`, `high`. |
| referredSettingInformationList | [deviceManagementConfigurationReferredSettingInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationreferredsettinginformation?view=graph-rest-beta) collection | List of referred setting information. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| id | String | Identifier for item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| description | String | Description of the setting. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| helpText | String | Help text of the setting. Give more details of the setting. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| name | String | Name of the item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| displayName | String | Name of the setting. For example: Allow Toast. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| version | String | Item Version Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| childIds | String collection | Dependent child settings to this group of settings. Inherited from [deviceManagementConfigurationSettingGroupDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupdefinition?view=graph-rest-beta) |
| dependentOn | [deviceManagementConfigurationDependentOn](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationdependenton?view=graph-rest-beta) collection | List of Dependencies for the setting group Inherited from [deviceManagementConfigurationSettingGroupDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupdefinition?view=graph-rest-beta) |
| dependedOnBy | [deviceManagementConfigurationSettingDependedOnBy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdependedonby?view=graph-rest-beta) collection | List of child settings that depend on this setting Inherited from [deviceManagementConfigurationSettingGroupDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupdefinition?view=graph-rest-beta) |
| maximumCount | Int32 | Maximum number of setting group count in the collection. Valid values 1 to 100 |
| minimumCount | Int32 | Minimum number of setting group count in the collection. Valid values 1 to 100 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSettingGroupCollectionDefinition",
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
  "version": "String",
  "childIds": [
    "String"
  ],
  "dependentOn": [
    {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationDependentOn",
      "dependentOn": "String",
      "parentSettingId": "String"
    }
  ],
  "dependedOnBy": [
    {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingDependedOnBy",
      "dependedOnBy": "String",
      "required": true
    }
  ],
  "maximumCount": 1024,
  "minimumCount": 1024
}
```
