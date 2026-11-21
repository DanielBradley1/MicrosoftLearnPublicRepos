<!-- Source: https://learn.microsoft.com/en-us/graph/api/identityverificationevent-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Update identityVerificationEvent

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Apply or update the administrative override reason on an [identityVerificationEvent](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationevent?view=graph-rest-beta). Only **overrideDetails.reason** can be updated. The service sets **actorType**, **actorId**, and **overriddenDateTime** from the caller's identity on each successful update.

This operation doesn't change the verification facts, lifecycle state, or the user's aggregate verification status.

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
PATCH /users/{user-id}/identityVerificationStatus/verificationEvents/{identityVerificationEvent-id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON object containing **overrideDetails.reason**.

| Property | Type | Description |
| :--- | :--- | :--- |
| overrideDetails | [verificationEventOverride](https://learn.microsoft.com/en-us/graph/api/resources/verificationeventoverride?view=graph-rest-beta) | An object containing the **reason** for the override, up to 500 characters. Don't supply actor information or timestamps; the service sets those properties. |

Attempts to update any other property, including **id**, **verification**, **lifecycle**, or the server-managed override properties, return `400 Bad Request` with the error code `propertyNotPatchable`.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Update an override reason

#### Request

The following example applies an administrative override reason.

```http
PATCH https://graph.microsoft.com/beta/users/c2b3a4d5-6e7f-4890-a123-4567890abcde/identityVerificationStatus/verificationEvents/9c2d5e61-1a3b-4a2f-9f6e-2f8b6c4d91aa
Content-Type: application/json

{
  "overrideDetails": {
    "reason": "In-person identity proofing confirmed by help desk"
  }
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
