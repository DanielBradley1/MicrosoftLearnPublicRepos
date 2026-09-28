<!-- Source: https://learn.microsoft.com/en-us/graph/api/qrcode-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-24 -->

# Create or Update QR code

Namespace: microsoft.graph

Create a standard or temporary QR code, if there is no active QR code, or update a standard QR code. Only the **expireDateTime** property can be updated for a standard QR code.

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

Update your own QR Code.

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

```http
PATCH /me/authentication/qrCodePinMethod/standardQRCode
PATCH /me/authentication/qrCodePinMethod/temporaryQRCode
```

Update another user's QR Code.

Note

When calling the `/users/{id}` endpoint with `{id}` representing the signed-in user, the least privileged delegated permissions are *UserAuthenticationMethod.Read* for read operations and *UserAuthenticationMethod.ReadWrite* for write operations.

```http
PATCH /users/{id}/authentication/qrCodePinMethod/standardQRCode
PATCH /users/{id}/authentication/qrCodePinMethod/temporaryQRCode
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| startDateTime | DateTimeOffset | The date and time when the QR code becomes available to use. |
| expireDateTime | DateTimeOffset | The QR code expires and becomes unusable based on this property's value. This property can be modified for a standard QR code up to the maximum lifetime of 395 days from the **startDateTime** value. This property can't be modified for a temporary QR code. |

## Response

If successful, this method returns a `201 Created` response code and an updated [qrCode](https://learn.microsoft.com/en-us/graph/api/resources/qrcode?view=graph-rest-1.0) object in the response body. The QR code image is returned only when creating a QR code object. It's not returned when updating a standard QR code object.

## Examples

### Example 1: Create a standard QR code

#### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/users/7c4999f7-9c25-4f8e-8b84-766eb28a1b49/authentication/qrCodePinMethod/standardQRCode
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.qrCode",
  "expireDateTime": "2025-12-19T12:00:00Z",
  "startDateTime": "2025-01-01T12:00:00Z",
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.qrCode",
  "id": "44f2f040-ea9d-4283-9e7b-b63ddae391a9",
  "expireDateTime": "2025-12-19T12:00:00Z",
  "startDateTime": "2025-01-01T12:00:00Z",
  "createdDateTime": "2025-03-04T21:27:46.9771036Z",
  "lastUsedDateTime": "0001-01-01T00:00:00Z",
  "image": {
    "@odata.type": "#microsoft.graph.qrCodeImageDetails",
    "binaryValue": "SGVsbG9Xb3JsZCE=",
    "version": 1,
    "errorCorrectionLevel": "l",
    "rawContent": "SGVsbG9Xb3JsZCEyTXlSYXdDb250ZW50"
  }
}
```

### Example 2: Update a standard QR code

#### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/me/authentication/qrCodePinMethod/standardQRCode
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.qrCode",
  "expireDateTime": "2025-12-01T12:00:00Z",
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.qrCode",
  "id": "44f2f040-ea9d-4283-9e7b-b63ddae391a9",
  "expireDateTime": "2025-12-01T12:00:00Z",
  "startDateTime": "2025-01-01T12:00:00Z",
  "createdDateTime": "2025-03-04T21:27:46.9771036Z",
  "lastUsedDateTime": "0001-01-01T00:00:00Z",
  "image": null
}
```
