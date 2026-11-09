<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementserviceusagerecord-get -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# Get costManagementServiceUsageRecord

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Retrieve one governed service's share of the tenant's consumption of Copilot Credits for one completed UTC day, represented by a [costManagementServiceUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementserviceusagerecord) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotCostManagement-Reports.Read.All | CopilotCostManagement.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CopilotCostManagement-Reports.Read.All | CopilotCostManagement.Read.All |

## HTTP request

```http
GET /copilot/costManagement/usageReports/serviceUsageRecords/{serviceId}?startDate={startDate}&endDate={endDate}
```

## Query parameters

In the request URL, provide the following required query parameters with values. The range must select exactly one completed UTC day. Current-day, future, and multi-day ranges are rejected, not clamped. Validation doesn't enforce an oldest permitted `startDate`.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `endDate` | Date | Required. The exclusive end of the reporting day, in `YYYY-MM-DD` format. Must equal `startDate` plus one day, and its UTC midnight must not be later than the current time. |
| `startDate` | Date | Required. The inclusive start of the reporting day, in `YYYY-MM-DD` format \(UTC\). |

## Optional query parameters

This method supports the `$select` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [costManagementServiceUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementserviceusagerecord) object in the response body.

If no usage is represented for the service on the requested day, the method returns a `404 Not Found` response with the `usageDataUnavailable` error code. This response isn't proof of zero consumption. If `startDate` or `endDate` is missing or malformed, or if the range doesn't select exactly one completed UTC day \(for example, a current-day, future, or multi-day range\), the method returns a `400 Bad Request` response with the `unsupportedQuery` error code. If the usage source fails, the method returns a `503 Service Unavailable` response with the `sourceUnavailable` error code; don't treat it as zero consumption.

## Example

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/copilot/costManagement/usageReports/serviceUsageRecords/cowork?startDate=2026-07-01&endDate=2026-07-02
```

### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#copilot/costManagement/usageReports/serviceUsageRecords/$entity",
  "serviceId": "cowork",
  "consumedQuantity": 184320.5,
  "unit": "copilotCredit"
}
```
