<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-refreshstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# relatedTenant: refreshStatus

Namespace: microsoft.graph

Get the status of the most recent [related tenants refresh operation](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-refresh?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TenantGovernance-RelatedTenant.Read.All | TenantGovernance-RelatedTenant.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TenantGovernance-RelatedTenant.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). The following least privileged roles are supported for this operation.

- Tenant Governance Administrator
- Global Reader
- Tenant Governance Reader

## HTTP request

```http
GET /directory/tenantGovernance/relatedTenants/refreshStatus
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [relatedTenantsRefreshStatus](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenantsrefreshstatus?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/directory/tenantGovernance/relatedTenants/refreshStatus
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.relatedTenantsRefreshStatus",
  "isFirstRefresh": false,
  "mostRecentRefreshDateTime": "2026-09-14T18:30:00Z",
  "mostRecentRefreshRequestStatus": "Completed"
}
```
