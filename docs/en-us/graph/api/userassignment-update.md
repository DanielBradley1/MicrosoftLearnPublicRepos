<!-- Source: https://learn.microsoft.com/en-us/graph/api/userassignment-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# userAssignment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the assignment of a user to a [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta). The assignee identity \(`user`\) is returned by default; `assignedBy` and `assignedDateTime` require $select.

To assign users when creating a task, supply **userAssignments** in the [Create task](https://learn.microsoft.com/en-us/graph/planner-post-tasks_v2?view=graph-rest-beta) request. The service supplies the assignment audit fields.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/task-list-userassignments?view=graph-rest-beta) | [userAssignment](https://learn.microsoft.com/en-us/graph/api/userassignment?view=graph-rest-beta) collection | Get a list of the userAssignment objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/userassignment-get?view=graph-rest-beta) | [userAssignment](https://learn.microsoft.com/en-us/graph/api/userassignment?view=graph-rest-beta) | Read the properties and relationships of [userAssignment](https://learn.microsoft.com/en-us/graph/api/userassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/identityset?view=graph-rest-beta) | Identity of the user \(or application\) that made the assignment. Read-only. |
| assignedDateTime | DateTimeOffset | Date and time the assignment was made. Read-only. |
| capabilities | [userAssignmentCapability](https://learn.microsoft.com/en-us/graph/api/userassignmentcapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/entity?view=graph-rest-beta) |
| user | [identity](https://learn.microsoft.com/en-us/graph/api/identity?view=graph-rest-beta) | Identity of the user assigned to the task. |

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
