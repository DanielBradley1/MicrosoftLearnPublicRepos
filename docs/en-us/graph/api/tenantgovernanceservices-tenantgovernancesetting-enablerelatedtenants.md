<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-tenantgovernancesetting-enablerelatedtenants?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# tenantGovernanceSetting: enableRelatedTenants

Namespace: microsoft.graph

Enable the related tenants feature for tenant discovery. After calling this action, the **isRelatedTenantsEnabled** property of [tenantGovernanceSetting](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancesetting?view=graph-rest-1.0) is set to `true`, which allows the use of related tenant APIs.

Important

This action must be called before using any related tenant APIs. Related tenant APIs won't run successfully unless this feature is explicitly enabled.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TenantGovernance-Setting.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). *Tenant Governance Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /directory/tenantGovernance/settings/enableRelatedTenants
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/directory/tenantGovernance/settings/enableRelatedTenants
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
