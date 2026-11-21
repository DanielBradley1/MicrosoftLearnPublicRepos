<!-- Source: https://learn.microsoft.com/en-us/graph/api/planner-post-tasks_v2?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Create task

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new task object.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /planner/tasks_v2
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) object.

You can specify the following properties when creating a **task**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Title of the task. Required. |
| planId | String | ID of the plan that contains the task. Required. Immutable after creation. |
| bucketId | String | ID of the bucket that the task belongs to. Optional. |
| goalIds | String collection | IDs of the goals that the task is associated with. Optional. |
| status | plannerTaskStatus | Indicates progress on the task. The possible values are: `notStarted`, `inProgress`, `completed`, `blocked`, `unknownFutureValue`. Optional. |
| priority | Int32 | Priority of the task. Supported values range from 0 \(urgent\) to 10 \(low\). Optional. |
| percentComplete | Int32 | Percentage of the task's completion, ranging from 0 to 100. Optional. |
| startDateTime | [dateWithOptionalTime](https://learn.microsoft.com/en-us/graph/api/resources/datewithoptionaltime?view=graph-rest-beta) | Date and, optionally, time the task is scheduled to start. Optional. |
| dueDateTime | [dateWithOptionalTime](https://learn.microsoft.com/en-us/graph/api/resources/datewithoptionaltime?view=graph-rest-beta) | Date and, optionally, time the task is due. Optional. |
| finishDateTime | [dateWithOptionalTime](https://learn.microsoft.com/en-us/graph/api/resources/datewithoptionaltime?view=graph-rest-beta) | Date and, optionally, time the task was finished. Optional. |
| notes | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-beta) | Additional details or notes about the task. Optional. |
| recurrence | [plannerTaskRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskrecurrence?view=graph-rest-beta) | Recurrence pattern for the task, if it repeats. Optional. |
| planView | [taskPlanView](https://learn.microsoft.com/en-us/graph/api/resources/taskplanview?view=graph-rest-beta) | Task view settings scoped to the plan, such as applied category IDs. Optional. |
| personalView | [taskPersonalView](https://learn.microsoft.com/en-us/graph/api/resources/taskpersonalview?view=graph-rest-beta) | Per-user personal view settings for the task, such as My Day membership. Optional. |
| parentTaskId | String | ID of the parent task, if this task is a subtask. Optional. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. Optional. |
| checklist | [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta) collection | Checklist items to create with the task by using a deep insert. Optional. |
| links | [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) collection | Content links to create with the task by using a deep insert. Optional. |
| userAssignments | [userAssignment](https://learn.microsoft.com/en-us/graph/api/resources/userassignment?view=graph-rest-beta) collection | Assignments to create with the task. Identify each assignee by `user.id`. Optional. |

The **planId** property is required at creation and can't be changed afterward. Don't copy audit metadata, computed flags, or other read-only properties from a GET response into this request.

For **startDateTime**, **dueDateTime**, and **finishDateTime**, specify only **date**. The **time**, **timeZone**, and **isTimeSpecified** components aren't writable.

You can create a task and supported related objects in one POST request. This is a **deep insert**: include new checklist items, content links, or user assignments as arrays in the task request body. Omit a collection when you don't need it, or use an empty array; don't send `null` for these collections. The service generates identifiers and audit metadata for the new objects.

Deep insert isn't a standalone POST to a child collection, a `$ref` operation, or an instruction to replace a collection during PATCH. Support for one nested collection doesn't imply support for arbitrary relationships. Feature availability also depends on the plan's capabilities.

Properties such as **parentTaskId** and **recurrence** depend on the plan's supported features. Don't assume every property in the table is available for every plan.

## Response

If successful, this method returns a `201 Created` response code and a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Create a task

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/planner/tasks_v2
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.task",
  "displayName": "Prepare quarterly report",
  "planId": "b3d9f9a2-3e14-4a4b-9b2b-6b6d9e6a2f31",
  "bucketId": "9c9c7a3d-5b7f-45e9-9df9-9f8b0f7edc9a",
  "status": "notStarted",
  "priority": 5,
  "percentComplete": 0,
  "startDateTime": {
    "date": "2026-06-01"
  },
  "dueDateTime": {
    "date": "2026-06-15"
  },
  "notes": {
    "@odata.type": "microsoft.graph.itemBody",
    "content": "Compile Q2 sales figures and prepare summary slides.",
    "contentType": "text"
  }
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.task",
  "id": "86d64a5b-109d-39c9-dd43-d7fffb6a1670",
  "displayName": "Prepare quarterly report",
  "planId": "b3d9f9a2-3e14-4a4b-9b2b-6b6d9e6a2f31",
  "bucketId": "9c9c7a3d-5b7f-45e9-9df9-9f8b0f7edc9a",
  "status": "notStarted"
}
```

### Example 2: Create a task with checklist items and assignees

#### Request

This request creates a task, two checklist items, and an assignment to an existing user. Replace **planId** and **user.id** with identifiers accessible to the caller. Don't supply IDs, **assignedBy**, or **assignedDateTime** for the new assignment.

```http
POST https://graph.microsoft.com/beta/planner/tasks_v2
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.task",
  "displayName": "Prepare launch announcement",
  "planId": "b3d9f9a2-3e14-4a4b-9b2b-6b6d9e6a2f31",
  "checklist": [
    {
      "displayName": "Review the announcement",
      "isChecked": false
    },
    {
      "displayName": "Approve the publication date",
      "isChecked": false
    }
  ],
  "userAssignments": [
    {
      "user": {
        "id": "a96b71cc-d742-4b79-9c2a-a56287b7b2c7"
      }
    }
  ]
}
```

#### Response

The following response is shortened. To read the created related objects, get the returned task with `$expand=checklist,userAssignments`.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.task",
  "id": "86d64a5b-109d-39c9-dd43-d7fffb6a1670",
  "displayName": "Prepare launch announcement",
  "planId": "b3d9f9a2-3e14-4a4b-9b2b-6b6d9e6a2f31"
}
```
