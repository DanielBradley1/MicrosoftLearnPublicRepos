<!-- Source: https://learn.microsoft.com/en-us/graph/api/accessdriftreport-downloadfile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# accessDriftReport: downloadFile

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Download the latest tenant-wide access drift report file directly. The response streams the raw file bytes without exposing a SAS URI. The report includes all catalogs and resources for the specified resource type.

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
POST /identityGovernance/insights/accessDriftReport/microsoft.graph.downloadFile
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
| request | [accessDriftReportRequest](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftreportrequest?view=graph-rest-beta) | Required. The access drift report request. The request must include the **resourceType** and **reportFormat** properties. This action doesn't support filtering by catalog or resource. To retrieve catalog-scoped access drift data, use the access drift summary and details APIs with a catalog filter. |

## Response

If successful, this action returns a `200 OK` response code and the report file content in the response body. The response sets `Content-Disposition: attachment` with the filename.

If the requested report has not been generated yet, this action returns a `202 Accepted` response code with no response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/identityGovernance/insights/accessDriftReport/microsoft.graph.downloadFile
Content-Type: application/json

{
  "request": {
    "resourceType": "group",
    "reportFormat": "csv"
  }
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: text/csv
Content-Disposition: attachment; filename="accessDriftReport_group_generatedOn_2026-10-09_tenantId_00000000-0000-0000-0000-000000000001.csv"

resourceId,resourceName,resourceType,catalogIdentifier,catalogName,driftType,identityId,principalName
grp-hr-001,HR Team,group,cat-002,HR catalog,unauthorized,user-001,jane@contoso.com
```
