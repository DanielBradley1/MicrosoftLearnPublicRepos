<!-- Source: https://learn.microsoft.com/en-us/graph/api/qrcode-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-13 -->

# Get qrCode

Namespace: microsoft.graph

Read the properties and relationships of a [qrCode](https://learn.microsoft.com/en-us/graph/api/resources/qrcode?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthMethod-QR.Read | UserAuthenticationMethod.ReadWrite.All, UserAuthenticationMethod.Read, UserAuthenticationMethod.Read.All, UserAuthenticationMethod.ReadWrite, UserAuthMethod-QR.Read.All, UserAuthMethod-QR.ReadWrite, UserAuthMethod-QR.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | UserAuthMethod-QR.Read.All | UserAuthenticationMethod.ReadWrite.All, UserAuthenticationMethod.Read.All, UserAuthMethod-QR.ReadWrite.All |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Authentication Administrator
- Privileged Authentication Administrator

## HTTP request

Retrieve your own QR Code.

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

```http
GET /me/authentication/qrCodePinMethod/standardQRCode
GET /me/authentication/qrCodePinMethod/temporaryQRCode
```

Retrieve another user's QR Code.

Note

When calling the `/users/{id}` endpoint with `{id}` representing the signed-in user, the least privileged delegated permissions are *UserAuthenticationMethod.Read* for read operations and *UserAuthenticationMethod.ReadWrite* for write operations.

```http
GET /users/{id}/authentication/qrCodePinMethod/standardQRCode
GET /users/{id}/authentication/qrCodePinMethod/temporaryQRCode
```

## Optional query parameters

This method doesn't support OData query parameters.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [qrCode](https://learn.microsoft.com/en-us/graph/api/resources/qrcode?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```msgraph
GET https://graph.microsoft.com/v1.0/users/7c4999f7-9c25-4f8e-8b84-766eb28a1b49/authentication/qrCodePinMethod/standardQRCode
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.qrCode",
    "id": "cb960eac-7a22-1979-ec68-1ec73264ae8d",
    "expireDateTime": "2025-01-22T12:00:00Z",
    "startDateTime": "2024-02-01T00:00:00Z",
    "createdDateTime": "2024-02-01T19:58:51.2210909Z",
    "lastUsedDateTime": "0001-01-01T00:00:00Z",
    "image": null
  }
}
```
