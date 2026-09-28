<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewsetquery?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# reviewSetQuery resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Represents a review set query, which is used to query and cull data stored in an eDiscovery [reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewsetquery-list?view=graph-rest-beta) | [microsoft.graph.ediscovery.reviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewsetquery?view=graph-rest-beta) collection | List the review set queries in a review set. |
| [Create](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewsetquery-post?view=graph-rest-beta) | [microsoft.graph.ediscovery.reviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewsetquery?view=graph-rest-beta) | Create a new review set query. |
| [Get](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewsetquery-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.reviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewsetquery?view=graph-rest-beta) | Read the properties and relationships of a **reviewSetQuery** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewsetquery-update?view=graph-rest-beta) | None | Update a review set query. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewsetquery-delete?view=graph-rest-beta) | None | Delete review set query. |
| [Apply tags](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewsetquery-applytags?view=graph-rest-beta) | None | Apply tags to documents that match the specified query. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who created the query. |
| createdDateTime | DateTimeOffset | The time and date when the query was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| displayName | String | The name of the query. |
| id | String | The unique identifier of the query. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who last modified the query. |
| lastModifiedDateTime | DateTimeOffset | The date and time the query was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| query | String | The query string in KQL \(Keyword Query Language\) query. For details, see [Document metadata fields in Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/document-metadata-fields-in-advanced-ediscovery). This field maps directly to the keywords condition. You can refine searches by using fields listed in the *searchable field name* paired with values; for example, *subject:"Quarterly Financials" AND Date>=06/01/2016 AND Date<=07/01/2016*. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.reviewSetQuery",
  "query": "String",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "displayName": "String",
  "createdDateTime": "String (timestamp)"
}
```
