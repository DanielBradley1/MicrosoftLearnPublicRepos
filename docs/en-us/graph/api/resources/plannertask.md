<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# plannerTask resource type

Namespace: microsoft.graph

Represents a Planner task in Microsoft 365. A Planner task is contained in a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) and can be assigned to a [bucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-1.0) in a plan. Each task object has a [details](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-1.0) object that can contain more information about the task. For more information about relationships between group, plan, and task, See [Use the Planner REST API](https://learn.microsoft.com/en-us/graph/api/resources/planner-overview?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/planner-post-tasks?view=graph-rest-1.0) | [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) | Create **plannerTask** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/plannertask-get?view=graph-rest-1.0) | [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) | Read properties and relationships of **plannerTask** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/plannertask-update?view=graph-rest-1.0) | [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) | Update **plannerTask** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/plannertask-delete?view=graph-rest-1.0) | None | Delete **plannerTask** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeChecklistItemCount | Int32 | Number of checklist items with value set to `false`, representing incomplete items. |
| appliedCategories | [plannerAppliedCategories](https://learn.microsoft.com/en-us/graph/api/resources/plannerappliedcategories?view=graph-rest-1.0) | The categories to which the task has been applied. See [applied Categories](https://learn.microsoft.com/en-us/graph/api/resources/plannerappliedcategories?view=graph-rest-1.0) for possible values. |
| assigneePriority | String | Hint used to order items of this type in a list view. The format is defined as outlined [here](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |
| assignments | [plannerAssignments](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignments?view=graph-rest-1.0) | The set of assignees the task is assigned to. |
| bucketId | String | Bucket ID to which the task belongs. The bucket needs to be in the plan that the task is in. It's 28 characters long and case-sensitive. [Format validation](https://learn.microsoft.com/en-us/graph/api/resources/planner-identifiers-disclaimer?view=graph-rest-1.0) is done on the service. |
| checklistItemCount | Int32 | Number of checklist items that are present on the task. |
| completedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user that completed the task. |
| completedDateTime | DateTimeOffset | Read-only. Date and time at which the `'percentComplete'` of the task is set to `'100'`. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| conversationThreadId | String | Thread ID of the conversation on the task. This is the ID of the conversation thread object created in the group. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user that created the task. |
| createdDateTime | DateTimeOffset | Read-only. Date and time at which the task is created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| dueDateTime | DateTimeOffset | Date and time at which the task is due. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| hasDescription | Boolean | Read-only. Value is `true` if the details object of the task has a nonempty description and `false` otherwise. |
| id | String | Read-only. ID of the task. It's 28 characters long and case-sensitive. [Format validation](https://learn.microsoft.com/en-us/graph/api/resources/planner-identifiers-disclaimer?view=graph-rest-1.0) is done on the service. |
| orderHint | String | Hint used to order items of this type in a list view. The format is defined as outlined [here](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |
| percentComplete | Int32 | Percentage of task completion. When set to `100`, the task is considered completed. |
| planId | String | Plan ID to which the task belongs. |
| previewType | String | This sets the type of preview that shows up on the task. The possible values are: `automatic`, `noPreview`, `checklist`, `description`, `reference`. |
| priority | Int32 | Priority of the task. The valid range of values is between `0` and `10`, with the increasing value being lower priority \(`0` has the highest priority and `10` has the lowest priority\). Currently, Planner interprets values `0` and `1` as "urgent", `2`, `3` and `4` as "important", `5`, `6`, and `7` as "medium", and `8`, `9`, and `10` as "low". Additionally, Planner sets the value `1` for "urgent", `3` for "important", `5` for "medium", and `9` for "low". |
| referenceCount | Int32 | Number of external references that exist on the task. |
| startDateTime | DateTimeOffset | Date and time at which the task starts. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| title | String | Title of the task. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignedToTaskBoardFormat | [plannerAssignedToTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignedtotaskboardtaskformat?view=graph-rest-1.0) | Read-only. Nullable. Used to render the task correctly in the task board view when grouped by assignedTo. |
| bucketTaskBoardFormat | [plannerBucketTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerbuckettaskboardtaskformat?view=graph-rest-1.0) | Read-only. Nullable. Used to render the task correctly in the task board view when grouped by bucket. |
| details | [plannerTaskDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-1.0) | Read-only. Nullable. More details about the task. |
| progressTaskBoardFormat | [plannerProgressTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerprogresstaskboardtaskformat?view=graph-rest-1.0) | Read-only. Nullable. Used to render the task correctly in the task board view when grouped by progress. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "activeChecklistItemCount": "Int32",
  "appliedCategories": {"@odata.type": "microsoft.graph.plannerAppliedCategories"},
  "assigneePriority": "String",
  "assignments": {"@odata.type": "microsoft.graph.plannerAssignments"},
  "bucketId": "String",
  "checklistItemCount": "Int32",
  "completedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "completedDateTime": "String (timestamp)",
  "conversationThreadId": "String",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "dueDateTime": "String (timestamp)",
  "hasDescription": "Boolean",
  "id": "String (identifier)",
  "orderHint": "String",
  "percentComplete": "Int32",
  "priority": "Int32",
  "planId": "String",
  "previewType": "String",
  "referenceCount": "Int32",
  "startDateTime": "String (timestamp)",
  "title": "String"
}
```
