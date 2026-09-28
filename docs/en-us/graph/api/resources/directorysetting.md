<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/directorysetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-08 -->

# directorySetting resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Directory settings define the configurations that can be used to customize the tenant-wide and object-specific restrictions and allowed behavior. For examples, you can block word lists for group display names or define whether guests are allowed to be group owners.

By default, all entities inherit the preset defaults. To change the default settings, you must create a new settings object using the [directorySettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/directorysettingtemplate?view=graph-rest-beta). When the same setting is defined at both the tenant-wide and to a specific group, the entity-level setting overrides the tenant-wide setting. For example, the tenant-wide setting might allow existing members of groups to invite guests; but an individual group setting can override and not allow the operation.

Group-specific settings apply to only Microsoft 365 groups.

Tip

The `/v1.0` version of this resource is named [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0&preserve-view=true).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/group-list-settings?view=graph-rest-beta) | [directorySetting](https://learn.microsoft.com/en-us/graph/api/resources/directorysetting?view=graph-rest-beta) collection | List properties of all setting objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/group-post-settings?view=graph-rest-beta) | [directorySetting](https://learn.microsoft.com/en-us/graph/api/resources/directorysetting?view=graph-rest-beta) | Create a setting object based on a directorySettingTemplate. |
| [Get](https://learn.microsoft.com/en-us/graph/api/directorysetting-get?view=graph-rest-beta) | [directorySetting](https://learn.microsoft.com/en-us/graph/api/resources/directorysetting?view=graph-rest-beta) | Read properties of a specific setting object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/directorysetting-update?view=graph-rest-beta) | [directorySetting](https://learn.microsoft.com/en-us/graph/api/resources/directorysetting?view=graph-rest-beta) | Update a setting object. Only settingValues can be changed in an update. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/directorysetting-delete?view=graph-rest-beta) | None | Delete a setting object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | string | Display name of this group of settings, which comes from the associated template. Read-only. |
| id | string | Unique identifier for these settings. Read-only. |
| templateId | string | Unique identifier for the template used to create this group of settings. Read-only. |
| values | [settingValue](https://learn.microsoft.com/en-us/graph/api/resources/settingvalue?view=graph-rest-beta) collection | Collection of name-value pairs corresponding to the name and defaultValue properties in the referenced [directorySettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/directorysettingtemplate?view=graph-rest-beta) object. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "string",
  "id": "string (identifier)",
  "templateId": "string",
  "values": [{"@odata.type": "microsoft.graph.settingValue"}]
}
```
