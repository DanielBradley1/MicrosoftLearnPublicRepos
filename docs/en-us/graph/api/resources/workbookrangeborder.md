<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeborder?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# workbookRangeBorder resource type

Namespace: microsoft.graph

Represents the border of an object.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rangeborder-list?view=graph-rest-1.0) | [workbookRangeBorder](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeborder?view=graph-rest-1.0) collection | Get rangeBorder object collection. |
| [Get](https://learn.microsoft.com/en-us/graph/api/rangeborder-get?view=graph-rest-1.0) | [workbookRangeBorder](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeborder?view=graph-rest-1.0) | Read properties and relationships of rangeBorder object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/rangeborder-update?view=graph-rest-1.0) | [workbookRangeBorder](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeborder?view=graph-rest-1.0) | Update RangeBorder object. |
| [Get range border at](https://learn.microsoft.com/en-us/graph/api/rangebordercollection-itemat?view=graph-rest-1.0) | [workbookRangeBorder](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeborder?view=graph-rest-1.0) | Gets a border object using its index |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| color | string | The HTML color code that represents the color of the border line. Can either be of the form #RRGGBB, for example "FFA500", or a named HTML color, for example "orange". |
| id | string | The border identifier. The possible values are: `EdgeTop`, `EdgeBottom`, `EdgeLeft`, `EdgeRight`, `InsideVertical`, `InsideHorizontal`, `DiagonalDown`, `DiagonalUp`. Read-only. |
| sideIndex | string | Indicates the specific side of the border. The possible values are: `EdgeTop`, `EdgeBottom`, `EdgeLeft`, `EdgeRight`, `InsideVertical`, `InsideHorizontal`, `DiagonalDown`, `DiagonalUp`. Read-only. |
| style | string | Indicates the line style for the border. The possible values are: `None`, `Continuous`, `Dash`, `DashDot`, `DashDotDot`, `Dot`, `Double`, `SlantDashDot`. |
| weight | string | The weight of the border around a range. The possible values are: `Hairline`, `Thin`, `Medium`, `Thick`. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "color": "string",
  "id": "string",
  "sideIndex": "string",
  "style": "string",
  "weight": "string"
}
```
