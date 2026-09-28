<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/settingtemplatevalue?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-09 -->

# settingTemplateValue resource type

Namespace: microsoft.graph

Represents an individual [template setting definition](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0), including the default value for the setting, if the setting is not instantiated. For more information about supported settings, see [Overview of group settings](https://learn.microsoft.com/en-us/graph/group-directory-settings).

### Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultValue | String | Default value for the setting. |
| description | String | Description of the setting. |
| name | String | Name of the setting. |
| type | String | Type of the setting. |

### JSON representation

The following JSON representation shows the resource type.

```json
{
  "defaultValue": "String",
  "description": "String",
  "name": "String",
  "type": "String"
}
```
