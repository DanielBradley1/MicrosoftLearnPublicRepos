<!-- Source: https://learn.microsoft.com/en-us/graph/api/task-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Get task\_v2

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read the properties and relationships of [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.Read | Tasks.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Tasks.Read.All | Tasks.ReadWrite.All |

## HTTP request

```http
GET /planner/tasks_v2/{taskId}
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/planner/tasks_v2/{taskId}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
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
}
```
