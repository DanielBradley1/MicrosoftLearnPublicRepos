<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-12 -->

# ediscoveryCase resource type

Namespace: microsoft.graph.security

In the context of eDiscovery, contains custodians, searches, review sets. For details, see [Overview of Microsoft Purview eDiscovery \(Premium\)](https://learn.microsoft.com/en-us/microsoft-365/compliance/overview-ediscovery-20).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-casesroot-list-ediscoverycases?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0) collection | Get a list of the [ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-casesroot-post-ediscoverycases?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0) | Create a new [ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-get?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0) | Read the properties and relationships of an [ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-update?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0) | Update the properties of an [ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-casesroot-delete-ediscoverycases?view=graph-rest-1.0) | None | Delete an [ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0) object. |
| [Close](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-close?view=graph-rest-1.0) | None | Close an [ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0) object. |
| [Reopen](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-reopen?view=graph-rest-1.0) | None | Reopen an [ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0) object. |
| [List custodians](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-custodians?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0) collection | Get the ediscoveryCustodian resources from the custodians navigation property. |
| [Create custodian](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-custodians?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0) | Create a new ediscoveryCustodian object. |
| [List legal holds](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-legalholds?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) collection | Get the ediscoveryHoldPolicy resources from the legalHolds navigation property. |
| [Delete legal holds](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-delete-legalholds?view=graph-rest-1.0) | None | Delete an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) object. |
| [Create hold policy](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-legalholds?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) | Create a new ediscoveryHoldPolicy object. |
| [List noncustodial data sources](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-list-noncustodialsources?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) collection | Get the ediscoveryNoncustodialDataSource resources from the noncustodialDataSources navigation property. |
| [Create noncustodial data source](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-noncustodialdatasources?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) | Create a new ediscoveryNoncustodialDataSource object. |
| [List operations](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-operations?view=graph-rest-1.0) | [microsoft.graph.security.caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0) collection | Get the caseOperation resources from the operations navigation property. |
| [List review sets](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-reviewsets?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) collection | Get the ediscoveryReviewSet resources from the reviewSets navigation property. |
| [Create review set](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-reviewsets?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) | Create a new ediscoveryReviewSet object. |
| [List searches](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-searches?view=graph-rest-1.0) | [microsoft.graph.security.ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) collection | Get the ediscoverySearch resources from the searches navigation property. |
| [Create search](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-searches?view=graph-rest-1.0) | [microsoft.graph.security.ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) | Create a new ediscoverySearch object. |
| [List tags](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-tags?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) collection | Get the ediscoveryReviewTag resources from the tags navigation property. |
| [Create review tag](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-tags?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) | Create a new ediscoveryReviewTag object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| closedBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who closed the case. |
| closedDateTime | DateTimeOffset | The date and time when the case was closed. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who created the case. |
| createdDateTime | DateTimeOffset | The date and time when the entity was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| description | String | The case description. |
| displayName | String | The case name. |
| externalId | String | The external case number for customer reference. |
| id | String | The ID for the eDiscovery case. Read-only. |
| lastModifiedBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The last user who modified the case. |
| lastModifiedDateTime | DateTimeOffset | The latest date and time when the case was modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| status | microsoft.graph.security.caseStatus | The case status. Possible values are `unknown`, `active`, `pendingDelete`, `closing`, `closed`, and `closedWithError`. For details, see the following table. |

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
| custodians | [microsoft.graph.security.ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0) collection | Returns a list of case **ediscoveryCustodian** objects for this **case**. |
| legalHolds | [microsoft.graph.security.ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) collection | Returns a list of case **eDiscoveryHoldPolicy** objects for this **case**. |
| noncustodialDataSources | [microsoft.graph.security.ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) collection | Returns a list of case **ediscoveryNoncustodialDataSource** objects for this **case**. |
| operations | [microsoft.graph.security.caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0) collection | Returns a list of case **caseOperation** objects for this **case**. |
| reviewSets | [microsoft.graph.security.ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) collection | Returns a list of **eDiscoveryReviewSet** objects in the case. |
| searches | [microsoft.graph.security.ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) collection | Returns a list of **eDiscoverySearch** objects associated with this case. |
| settings | [microsoft.graph.security.ediscoveryCaseSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasesettings?view=graph-rest-1.0) | Returns a list of **eDIscoverySettings** objects in the case. |
| tags | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) collection | Returns a list of **ediscoveryReviewTag** objects associated to this case. |
| caseMembers | [microsoft.graph.security.ediscoveryCaseMember](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasemember?view=graph-rest-1.0) collection | Represents members of an eDiscovery case. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryCase",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "status": "String",
  "closedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "closedDateTime": "String (timestamp)",
  "externalId": "String"
}
```
