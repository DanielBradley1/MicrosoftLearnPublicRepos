<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-08 -->

# groupSettingTemplate resource type

Namespace: microsoft.graph

Group setting templates represent system-defined settings available to the tenant. [Group settings](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) can be created based on the available **groupSettingTemplates**, and values changed from their preset defaults. Group setting templates cannot be created, updated or deleted. These settings can represent tenant-wide settings, or can represent specific group settings. Currently, the only templates available for groups apply to Microsoft 365 groups, and include settings such as whether users can create groups or invite guests from outside the organization to become members of a group.

For more information about the Microsoft 365 groups-specific settings, see [group \(directory\) settings](https://learn.microsoft.com/en-us/graph/group-directory-settings).

Tip

The `/beta` version of this resource is named [directorySettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/directorysettingtemplate?view=graph-rest-beta&preserve-view=true).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/groupsettingtemplate-get?view=graph-rest-1.0) | [groupSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0) | Read the specific properties of one of the system defined groupSettingTemplate objects. |
| [List](https://learn.microsoft.com/en-us/graph/api/groupsettingtemplate-list?view=graph-rest-1.0) | [Collection of groupSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0) | List all of the system defined groupSettingTemplate objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description of the template. |
| displayName | String | Display name of the template. The template named `Group.Unified` can be used to configure tenant-wide Microsoft 365 group settings, while the template named `Group.Unified.Guest` can be used to configure group-specific settings. |
| id | String | Unique identifier for the template. Read-only. |
| values | [settingTemplateValue](https://learn.microsoft.com/en-us/graph/api/resources/settingtemplatevalue?view=graph-rest-1.0) collection | Collection of settingTemplateValues that list the set of available settings, defaults and types that make up this template. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "values": [{ "@odata.type": "microsoft.graph.settingTemplateValue" }]
}
```
