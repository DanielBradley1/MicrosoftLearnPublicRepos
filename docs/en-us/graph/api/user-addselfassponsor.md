<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-addselfassponsor?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# user: addSelfAsSponsor

Namespace: microsoft.graph.identityGovernance

Add the signed-in [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) as a sponsor of a sponsorless guest user. The signed-in user must be a member user. This action is idempotent and returns `204 No Content` if the signed-in user is already a sponsor.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not required. | None. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

This action supports delegated access for work or school accounts only. Personal Microsoft accounts aren't supported. Application calls are rejected with `400 Bad Request`. The lifecycle workflows action doesn't check an additional named Graph scope or admin role.

The signed-in caller must exist and must not be a guest. The target must exist and must be a guest. Adding a sponsor is allowed only when the target has no sponsors, except that a caller who already sponsors the target receives a successful response.

## HTTP request

```http
POST /users/{guestUserId}/microsoft.graph.identityGovernance.addSelfAsSponsor
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `204 No Content` response code. It doesn't return anything in the response body.

## Examples

### Request

```http
POST https://graph.microsoft.com/v1.0/users/e4f5d67a-5a10-4c40-9734-0c5f2d83a1bf/microsoft.graph.identityGovernance.addSelfAsSponsor
```

### Response

```http
HTTP/1.1 204 No Content
```
