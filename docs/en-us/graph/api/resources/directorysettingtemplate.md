<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/directorysettingtemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-08 -->

# directorySettingTemplate resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Directory setting templates represent system-defined settings available to the tenant. [Directory settings](https://learn.microsoft.com/en-us/graph/api/resources/directorysetting?view=graph-rest-beta) can be created based on the available **directorySettingTemplates**, and values changed from their preset defaults. Directory setting templates can't be created, updated, or deleted. These settings can represent tenant-wide settings, or can represent specific entity settings. Currently, the only templates available for groups apply to Microsoft 365 groups, and include settings such as whether users can create groups or invite guests from outside the organization to become members of a group.

For more information about the Microsoft 365 groups-specific settings, see [group \(directory\) settings](https://learn.microsoft.com/en-us/graph/group-directory-settings).

Tip

The `/v1.0` version of this resource is named [groupSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0&preserve-view=true).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/directorysettingtemplate-get?view=graph-rest-beta) | [directorySettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/directorysettingtemplate?view=graph-rest-beta) | Read the specific properties of one of the system defined directorySettingTemplate objects. |
| [List](https://learn.microsoft.com/en-us/graph/api/directorysettingtemplate-list?view=graph-rest-beta) | [Collection of directorySettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/directorysettingtemplate?view=graph-rest-beta) | List all of the system defined directorySettingTemplate objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | string | Description of the template. Read-only. |
| displayName | string | Display name of the template. Read-only. |
| id | string | Unique identifier for the template. Read-only. |
| values | [settingTemplateValue](https://learn.microsoft.com/en-us/graph/api/resources/settingtemplatevalue?view=graph-rest-beta) collection | Collection of settingTemplateValues that list the set of available settings, defaults, and types that make up this template. Read-only. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "string",
  "displayName": "string",
  "id": "string (identifier)",
  "values": [{"@odata.type": "microsoft.graph.settingTemplateValue"}]
}
```
