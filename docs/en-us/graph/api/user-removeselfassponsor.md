<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-removeselfassponsor?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# user: removeSelfAsSponsor

Namespace: microsoft.graph.identityGovernance

Remove the signed-in [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) as a sponsor of a guest user.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not required. | None. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

This action supports delegated access for work or school accounts only. Personal Microsoft accounts aren't supported. Application calls are rejected with `400 Bad Request`. The lifecycle workflows action doesn't check an additional named Graph scope or admin role.

The signed-in caller must exist and must not be a guest. The target must exist and must be a guest. The action removes only the signed-in caller's sponsorship; it doesn't remove any other sponsor.

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
POST https://graph.microsoft.com/v1.0/users/e4f5d67a-5a10-4c40-9734-0c5f2d83a1bf/microsoft.graph.identityGovernance.removeSelfAsSponsor
```

### Response

```http
HTTP/1.1 204 No Content
```
