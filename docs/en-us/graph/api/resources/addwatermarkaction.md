<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/addwatermarkaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# addWatermarkAction resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Represents an action that specifies the details on the content watermark to be added to the information, if applicable.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| fontColor | String | Color of the font to use for the watermark. |
| fontName | String | Name of the font to use for the watermark. |
| fontSize | Int32 | Font size to use for the watermark. |
| layout | String | The possible values are: `horizontal`, `diagonal`. |
| text | String | The contents of the watermark itself. |
| uiElementName | String | The name of the UI element where the watermark should be placed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "fontColor": "String",
  "fontName": "String",
  "fontSize": 1024,
  "layout": "String",
  "text": "String",
  "uiElementName": "String"
}
```
