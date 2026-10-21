<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserservicebalance-list -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# List costManagementUserServiceBalances

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Get a list of per-service balance rows for a user, represented by [costManagementUserServiceBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserservicebalance) objects. Paging is continuation-based: follow the `@odata.nextLink` property for subsequent pages rather than using `$skip`.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotCostManagement-UserData.Read.All | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /copilot/costManagement/userBalances/{userId}/serviceBalances
```

## Optional query parameters

This method supports `$select`, `$top`, `$count`, `$orderby` \(on `serviceId`\), and `$filter` on `serviceId` \(`eq`, with the property on either side, or `in`, with the property on the left and a literal string collection on the right\) and `isConsumptionAllowed` \(`eq` only, with the property on either side\). Clauses combine with `and` only; repeated clauses on the same property are intersected, and a contradictory combination is valid and returns no rows. `serviceId` comparisons are case-sensitive. `ne`, `or`, `not`, functions, range comparisons, `in` on `isConsumptionAllowed`, and `null` comparisons aren't supported. `$skip` and `$search` aren't supported. For example, use `$filter=isConsumptionAllowed eq false`. `$top` is an upper bound, not a guaranteed page size. If the service returns an `@odata.nextLink` property, follow that complete URL unchanged; don't assume a page size or construct an offset.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [costManagementUserServiceBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserservicebalance) objects in the response body.

## Example

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/copilot/costManagement/userBalances/aa110000-0000-0000-0000-000000000000/serviceBalances?$filter=isConsumptionAllowed eq false
```

### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#copilot/costManagement/userBalances('aa110000-0000-0000-0000-000000000000')/serviceBalances",
  "value": [
    {
      "serviceId": "workIQ",
      "spendingPolicyId": "3f9e2c1a-0000-0000-0000-00000000c21b",
      "configuredPeriodLimit": { "@odata.type": "#microsoft.graph.limitedCostManagementQuantity", "value": 10000, "unit": "copilotCredit" },
      "configuredPerUserLimit": { "@odata.type": "#microsoft.graph.limitedCostManagementQuantity", "value": 500, "unit": "copilotCredit" },
      "effectiveCapacityQuantity": { "@odata.type": "#microsoft.graph.limitedCostManagementQuantity", "value": 0, "unit": "copilotCredit" },
      "consumedQuantity": 180,
      "remainingQuantity": { "@odata.type": "#microsoft.graph.limitedCostManagementQuantity", "value": 0, "unit": "copilotCredit" },
      "unit": "copilotCredit",
      "isConsumptionAllowed": false,
      "accessDecisionReason": "limitExhausted",
      "dataStatus": {
        "lastModifiedDateTime": "2026-07-27T09:15:00Z"
      }
    }
  ]
}
```
