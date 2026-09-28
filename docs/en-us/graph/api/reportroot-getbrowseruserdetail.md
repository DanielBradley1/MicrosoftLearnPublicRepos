<!-- Source: https://learn.microsoft.com/en-us/graph/api/reportroot-getbrowseruserdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# reportRoot: getBrowserUserDetail

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a report that provides the browser \(Microsoft Edge\) used by users when they access the Microsoft 365 services over a selected period.

> **Note:** For details about different report views and names, see [Microsoft 365 Reports in the admin center - Microsoft browser usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/browser-usage-report).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Reports.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Reports.Read.All | Not available. |

> **Note:** For delegated permissions to allow apps to read service usage reports on behalf of a user, the tenant administrator must have assigned the user the appropriate Microsoft Entra ID limited administrator role. For more information, see [Authorization for APIs to read Microsoft 365 usage reports](https://learn.microsoft.com/en-us/graph/reportroot-authorization).

## HTTP request

```http
GET /reports/getBrowserUserDetail(period='{period_value}')
```

## Function parameters

In the request URL, provide the following parameter with a valid value.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| period | string | Specifies the length of time over which the report is aggregated. The supported values for {period\_value} are: `D7`, `D30`, `D90`, and `D180`. These values follow the format D*n* where *n* represents the number of days over which the report is aggregated. Required. |

## Optional query parameters

This method supports the `$format`, `$top`, and `$skipToken` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response. The default output type is `text/csv`. However, if you want to specify the output type, you can use the OData `$format` query parameter to set the default output to `text/csv` or `application/json`.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

### CSV

If successful, this method returns a `302 Found` response that redirects to a preauthenticated download URL for the report. That URL can be found in the `Location` header in the response.

Preauthenticated download URLs are only valid for a short period of time \(a few minutes\) and don't require an `Authorization` header.

The CSV file has the following headers for columns:

- Report Refresh Date
- User Principal Name
- Report Period
- Edge

### JSON

If successful, this method returns a `200 OK` response code and a JSON object in the response body.

The default page size for this request is 200 items.

## Examples

### Example 1: CSV output

Here's an example that outputs CSV.

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/reports/getBrowserUserDetail(period='D7')?$format=text/csv
```

#### Response

The following example shows the response.

```http
HTTP/1.1 302 Found
Content-Type: text/plain
Location: https://reports.office.com/data/download/JDFKdf2_eJXKS034dbc7e0t__XDe
```

Follow the 302 redirection and the CSV file that downloads have the following schema.

```http
HTTP/1.1 200 OK
Content-Type: application/octet-stream

Report Refresh Date, User Principal Name, Report Period, Edge
```

### Example 2: JSON output

Here's an example that returns JSON.

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/reports/getBrowserUserDetail(period='D7')?$format=application/json
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 304

{
  "@odata.nextLink": "https://graph.microsoft.com/beta/reports/getBrowserUserDetail(period='D7')?$format=application/json&$skiptoken=D07uj",
   "value":[
      {
         "reportRefreshDate":"2021-04-17",
         "userPrincipalName": "admin@contoso.com",
         "details":[
            {
               "reportPeriod":7,
               "edge":true
            }
         ]
      }
   ]
}
```
