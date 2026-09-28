<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tasks-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# Use the To Do API built on base tasks in Microsoft Graph \(deprecated\)

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The to-do API set built on [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta&preserve-view=true) was deprecated on May 31, 2022, and stopped returning data on August 31, 2022. Use the [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-beta&preserve-view=true) API instead.

Use the Microsoft Graph To Do API to create an app that connects with users' task in their mailbox. Build a variety of experiences with tasks, such as the following:

- Create tasks from your app’s workflow, for example, from email or notifications, and save them in To Do. Use the [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource?view=graph-rest-beta) entity to store the link back to your app.
- Sync your app’s existing tasks with To Do and create a single task view for better prioritization and manageability.
- Manage To Do tasks in a custom business application.
- Create [checklistItems](https://learn.microsoft.com/en-us/graph/api/resources/checklistitem?view=graph-rest-beta) on a task to break down complex tasks in smaller steps.

Currently, the API supports only permissions delegated by the signed-in user.

Before starting with the To Do API, take a look at the resources and how they relate to one another.

![Screenshot highlighting To Do API entities. Screenshot shows list of task lists on the left, tasks within a specific task list in the center and, on the right, checklist items and linked resource along with other task properties.](https://learn.microsoft.com/en-us/graph/images/tasks-api-entities.png)

## Task list

In this API set, a task list is represented by [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) which is a logical container of [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) resources. You can currently create tasks only in a task list. Tasks created without specifying list get created in the default Tasks list. To [get all your task lists](https://learn.microsoft.com/en-us/graph/api/basetasklist-get?view=graph-rest-beta), make the following HTTP request:

```http
GET /me/tasks/lists
```

## Task

In this API set, a task is represented by a [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) resource which is a piece of work or personal item that can be tracked and completed. To get your tasks from a task list, make the following HTTP request:

```http
GET /me/tasks/lists/{taskListId}/tasks
```

## Checklist item

A [checklistItem](https://learn.microsoft.com/en-us/graph/api/resources/checklistitem?view=graph-rest-beta) represents an item that helps break down complex task in much smaller steps. To get a **checklistItem** from a task, make the following HTTP request:

```http
GET /me/tasks/lists/{taskListId}/tasks/{taskId}/checklistItems/{checklistItems}
```

## Linked resource

A [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) represents any item from a partner application related to the task; for example, an email from where a task was created. You can use it to store information and the link back to the related item in your app. To get a linked resource from a task, make the following HTTP request:

```http
GET /me/tasks/lists/{taskListId}/tasks/{taskId}/linkedresources/{linkedResourceId}
```

## Track changes using delta query

For performance reasons, you may want to maintain a local cache of objects, and periodically synchronize the local cache with the server, using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview).

The following To Do API resources support delta query:

- [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) collection in a task list
- [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta)
