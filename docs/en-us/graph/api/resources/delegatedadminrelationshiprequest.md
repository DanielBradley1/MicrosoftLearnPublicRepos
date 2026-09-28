<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshiprequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# delegatedAdminRelationshipRequest resource type

Namespace: microsoft.graph

Represents a request specific to a delegated admin relationship between a partner and a customer. It allows the Microsoft partner administrator to take actions on a relationship such as locking a relationship for approval or terminating a relationship. It also allows the Microsoft indirect reseller partner administrator to approve or reject a relationship created for them by a Microsoft indirect provider partner.

Base type of [resellerDelegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/resellerdelegatedadminrelationship?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/delegatedadminrelationship-list-requests?view=graph-rest-1.0) | [delegatedAdminRelationshipRequest](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshiprequest?view=graph-rest-1.0) collection | Get a list of the **delegatedAdminRelationshipRequest** objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/delegatedadminrelationship-post-requests?view=graph-rest-1.0) | [delegatedAdminRelationshipRequest](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshiprequest?view=graph-rest-1.0) | Create a new **delegatedAdminRelationshipRequest** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/delegatedadminrelationshiprequest-get?view=graph-rest-1.0) | [delegatedAdminRelationshipRequest](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshiprequest?view=graph-rest-1.0) | Read the properties and relationships of a **delegatedAdminRelationshipRequest** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | delegatedAdminRelationshipRequestAction | The action to be performed on the delegated admin relationship. The possible values are: `lockForApproval`, `approve`, `terminate`, `unknownFutureValue`, `reject`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `reject`. For a partner to finalize a relationship in the `created` **status**, set the **action** to `lockForApproval`. For a partner to terminate a relationship in the `active` **status**, set the **action** to `terminate`. For an indirect reseller to approve a relationship created by an indirect provider in the `approvalPending` **status**, set the **action** to `approve`. For an indirect reseller to reject a relationship created by an indirect provider in the `approvalPending` **status**, set the **action** to `reject`. |
| createdDateTime | DateTimeOffset | The date and time in ISO 8601 format and in UTC time when the relationship request was created. Read-only. |
| id | String | The unique identifier of the relationship request. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time in ISO 8601 format and UTC time when this relationship request was last modified. Read-only. |
| status | delegatedAdminRelationshipRequestStatus | The status of the request. Read-only. The possible values are: `created`, `pending`, `succeeded`, `failed`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.delegatedAdminRelationshipRequest",
  "action": "String",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "status": "String"
}
```
