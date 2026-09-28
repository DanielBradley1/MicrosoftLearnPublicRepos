<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# ediscoveryHoldPolicy resource type

Namespace: microsoft.graph.security

Represents a legal hold policy. Legal holds are holds that are tied to an eDiscovery case. Legal holds should not be confused with retention holds, which are used to control retention policies for Microsoft 365 content. eDiscovery legal holds are for holding content indefinitely for litigation, internal investigations, and other legal actions where content needs to be protected against deletion. For more information, see [Manage holds in eDiscovery \(Premium\)](https://learn.microsoft.com/en-us/microsoft-365/compliance/managing-holds)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-legalholds?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) collection | Get a list of the [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-legalholds?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) | Create a new [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-get?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) | Read the properties and relationships of an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-update?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) | Update the properties of an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-delete-legalholds?view=graph-rest-1.0) | None | Delete an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) object. |
| [Retry policy](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-retrypolicy?view=graph-rest-1.0) | None | Trigger a retry of an [eDiscovery hold policy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0). |
| **Site sources** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-list-sitesources?view=graph-rest-1.0) | [microsoft.graph.security.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) collection | Get a list of the [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) objects associated with an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-post-sitesources?view=graph-rest-1.0) | [microsoft.graph.security.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) | Create a new [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-delete-sitesources?view=graph-rest-1.0) | None | Delete a [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) object associated with an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0). |
| **User sources** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-list-usersources?view=graph-rest-1.0) | [microsoft.graph.security.userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) collection | Get a list of the [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) objects associated with an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-post-usersources?view=graph-rest-1.0) | [microsoft.graph.security.userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) | Create a new [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-delete-usersources?view=graph-rest-1.0) | None | Delete a [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) object associated with an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentQuery | String | KQL query that specifies content to be held in the specified locations. To learn more, see [Keyword queries and search conditions for Content Search and eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/keyword-queries-and-search-conditions). To hold all content in the specified locations, leave **contentQuery** blank. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the legal hold. |
| createdDateTime | DateTimeOffset | The date and time the legal hold was created. |
| description | String | The legal hold description. |
| displayName | String | The display name of the legal hold. |
| errors | String collection | Lists any errors that happened while placing the hold. |
| id | String | The ID for the eDiscovery case. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnabled | Boolean | Indicates whether the hold is enabled and actively holding content. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | the user who last modified the legal hold. |
| lastModifiedDateTime | DateTimeOffset | The date and time the legal hold was last modified. |
| status | microsoft.graph.security.policyStatus | The status of the legal hold. The possible values are: `Pending`, `Error`, `Success`. |

### policyStatus values

| Member | Description |
| :--- | --- |
| Pending | The hold distribution process is in progress. |
| Error | There was an error when the hold was applied. |
| Success | The hold was successfully applied and is holding the specified content. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| siteSources | [microsoft.graph.security.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) collection | Data sources that represent SharePoint sites. |
| userSources | [microsoft.graph.security.userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) collection | Data sources that represent Exchange mailboxes. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryHoldPolicy",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "status": "String",
  "isEnabled": "Boolean",
  "contentQuery": "String",
  "errors": [
    "String"
  ]
}
```
