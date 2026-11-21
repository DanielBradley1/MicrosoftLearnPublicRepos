<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-attest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# user: attest

Namespace: microsoft.graph.identityGovernance

Attest to the continued need for a guest [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) in the organization.

## Permissions

This API supports delegated access only. Application \(app-only\) access isn't supported.

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-Guests.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

Guest user attestation supports delegated access only. Application access is rejected even with the `LifecyclePolicies-Guests.ReadWrite.All` application permission. No role, ownership, or sponsorship grants an application an exception.

The lifecycle workflows service accepts either of the following delegated authorization paths:

- **Administrator:** Both the `LifecyclePolicies-Guests.ReadWrite.All` delegated scope and a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) are required. *Lifecycle Workflows Administrator* is the least privileged role supported for this path. Scope alone or role alone is insufficient. Global Reader doesn't qualify.
- **Sponsor:** The signed-in user must be a direct sponsor of the target guest or a direct member of a group sponsoring that guest. This path doesn't additionally require the preceding scope or admin role in the lifecycle workflows handler. Sponsorship must be successfully verified; a failed or forbidden sponsorship lookup doesn't grant access.

Ownership isn't an authorization path. The target user must exist, be a guest, and have an enabled account. Requests must also satisfy Microsoft Graph authentication and permission validation.

## HTTP request

```http
POST /users/{guestUserId}/microsoft.graph.identityGovernance.attest
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
POST https://graph.microsoft.com/v1.0/users/e4f5d67a-5a10-4c40-9734-0c5f2d83a1bf/microsoft.graph.identityGovernance.attest
```

### Response

```http
HTTP/1.1 204 No Content
```
