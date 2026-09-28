<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-12 -->

# ediscoveryReviewSet resource type

Namespace: microsoft.graph.security

Represents the static set of electronically stored information collected for use in a litigation, investigation, or regulatory request.

Inherited from [dataSet](https://learn.microsoft.com/en-us/graph/api/resources/security-dataset?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-reviewsets?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) collection | Get a list of the [ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-reviewsets?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) | Create a new [ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-get?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) | Read the properties and relationships of an [ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-update?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) | Update the properties of an [ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) object. |
| [Export](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-export?view=graph-rest-1.0) | None | Initiate an export of data from a [review set](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0). |
| [Add to review set](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-addtoreviewset?view=graph-rest-1.0) | None | Start the process of adding a collection from Microsoft 365 services to a [review set](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0). |
| [List queries](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-list-queries?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) collection | Get the list of [queries](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) associated with an eDiscovery review set. |
| [Create review set query](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-post-queries?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) | Create a new ediscoveryReviewSetQuery object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the review set. Read-only. Inherited from [dataSet](https://learn.microsoft.com/en-us/graph/api/resources/security-dataset?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time when the review set was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [dataSet](https://learn.microsoft.com/en-us/graph/api/resources/security-dataset?view=graph-rest-1.0). |
| description | String | The review set description. Inherited from [dataSet](https://learn.microsoft.com/en-us/graph/api/resources/security-dataset?view=graph-rest-1.0). |
| displayName | String | The review set name. The name is unique with a maximum limit of 64 characters. Inherited from [dataSet](https://learn.microsoft.com/en-us/graph/api/resources/security-dataset?view=graph-rest-1.0). |
| id | String | The review set unique identifier. Read-only. Inherited from [dataSet](https://learn.microsoft.com/en-us/graph/api/resources/security-dataset?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| queries | [microsoft.graph.security.ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) collection | Represents queries within the review set. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryReviewSet",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)"
}
```
