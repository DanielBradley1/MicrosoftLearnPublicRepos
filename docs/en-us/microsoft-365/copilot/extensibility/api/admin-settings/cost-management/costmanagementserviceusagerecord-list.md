<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementserviceusagerecord-list -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# List costManagementServiceUsageRecords

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Get a list of [costManagementServiceUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementserviceusagerecord) objects that report each governed service's share of the tenant's consumption of Copilot Credits for one completed UTC day. The collection is paged even though the set of governed services is small today: follow the `@odata.nextLink` property for subsequent pages rather than using `$skip`.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotCostManagement-Reports.Read.All | CopilotCostManagement.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CopilotCostManagement-Reports.Read.All | CopilotCostManagement.Read.All |

## HTTP request

```http
GET /copilot/costManagement/usageReports/serviceUsageRecords?startDate={startDate}&endDate={endDate}
```

## Query parameters

In the request URL, provide the following required query parameters with values. The range must select exactly one completed UTC day. Current-day, future, and multi-day ranges are rejected, not clamped. Validation doesn't enforce an oldest permitted `startDate`.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `endDate` | Date | Required. The exclusive end of the reporting day, in `YYYY-MM-DD` format. Must equal `startDate` plus one day, and its UTC midnight must not be later than the current time. |
| `startDate` | Date | Required. The inclusive start of the reporting day, in `YYYY-MM-DD` format \(UTC\). |

## Optional query parameters

This method supports the `$count`, `$filter` \(on `serviceId`, which supports only the `eq` operator\), `$orderby` \(on `consumedQuantity` only, `asc` or `desc`\), `$select`, and `$top` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response. Ties in `consumedQuantity` are broken internally; ordering on `serviceId` isn't supported. `$skip` and `$search` aren't supported.

`$top` accepts an integer from 1 through 100, and the default is 10. Values outside that range are rejected with a `400 Bad Request` response, not capped. `$top` is an upper bound, not a guaranteed page size. If the service returns an `@odata.nextLink` property, follow that complete URL unchanged; don't construct an offset. The continuation keeps the original date range, filter, and order, but it isn't a point-in-time snapshot.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [costManagementServiceUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementserviceusagerecord) objects in the response body.

If `startDate` or `endDate` is missing, malformed, or doesn't select exactly one completed UTC day, or if the request uses an unsupported query option, a `$top` value outside 1 through 100, or a mismatched continuation token, the method returns a `400 Bad Request` response with the `unsupportedQuery` error code. The service rejects the request before it reads the usage source. If the usage source fails, the method returns a `503 Service Unavailable` response with the `sourceUnavailable` error code; don't treat it as zero consumption.

## Example

### Request

The following example shows a request that splits the tenant's consumption on July 1, 2026, by service, ordered from highest to lowest consumption.

```http
GET https://graph.microsoft.com/beta/copilot/costManagement/usageReports/serviceUsageRecords?startDate=2026-07-01&endDate=2026-07-02&$orderby=consumedQuantity desc
```

### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.costManagementServiceUsageRecord)",
  "value": [
    {
      "serviceId": "cowork",
      "consumedQuantity": 184320.5,
      "unit": "copilotCredit"
    },
    {
      "serviceId": "workIQ",
      "consumedQuantity": 42980.0,
      "unit": "copilotCredit"
    }
  ]
}
```
