<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-removeselfassponsor?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# user: removeSelfAsSponsor

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Remove the signed-in [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) as a sponsor of a guest user.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not required. | None. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /users/{guestUserId}/microsoft.graph.identityGovernance.removeSelfAsSponsor
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `204 No Content` response code. It doesn't return anything in the response body. If the signed-in user isn't currently a sponsor of the guest user, the action returns `404 Not Found`.

## Examples

### Request

```http
POST https://graph.microsoft.com/beta/users/e4f5d67a-5a10-4c40-9734-0c5f2d83a1bf/microsoft.graph.identityGovernance.removeSelfAsSponsor
```

### Response

```http
HTTP/1.1 204 No Content
```
