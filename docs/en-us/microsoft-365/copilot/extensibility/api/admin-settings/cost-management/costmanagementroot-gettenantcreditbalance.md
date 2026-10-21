<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementroot-gettenantcreditbalance -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# costManagementRoot: getTenantCreditBalance

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Gets the tenant-wide Copilot credit balance snapshot, with one row per billing method.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotCostManagement.Read.All | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CopilotCostManagement.Read.All | Not supported. |

## HTTP request

```http
GET /copilot/costManagement/getTenantCreditBalance
```

## Optional query parameters

This method doesn't support any [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [costManagementTenantCreditBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementtenantcreditbalance) object in the response body.

## Example

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/copilot/costManagement/getTenantCreditBalance
```

### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.costManagementTenantCreditBalance",
  "billingMethodBalances": [
    {
      "billingMethod": "prepaidCredits",
      "purchasedQuantity": 100000,
      "consumedQuantity": 42150,
      "remainingQuantity": 57850,
      "unit": "copilotCredit",
      "dataStatus": {
        "lastModifiedDateTime": "2026-07-27T09:15:00Z"
      }
    }
  ]
}
```
