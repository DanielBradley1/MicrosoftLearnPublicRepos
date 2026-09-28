<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-addcontentheaderaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# addContentHeaderAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action that specifies the details on the content header to be added to the information, if applicable.

Inherits from [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alignment | String | The horizontal alignment of the header. |
| fontColor | String | Color of the font to use for the header. |
| fontName | String | Name of the font to use for the header. |
| fontSize | Int32 | Font size to use for the header. |
| margin | Int32 | The margin of the header from the top of the document. |
| text | String | The contents of the header itself. |
| uiElementName | String | The name of the UI element where the header should be placed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.addContentHeaderAction",
  "alignment": "String",
  "fontColor": "String",
  "fontName": "String",
  "fontSize": "Integer",
  "margin": "Integer",
  "text": "String",
  "uiElementName": "String"
}
```
