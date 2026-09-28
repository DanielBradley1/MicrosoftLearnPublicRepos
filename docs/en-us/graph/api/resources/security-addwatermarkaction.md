<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-addwatermarkaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# addWatermarkAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action that specifies the details on the content watermark to be added to the information, if applicable.

Inherits from [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| fontColor | String | Color of the font to use for the watermark. |
| fontName | String | Name of the font to use for the watermark. |
| fontSize | Int32 | Font size to use for the watermark. |
| layout | String | The layout of the watermark. The possible values are: `horizontal`, `diagonal`. |
| text | String | The contents of the watermark itself. |
| uiElementName | String | The name of the UI element where the watermark should be placed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.addWatermarkAction",
  "fontColor": "String",
  "fontName": "String",
  "fontSize": "Integer",
  "layout": "String",
  "text": "String",
  "uiElementName": "String"
}
```
