<!-- Source: https://learn.microsoft.com/en-us/graph/api/partners-billing-billedaggregatedusage-export?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# billedAggregatedUsage: export

Namespace: microsoft.graph.partners.billing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

This API is available for Cloud Solution Provider \(CSP\) partners only to access their billed and unbilled reconciliation data for a tenant. To learn more about the CSP program, see [Microsoft Cloud Solution Provider](https://learn.microsoft.com/en-us/partner-center/csp-overview).

Export billed aggregated Azure usage data for a specific invoice from a [billedAggregatedUsage](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-billedaggregatedusage?view=graph-rest-beta) resource.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PartnerBilling.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PartnerBilling.Read.All | Not available. |

## HTTP request

```http
POST /reports/partners/billing/aggregatedUsage/billed/export
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| invoiceId | String | The invoice ID for which to export billed aggregated Azure usage data. Required. |

## Response

If successful, this method returns a `202 Accepted` response code and a `Location` header that contains the URL to the long-running operation. You can check the status of the long-running operation by making a GET request to this URL that returns one of the following objects in the response body: [microsoft.graph.partners.billing.runningOperation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-runningoperation?view=graph-rest-beta), [microsoft.graph.partners.billing.exportSuccessOperation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-exportsuccessoperation?view=graph-rest-beta), or [microsoft.graph.partners.billing.failedOperation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-failedoperation?view=graph-rest-beta).

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/reports/partners/billing/aggregatedUsage/billed/export
Content-Type: application/json

{
  "invoiceId": "G000000"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/beta/reports/partners/billing/operations/9ab9cb54-d07f-4f52-9ea6-a09d7de52c14
```
