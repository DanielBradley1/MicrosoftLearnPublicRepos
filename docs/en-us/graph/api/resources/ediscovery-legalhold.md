<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# legalHold resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Represents a legal hold. Legal holds are holds that are tied to an eDiscovery case. Legal holds should not be confused with retention holds, which are used to control retention policies for Microsoft 365 content. eDiscovery legal holds are for holding content indefinitely for litigation, internal investigations, and other legal actions where content needs to be protected against deletion. For more information, see [Manage holds in Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/managing-holds)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-list-legalholds?view=graph-rest-beta) | [microsoft.graph.ediscovery.legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) collection | Get a list of the **legalHold** objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-post-legalholds?view=graph-rest-beta) | [microsoft.graph.ediscovery.legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) | Create a new **legalHold** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/ediscovery-legalhold-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) | Read the properties and relationships of a **legalHold** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/ediscovery-legalhold-update?view=graph-rest-beta) | [microsoft.graph.ediscovery.legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) | Update the properties of a **legalHold** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/ediscovery-legalhold-delete?view=graph-rest-beta) | None | Delete a **legalHold** object. |
| [List site sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-legalhold-list-sitesources?view=graph-rest-beta) | [microsoft.graph.ediscovery.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sitesource?view=graph-rest-beta) collection | Get the list of [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sitesource?view=graph-rest-beta) objects associated with a legal hold. |
| [Create site source](https://learn.microsoft.com/en-us/graph/api/ediscovery-legalhold-post-sitesources?view=graph-rest-beta) | [microsoft.graph.ediscovery.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sitesource?view=graph-rest-beta) | Create a new siteSource object. |
| [List user sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-legalhold-list-usersources?view=graph-rest-beta) | [microsoft.graph.ediscovery.userSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-usersource?view=graph-rest-beta) collection | Get the list of [userSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-usersource?view=graph-rest-beta) objects associated with a legal hold. |
| [Create user source](https://learn.microsoft.com/en-us/graph/api/ediscovery-legalhold-post-usersources?view=graph-rest-beta) | [microsoft.graph.ediscovery.userSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-usersource?view=graph-rest-beta) | Create a new **userSource** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentQuery | String | KQL query that specifies content to be held in the specified locations. To learn more, see [Keyword queries and search conditions for Content Search and eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/keyword-queries-and-search-conditions). To hold all content in the specified locations, leave **contentQuery** blank. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The user who created the legal hold. |
| createdDateTime | DateTimeOffset | The date and time the legal hold was created. |
| description | String | The legal hold description. |
| displayName | String | The display name of the legal hold. |
| errors | String collection | Lists any errors that happened while placing the hold. |
| id | String | The ID for the eDiscovery case. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isEnabled | Boolean | Indicates whether the hold is enabled and actively holding content. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | the user who last modified the legal hold. |
| lastModifiedDateTime | DateTimeOffset | The date and time the legal hold was last modified. |
| status | microsoft.graph.ediscovery.legalHoldStatus | The status of the legal hold. The possible values are: `Pending`, `Error`, `Success`, `UnknownFutureValue`. |

### legalHoldStatus values

| Member | Description |
| :--- | --- |
| Pending | The hold distribution process is in progress. |
| Error | There was an error when the hold was applied. For details, see the errors property of the legalHold object. |
| Success | The hold was successfully applied and is holding the specified content. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| siteSources | [microsoft.graph.ediscovery.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sitesource?view=graph-rest-beta) collection | Data source entity for SharePoint sites associated with the legal hold. |
| userSources | [microsoft.graph.ediscovery.userSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-usersource?view=graph-rest-beta) collection | Data source entity for a the legal hold. This is the container for a mailbox and OneDrive for Business site. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.legalHold",
  "id": "String (identifier)",
  "description": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "isEnabled": "Boolean",
  "status": "String",
  "contentQuery": "String",
  "errors": [
    "String"
  ],
  "displayName": "String",
  "createdDateTime": "String (timestamp)"
}
```
