<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttask?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# workbookDocumentTask resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a document task in a workbook. A **workbookDocumentTask** is associated with a comment.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List workbookDocumentTasks](https://learn.microsoft.com/en-us/graph/api/workbookdocumenttask-get?view=graph-rest-beta) | [workbookDocumentTask](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttask?view=graph-rest-beta) collection | Get a list of [workbookDocumentTask](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttask?view=graph-rest-beta) objects. |
| [Get workbookDocumentTask](https://learn.microsoft.com/en-us/graph/api/workbookdocumenttask-get?view=graph-rest-beta) | [workbookDocumentTask](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttask?view=graph-rest-beta) | Get the properties and relationships of a [workbookDocumentTask](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttask?view=graph-rest-beta) object. |
| [List workbookDocumentTaskChanges](https://learn.microsoft.com/en-us/graph/api/workbookdocumenttask-list-changes?view=graph-rest-beta) | [workbookDocumentTaskChange](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttaskchange?view=graph-rest-beta) collection | Get a list of [workbookDocumentTaskChange](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttaskchange?view=graph-rest-beta) objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignees | [workbookEmailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/workbookemailidentity?view=graph-rest-beta) collection | A collection of user identities the task is assigned to. |
| completedBy | [workbookEmailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/workbookemailidentity?view=graph-rest-beta) | The identity of the user who completed the task. Nullable. |
| completedDateTime | DateTimeOffset | Date and time when the task was completed. Nullable. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| createdBy | [workbookEmailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/workbookemailidentity?view=graph-rest-beta) | A user identity that creates the task. Nullable. |
| createdDateTime | DateTimeOffset | Date and time when the task was created. Nullable. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The unique identifier for the task. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| percentComplete | Int32 | An integer value from `0` to `100` that represents the percentage of the completion of the task. `100` means that the task is completed. Nullable. |
| priority | Int32 | An integer value from `0` to `10` that represents the priority of the task. A lower value indicates a higher priority. Nullable. |
| startAndDueDateTime | [workbookDocumentTaskSchedule](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttaskschedule?view=graph-rest-beta) | Start and due date of the task. Nullable. |
| title | String | The title of the task. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| changes | [workbookDocumentTaskChange](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttaskchange?view=graph-rest-beta) collection | A collection of task change histories. |
| comment | [workbookComment](https://learn.microsoft.com/en-us/graph/api/resources/workbookcomment?view=graph-rest-beta) | The comment that the task is associated with. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workbookDocumentTask",
  "assignees": [{"@odata.type": "microsoft.graph.workbookEmailIdentity"}],
  "completedBy": {"@odata.type": "microsoft.graph.workbookEmailIdentity"},
  "completedDateTime": "String (timestamp)",
  "createdBy": {"@odata.type": "microsoft.graph.workbookEmailIdentity"},
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "percentComplete": "Int32",
  "priority": "Int32",
  "startAndDueDateTime": {"@odata.type": "microsoft.graph.workbookDocumentTaskSchedule"},
  "title": "String"
}
```
