<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# browserSite resource type

Namespace: microsoft.graph

Represents a site to use in [Internet Explorer mode](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode) that resides on a [site list](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/browsersitelist-list-sites?view=graph-rest-1.0) | [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) collection | Get a list of the [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/browsersitelist-post-sites?view=graph-rest-1.0) | [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) | Create a new [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) object in a [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/browsersite-get?view=graph-rest-1.0) | [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) | Get a [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) that resides on a [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0). |
| [Update](https://learn.microsoft.com/en-us/graph/api/browsersite-update?view=graph-rest-1.0) | None | Update the properties of a [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/browsersitelist-delete-sites?view=graph-rest-1.0) | None | Delete a [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) from a [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowRedirect | Boolean | Controls the behavior of redirected sites. If `true`, indicates that the site will open in Internet Explorer 11 or Microsoft Edge even if the site is navigated to as part of a HTTP or meta refresh redirection chain. |
| comment | String | The comment for the site. |
| compatibilityMode | browserSiteCompatibilityMode | Controls what compatibility setting is used for specific sites or domains. The possible values are: `default`, `internetExplorer8Enterprise`, `internetExplorer7Enterprise`, `internetExplorer11`, `internetExplorer10`, `internetExplorer9`, `internetExplorer8`, `internetExplorer7`, `internetExplorer5`, `unknownFutureValue`. |
| createdDateTime | DateTimeOffset | The date and time when the site was created. |
| deletedDateTime | DateTimeOffset | The date and time when the site was deleted. |
| history | [browserSiteHistory](https://learn.microsoft.com/en-us/graph/api/resources/browsersitehistory?view=graph-rest-1.0) collection | The history of modifications applied to the site. |
| id | String | The unique identifier for the site. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who last modified the site. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the site was last modified. |
| mergeType | browserSiteMergeType | The merge type of the site. The possible values are: `noMerge`, `default`, `unknownFutureValue`. |
| status | browserSiteStatus | Indicates the status of the site. The possible values are: `published`, `pendingAdd`, `pendingEdit`, `pendingDelete`, `unknownFutureValue`. |
| targetEnvironment | browserSiteTargetEnvironment | The target environment that the site should open in. The possible values are: `internetExplorerMode`, `internetExplorer11`, `microsoftEdge`, `configurable`, `none`, `unknownFutureValue`.  <br>  <br>Prior to June 15, 2022, the `internetExplorer11` option would allow opening a site in the Internet Explorer 11 \(IE11\) desktop application. Following the retirement of IE11 on June 15, 2022, the `internetExplorer11` option will no longer open an IE11 window and will instead behave the same as the `internetExplorerMode` option. |
| webUrl | String | The URL of the site. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.browserSite",
  "allowRedirect": "Boolean",
  "comment": "String",
  "compatibilityMode": "String",
  "createdDateTime": "String (timestamp)",
  "deletedDateTime": "String (timestamp)",
  "history": [
    {
      "@odata.type": "microsoft.graph.browserSiteHistory"
    }
  ],
  "id": "String (identifier)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "mergeType": "String",
  "status": "String",
  "targetEnvironment": "String",
  "webUrl": "String"
}
```

## Related content

- [Internet Explorer mode \(IE mode\)](https://www.microsoft.com/edge/business/ie-mode)
- [What is Internet Explorer \(IE\) mode?](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode)
- [Cloud Site List Management for Internet Explorer \(IE\) mode](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode-cloud-site-list-mgmt)
