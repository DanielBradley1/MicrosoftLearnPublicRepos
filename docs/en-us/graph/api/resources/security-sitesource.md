<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-26 -->

# siteSource resource type

Namespace: microsoft.graph.security

The container for a site associated with a custodian.

Inherits from [dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| **eDiscovery custodian** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-list-sitesources?view=graph-rest-1.0) | [microsoft.graph.security.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) collection | Get a list of the [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) objects associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-post-sitesources?view=graph-rest-1.0) | [microsoft.graph.security.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) | Create a new [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) object associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-delete-sitesources?view=graph-rest-1.0) | None | Delete a [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) object associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| **eDiscovery hold policy** |  |  |
| [List siteSources](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-list-sitesources?view=graph-rest-1.0) | [microsoft.graph.security.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) collection | Get a list of the [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) objects associated with an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-post-sitesources?view=graph-rest-1.0) | [microsoft.graph.security.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) | Create a new [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-delete-sitesources?view=graph-rest-1.0) | None | Delete a [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) object associated with an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the **siteSource**. |
| createdDateTime | DateTimeOffset | The date and time the **siteSource** was created. |
| displayName | String | The display name of the **siteSource**. This is the name of the SharePoint site. |
| id | String | The ID of the **siteSource**. |
| holdStatus | microsoft.graph.security.dataSourceHoldStatus | The hold status of the **siteSource**. The possible values are: `notApplied`, `applied`, `applying`, `removing`, `partial`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| site | [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) | The SharePoint site associated with the **siteSource**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.siteSource",
  "id": "String (identifier)",
  "displayName": "String",
  "holdStatus": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```
