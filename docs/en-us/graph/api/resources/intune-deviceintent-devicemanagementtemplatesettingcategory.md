<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementTemplateSettingCategory resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity representing a template setting category

Inherits from [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementTemplateSettingCategories](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplatesettingcategory-list?view=graph-rest-beta) | [deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory?view=graph-rest-beta) objects. |
| [Get deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplatesettingcategory-get?view=graph-rest-beta) | [deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory?view=graph-rest-beta) object. |
| [Create deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplatesettingcategory-create?view=graph-rest-beta) | [deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory?view=graph-rest-beta) | Create a new [deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory?view=graph-rest-beta) object. |
| [Delete deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplatesettingcategory-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory?view=graph-rest-beta). |
| [Update deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplatesettingcategory-update?view=graph-rest-beta) | [deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory?view=graph-rest-beta) | Update the properties of a [deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The category ID Inherited from [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta) |
| displayName | String | The category name Inherited from [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta) |
| hasRequiredSetting | Boolean | The category contains top level required setting Inherited from [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| settingDefinitions | [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) collection | The setting definitions this category contains Inherited from [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta) |
| recommendedSettings | [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) collection | The settings this category contains |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementTemplateSettingCategory",
  "id": "String (identifier)",
  "displayName": "String",
  "hasRequiredSetting": true
}
```
