<!-- Source: https://learn.microsoft.com/en-us/graph/api/identityverificationstatus-post-verificationevents?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Create identityVerificationEvent

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Record an [identityVerificationEvent](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationevent?view=graph-rest-beta) in a user's [identityVerificationStatus](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationstatus?view=graph-rest-beta). The service recomputes the user's aggregate status when it records the event.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IdentityVerification.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IdentityVerification.ReadWrite.All | Not available. |

## HTTP request

```http
POST /users/{user-id}/identityVerificationStatus/verificationEvents
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [identityVerificationEvent](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationevent?view=graph-rest-beta) object.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Required. The client-supplied event identifier, which also acts as an idempotency key. |
| lifecycle | [verificationEventLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/verificationeventlifecycle?view=graph-rest-beta) | Required. Supply **source** to identify the source of the event. The service sets **state** and **invalidatedDateTime**. |
| overrideDetails | [verificationEventOverride](https://learn.microsoft.com/en-us/graph/api/resources/verificationeventoverride?view=graph-rest-beta) | Optional. Supply **reason** for an administrative or programmatic override. The service sets the actor information and timestamp. |
| verification | [verificationEventDetail](https://learn.microsoft.com/en-us/graph/api/resources/verificationeventdetail?view=graph-rest-beta) | Required. The verification facts. Supply **state** as `issued` or `verified`. For a completed verification, supply **source** and **verifiedDateTime**. These values can be `null` when the state is `issued`. The **issuedDateTime** property is optional. |

The event ID enables safe retries. Repeating an existing event ID with the same verification and lifecycle facts returns `204 No Content`. A mismatched replay returns `409 Conflict`, except for the supported promotion of an event from `issued` to `verified`. Don't use event PATCH to change verification facts.

## Response

If successful, this method returns a `201 Created` response code and an [identityVerificationEvent](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationevent?view=graph-rest-beta) object in the response body. An equivalent replay returns `204 No Content` without a response body.

## Examples

### Example 1: Record a completed identity verification

#### Request

The following example records a completed verification.

```http
POST https://graph.microsoft.com/beta/users/c2b3a4d5-6e7f-4890-a123-4567890abcde/identityVerificationStatus/verificationEvents
Content-Type: application/json

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
    "source": "entra"
  }
}
```

#### Response

The following example shows the response for a newly created event.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.identityVerificationEvent",
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
```
