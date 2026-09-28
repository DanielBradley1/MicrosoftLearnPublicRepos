<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# reviewSet resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Represents static set of electronically stored information collected for use in a litigation, investigation, or regulatory request.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List reviewSets](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-list-reviewsets?view=graph-rest-beta) | [microsoft.graph.ediscovery.reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta) collection | Get a collection of **reviewSet** objects. |
| [Create reviewSet](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-post-reviewsets?view=graph-rest-beta) | [microsoft.graph.ediscovery.reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta) | Create a new **reviewSet**. |
| [Get reviewSet](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewset-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta) | Read the properties and relationships of a **reviewSet** object. |
| [List queries](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewsetquery-list?view=graph-rest-beta) | [microsoft.graph.ediscovery.reviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewsetquery?view=graph-rest-beta) collection | Get a list of **reviewSetQuery** resources. |
| [export](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewset-export?view=graph-rest-beta) | None | Initiate an export of data from the **reviewset**. |
| [addToReviewSet](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewset-addtoreviewset?view=graph-rest-beta) | None | Add data from a **sourceCollection** to a **reviewset**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who created the review set. Read-only. |
| createdDateTime | DateTimeOffset | The datetime when the review set was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| displayName | String | The review set name. The name is unique with a maximum limit of 64 characters. |
| id | String | The review set unique identifier. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| queries | [microsoft.graph.ediscovery.reviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewsetquery?view=graph-rest-beta) collection | Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.reviewSet",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "id": "String (identifier)",
  "displayName": "String",
  "createdDateTime": "String (timestamp)"
}
```
