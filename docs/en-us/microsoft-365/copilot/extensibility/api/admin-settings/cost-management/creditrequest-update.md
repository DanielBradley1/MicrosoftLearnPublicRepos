<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-update -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# Update creditRequest

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Update a [creditRequest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequest) object. Use this method to approve or reject a single credit request. To decide multiple credit requests in one call, use [batchRecordDecisions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-batchrecorddecisions).

The supported state transitions are `pending` to `approved` and `pending` to `rejected`. Requesting the current state is a no-op that returns `204 No Content` and preserves the ETag, `decisionBy`, `lastModifiedDateTime`, and `expirationDateTime`. The `If-Match` ETag is still checked for a no-op request, so a same-state request with a stale ETag returns `412 Precondition Failed`. A state change sets `decisionBy` and resets `expirationDateTime` to 90 days later.

In addition to the permissions in the following section, the signed-in user must have one of the following Microsoft Entra roles: Global Administrator, Billing Administrator, or AI Administrator.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotCostManagement-CreditReq.ReadWrite.All | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /copilot/costManagement/creditRequests/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| `Content-Type` | `application/json`. Required. |
| `If-Match` | The strong ETag of the credit request from the latest read, for example, `"7f94e342"`. Weak \(`W/`\) ETags and `*` aren't supported. Required. |

## Request body

In the request body, supply a JSON object with the following property. Only `state` can be updated; all other properties are read-only.

| Property | Type | Description |
| :--- | :--- | :--- |
| `state` | [creditRequestState](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequest#creditrequeststate-enumeration) | The target state. Use `approved` or `rejected`. |

## Response

If successful, this method returns a `204 No Content` response code and an `ETag` header. It doesn't return anything in the response body. The `ETag` value is updated when the state changes; for a same-state no-op, it's unchanged.

This method can also return the following errors:

- `400 Bad Request` with the `invalidRequest` error code if the requested state transition isn't supported, or if the `If-Match` header is malformed, is a weak \(`W/`\) ETag, or is `*`.
- `404 Not Found` with the `itemNotFound` error code if the credit request doesn't exist.
- `412 Precondition Failed` with the `preconditionFailed` error code if the `If-Match` ETag is stale, including for a same-state request. Read the credit request again and retry with the current ETag.
- `428 Precondition Required` with the `preconditionRequired` error code if the `If-Match` header is missing.

## Example

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/copilot/costManagement/creditRequests/9c424e3a-a83d-47ef-88ec-9192ec89f084
If-Match: "7f94e342"
Content-Type: application/json

{
  "state": "approved"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
ETag: "9ca5a72e"
```
