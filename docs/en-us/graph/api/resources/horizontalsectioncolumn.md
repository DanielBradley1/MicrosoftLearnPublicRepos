<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/horizontalsectioncolumn?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# horizontalSectionColumn resource type

Namespace: microsoft.graph

Represents a vertical column in a given horizontal section.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List horizontalSectionColumns](https://learn.microsoft.com/en-us/graph/api/horizontalsectioncolumn-list?view=graph-rest-1.0) | [horizontalSectionColumn](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsectioncolumn?view=graph-rest-1.0) collection | Get a list of the [horizontalSectionColumn](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsectioncolumn?view=graph-rest-1.0) objects and their properties. |
| [Get horizontalSectionColumn](https://learn.microsoft.com/en-us/graph/api/horizontalsectioncolumn-get?view=graph-rest-1.0) | [horizontalSectionColumn](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsectioncolumn?view=graph-rest-1.0) | Read the properties and relationships of a [horizontalSectionColumn](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsectioncolumn?view=graph-rest-1.0) object. |
| [List webParts](https://learn.microsoft.com/en-us/graph/api/webpart-list?view=graph-rest-1.0) | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) Collection | Get a list of webparts associated with a [horizontalSectionColumn](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsectioncolumn?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| width | Int32 | Width of the column. A horizontal section is divided into 12 grids. A column should have a value of 1-12 to represent its range spans. For example, there can be two columns both have a width of 6 in a section. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| webparts | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) collection | The collection of WebParts in this column. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.horizontalSectionColumn",
  "id": "String (identifier)",
  "width": "Integer"
}
```
