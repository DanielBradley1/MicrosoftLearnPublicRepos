<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# verticalSection resource type

Namespace: microsoft.graph

Represents the vertical section in a given SharePoint page.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/webpart-list?view=graph-rest-1.0) | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) Collection | Get a list of web parts associated with a [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/sitepage-post-verticalsection?view=graph-rest-1.0) | [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) | Create a new [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/verticalsection-get?view=graph-rest-1.0) | [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) | Read the properties and relationships of a [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/verticalsection-update?view=graph-rest-1.0) | [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) | Update the properties of a [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/verticalsection-delete?view=graph-rest-1.0) | [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) | Delete a [verticalSection](https://learn.microsoft.com/en-us/graph/api/resources/verticalsection?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emphasis | [sectionEmphasisType](https://learn.microsoft.com/en-us/graph/api/resources/horizontalsection?view=graph-rest-1.0#sectionemphasistype-values) | Enumeration value that indicates the emphasis of the section background. The possible values are: `none`, `netural`, `soft`, `strong`, `unknownFutureValue`. |
| id | String | Unique identifier of the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| webparts | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) collection | The set of web parts in this section. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verticalSection",
  "id": "String (identifier)",
  "emphasis": "String"
}
```
