<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-pluginsetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# pluginSetting resource type

Namespace: microsoft.graph.security.securityCopilot

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the settings for a [plugin](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-plugin?view=graph-rest-beta) in Security Copilot.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| acceptableValues | String collection | Acceptable values for plugin type |
| defaultValue | String | Default value available for the plugin if not configured |
| description | String | Description of the value requested |
| displayType | microsoft.graph.security.securityCopilot.pluginSettingDisplayType | Display type available any user experience if required. The possible values are: `none`, `textbox`, `checkbox`, `dropdown`, `unknownFutureValue`. |
| hintText | String | Hint for the plugin |
| isRequired | Boolean | Setting whether the value is required |
| label | String | Label for the setting |
| name | String | Name of the setting |
| settingValue | microsoft.graph.security.securityCopilot.pluginSettingType | Available setting values. The possible values are: `string`, `bool`, `array`, `enum`, `secretString`, `unknownFutureValue`. |
| value | String | Value |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.securityCopilot.pluginSetting",
  "name": "String",
  "label": "String",
  "description": "String",
  "hintText": "String",
  "settingValue": "String",
  "isRequired": "Boolean",
  "defaultValue": "String",
  "value": "String",
  "acceptableValues": [
    "String"
  ],
  "displayType": "String"
}
```
