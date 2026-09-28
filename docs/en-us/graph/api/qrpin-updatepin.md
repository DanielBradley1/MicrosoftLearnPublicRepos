<!-- Source: https://learn.microsoft.com/en-us/graph/api/qrpin-updatepin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-13 -->

# qrPin: updatePin

Namespace: microsoft.graph

Update the [qrPin](https://learn.microsoft.com/en-us/graph/api/resources/qrpin?view=graph-rest-1.0). Any user can update their own [qrPin](https://learn.microsoft.com/en-us/graph/api/resources/qrpin?view=graph-rest-1.0) without belonging to any administrator role.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.AccessAsUser.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Authentication Administrator
- Privileged Authentication Administrator

When users manage their own authentication methods, the system prompts them to complete multi-factor authentication \(MFA\) if they last authenticated more than 10 minutes ago in the current session.

## HTTP request

Update your own QR Code PIN.

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

```http
PATCH /me/authentication/qrCodePinMethod/pin/updatepin
```

Update another user's QR Code PIN.

Note

When calling the `/users/{id}` endpoint with `{id}` representing the signed-in user, the least privileged delegated permissions are *UserAuthenticationMethod.Read* for read operations and *UserAuthenticationMethod.ReadWrite* for write operations.

```http
PATCH /users/{usersId}/authentication/qrCodePinMethod/pin/updatepin
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| currentPin | String | the code of current [qrPin](https://learn.microsoft.com/en-us/graph/api/resources/qrpin?view=graph-rest-1.0). |
| newPin | String | the code of new [qrPin](https://learn.microsoft.com/en-us/graph/api/resources/qrpin?view=graph-rest-1.0). |

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/me/authentication/qrCodePinMethod/pin/updatePin
Content-Type: application/json

{
  "currentPin": "09599786",
  "newPin": "56745755"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
