<!-- Source: https://learn.microsoft.com/en-us/graph/api/plan-delete-tasks?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Delete task

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Delete a task object.

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
DELETE /planner/tasks_v2/{taskId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| If-Match | The complete ETag of the resource to update or delete. Required. |

Use the complete ETag returned by the latest read of this resource as the `If-Match` value. Don't construct or compare ETags yourself. A missing, invalid, or no-longer-usable ETag results in `412 Precondition Failed`. A conflicting change can result in `409 Conflict`; read the resource again and reconcile the changes before retrying. An older ETag doesn't necessarily fail when the service can merge nonconflicting changes.

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/beta/planner/tasks_v2/{taskId}
If-Match: {etag}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
