<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/loginpagebrandingvisualelement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# loginPageBrandingVisualElement resource type

Namespace: microsoft.graph

Contains details about customizable properties of elements on the login page of the [organization's branding themes](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandingtheme?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customText | String | A string to replace the default visual element text that is displayed on the login page. The text must be in Unicode format. Maximum length: 256. |
| customUrl | String | A custom URL to replace the default URL of the visual element hyperlink. This URL must be in ASCII format or non-ASCII characters must be URL encoded. Maximum length: 128. |
| isHidden | Boolean | Option to hide the visual element on the login page. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.loginPageBrandingVisualElement",
  "customText": "String",
  "customUrl": "String",
  "isHidden": "Boolean"
}
```
