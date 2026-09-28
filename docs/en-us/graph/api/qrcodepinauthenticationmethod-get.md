<!-- Source: https://learn.microsoft.com/en-us/graph/api/qrcodepinauthenticationmethod-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-13 -->

# Get qrCodePinAuthenticationMethod

Namespace: microsoft.graph

Read the properties of a user's [qrCodePinAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethod?view=graph-rest-1.0) object. This returns the QR code PIN authentication method registered to the user.

Note

The PIN code is only returned at creation or reset time. For GET operations, the **code** property in the **pin** object returns `null`.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

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

```http
GET /users/{id | userPrincipalName}/authentication/qrCodePinMethod
```

## Optional query parameters

This method doesn't support optional query parameters to customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [qrCodePinAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethod?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/users/7c4999ca-a540-47ab-9ab9-8c362f5bf0fe/authentication/qrCodePinMethod
```

### Response

The following example shows the response.

> **Note:** The **image** property in the QR code objects returns `null` for GET operations because the QR code private key isn't stored on the server.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.qrCodePinAuthenticationMethod",
  "id": "6C2F8B36-B6F0-46FA-9548-1EBA48BEBBDE",
  "createdDateTime": "2026-01-27T12:00:00Z",
  "standardQRCode": {
    "id": "6C2F8B36-B6F0-46FA-9548-1EBA48BEBBDE",
    "image": null,
    "startDateTime": "2026-01-27T12:00:00Z",
    "expireDateTime": "2027-01-27T12:00:00Z",
    "createdDateTime": "2026-01-27T12:00:00Z",
    "lastUsedDateTime": "2026-01-30T08:15:00Z"
  },
  "temporaryQRCode": {
    "id": "8DF9D1B6-B4BD-4EF8-8E90-2CC63C549C80",
    "image": null,
    "startDateTime": "2026-01-30T08:00:00Z",
    "expireDateTime": "2026-01-30T18:00:00Z",
    "createdDateTime": "2026-01-30T08:00:00Z",
    "lastUsedDateTime": "2026-01-30T08:15:00Z"
  },
  "pin": {
    "code": null,
    "forceChangePinNextSignIn": false,
    "createdDateTime": "2026-01-27T12:00:00Z",
    "updatedDateTime": "2026-01-28T09:30:00Z"
  }
}
```
