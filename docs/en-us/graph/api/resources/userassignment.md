<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# userAssignment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the assignment of a user to a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta). The assignee identity \(`user`\) is returned by default; `assignedBy` and `assignedDateTime` require $select.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/task-list-userassignments?view=graph-rest-beta) | [userAssignment](https://learn.microsoft.com/en-us/graph/api/resources/userassignment?view=graph-rest-beta) collection | Get a list of the userAssignment objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/task-post-userassignments?view=graph-rest-beta) | [userAssignment](https://learn.microsoft.com/en-us/graph/api/resources/userassignment?view=graph-rest-beta) | Create a new userAssignment object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/userassignment-get?view=graph-rest-beta) | [userAssignment](https://learn.microsoft.com/en-us/graph/api/resources/userassignment?view=graph-rest-beta) | Read the properties and relationships of [userAssignment](https://learn.microsoft.com/en-us/graph/api/resources/userassignment?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/userassignment-update?view=graph-rest-beta) | [userAssignment](https://learn.microsoft.com/en-us/graph/api/resources/userassignment?view=graph-rest-beta) | Update the properties of a userAssignment object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) that made the assignment. |
| assignedDateTime | DateTimeOffset | Date and time the assignment was made. |
| capabilities | [userAssignmentCapability](https://learn.microsoft.com/en-us/graph/api/resources/userassignmentcapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| user | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | Identity of the user assigned to the task. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userAssignment",
  "id": "String (identifier)",
  "user": {
    "@odata.type": "microsoft.graph.identity"
  },
  "assignedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "assignedDateTime": "String (timestamp)",
  "capabilities": {
    "@odata.type": "microsoft.graph.userAssignmentCapability"
  }
}
```
