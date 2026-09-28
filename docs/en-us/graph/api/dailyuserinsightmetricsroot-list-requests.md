<!-- Source: https://learn.microsoft.com/en-us/graph/api/dailyuserinsightmetricsroot-list-requests?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# List daily requests

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of daily [user requests](https://learn.microsoft.com/en-us/graph/api/resources/userrequestsmetric?view=graph-rest-beta) on apps registered in your tenant configured for Microsoft Entra External ID for customers.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Insights-UserMetric.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Insights-UserMetric.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator
- Company Administrator
- Global Readers
- Reports Reader
- Security Administrator
- Security Operator
- Security Reader

## HTTP request

```http
GET /reports/userInsights/daily/requests
```

## Optional query parameters

This method supports the `$filter` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [userRequestsMetric](https://learn.microsoft.com/en-us/graph/api/resources/userrequestsmetric?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/reports/userInsights/daily/requests
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.userRequestsMetric",
      "id": "dd1b6cfa-6715-25f6-c864-9c9bc39ba36f",
      "factDate": "2023-09-01",
      "requestCount": 11429
    }
  ]
}
```
