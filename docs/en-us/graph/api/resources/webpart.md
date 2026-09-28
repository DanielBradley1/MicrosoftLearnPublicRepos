<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# webPart resource type

Namespace: microsoft.graph

Represents a specific web part instance on a SharePoint page.

This is an abstract type.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/webpart-list?view=graph-rest-1.0) | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) collection | Get a list of the [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/webpart-get?view=graph-rest-1.0) | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) | Read the properties and relationships of a [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/webpart-delete?view=graph-rest-1.0) | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) | Deletes a [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/sitepage-create-webpart?view=graph-rest-1.0) | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) | Create a new [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/webpart-update?view=graph-rest-1.0) | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) | Update the properties of a [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) object. |
| [Get position](https://learn.microsoft.com/en-us/graph/api/webpart-getposition?view=graph-rest-1.0) | [webPartPosition](https://learn.microsoft.com/en-us/graph/api/resources/webpartposition?view=graph-rest-1.0) | Get the [webPartPosition](https://learn.microsoft.com/en-us/graph/api/resources/webpartposition?view=graph-rest-1.0) information of a [WebPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0). |
| [Get by position](https://learn.microsoft.com/en-us/graph/api/sitepage-getwebpartsbyposition?view=graph-rest-1.0) | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) collection | Get a list of the [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) objects filtered by [webPartPosition](https://learn.microsoft.com/en-us/graph/api/resources/webpartposition?view=graph-rest-1.0) information. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique instance identifier of the web part. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webPart",
  "id": "String (identifier)"
}
```
