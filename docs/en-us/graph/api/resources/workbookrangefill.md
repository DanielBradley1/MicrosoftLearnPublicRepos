<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookrangefill?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# workbookRangeFill resource type

Namespace: microsoft.graph

Represents the background of a range object.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/rangefill-get?view=graph-rest-1.0) | [workbookRangeFill](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangefill?view=graph-rest-1.0) | Read the properties and relationships of a workbookRangeFill object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/rangefill-update?view=graph-rest-1.0) | [workbookRangeFill](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangefill?view=graph-rest-1.0) | Update a workbookRangeFill object. |
| [Clear](https://learn.microsoft.com/en-us/graph/api/rangefill-clear?view=graph-rest-1.0) | None | Reset the range background. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| color | string | HTML color code representing the color of the border line. Can either be of the form #RRGGBB, for example "FFA500", or be a named HTML color, for example "orange". |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "color": "string"
}
```
