<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-04 -->

# sitePage resource type

Namespace: microsoft.graph

This resource represents a page in the sitePages [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). It contains the title, layout, and a collection of [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0)s.

Inherits from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/sitepage-list?view=graph-rest-1.0) | [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) collection | Get a list of the [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/sitepage-create?view=graph-rest-1.0) | [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) | Create a new [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/sitepage-get?view=graph-rest-1.0) | [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) | Read the properties and relationships of a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/sitepage-update?view=graph-rest-1.0) | [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) | Update the properties of a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/basesitepage-delete?view=graph-rest-1.0) | None | Deletes a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) object. |
| [Publish](https://learn.microsoft.com/en-us/graph/api/sitepage-publish?view=graph-rest-1.0) | None | Publish a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) object. |
| [Get by position](https://learn.microsoft.com/en-us/graph/api/sitepage-getwebpartsbyposition?view=graph-rest-1.0) | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) collection | Get a collection of [WebPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) by providing [webPartPosition](https://learn.microsoft.com/en-us/graph/api/resources/webpartposition?view=graph-rest-1.0) information. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentType | [contentTypeInfo](https://learn.microsoft.com/en-us/graph/api/resources/contenttypeinfo?view=graph-rest-1.0) | The content type of this item. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the creator of this item. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time the item was created. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| description | String | The descriptive text for the item. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| eTag | String | ETag for the item. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| id | String | The unique identifier of the item. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | TIdentity of the last modifier of this item. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time the item was last modified. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| name | String | The name of the item. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| pageLayout | [pageLayoutType](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0#pagelayouttype-values) | The name of the page layout of the page. The possible values are: `microsoftReserved`, `article`, `home`, `unknownFutureValue`. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| parentReference | [itemReference](https://learn.microsoft.com/en-us/graph/api/resources/itemreference?view=graph-rest-1.0) | Parent information, if the item has a parent. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| promotionKind | [pagePromotionType](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0#pagepromotiontype-values) | Indicates the promotion kind of the sitePage. The possible values are: `microsoftReserved`, `page`, `newsPost`, `unknownFutureValue`. |
| publishingState | [publicationFacet](https://learn.microsoft.com/en-us/graph/api/resources/publicationfacet?view=graph-rest-1.0) | The publishing status and the MM.mm version of the page. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| reactions | [reactionsFacet](https://learn.microsoft.com/en-us/graph/api/resources/reactionsfacet?view=graph-rest-1.0) | Reactions information for the page. |
| showComments | Boolean | Determines whether or not to show comments at the bottom of the page. |
| showRecommendedPages | Boolean | Determines whether or not to show recommended pages at the bottom of the page. |
| thumbnailWebUrl | String | Url of the sitePage's thumbnail image |
| title | String | Title of the sitePage. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| titleArea | [titleArea](https://learn.microsoft.com/en-us/graph/api/resources/titlearea?view=graph-rest-1.0) | Title area on the SharePoint page. |
| webUrl | String | URL that displays the resource in the browser. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |

### pagePromotionType values

| Value | Description |
| --- | --- |
| `microsoftReserved` | The page is a special type, reserved for use by Microsoft only. This value cannot be used when creating the page with [Create sitePage](https://learn.microsoft.com/en-us/graph/api/sitepage-create?view=graph-rest-1.0) method. |
| `page` | The page is promoted as a normal page |
| `newsPost` | The page is promoted as a news post |
| `unknownFutureValue` | Marker value for future compatibility. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| canvasLayout | [canvasLayout](https://learn.microsoft.com/en-us/graph/api/resources/canvaslayout?view=graph-rest-1.0) | Indicates the layout of the content in a given SharePoint page, including horizontal sections and vertical sections. |
| createdByUser | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | Identity of the creator of this item. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| lastModifiedByUser | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | Identity of the last modifier of this item. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0). |
| webParts | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) collection | Collection of webparts on the SharePoint page. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sitePage",
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
  "promotionKind": "String",
  "publishingState": {
    "@odata.type": "microsoft.graph.publicationFacet"
  },
  "reactions": {
    "@odata.type": "microsoft.graph.reactionsFacet"
  },
  "showComments": "Boolean",
  "showRecommendedPages": "Boolean",
  "thumbnailWebUrl": "String",
  "titleArea": {
    "@odata.type": "microsoft.graph.titleArea"
  }
}
```
