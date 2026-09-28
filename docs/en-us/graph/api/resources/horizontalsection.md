<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# horizontalSection resource type

Namespace: microsoft.graph

Represents a horizontal section in a given SharePoint page.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/horizontalsection-list?view=graph-rest-1.0) | [horizontalSection](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0) collection | Get a list of the [horizontalSection](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/sitepage-post-horizontalsection?view=graph-rest-1.0) | [horizontalSection](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0) | Create a new [horizontalSection](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/horizontalsection-get?view=graph-rest-1.0) | [horizontalSection](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0) | Read the properties and relationships of a [horizontalSection](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/horizontalsection-update?view=graph-rest-1.0) | [horizontalSection](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0) | Update the properties of a [horizontalSection](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/horizontalsection-delete?view=graph-rest-1.0) | [horizontalSection](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0) | Delete a [horizontalSection](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emphasis | [sectionEmphasisType](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0#sectionemphasistype-values) | Enumeration value that indicates the emphasis of the section background. The possible values are: `none`, `netural`, `soft`, `strong`, `unknownFutureValue`. |
| id | String | Unique identifier of the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| layout | [horizontalSectionLayoutType](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0#horizontalsectionlayouttype-values) | Layout type of the section. The possible values are: `none`, `oneColumn`, `twoColumns`, `threeColumns`, `oneThirdLeftColumn`, `oneThirdRightColumn`, `fullWidth`, `unknownFutureValue`. |

### sectionEmphasisType values

| Member | Description |
| :--- | :--- |
| none | The section has no background. |
| neutral | The section has a neutral emphasis in the background. |
| soft | The section has a soft emphasis in the background. |
| strong | The section has a strong emphasis in the background. |
| unknownFutureValue | Marker value for future compatibility. |

### horizontalSectionLayoutType values

| Member | Description |
| :--- | :--- |
| none | The section has no layout. |
| oneColumn | The section has only one column. |
| twoColumns | The section has two columns. |
| threeColumns | The section has three columns. |
| oneThirdLeftColumn | The section has a 1/3 column on the left and 2/3 column on the right. |
| oneThirdRightColumn | The section has a 2/3 column on the left and 1/3 column on the right. |
| fullWidth | The section has one full width column. |
| unknownFutureValue | Marker value for future compatibility. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| columns | [horizontalSectionColumn](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsectioncolumn?view=graph-rest-1.0) collection | The set of vertical columns in this section. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.horizontalSection",
  "id": "String (identifier)",
  "layout": "String",
  "emphasis": "String"
}
```
