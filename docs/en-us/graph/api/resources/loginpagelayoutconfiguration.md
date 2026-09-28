<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/loginpagelayoutconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# loginPageLayoutConfiguration resource type

Namespace: microsoft.graph

Contains details of the layout of the sign-in page for a tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| layoutTemplateType | layoutTemplateType | Represents the layout template to be displayed on the login page for a tenant. The possible values are<br><br>- `default` - Represents the default Microsoft layout with a centered lightbox.<br>- `verticalSplit` - Represents a layout with a background on the left side and a full-height lightbox to the right.<br>- `unknownFutureValue` - Evolvable enumeration sentinel value. Don't use. |
| isHeaderShown | Boolean | Option to show the header on the sign-in page. |
| isFooterShown | Boolean | Option to show the footer on the sign-in page. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.loginPageLayoutConfiguration",
  "layoutTemplateType": "String",
  "isHeaderShown": "Boolean",
  "isFooterShown": "Boolean",
}
```
