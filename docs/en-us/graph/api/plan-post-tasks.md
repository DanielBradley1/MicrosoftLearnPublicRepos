<!-- Source: https://learn.microsoft.com/en-us/graph/api/plan-post-tasks?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Create task

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new task object.

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
POST /me/planner/tasks_v2
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
| planId | String | ID of the plan that contains the task. Immutable after creation. Optional. |
| bucketId | String | ID of the bucket that the task belongs to. Optional. |
| goalIds | String collection | IDs of the goals that the task is associated with. Optional. |
| status | plannerTaskStatus | Indicates progress on the task. The possible values are: `notStarted`, `inProgress`, `completed`, `blocked`, `unknownFutureValue`. Optional. |
| priority | Int32 | Priority of the task. Supported values range from 0 \(urgent\) to 10 \(low\). Required. |
| percentComplete | Int32 | Percentage of the task's completion, ranging from 0 to 100. Required. |
| startDateTime | [dateWithOptionalTime](https://learn.microsoft.com/en-us/graph/api/resources/datewithoptionaltime?view=graph-rest-beta) | Date and, optionally, time the task is scheduled to start. Optional. |
| dueDateTime | [dateWithOptionalTime](https://learn.microsoft.com/en-us/graph/api/resources/datewithoptionaltime?view=graph-rest-beta) | Date and, optionally, time the task is due. Optional. |
| finishDateTime | [dateWithOptionalTime](https://learn.microsoft.com/en-us/graph/api/resources/datewithoptionaltime?view=graph-rest-beta) | Date and, optionally, time the task was finished. Optional. |
| notes | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-beta) | Additional details or notes about the task. Optional. |
| recurrence | [plannerTaskRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskrecurrence?view=graph-rest-beta) | Recurrence pattern for the task, if it repeats. Optional. |
| planView | [taskPlanView](https://learn.microsoft.com/en-us/graph/api/resources/taskplanview?view=graph-rest-beta) | Task view settings scoped to the plan, such as applied category IDs. Optional. |
| personalView | [taskPersonalView](https://learn.microsoft.com/en-us/graph/api/resources/taskpersonalview?view=graph-rest-beta) | Per-user personal view settings for the task, such as My Day membership. Optional. |
| parentTaskId | String | ID of the parent task, if this task is a subtask. Optional. |
| hasChildren | Boolean | Indicates whether the task has subtasks. Optional. |
| isCritical | Boolean | Indicates whether the task is on the critical path, as computed from its dependencies. Optional. |
| hasChat | Boolean | Indicates whether the task has an associated chat. Optional. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/planner/tasks_v2
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.task",
  "displayName": "Prepare quarterly report",
  "planId": "b3d9f9a2-3e14-4a4b-9b2b-6b6d9e6a2f31",
  "bucketId": "9c9c7a3d-5b7f-45e9-9df9-9f8b0f7edc9a",
  "goalIds": [
    "3f8a1c9d-6b42-4e7a-9d31-8c2f6b9a4e17"
  ],
  "status": "notStarted",
  "priority": 5,
  "percentComplete": 0,
  "startDateTime": {
    "@odata.type": "microsoft.graph.dateWithOptionalTime",
    "date": "2026-06-01",
    "isTimeSpecified": false
  },
  "dueDateTime": {
    "@odata.type": "microsoft.graph.dateWithOptionalTime",
    "date": "2026-06-15",
    "isTimeSpecified": false
  },
  "notes": {
    "@odata.type": "microsoft.graph.itemBody",
    "content": "Compile Q2 sales figures and prepare summary slides.",
    "contentType": "text"
  },
  "recurrence": {
    "@odata.type": "microsoft.graph.plannerTaskRecurrence",
    "schedule": {
      "@odata.type": "microsoft.graph.plannerRecurrenceSchedule",
      "patternStartDateTime": "2026-06-01T00:00:00Z",
      "pattern": {
        "@odata.type": "microsoft.graph.recurrencePattern",
        "type": "weekly",
        "interval": 1,
        "daysOfWeek": [
          "monday"
        ],
        "firstDayOfWeek": "sunday"
      }
    }
  },
  "planView": {
    "@odata.type": "microsoft.graph.taskPlanView",
    "appliedCategoryIds": [
      "e4f8a3c6-9d21-4b7a-8e42-6c1f9a3d5b28"
    ]
  },
  "personalView": {
    "@odata.type": "microsoft.graph.taskPersonalView",
    "isOnMyDay": true
  },
  "parentTaskId": "2c8f4b6a-9d31-4e7c-8a52-3f6b9d2e4c81",
  "hasChildren": false,
  "isCritical": false,
  "hasChat": false,
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection",
    "projectCode": "PRJ-4521"
  }
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.task",
  "id": "86d64a5b-109d-39c9-dd43-d7fffb6a1670",
  "displayName": "String",
  "planId": "String",
  "bucketId": "String",
  "goalIds": [
    "String"
  ],
  "status": "String",
  "priority": "Integer",
  "percentComplete": "Integer",
  "startDateTime": {
    "@odata.type": "microsoft.graph.dateWithOptionalTime"
  },
  "dueDateTime": {
    "@odata.type": "microsoft.graph.dateWithOptionalTime"
  },
  "finishDateTime": {
    "@odata.type": "microsoft.graph.dateWithOptionalTime"
  },
  "notes": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "creationInfo": {
    "@odata.type": "microsoft.graph.creationInfo"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "completedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "completedDateTime": "String (timestamp)",
  "recurrence": {
    "@odata.type": "microsoft.graph.plannerTaskRecurrence"
  },
  "archivalInfo": {
    "@odata.type": "microsoft.graph.plannerArchivalInfo"
  },
  "planView": {
    "@odata.type": "microsoft.graph.taskPlanView"
  },
  "personalView": {
    "@odata.type": "microsoft.graph.taskPersonalView"
  },
  "parentTaskId": "String",
  "hasChildren": "Boolean",
  "isCritical": "Boolean",
  "hasChat": "Boolean",
  "capabilities": {
    "@odata.type": "microsoft.graph.taskCapability"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
