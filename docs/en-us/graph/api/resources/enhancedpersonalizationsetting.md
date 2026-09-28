<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/enhancedpersonalizationsetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-06-17 -->

# enhancedPersonalizationSetting resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a setting that controls whether Microsoft 365 Copilot can use features that enhance its personalization capabilities. If enabled multiple features contributing to deeper personalization are enabled. For more information, see [control enhanced personalization privacy](https://learn.microsoft.com/en-us/graph/control-enhanced-personalization-privacy).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/enhancedpersonalizationsetting-get?view=graph-rest-beta) | [enhancedPersonalizationSetting](https://learn.microsoft.com/en-us/graph/api/resources/enhancedpersonalizationsetting?view=graph-rest-beta) | Read the properties and relationships of an enhancedPersonalizationSetting object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/enhancedpersonalizationsetting-update?view=graph-rest-beta) | [enhancedPersonalizationSetting](https://learn.microsoft.com/en-us/graph/api/resources/enhancedpersonalizationsetting?view=graph-rest-beta) | Update the properties of an enhancedPersonalizationSetting object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| disabledForGroup | String | The ID of a Microsoft Entra group to which the value is used to disable the control for populated users. The default value is `null`. This parameter is optional. |
| isEnabledInOrganization | Boolean | If true, enables the enhanced personalization control and therefore related features as defined in [control enhanced personalization privacy](https://learn.microsoft.com/en-us/graph/control-enhanced-personalization-privacy) |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.enhancedPersonalizationSetting",
  "isEnabledInOrganization": "Boolean",
  "disabledForGroup": "String"
}
```
