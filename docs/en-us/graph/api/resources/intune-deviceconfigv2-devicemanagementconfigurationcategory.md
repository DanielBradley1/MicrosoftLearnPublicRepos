<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcategory?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# deviceManagementConfigurationCategory resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device Management Configuration Policy

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementConfigurationCategories](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationcategory-list?view=graph-rest-beta) | [deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcategory?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcategory?view=graph-rest-beta) objects. |
| [Get deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationcategory-get?view=graph-rest-beta) | [deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcategory?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcategory?view=graph-rest-beta) object. |
| [Create deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationcategory-create?view=graph-rest-beta) | [deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcategory?view=graph-rest-beta) | Create a new [deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcategory?view=graph-rest-beta) object. |
| [Delete deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationcategory-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcategory?view=graph-rest-beta). |
| [Update deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationcategory-update?view=graph-rest-beta) | [deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcategory?view=graph-rest-beta) | Update the properties of a [deviceManagementConfigurationCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcategory?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the category. |
| description | String | Description of the category. For example: Display |
| categoryDescription | String | Description of the category header in policy summary. |
| helpText | String | Help text of the category. Give more details of the category. |
| name | String | Name of the item |
| displayName | String | Name of the category. For example: Device Lock |
| platforms | [deviceManagementConfigurationPlatforms](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationplatforms?view=graph-rest-beta) | Platforms types, which settings in the category have. The possible values are: none. android, androidEnterprise, iOs, macOs, windows10X, windows10, aosp, and linux. If this property is not set, or set to none, returns categories in all platforms. Supports: $filters, $select. Read-only. The possible values are: `none`, `android`, `iOS`, `macOS`, `windows10X`, `windows10`, `linux`, `unknownFutureValue`, `androidEnterprise`, `aosp`, `visionOS`, `tvOS`. |
| technologies | [deviceManagementConfigurationTechnologies](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationtechnologies?view=graph-rest-beta) | Technologies types, which settings in the category have. The possible values are: none, mdm, configManager, intuneManagementExtension, thirdParty, documentGateway, appleRemoteManagement, microsoftSense, exchangeOnline, edgeMam, linuxMdm, extensibility, enrollment, endpointPrivilegeManagement. If this property is not set, or set to none, returns categories in all platforms. Supports: $filters, $select. Read-only. The possible values are: `none`, `mdm`, `windows10XManagement`, `configManager`, `appleRemoteManagement`, `microsoftSense`, `exchangeOnline`, `mobileApplicationManagement`, `linuxMdm`, `extensibility`, `enrollment`, `endpointPrivilegeManagement`, `unknownFutureValue`, `windowsOsRecovery`, `android`. |
| settingUsage | [deviceManagementConfigurationSettingUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingusage?view=graph-rest-beta) | Indicates that the category contains settings that are used for compliance, configuration, or reusable settings. The possible values are: configuration, compliance, reusableSetting. Each setting usage has separate API end-point to call. Read-only. The possible values are: `none`, `configuration`, `compliance`, `unknownFutureValue`, `inventory`. |
| parentCategoryId | String | Direct parent id of the category. If the category is the root, the parent id is same as its id. |
| rootCategoryId | String | Root id of the category. |
| childCategoryIds | String collection | List of child ids of the category. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationCategory",
  "id": "String (identifier)",
  "description": "String",
  "categoryDescription": "String",
  "helpText": "String",
  "name": "String",
  "displayName": "String",
  "platforms": "String",
  "technologies": "String",
  "settingUsage": "String",
  "parentCategoryId": "String",
  "rootCategoryId": "String",
  "childCategoryIds": [
    "String"
  ]
}
```
