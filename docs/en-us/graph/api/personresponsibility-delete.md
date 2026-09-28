<!-- Source: https://learn.microsoft.com/en-us/graph/api/personresponsibility-delete?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Delete personResponsibility

Namespace: microsoft.graph

Deletes a [personResponsibility](https://learn.microsoft.com/en-us/graph/api/resources/personresponsibility?view=graph-rest-beta) object from a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.Read | AgentIdUser.ReadWrite.All, AgentIdUser.ReadWrite.IdentityParentedBy, User.Read.All, User.ReadBasic.All, User.ReadWrite, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | User.Read | User.ReadWrite |
| Application | Not supported. | Not supported. |

## HTTP request

```http
DELETE /me/responsibilities/{id}
DELETE /users/{id | userPrincipalName}/responsibilities/{id}
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

```http
DELETE https://graph.microsoft.com/beta/me/responsibilities/0fb4c1e3-c1e3-0fb4-e3c1-b40fe3c1b40f
```

### Response

```http
HTTP/1.1 204 No Content
```
