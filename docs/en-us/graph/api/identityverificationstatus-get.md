<!-- Source: https://learn.microsoft.com/en-us/graph/api/identityverificationstatus-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Get identityVerificationStatus

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read a user's [identityVerificationStatus](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationstatus?view=graph-rest-beta), including recent verification events. The response automatically includes up to 10 events, ordered by recency.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

The following permissions apply to reading another user's status.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IdentityVerification.Read.All | IdentityVerification.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IdentityVerification.Read.All | IdentityVerification.ReadWrite.All |

To read only the signed-in user's status through `/me`, use the `IdentityVerification.Read` delegated permission. This permission doesn't grant access to other users' status.

## HTTP request

Get the signed-in user's status.

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

```http
GET /me/identityVerificationStatus
```

Get a specified user's status.

```http
GET /users/{user-id}/identityVerificationStatus
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [identityVerificationStatus](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationstatus?view=graph-rest-beta) object in the response body.

The service doesn't return an `expired` state. Compare **expiryDateTime**, or an event's **verification.expiresDateTime**, with the current time to determine expiry.

## Examples

### Example 1: Get a user's identity verification status

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/users/c2b3a4d5-6e7f-4890-a123-4567890abcde/identityVerificationStatus
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.identityVerificationStatus",
  "id": "c2b3a4d5-6e7f-4890-a123-4567890abcde",
  "state": "verified",
  "lastVerifiedDateTime": "2026-01-18T03:10:21Z",
  "expiryDateTime": "2027-01-18T03:10:21Z",
  "verificationEvents": [
    {
      "id": "9c2d5e61-1a3b-4a2f-9f6e-2f8b6c4d91aa",
      "verification": {
        "state": "verified",
        "verifiedIdProfileId": "b3c4d5e6-f7a8-4901-a234-56789abcdef0",
        "externalCredentialId": "urn:pic:73b78a00-5b9e-4f8c-85dd-b60a08dc1123",
        "source": "Contoso Identity Services",
        "issuedDateTime": "2026-01-18T03:00:00Z",
        "verifiedDateTime": "2026-01-18T03:10:21Z",
        "expiresDateTime": "2027-01-18T03:10:21Z"
      },
      "lifecycle": {
        "source": "entra",
        "state": "active",
        "invalidatedDateTime": null
      },
      "overrideDetails": null
    }
  ]
}
```
