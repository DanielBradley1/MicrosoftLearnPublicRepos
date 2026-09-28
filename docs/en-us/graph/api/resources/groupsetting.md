<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-08 -->

# groupSetting resource type

Namespace: microsoft.graph

Group settings define the configurations that can be used to customize the tenant-wide and object-specific restrictions and allowed behavior. For examples, you can block word lists for group display names or define whether guests are allowed to be group owners.

By default, all groups inherit the preset defaults. To change the default settings, you must create a new settings object using the [groupSettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0). When the same setting is defined at both the tenant-wide and to a specific group, the group-level setting overrides the tenant-wide setting. For example, the tenant-wide setting might allow existing members of groups to invite guests; but an individual group setting can override and not allow the operation.

Group-specific settings apply to only Microsoft 365 groups.

Tip

The `/beta` version of this resource is named [directorySetting](https://learn.microsoft.com/en-us/graph/api/resources/directorysetting?view=graph-rest-beta&preserve-view=true).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/group-list-settings?view=graph-rest-1.0) | [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) collection | List properties of all setting objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/group-post-settings?view=graph-rest-1.0) | [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) | Create a setting object based on a **groupSettingTemplate**. |
| [Get](https://learn.microsoft.com/en-us/graph/api/groupsetting-get?view=graph-rest-1.0) | [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) | Read properties of a specific setting object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/groupsetting-update?view=graph-rest-1.0) | [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) | Update the setting object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/groupsetting-delete?view=graph-rest-1.0) | None | Delete a setting object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of this group of settings, which comes from the associated template. |
| id | String | Unique identifier for these settings. Read-only. |
| templateId | String | Unique identifier for the tenant-level [groupSettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0) object that's been customized for this group-level settings object. Read-only. |
| values | [settingValue](https://learn.microsoft.com/en-us/graph/api/resources/settingvalue?view=graph-rest-1.0) collection | Collection of name-value pairs corresponding to the **name** and **defaultValue** properties in the referenced [groupSettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0) object. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "id": "String (identifier)",
  "templateId": "String",
  "values": [{ "@odata.type": "microsoft.graph.settingValue" }]
}
```
