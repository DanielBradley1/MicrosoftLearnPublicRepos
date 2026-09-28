<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentuser-delete-manager?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# Remove manager \(for agentUser\)

Namespace: microsoft.graph

Remove an [agentUser's](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0) manager.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentIdUser.ReadWrite.IdentityParentedBy | AgentIdUser.ReadWrite.All, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentIdUser.ReadWrite.IdentityParentedBy | AgentIdUser.ReadWrite.All, User.ReadWrite.All |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Agent ID Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
DELETE /users/{usersId}/manager/{id}/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/v1.0/users/{usersId}/manager/{id}/$ref
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
