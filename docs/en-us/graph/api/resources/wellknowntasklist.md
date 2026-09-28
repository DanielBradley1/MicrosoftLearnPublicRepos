<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/wellknowntasklist?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# wellKnownTaskList resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The to-do API set built on [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta&preserve-view=true) was deprecated on May 31, 2022, and stopped returning data on August 31, 2022. Use the [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-beta&preserve-view=true) API instead.

A built-in task list that can't be renamed or deleted. To Do has two built-in lists, **flagged email** and **tasks** list.

This resource supports adding your data to custom properties as [open extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)

Inherits from [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List base task lists](https://learn.microsoft.com/en-us/graph/api/tasks-list-lists?view=graph-rest-beta) | [wellKnownTaskList](https://learn.microsoft.com/en-us/graph/api/resources/wellknowntasklist?view=graph-rest-beta) collection | Get a list of the [wellKnownTaskList](https://learn.microsoft.com/en-us/graph/api/resources/wellknowntasklist?view=graph-rest-beta) objects and their properties. |
| [Get base task list](https://learn.microsoft.com/en-us/graph/api/basetasklist-get?view=graph-rest-beta) | [wellKnownTaskList](https://learn.microsoft.com/en-us/graph/api/resources/wellknowntasklist?view=graph-rest-beta) | Read the properties and relationships of a [wellKnownTaskList](https://learn.microsoft.com/en-us/graph/api/resources/wellknowntasklist?view=graph-rest-beta) object. |
| [List base tasks](https://learn.microsoft.com/en-us/graph/api/basetasklist-list-tasks?view=graph-rest-beta) | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) collection | Get the baseTask resources from the tasks navigation property. |
| [Create base task](https://learn.microsoft.com/en-us/graph/api/basetasklist-post-tasks?view=graph-rest-beta) | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) | Create a new baseTask object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the task list. Inherited from [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta). |
| id | String | The identifier of the task list, unique in the user's mailbox. Read-only. Inherited from [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta). |
| wellKnownListName | wellKnownListName\_v2 | Property indicating the list name if the given list is a well-known list. The possible values are: `none`, `defaultList`, `flaggedEmails`, `unknownFutureValue`. |

### wellknownListName values

| Member | Description |
| :--- | :--- |
| none | User created list. |
| defaultList | Built-in **tasks** list. |
| flaggedEmails | Built-in **flagged email** list. Tasks from flagged emails are present in this list. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-beta) collection | The collection of open extensions defined for the task list. Nullable. Inherited from [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) |
| tasks | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) collection | The tasks in this task list. Read-only. Nullable. Inherited from [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.wellKnownTaskList",
  "displayName": "String",
  "id": "String (identifier)",
  "wellKnownListName": "String"
}
```
