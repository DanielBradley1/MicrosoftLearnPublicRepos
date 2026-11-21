<!-- Source: https://learn.microsoft.com/en-us/graph/api/planner-list-tasks_v2?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# List tasks\_v2

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) objects and their properties.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.Read | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Tasks.Read.All | Not available. |

## HTTP request

```http
GET /planner/tasks_v2
```

## Optional query parameters

Use `$filter` to filter by `planId`, `bucketId`, `percentComplete`, `startDateTime`, or `dueDateTime`. For example, filter by `planId` to retrieve tasks in a specific plan.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/planner/tasks_v2?$filter=planId eq 'b3d9f9a2-3e14-4a4b-9b2b-6b6d9e6a2f31'
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.task",
      "id": "86d64a5b-109d-39c9-dd43-d7fffb6a1670",
      "displayName": "Product launch",
      "planId": "b3d9f9a2-3e14-4a4b-9b2b-6b6d9e6a2f31",
      "bucketId": "9c9c7a3d-5b7f-45e9-9df9-9f8b0f7edc9a",
      "status": "notStarted"
    }
  ]
}
```
