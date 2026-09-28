<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# delegatedAdminAccessAssignment resource type

Namespace: microsoft.graph

Represents an assignment of administrative roles to a Microsoft partner using delegated administration. The administrative roles are assigned to the Microsoft partner through an access container \(like a security group\). Once it's active, the members of the access container get access to the roles specified in the access details.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/delegatedadminrelationship-post-accessassignments?view=graph-rest-1.0) | [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) | Create a new **delegatedAdminAccessAssignment** object. |
| [List](https://learn.microsoft.com/en-us/graph/api/delegatedadminrelationship-list-accessassignments?view=graph-rest-1.0) | [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) collection | Get a list of the **delegatedAdminAccessAssignment** objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/delegatedadminaccessassignment-get?view=graph-rest-1.0) | [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) | Read the properties and relationships of a **delegatedAdminAccessAssignment** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/delegatedadminaccessassignment-update?view=graph-rest-1.0) | [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) | Update the properties of a **delegatedAdminAccessAssignment** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/delegatedadminaccessassignment-delete?view=graph-rest-1.0) | None | Delete a **delegatedAdminAccessAssignment** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessContainer | [delegatedAdminAccessContainer](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccesscontainer?view=graph-rest-1.0) | The access container through which members are assigned access. For example, a security group. |
| accessDetails | [delegatedAdminAccessDetails](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessdetails?view=graph-rest-1.0) | The access details containing the identifiers of the administrative roles that the partner is assigned in the customer tenant. |
| createdDateTime | DateTimeOffset | The date and time in ISO 8601 format and in UTC time when the access assignment was created. Read-only. |
| id | String | The unique identifier of the access assignment. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time in ISO 8601 and in UTC time when this access assignment was last modified. Read-only. |
| status | delegatedAdminAccessAssignmentStatus | The status of the access assignment. Read-only. The possible values are: `pending`, `active`, `deleting`, `deleted`, `error`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.delegatedAdminAccessAssignment",
  "id": "String (identifier)",
  "status": "String",
  "accessContainer": {
    "@odata.type": "microsoft.graph.delegatedAdminAccessContainer"
  },
  "accessDetails": {
    "@odata.type": "microsoft.graph.delegatedAdminAccessDetails"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
