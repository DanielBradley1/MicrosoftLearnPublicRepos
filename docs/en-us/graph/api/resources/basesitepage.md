<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-04 -->

# baseSitePage resource type

Namespace: microsoft.graph

An abstract type that represents a page in the site page library.

Inherits from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/basesitepage-list?view=graph-rest-1.0) | [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0) collection | Get the collection of [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0) objects from the site pages [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/basesitepage-get?view=graph-rest-1.0) | [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0) | Get the metadata for a [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0) in the site pages [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/basesitepage-delete?view=graph-rest-1.0) | None | Delete a [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentType | [contentTypeInfo](https://learn.microsoft.com/en-us/graph/api/resources/contenttypeinfo?view=graph-rest-1.0) | The content type of this item. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the creator of this item. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time the item was created. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| description | String | The descriptive text for the item. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| eTag | String | ETag for the item. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| id | String | The unique identifier of the item. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the last modifier of this item. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time the item was last modified. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| name | String | The name of the item. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| pageLayout | [pageLayoutType](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0#pagelayouttype-values) | The name of the page layout of the page. The possible values are: `microsoftReserved`, `article`, `home`, `unknownFutureValue`. |
| parentReference | [itemReference](https://learn.microsoft.com/en-us/graph/api/resources/itemreference?view=graph-rest-1.0) | Parent information, if the item has a parent. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| publishingState | [publicationFacet](https://learn.microsoft.com/en-us/graph/api/resources/publicationfacet?view=graph-rest-1.0) | The publishing status and the MM.mm version of the page. |
| title | String | Title of the sitePage. |
| webUrl | String | URL that displays the resource in the browser. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |

### pageLayoutType values

| Value | Description |
| --- | --- |
| microsoftReserved | The page is a special type reserved for Microsoft use only. |
| article | The page is an article page. |
| home | The page is a home page. |
| unknownFutureValue | Marker value for future compatibility. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| createdByUser | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | Identity of the creator of this item. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0) |
| lastModifiedByUser | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | Identity of the last modifier of this item. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.baseSitePage",
  "id": "String (identifier)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "contentType": {
    "@odata.type": "microsoft.graph.contentTypeInfo"
  },
  "description": "String",
  "eTag": "String",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "name": "String",
  "parentReference": {
    "@odata.type": "microsoft.graph.itemReference"
  },
  "webUrl": "String",
  "title": "String",
  "pageLayout": "String",
  "publishingState": {
    "@odata.type": "microsoft.graph.publicationFacet"
  }
}
```
