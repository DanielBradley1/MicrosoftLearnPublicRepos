<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-getdestinationsummaries?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# reports: getDestinationSummaries

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get counts of the visits to the top [destination aggregations](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-destinationsummary?view=graph-rest-beta) as logged in Global Secure Access.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

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
GET /networkAccess/reports/getDestinationSummaries(startDateTime={startDateTime},endDateTime={endDateTime},aggregatedBy={aggregatedBy})
```

## Function parameters

In the request URL, provide the following query parameters with values. The following table shows the parameters that can be used with this function.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| startDateTime | DateTimeOffset | The date and time when the reporting period begins. |
| endDateTime | DateTimeOffset | The date and time when the reporting period ends. |
| aggregatedBy | microsoft.graph.networkaccess.aggregationFilter | The aggregation filter used for the summary. The possible values are: `transactions`, `users`,`devices`. Required. |
| trafficType | String | Traffic classification. The possible values are: `microsoft365`, `private`,`internet`. Required. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [microsoft.graph.networkaccess.destinationSummary](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-destinationsummary?view=graph-rest-beta) collection in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/networkAccess/reports/getDestinationSummaries (aggregatedBy='devices', startDateTime=2023-01-01T00:00:00Z,endDateTime=2023-01-31T00:00:00Z)
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.networkaccess.destinationSummary)",
  "value": [
    {
      "destination": "office365.com",
      "count": 100000
    },
    {
      "destination": "pluto.com",
      "count": 4949
    },
    {
      "destination": "yahoo.com",
      "count": 4000
    },
    {
      "destination": "sharepoint.com",
      "count": 989
    }
  ]
}
```
