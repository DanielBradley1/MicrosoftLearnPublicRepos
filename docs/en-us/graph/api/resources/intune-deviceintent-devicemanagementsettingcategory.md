<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementSettingCategory resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity representing a setting category

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementSettingCategories](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementsettingcategory-list?view=graph-rest-beta) | [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta) objects. |
| [Get deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementsettingcategory-get?view=graph-rest-beta) | [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta) object. |
| [Create deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementsettingcategory-create?view=graph-rest-beta) | [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta) | Create a new [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta) object. |
| [Delete deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementsettingcategory-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta). |
| [Update deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementsettingcategory-update?view=graph-rest-beta) | [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta) | Update the properties of a [deviceManagementSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcategory?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The category ID |
| displayName | String | The category name |
| hasRequiredSetting | Boolean | The category contains top level required setting |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| settingDefinitions | [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) collection | The setting definitions this category contains |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementSettingCategory",
  "id": "String (identifier)",
  "displayName": "String",
  "hasRequiredSetting": true
}
```
