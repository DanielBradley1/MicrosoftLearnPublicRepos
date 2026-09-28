<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookicon?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# workbookIcon resource type

Namespace: microsoft.graph

Represents an icon in a cell in an Excel workbook.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/icon-get?view=graph-rest-1.0) | [workbookIcon](https://learn.microsoft.com/en-us/graph/api/resources/workbookicon?view=graph-rest-1.0) | Read the properties and relationships of a workbookIcon object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/icon-update?view=graph-rest-1.0) | [workbookIcon](https://learn.microsoft.com/en-us/graph/api/resources/workbookicon?view=graph-rest-1.0) | Update a workbookIcon object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| index | int | The index of the icon in the given set. |
| set | string | The set that the icon is part of. The possible values are: `Invalid`, `ThreeArrows`, `ThreeArrowsGray`, `ThreeFlags`, `ThreeTrafficLights1`, `ThreeTrafficLights2`, `ThreeSigns`, `ThreeSymbols`, `ThreeSymbols2`, `FourArrows`, `FourArrowsGray`, `FourRedToBlack`, `FourRating`, `FourTrafficLights`, `FiveArrows`, `FiveArrowsGray`, `FiveRating`, `FiveQuarters`, `ThreeStars`, `ThreeTriangles`, `FiveBoxes`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "index": "int",
  "set": "string"
}
```
