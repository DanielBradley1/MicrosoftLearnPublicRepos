<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshipoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# delegatedAdminRelationshipOperation resource type

Namespace: microsoft.graph

Represents a long-running operation related to a delegated admin relationship. An example of a long-running operation can be an update to the [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) object.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/delegatedadminrelationship-list-operations?view=graph-rest-1.0) | [delegatedAdminRelationshipOperation](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshipoperation?view=graph-rest-1.0) collection | Get a list of the **delegatedAdminRelationshipOperation** objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/delegatedadminrelationshipoperation-get?view=graph-rest-1.0) | [delegatedAdminRelationshipOperation](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshipoperation?view=graph-rest-1.0) | Read the properties and relationships of a **delegatedAdminRelationshipOperation** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The time in ISO 8601 format and in UTC time when the long-running operation was created. Read-only. |
| data | String | The data \(payload\) for the operation. Read-only. |
| id | String | The unique identifier of the delegated admin long-running operation. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The time in ISO 8601 format and in UTC time when the long-running operation was last modified. Read-only. |
| operationType | delegatedAdminRelationshipOperationType | The type of long-running operation. The possible values are: `delegatedAdminAccessAssignmentUpdate`, `unknownFutureValue`,`delegatedAdminRelationshipUpdate`. Read-only. Use the `Prefer: include-unknown-enum-members` request header to get the following members from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `delegatedAdminRelationshipUpdate`. |
| status | longRunningOperationStatus | The status of the operation. Read-only. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`. Read-only. Supports `$orderby`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.delegatedAdminRelationshipOperation",
  "id": "String (identifier)",
  "operationType": "String",
  "data": "String",
  "status": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
