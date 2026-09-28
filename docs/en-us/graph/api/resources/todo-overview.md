<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/todo-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-29 -->

# Use the Microsoft To Do API

Use the Microsoft Graph To Do API to create an app that connects with tasks across Microsoft To Do clients. Build a variety of experiences with tasks, such as the following:

- Create tasks from your app’s workflow, for example, from email or notifications, and save them in To Do. Use the [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource?view=graph-rest-1.0) entity to store the link back to your app.
- Sync your app’s existing tasks with To Do and create a single task view for better prioritization and manageability.
- Manage To Do tasks in a custom business application.

The API supports both delegated and application permissions.

Before starting with the To Do API, take a look at the resources and how they relate to one another.

![Screenshot highlighting To Do API entities. Screenshot shows list of task lists on the left, tasks within a specific task list in the center and, on the right, checklist items and linked resource along with other task properties.](https://learn.microsoft.com/en-us/graph/images/tasks-api-entities.png)

## Task list

A [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0) represents a logical container of [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) resources. You can currently create tasks only in a task list. To [get all your task lists](https://learn.microsoft.com/en-us/graph/api/todotasklist-get?view=graph-rest-1.0), make the following HTTP request:

```http
GET /me/todo/lists
```

## Task

A [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) represents a task, i.e. a piece of work or personal item that can be tracked and completed. To get your tasks from a task list, make the following HTTP request:

```http
GET /me/todo/lists/{todoTaskListId}/tasks
```

## Checklist item

A [checklistItem](https://learn.microsoft.com/en-us/graph/api/resources/checklistitem?view=graph-rest-1.0) represents a subtask in a bigger [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0). **ChecklistItem** allows breaking down a complex task into more actionable, smaller tasks. To get a **checklistItem** from a task, make the following HTTP request:

```http
GET /me/todo/lists/{todoTaskListId}/tasks/{todoTaskId}/checklistItems/{checklistItems}
```

## Linked resource

A [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource?view=graph-rest-1.0) represents any item from a partner application related to the task, for example, an item like email from where a task was created. You can use it to store information and the link back to the related item in your app. To get a linked resource from a task, make the following HTTP request:

```http
GET /me/todo/lists/{todoTaskListId}/tasks/{todoTaskId}/linkedresources/{linkedResourceId}
```

## Track changes using delta query

For performance reasons, you may want to maintain a local cache of objects, and periodically synchronize the local cache with the server, using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview).

The following To Do API resources support delta query:

- [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) collection in a task list
- [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0)
