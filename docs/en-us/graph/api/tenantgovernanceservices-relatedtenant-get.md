<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Get relatedTenant

Namespace: microsoft.graph

Read the properties and relationships of a [relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0) object.

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
GET /directory/tenantGovernance/relatedTenants/{relatedTenantId}
```

## Optional query parameters

This method doesn't support OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/directory/tenantGovernance/relatedTenants/{relatedTenantId}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.relatedTenant",
  "id": "aaaabbbb-0000-cccc-1111-dddd2222eeee",
  "createdDateTime": "2026-02-15T05:34:29.4426526Z",
  "isMicrosoftInfrastructure": false,
  "b2BRegistrationMetrics": {
    "initial": {
      "createdDateTime": "2026-02-13T20:54:25Z",
      "watermarkDateTime": "2026-02-12T00:00:00Z",
      "inboundTotalUsers": 1,
      "outboundTotalUsers": 0
    },
    "recent": {
      "updateDateTime": "2026-02-16T23:13:49Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundTotalUsers": 0,
      "outboundTotalUsers": 0
    }
  },
  "b2BSignInActivityMetrics": {
    "initial": {
      "createdDateTime": "2026-02-17T08:08:23Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundMonthlyTotalUsers": 1,
      "outboundMonthlyTotalUsers": 0,
      "inboundMonthlyTotalApplications": 10,
      "outboundMonthlyTotalApplications": 0
    },
    "recent": {
      "updateDateTime": "2026-02-17T08:08:23Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundMonthlyTotalUsers": 1,
      "outboundMonthlyTotalUsers": 0,
      "inboundMonthlyTotalApplications": 10,
      "outboundMonthlyTotalApplications": 0
    }
  },
  "appB2BSignInActivityMetrics": {
    "initial": {
      "createdDateTime": "2026-02-17T08:08:23Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundMonthlyTotalUsers": 1,
      "outboundMonthlyTotalUsers": 0,
      "inboundMonthlyTotalApplications": 1,
      "outboundMonthlyTotalApplications": 0
    },
    "recent": {
      "updateDateTime": "2026-02-17T08:08:23Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundMonthlyTotalUsers": 1,
      "outboundMonthlyTotalUsers": 0,
      "inboundMonthlyTotalApplications": 1,
      "outboundMonthlyTotalApplications": 0
    }
  },
  "multiTenantApplicationMetrics": {
    "initial": {
      "createdDateTime": "2026-01-01T00:00:00Z",
      "watermarkDateTime": "2026-12-30T04:00:00Z",
      "inboundMonthlyTotalApplications": 10,
      "outboundMonthlyTotalApplications": 0
    },
    "recent": {
      "updateDateTime": "2026-01-01T00:00:00Z",
      "watermarkDateTime": "2026-12-30T04:00:00Z",
      "inboundMonthlyTotalApplications": 10,
      "outboundMonthlyTotalApplications": 0
    }
  },
  "billingMetrics": {
    "initial": {
      "createdDateTime": "2025-10-02T12:09:40Z",
      "watermarkDateTime": "2025-10-01T00:00:00Z",
      "localAssociatedTenantCount": 2,
      "localAssociatedTenantBillingManagementActiveCount": 1,
      "localAssociatedTenantProvisioningActiveCount": 2,
      "localAssociatedTenantIds": [
        "/providers/Microsoft.Billing/billingAccounts/00000000-0000-0000-0000-000000000000:00000000-0000-0000-0000-000000000000_2019-05-31/associatedTenants/11111111-1111-1111-1111-111111111111",
        "/providers/Microsoft.Billing/billingAccounts/9a157b81-1503-516b-4fe8-7849e97ca70e:e6bd1c01-9e9b-4fa7-a9f1-6fe6cbad31fa_2019-05-31/associatedTenants/22222222-2222-2222-2222-222222222222"
      ],
      "foreignAssociatedTenantCount": 0,
      "foreignAssociatedTenantBillingManagementActiveCount": 0,
      "foreignAssociatedTenantProvisioningActiveCount": 0
    },
    "recent": {
      "updateDateTime": "2025-11-02T12:09:40Z",
      "watermarkDateTime": "2025-11-01T00:00:00Z",
      "localAssociatedTenantCount": 3,
      "localAssociatedTenantBillingManagementActiveCount": 2,
      "localAssociatedTenantProvisioningActiveCount": 2,
      "localAssociatedTenantIds": [
        "/providers/Microsoft.Billing/billingAccounts/00000000-0000-0000-0000-000000000000:00000000-0000-0000-0000-000000000000_2019-05-31/associatedTenants/11111111-1111-1111-1111-111111111111",
        "/providers/Microsoft.Billing/billingAccounts/9a157b81-1503-516b-4fe8-7849e97ca70e:e6bd1c01-9e9b-4fa7-a9f1-6fe6cbad31fa_2019-05-31/associatedTenants/22222222-2222-2222-2222-222222222222",
        "/providers/Microsoft.Billing/billingAccounts/ffffffff-ffff-ffff-ffff-ffffffffffff:eeeeeeee-eeee-eeee-eeee-eeeeeeeeeeee_2019-05-31/associatedTenants/33333333-3333-3333-3333-333333333333"
      ],
      "foreignAssociatedTenantCount": 1,
      "foreignAssociatedTenantBillingManagementActiveCount": 0,
      "foreignAssociatedTenantProvisioningActiveCount": 1,
    }
  }
}
```
