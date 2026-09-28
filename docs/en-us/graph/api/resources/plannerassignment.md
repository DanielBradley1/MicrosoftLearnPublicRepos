<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# plannerAssignment resource type

Namespace: microsoft.graph

The **plannerAssignment** resource represents the assignment of a task to a user. This type is used in the open type [plannerAssignments](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignments?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the user that performed the assignment of the task, that is, the assignor. |
| assignedDateTime | DateTimeOffset | The time when the task was assigned. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| orderHint | String | Hint used to order assignees in a task. The format is defined as outlined [here](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "assignedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "assignedDateTime": "String (timestamp)",
  "orderHint": "String"
}
```
