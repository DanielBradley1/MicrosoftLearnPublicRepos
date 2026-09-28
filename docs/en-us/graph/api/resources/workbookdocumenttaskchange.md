<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttaskchange?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# workbookDocumentTaskChange resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a task change history of a [workbookDocumentTask](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttask?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/workbookdocumenttaskchange-get?view=graph-rest-beta) | [workbookDocumentTaskChange](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttaskchange?view=graph-rest-beta) | Get the properties and relationships of a [workbookDocumentTaskChange](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttaskchange?view=graph-rest-beta) object. |
| [List](https://learn.microsoft.com/en-us/graph/api/workbookdocumenttask-list-changes?view=graph-rest-beta) | [workbookDocumentTaskChange](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttaskchange?view=graph-rest-beta) collection | Get a list of [workbookDocumentTaskChange](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttaskchange?view=graph-rest-beta) objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignee | [workbookEmailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/workbookemailidentity?view=graph-rest-beta) | The user identity the task is assigned to. Only present when the **type** property is `assign`. Nullable. |
| changedBy | [workbookEmailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/workbookemailidentity?view=graph-rest-beta) | The identity of the user who performs the change. |
| commentId | String | The identifier of the associated comment. |
| createdDateTime | DateTimeOffset | Date and time when the task was changed. Nullable. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| dueDateTime | DateTimeOffset | The due date and time for the task. Only present when the **type** property is `setSchedule`. Nullable. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The unique identifier of the change history. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| percentComplete | Int32 | An integer value from `0` to `100` that represents the percentage of the completion of the task and associated comment. `100` means that the task and associated comment are completed. If you change the completion from `100` to a lower value, the associated task and comment are reactivated. Only present when the **type** property is `setPercentComplete`. Nullable. |
| priority | Int32 | An integer value from `0` to `10` that represents the priority of the task. A lower value indicates a higher priority. `5` indicates the default priority if not set. Only present when the **type** property is `setPriority`. Nullable. |
| startDateTime | DateTimeOffset | The start date and time for the task. Only present when the **type** property is `setSchedule`. Nullable. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| title | String | The title of the task. Only present when the **type** property is `setTitle`. Nullable. |
| type | String | The type of the change history. The possible values are: `create`, `assign`, `unassign`, `unassignAll`, `setPriority`, `setTitle`, `setPercentComplete`, `setSchedule`, `remove`, `restore`, `undo`. |
| undoChangeId | String | The ID of the **workbookDocumentTaskChange** that was undone for the `undo` change action. Only exists on an undo change history. Nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workbookDocumentTaskChange",
  "assignee": {"@odata.type": "microsoft.graph.workbookEmailIdentity"},
  "changedBy": {"@odata.type": "microsoft.graph.workbookEmailIdentity"},
  "commentId": "String",
  "createdDateTime": "String (timestamp)",
  "dueDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "percentComplete": "Int32",
  "priority": "Int32",
  "startDateTime": "String (timestamp)",
  "title": "String",
  "type": "String",
  "undoChangeId": "String"
}
```
