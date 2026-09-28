<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# deviceManagementConfigurationRedirectSettingDefinition resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Not yet documented

Inherits from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementConfigurationRedirectSettingDefinitions](https://learn.microsoft.com/en-us/graph/api/intune-mam-devicemanagementconfigurationredirectsettingdefinition-list?view=graph-rest-beta) | [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta) objects. |
| [Get deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-mam-devicemanagementconfigurationredirectsettingdefinition-get?view=graph-rest-beta) | [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta) object. |
| [Create deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-mam-devicemanagementconfigurationredirectsettingdefinition-create?view=graph-rest-beta) | [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta) | Create a new [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta) object. |
| [Delete deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-mam-devicemanagementconfigurationredirectsettingdefinition-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta). |
| [Update deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-mam-devicemanagementconfigurationredirectsettingdefinition-update?view=graph-rest-beta) | [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta) | Update the properties of a [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicability | [deviceManagementConfigurationSettingApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingapplicability?view=graph-rest-beta) | Details which device setting is applicable on Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| accessTypes | [deviceManagementConfigurationSettingAccessTypes](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingaccesstypes?view=graph-rest-beta) | Read/write access mode of the setting Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `none`, `add`, `copy`, `delete`, `get`, `replace`, `execute`. |
| keywords | String collection | Tokens which to search settings on Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| infoUrls | String collection | List of links more info for the setting can be found at Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| occurrence | [deviceManagementConfigurationSettingOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingoccurrence?view=graph-rest-beta) | Indicates whether the setting is required or not Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| baseUri | String | Base CSP Path Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| offsetUri | String | Offset CSP Path from Base Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| rootDefinitionId | String | Root setting definition if the setting is a child setting. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| categoryId | String | Specifies the area group under which the setting is configured in a specified configuration service provider \(CSP\) Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| settingUsage | [deviceManagementConfigurationSettingUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingusage?view=graph-rest-beta) | Setting type, for example, configuration and compliance Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `none`, `configuration`, `compliance`. |
| uxBehavior | [deviceManagementConfigurationControlType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationcontroltype?view=graph-rest-beta) | Setting control type representation in the UX Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `default`, `dropdown`, `smallTextBox`, `largeTextBox`, `toggle`, `multiheaderGrid`, `contextPane`. |
| visibility | [deviceManagementConfigurationSettingVisibility](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingvisibility?view=graph-rest-beta) | Setting visibility scope to UX Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `none`, `settingsCatalog`, `template`. |
| referredSettingInformationList | [deviceManagementConfigurationReferredSettingInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationreferredsettinginformation?view=graph-rest-beta) collection | List of referred setting information. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| id | String | Identifier for item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| description | String | Description of the item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| helpText | String | Help text of the item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| name | String | Name of the item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| displayName | String | Display name of the item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| version | String | Item Version Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| deepLink | String | A deep link that points to the specific location in the Intune console where feature support must be managed from. |
| redirectMessage | String | A message that explains that clicking the link will redirect the user to a supported page to manage the settings. |
| redirectReason | String | Indicates the reason for redirecting the user to an alternative location in the console. For example: WiFi profiles are not supported in the settings catalog and must be created with a template policy. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationRedirectSettingDefinition",
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
  "version": "String",
  "deepLink": "String",
  "redirectMessage": "String",
  "redirectReason": "String"
}
```
