<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-webcategoryreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# reports: webCategoryReport

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the [number of users, devices, and transactions for destination URLs](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategoriessummary?view=graph-rest-beta), grouped by web category.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccessPolicy.Read.All | NetworkAccessPolicy.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Global Secure Access Log Reader
- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
GET /networkAccessRoot/reports/webCategoryReport(startDateTime={startDateTime},endDateTime={endDateTime})
```

## Function parameters

In the request URL, provide the following query parameters with values. The following table shows the parameters that can be used with this function.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| startDateTime | DateTimeOffset | The date and time when the reporting period begins. |
| endDateTime | DateTimeOffset | The date and time when the reporting period ends. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [microsoft.graph.networkaccess.webCategoriesSummary](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategoriessummary?view=graph-rest-beta) collection in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/networkaccess/reports/webCategoriesReport(startDateTime=2023-08-20T12:12:59.076Z, endDateTime=2023-08-21T12:12:59.076Z) 
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
 "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.networkaccess.webCategoriesSummary)",
 "value": [
   {
     "webCategory": {
       "displayName": "Arts",
       "name": "arts",
       "group": "general surfing"
     },
     "userCount": 10,
     "deviceCount": 12,
     "transactionCount": 100
   }
 ]
}  
```
