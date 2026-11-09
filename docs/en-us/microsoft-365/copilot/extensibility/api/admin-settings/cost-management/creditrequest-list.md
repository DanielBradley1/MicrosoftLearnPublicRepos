<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-list -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# List creditRequests

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Get a list of [creditRequest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequest) objects. The results exclude audit-only requests, including from `@odata.count`, and are always sorted newest first by `createdDateTime`.

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
GET /copilot/costManagement/creditRequests
```

## Optional query parameters

This method supports the `$select`, `$count`, `$top`, and `$filter` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

- `$select` accepts the following properties: `id`, `state`, `requestType`, `requestedBy`, `decisionBy`, `createdDateTime`, `lastModifiedDateTime`, `expirationDateTime`, and `serviceId`. Any other value returns a `400 Bad Request` response code.
- `$filter` supports only the `eq` operator on the properties in the following table. You can combine clauses with `and`, with at most one `state` clause and one `serviceId` clause, for example, `state eq 'pending' and serviceId eq 'workIQ'`.
- `$count=true` excludes audit-only requests from the count.
- `$top` accepts values from 1 to 200; the default page size is 50.

`$orderby` isn't supported because the order is fixed \(newest first\). `$expand`, `$skip`, `$search`, and delta queries aren't supported.

| Property | Operators | Value |
| :--- | :--- | :--- |
| `serviceId` | `eq` | A service identifier string literal, such as `'workIQ'` or `'cowork'`. Comparisons are case-insensitive. |
| `state` | `eq` | A [creditRequestState](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequest#creditrequeststate-enumeration) member as an unqualified string literal, for example `'pending'`. Comparisons are case-insensitive. The qualified form, such as `microsoft.graph.creditRequestState'pending'`, isn't supported and returns a `400 Bad Request` response code. |

If the service returns an `@odata.nextLink` property, follow that URL unchanged to get the next page.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [creditRequest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequest) objects in the response body. Each item includes an `@odata.etag` annotation that contains its current ETag.

If the list query fails, or if the count fails when `$count=true` is specified, this method returns a `503 Service Unavailable` response code with the `serviceNotAvailable` error code.

## Example

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/copilot/costManagement/creditRequests?$filter=state eq 'pending'&$select=id,state,requestType,requestedBy,createdDateTime,serviceId&$count=true&$top=50
```

### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#copilot/costManagement/creditRequests",
  "@odata.count": 2,
  "value": [
    {
      "@odata.etag": "\"7f94e342\"",
      "id": "9c424e3a-a83d-47ef-88ec-9192ec89f084",
      "state": "pending",
      "requestType": "additionalCredits",
      "requestedBy": {
        "user": {
          "id": "6f7f4b9a-2880-4bf6-a47e-374172421dab"
        }
      },
      "createdDateTime": "2026-08-14T16:10:00Z",
      "serviceId": "workIQ"
    },
    {
      "@odata.etag": "\"d8f36711\"",
      "id": "14cf7865-b566-40b6-a14f-c8332137b641",
      "state": "pending",
      "requestType": "firstTimeAccess",
      "requestedBy": {
        "user": {
          "id": "95c5d17d-27a5-4b42-bb91-85ed65e794b7"
        }
      },
      "createdDateTime": "2026-08-14T15:42:00Z",
      "serviceId": "cowork"
    }
  ]
}
```
