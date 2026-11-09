<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-get -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# Get creditRequest

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Retrieve the properties of a [creditRequest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequest) object. The response includes the current ETag of the credit request, which you need to [update](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-update) it.

In addition to the permissions in the following section, the signed-in user must have one of the following Microsoft Entra roles: Billing Administrator, Global Administrator, AI Administrator, Global Reader, or AI Reader.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotCostManagement-CreditReq.Read.All | CopilotCostManagement-CreditReq.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /copilot/costManagement/creditRequests/{id}
```

## Optional query parameters

This method supports the `$select` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response. `$select` accepts the following properties: `id`, `state`, `requestType`, `requestedBy`, `decisionBy`, `createdDateTime`, `lastModifiedDateTime`, `expirationDateTime`, and `serviceId`. Any other value returns a `400 Bad Request` response code.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [creditRequest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequest) object in the response body. The current ETag is returned in the `ETag` response header and as the `@odata.etag` annotation in the response body.

If the credit request doesn't exist, this method returns a `404 Not Found` response code with the `itemNotFound` error code.

## Example

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/copilot/costManagement/creditRequests/9c424e3a-a83d-47ef-88ec-9192ec89f084
```

### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
ETag: "7f94e342"
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#copilot/costManagement/creditRequests/$entity",
  "@odata.etag": "\"7f94e342\"",
  "id": "9c424e3a-a83d-47ef-88ec-9192ec89f084",
  "state": "pending",
  "requestType": "additionalCredits",
  "requestedBy": {
    "user": {
      "id": "6f7f4b9a-2880-4bf6-a47e-374172421dab"
    }
  },
  "decisionBy": null,
  "createdDateTime": "2026-08-14T16:10:00Z",
  "lastModifiedDateTime": "2026-08-14T16:10:00Z",
  "expirationDateTime": "2026-11-12T16:10:00Z",
  "serviceId": "workIQ"
}
```
