<!-- Source: https://learn.microsoft.com/en-us/graph/api/qrcode-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-13 -->

# Delete qrCode

Namespace: microsoft.graph

Delete a standard or temporary [qrCode](https://learn.microsoft.com/en-us/graph/api/resources/qrcode?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthenticationMethod.ReadWrite.All | UserAuthMethod-QR.ReadWrite, UserAuthMethod-QR.ReadWrite.All, UserAuthenticationMethod.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | UserAuthenticationMethod.ReadWrite.All | UserAuthMethod-QR.ReadWrite.All |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Authentication Administrator
- Privileged Authentication Administrator

When users manage their own authentication methods, the system prompts them to complete multi-factor authentication \(MFA\) if they last authenticated more than 10 minutes ago in the current session.

## HTTP request

Delete your own QR Code.

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

```http
DELETE /me/authentication/qrCodePinMethod/standardQRCode
DELETE /me/authentication/qrCodePinMethod/temporaryQRCode
```

Delete another user's QR Code.

Note

When calling the `/users/{id}` endpoint with `{id}` representing the signed-in user, the least privileged delegated permissions are *UserAuthenticationMethod.Read* for read operations and *UserAuthenticationMethod.ReadWrite* for write operations.

```http
DELETE /users/{id}/authentication/qrCodePinMethod/standardQRCode
DELETE /users/{id}/authentication/qrCodePinMethod/temporaryQRCode
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
DELETE https://graph.microsoft.com/v1.0/users/7c4999f7-9c25-4f8e-8b84-766eb28a1b49/authentication/qrCodePinMethod/standardQRCode
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
