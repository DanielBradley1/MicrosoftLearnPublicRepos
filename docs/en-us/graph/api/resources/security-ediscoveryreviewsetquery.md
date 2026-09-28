<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# ediscoveryReviewSetQuery resource type

Namespace: microsoft.graph.security

Represents a review set query, which is used to query and cull data stored in a Microsoft Purview eDiscovery [reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-list-queries?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) collection | Get a list of the [ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-post-queries?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) | Create a new [ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewsetquery-get?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) | Read the properties and relationships of an [ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewsetquery-update?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) | Update the properties of an [ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-delete-queries?view=graph-rest-1.0) | None | Delete an [ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) object. |
| [Apply tags](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewsetquery-applytags?view=graph-rest-1.0) | None | Apply tags to documents that match the specified query. |
| [Export](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewsetquery-export?view=graph-rest-1.0) | None | Export documents that match the specified query from a review set. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentQuery | String | The query string in KQL \(Keyword Query Language\) query. For details, see [Document metadata fields in eDiscovery \(Premium\)](https://learn.microsoft.com/en-us/microsoft-365/compliance/document-metadata-fields-in-advanced-ediscovery). This field maps directly to the keywords condition. You can refine searches by using fields listed in the *searchable field name* paired with values; for example, *subject:"Quarterly Financials" AND Date>=06/01/2016 AND Date<=07/01/2016*. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who created the query. |
| createdDateTime | DateTimeOffset | The time and date when the query was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| description | String | The description of the **eDiscovery search**. |
| displayName | String | The name of the query. |
| id | String | The unique identifier of the query. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who last modified the query. |
| lastModifiedDateTime | DateTimeOffset | The date and time the query was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryReviewSetQuery",
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
  "contentQuery": "String"
}
```
