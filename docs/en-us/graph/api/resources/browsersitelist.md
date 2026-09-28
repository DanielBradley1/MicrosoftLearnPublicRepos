<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# browserSiteList resource type

Namespace: microsoft.graph

Represents an enterprise site list in a compliant cloud location that specifies sites to be opened in [Internet Explorer mode](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode). The site list contains one or more [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) and [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) resources.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/internetexplorermode-list-sitelists?view=graph-rest-1.0) | [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) collection | Get a list of the [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/internetexplorermode-post-sitelists?view=graph-rest-1.0) | [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) | Create a new [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) object to support [Internet Explorer mode](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode). |
| [Get](https://learn.microsoft.com/en-us/graph/api/browsersitelist-get?view=graph-rest-1.0) | [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) | Get a [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) that contains [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) and [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) resources. |
| [Update](https://learn.microsoft.com/en-us/graph/api/browsersitelist-update?view=graph-rest-1.0) | None | Update the properties of a [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/internetexplorermode-delete-sitelists?view=graph-rest-1.0) | None | Delete a [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) object. |
| [Publish](https://learn.microsoft.com/en-us/graph/api/browsersitelist-publish?view=graph-rest-1.0) | [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) | Publish the specified [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) for devices to download. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the site list. |
| displayName | String | The name of the site list. |
| id | String | The unique identifier for the site list. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who last modified the site list. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the site list was last modified. |
| publishedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who published the site list. |
| publishedDateTime | DateTimeOffset | The date and time when the site list was published. |
| revision | String | The current revision of the site list. |
| status | browserSiteListStatus | The current status of the site list. The possible values are: `draft`, `published`, `pending`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sharedCookies | [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) collection | A collection of shared cookies defined for the site list. |
| sites | [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) collection | A collection of sites defined for the site list. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.browserSiteList",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "publishedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "publishedDateTime": "String (timestamp)",
  "revision": "String",
  "status": "String"
}
```

## Related content

- [Internet Explorer mode \(IE mode\)](https://www.microsoft.com/edge/business/ie-mode)
- [What is Internet Explorer \(IE\) mode?](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode)
- [Cloud Site List Management for Internet Explorer \(IE\) mode](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode-cloud-site-list-mgmt)
