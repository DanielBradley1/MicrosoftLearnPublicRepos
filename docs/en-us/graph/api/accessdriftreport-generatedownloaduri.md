<!-- Source: https://learn.microsoft.com/en-us/graph/api/accessdriftreport-generatedownloaduri?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# accessDriftReport: generateDownloadUri

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Generate a time-limited download URI for the latest tenant-wide access drift report. The returned user-delegation SAS URI targets the single-file Parquet report, includes all catalogs and resources for the specified resource type, and is valid for 24 hours.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.Read.All | EntitlementManagement.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.Read.All | EntitlementManagement.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Directory Readers
- Reports Reader
- Identity Governance Administrator

## HTTP request

```http
POST /identityGovernance/insights/accessDriftReport/microsoft.graph.generateDownloadUri
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| request | [accessDriftReportRequest](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftreportrequest?view=graph-rest-beta) | Required. The access drift report request. The request must include the **resourceType** and **reportFormat** properties. Use `parquet` for **reportFormat** because the generated URI targets the single-file Parquet report. This action doesn't support filtering by catalog or resource. To retrieve catalog-scoped access drift data, use the access drift summary and details APIs with a catalog filter. |

## Response

If successful, this action returns a `200 OK` response code and an [accessDriftReport](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftreport?view=graph-rest-beta) in the response body.

If the requested report has not been generated yet, this action returns a `202 Accepted` response code with no response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/identityGovernance/insights/accessDriftReport/microsoft.graph.generateDownloadUri
Content-Type: application/json

{
  "request": {
    "resourceType": "application",
    "reportFormat": "parquet"
  }
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.accessDriftReport",
  "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "downloadUri": "https://storage.example.com/reports/access-drift-report.parquet?sv=2025-01-05&sig=aBcDeFgH",
  "expiresAt": "2026-08-29T16:00:00Z",
  "resourceType": "application"
}
```
