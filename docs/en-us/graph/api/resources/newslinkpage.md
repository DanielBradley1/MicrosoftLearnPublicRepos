<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-04 -->

# newsLinkPage resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a news link page in a site pages [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-beta).

Inherits from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/newslinkpage-list?view=graph-rest-beta) | [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) collection | Get a list of the [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/newslinkpage-create?view=graph-rest-beta) | [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) | Create a new [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) in the site pages [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-beta) of a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-beta). |
| [Get](https://learn.microsoft.com/en-us/graph/api/newslinkpage-get?view=graph-rest-beta) | [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) | Get the metadata of a [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) in the site pages [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-beta) of a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-beta). |
| [Update](https://learn.microsoft.com/en-us/graph/api/newslinkpage-update?view=graph-rest-beta) | [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) | Update the properties of a [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/basesitepage-delete?view=graph-rest-beta) | None | Delete a [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) object. |
| [Publish](https://learn.microsoft.com/en-us/graph/api/newslinkpage-publish?view=graph-rest-beta) | None | Publish the latest version of a [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) resource that makes the version available to all users. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bannerImageWebUrl | String | A link to the banner image for the **newsLinkPage**. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the creator of this **newsLinkPage**. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the **newsLinkPage** was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| description | String | The descriptive text for the **newsLinkPage**. The maximum length limit is 250 characters. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| eTag | String | ETag for the **newsLinkPage**. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| id | String | The unique identifier of the **newsLinkPage**. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the last modifier of this **newsLinkPage**. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the **newsLinkPage** was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| name | String | The name of the **newsLinkPage**. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| newsSharepointIds | [sharepointIds](https://learn.microsoft.com/en-us/graph/api/resources/sharepointids?view=graph-rest-beta) | The SharePoint IDs of the referenced news article if it's recognized as a SharePoint resource. Read-only. |
| newsWebUrl | String | The URL of the news article referenced by the **newsLinkPage**. It can be an external link. |
| pageLayout | [pageLayoutType](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta#pagelayouttype-values) | The name of the page layout of the page. The possible values are: `microsoftReserved`, `article`, `home`, `unknownFutureValue`, `newsLink`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this evolvable enum: `newsLink`. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| parentReference | [itemReference](https://learn.microsoft.com/en-us/graph/api/resources/itemreference?view=graph-rest-beta) | Parent information if the **newsLinkPage** has a parent. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| publishingState | [publicationFacet](https://learn.microsoft.com/en-us/graph/api/resources/publicationfacet?view=graph-rest-beta) | The publishing status and the version of the page. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| title | String | Title of the **newsLinkPage**. The maximum length limit is 110 characters. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| webUrl | String | URL that displays the resource in the browser. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |

### Instance attributes

Instance attributes are properties with special behaviors. These properties are temporary and either a\) define behavior the service should perform or b\) provide short-term property values, like a download URL for an item that expires.

| Property name | Type | Description |
| :--- | :--- | :--- |
| @microsoft.graph.bannerImageWebUrlContent | String | This annotation is used to send the image content in a multipart request. |
| @microsoft.graph.bannerImageWebUrlContentError | String | If a failure occurs when you upload or persist the banner image during a **newsLinkPage** creation, the response contains `@microsoft.graph.bannerImageWebUrlContentError` that provides details about the error. |

For a POST request example, see [Create newsLinkPage](https://learn.microsoft.com/en-us/graph/api/newslinkpage-create?view=graph-rest-beta).

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| createdByUser | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) | Identity of the user who created the **newsLinkPage**. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| lastModifiedByUser | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) | Identity of the user who last modified the **newsLinkPage**. Read-only. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.newsLinkPage",
  "bannerImageWebUrl": "String",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "eTag": "String",
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "name": "String",
  "newsSharepointIds": {"@odata.type": "microsoft.graph.sharepointIds"},
  "newsWebUrl": "String",
  "pageLayout": "String",
  "parentReference": {"@odata.type": "microsoft.graph.itemReference"},
  "publishingState": {"@odata.type": "microsoft.graph.publicationFacet"},
  "title": "String",
  "webUrl": "String"
}
```
