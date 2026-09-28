<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-04 -->

# pageTemplate resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a page template in the templates folder.

In addition to other properties, a **pageTemplate** resource contains the title, layout, and a collection of [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-beta) objects.

Inherits from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/pagetemplate-list?view=graph-rest-beta) | [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) | Get a list of the [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/pagetemplate-create?view=graph-rest-beta) | [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) | Create a new [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/pagetemplate-get?view=graph-rest-beta) | [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) | Get a [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) object and properties. |
| [Update](https://learn.microsoft.com/en-us/graph/api/pagetemplate-update?view=graph-rest-beta) | [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) | Update the properties of a [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/pagetemplate-delete?view=graph-rest-beta) | None | Delete a [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentType | [contentTypeInfo](https://learn.microsoft.com/en-us/graph/api/resources/contenttypeinfo?view=graph-rest-beta) | The content type of the page template. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the creator of the page template. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time the page template was created. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| description | String | The descriptive text for the page template. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| eTag | String | The eTag for the page template. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| id | String | The unique identifier of the page template. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the last modifier of the page template. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time the page template was last modified. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| name | String | The name of the page template. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| pageLayout | [pageLayoutType](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta#pagelayouttype-values) | The type of the page layout for the page. The possible values are: `microsoftReserved`, `article`, `home`, `unknownFutureValue`, `newsLink`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `newsLink`. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| parentReference | [itemReference](https://learn.microsoft.com/en-us/graph/api/resources/itemreference?view=graph-rest-beta) | The parent information, if the page template has a parent. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| publishingState | [publicationFacet](https://learn.microsoft.com/en-us/graph/api/resources/publicationfacet?view=graph-rest-beta) | The publishing status and the MM.mm version of the page template. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| thumbnailWebUrl | String | The URL of the page template's thumbnail image |
| title | String | The title of the page template. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| titleArea | [titleArea](https://learn.microsoft.com/en-us/graph/api/resources/titlearea?view=graph-rest-beta) | The title area on the SharePoint page template. |
| webUrl | String | The URL that displays the page template in the browser. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| canvasLayout | [canvasLayout](https://learn.microsoft.com/en-us/graph/api/resources/canvaslayout?view=graph-rest-beta) | The layout of the content in a given SharePoint page template, including horizontal sections and vertical sections. |
| createdByUser | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) | The identity of the user who created this site page template. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| lastModifiedByUser | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) | The identity of the last modifier of this item. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| webParts | [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-beta) collection | The collection of web parts on the SharePoint page. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.pageTemplate",
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
  },
  "thumbnailWebUrl": "String",
  "titleArea": {
    "@odata.type": "microsoft.graph.titleArea"
  }
}
```
