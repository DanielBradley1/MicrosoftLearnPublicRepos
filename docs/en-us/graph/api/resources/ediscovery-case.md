<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-case?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# case resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

In the context of eDiscovery, contains custodians, holds, collections, review sets, and exports. For details, see [Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/overview-ediscovery-20).

Note

Starting in September 2021, POST operations will create large cases. To learn more about large cases, see [Use large cases in Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/advanced-ediscovery-new-case-format). For details, see the [Changes to the Microsoft 365 advanced eDiscovery create case API](https://go.microsoft.com/fwlink/?linkid=2172604) blog post.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List cases](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-list?view=graph-rest-beta) | [microsoft.graph.ediscovery.case](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-case?view=graph-rest-beta) collection | Retrieve a list of [case](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-case?view=graph-rest-beta) objects. |
| [Create case](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-post?view=graph-rest-beta) | [microsoft.graph.ediscovery.case](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-case?view=graph-rest-beta) | Create a new **case** object. |
| [Get case](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.case](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-case?view=graph-rest-beta) | Retrieve the properties and relationships of a **case** object. |
| [Update case](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-update?view=graph-rest-beta) | [microsoft.graph.ediscovery.case](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-case?view=graph-rest-beta) | Update the properties of a **case** object. |
| [Delete case](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-delete?view=graph-rest-beta) | None | Delete a **case** object. |
| [Close case](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-close?view=graph-rest-beta) | None | Close an eDiscovery case. For details, see [Close a case](https://learn.microsoft.com/en-us/microsoft-365/compliance/close-or-delete-case#close-a-case). |
| [Reopen case](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-reopen?view=graph-rest-beta) | None | Reopen an eDiscovery case that was closed. For details, see [Reopen a closed case](https://learn.microsoft.com/en-us/microsoft-365/compliance/close-or-delete-case#reopen-a-closed-case). |
| Custodians |  |  |
| [List custodians](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-list-custodians?view=graph-rest-beta) | [microsoft.graph.ediscovery.custodian](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) collection | Get a list of the [custodian](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) objects and their properties. |
| [Create custodian](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-post-custodians?view=graph-rest-beta) | [microsoft.graph.ediscovery.custodian](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) | Create a new [custodian](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) object. After the custodian object is created, you will need to create the custodian's [userSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-usersource?view=graph-rest-beta) to reference their mailbox and OneDrive for Business site. |
| Legal holds |  |  |
| [List legalHolds](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-list-legalholds?view=graph-rest-beta) | [microsoft.graph.ediscovery.legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) collection | Get the [legalHolds](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) that are applied to a case. |
| [Create legalHold](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-post-legalholds?view=graph-rest-beta) | [microsoft.graph.ediscovery.legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) | Create a new [legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) object. |
| Review sets |  |  |
| [List reviewSets](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-list-reviewsets?view=graph-rest-beta) | [microsoft.graph.ediscovery.reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta) collection | Get the list of [reviewSets](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta) from a **case** object. |
| [Create reviewSet](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-post-reviewsets?view=graph-rest-beta) | [microsoft.graph.ediscovery.reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta) | Create a new [reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta) object. The request body contains the display name of the review set, which is the only writable property. |
| Case settings |  |  |
| [Get caseSettings](https://learn.microsoft.com/en-us/graph/api/ediscovery-casesettings-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.caseSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-casesettings?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.ediscovery.caseSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-casesettings?view=graph-rest-beta) object. |
| [Update caseSettings](https://learn.microsoft.com/en-us/graph/api/ediscovery-casesettings-update?view=graph-rest-beta) | [microsoft.graph.ediscovery.caseSsettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-casesettings?view=graph-rest-beta) | Update the properties of a [microsoft.graph.ediscovery.caseSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-casesettings?view=graph-rest-beta) object. |
| [resetToDefault](https://learn.microsoft.com/en-us/graph/api/ediscovery-casesettings-resettodefault?view=graph-rest-beta) | None | Reset all settings to the default values. |
| Source collections |  |  |
| [List sourceCollections](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-list-sourcecollections?view=graph-rest-beta) | [microsoft.graph.ediscovery.sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta) collection | Get the [sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta) from a **case** object. |
| [Create sourceCollection](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-post-sourcecollections?view=graph-rest-beta) | [microsoft.graph.ediscovery.sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta) | Create a new **sourceCollection** object. |
| Tags |  |  |
| [List tags](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-list-tags?view=graph-rest-beta) | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) collection | Retrieve a list of [tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) objects from an eDiscovery case. |
| [Create tag](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-post-tags?view=graph-rest-beta) | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) | Create a new tag for the specified case. The tags are used in review sets while reviewing content. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| closedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who closed the case. |
| closedDateTime | DateTimeOffset | The date and time when the case was closed. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who created the case. |
| createdDateTime | DateTimeOffset | The date and time when the entity was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| description | String | The case description. |
| displayName | String | The case name. |
| externalId | String | The external case number for customer reference. |
| id | String | The ID for the eDiscovery case. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The last user who modified the entity. |
| lastModifiedDateTime | DateTimeOffset | The latest date and time when the case was modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| status | microsoft.graph.ediscovery.caseStatus | The case status. Possible values are `unknown`, `active`, `pendingDelete`, `closing`, `closed`, and `closedWithError`. For details, see the following table. |

### caseStatus values

| Member | Description |
| :--- | --- |
| unknown | Case status is unknown. |
| active | Case is active. |
| pendingDelete | Case was deleted, but the delete has not been fully transacted. |
| closing | Case was closed, but the operation has not been fully transacted. |
| closed | The case is closed. |
| closedWithError | The case is closed, but there were errors releasing holds in the case. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| custodians | [microsoft.graph.ediscovery.custodian](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) collection | Returns a list of case **custodian** objects for this **case**. Nullable. |
| legalHolds | [microsoft.graph.ediscovery.legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) collection | Returns a list of case **legalHold** objects for this **case**. Nullable. |
| noncustodialDataSources | [microsoft.graph.ediscovery.noncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-noncustodialdatasource?view=graph-rest-beta) collection | Returns a list of case **noncustodialDataSource** objects for this **case**. Nullable. |
| operations | [microsoft.graph.ediscovery.caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta) collection | Returns a list of case **operation** objects for this **case**. Nullable. |
| reviewSets | [microsoft.graph.ediscovery.reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta) collection | Returns a list of **reviewSet** objects in the case. Read-only. Nullable. |
| caseSettings | [microsoft.graph.ediscovery.caseSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-casesettings?view=graph-rest-beta) collection | Returns a list of **settings** objects in the case. Read-only. Nullable. |
| sourceCollections | [microsoft.graph.ediscovery.sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta) collection | Returns a list of **sourceCollection** objects associated with this case. |
| tags | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) collection | Returns a list of **tag** objects associated to this case. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.case",
  "description": "String",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "status": "String",
  "closedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "closedDateTime": "String (timestamp)",
  "externalId": "String",
  "id": "String (identifier)",
  "displayName": "String",
  "createdDateTime": "String (timestamp)"
}
```
