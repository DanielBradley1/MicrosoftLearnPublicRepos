<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# browserSharedCookie resource type

Namespace: microsoft.graph

Represents a session cookie for [Internet Explorer mode](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode) that resides on a [site list](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0). Microsoft Edge and Internet Explorer processes use [shared session cookies](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) to allow a streamlined experience when performing tasks such as authentication. For more details, see [Cookie sharing between Microsoft Edge and Internet Explorer](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode-add-guidance-cookieshare).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/browsersitelist-list-sharedcookies?view=graph-rest-1.0) | [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) collection | Get a list of the [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/browsersitelist-post-sharedcookies?view=graph-rest-1.0) | [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) | Create a new [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) object in a [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/browsersharedcookie-get?view=graph-rest-1.0) | [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) | Get a [session cookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) that can be shared between a Microsoft Edge process and an Internet Explorer process, while using [Internet Explorer mode](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode). |
| [Update](https://learn.microsoft.com/en-us/graph/api/browsersharedcookie-update?view=graph-rest-1.0) | None | Update the properties of a [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/browsersitelist-delete-sharedcookies?view=graph-rest-1.0) | None | Delete a [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) from a [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| comment | String | The comment for the shared cookie. |
| createdDateTime | DateTimeOffset | The date and time when the shared cookie was created. |
| deletedDateTime | DateTimeOffset | The date and time when the shared cookie was deleted. |
| displayName | String | The name of the cookie. |
| history | [browserSharedCookieHistory](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookiehistory?view=graph-rest-1.0) collection | The history of modifications applied to the cookie. |
| hostOnly | Boolean | Controls whether a cookie is a host-only or domain cookie. |
| hostOrDomain | String | The URL of the cookie. |
| id | String | The unique identifier for the cookie. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who last modified the cookie. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the cookie was last modified. |
| path | String | The path of the cookie. |
| sourceEnvironment | browserSharedCookieSourceEnvironment | Specifies how the cookies are shared between Microsoft Edge and Internet Explorer. The possible values are: `microsoftEdge`, `internetExplorer11`, `both`, `unknownFutureValue`. |
| status | browserSharedCookieStatus | The status of the cookie. The possible values are: `published`, `pendingAdd`, `pendingEdit`, `pendingDelete`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.browserSharedCookie",
  "comment": "String",
  "createdDateTime": "String (timestamp)",
  "deletedDateTime": "String (timestamp)",
  "displayName": "String",
  "history": [
    {
      "@odata.type": "microsoft.graph.browserSharedCookieHistory"
    }
  ],
  "hostOnly": "Boolean",
  "hostOrDomain": "String",
  "id": "String (identifier)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "path": "String",
  "sourceEnvironment": "String",
  "status": "String"
}
```
