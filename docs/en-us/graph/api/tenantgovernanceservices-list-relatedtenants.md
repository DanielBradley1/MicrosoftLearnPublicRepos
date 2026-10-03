<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-list-relatedtenants?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# List relatedTenants

Namespace: microsoft.graph

Get a list of [relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0) objects and their properties, including relationship metrics.

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
GET /directory/tenantGovernance/relatedTenants
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

If successful, this method returns a `200 OK` response code and a collection of [relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/directory/tenantGovernance/relatedTenants
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directory/tenantGovernance/relatedTenants",
  "value": [
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
      "multiTenantApplicationMetrics": null,
      "billingMetrics": null
    },
    {
      "@odata.type": "#microsoft.graph.relatedTenant",
      "id": "bbbbcccc-1111-dddd-2222-eeee3333ffff",
      "createdDateTime": "2026-02-16T05:35:45.2357127Z",
      "isMicrosoftInfrastructure": false,
      "b2BRegistrationMetrics": null,
      "b2BSignInActivityMetrics": null,
      "appB2BSignInActivityMetrics": null,
      "multiTenantApplicationMetrics": {
        "initial": {
          "createdDateTime": "2026-02-15T08:29:31Z",
          "watermarkDateTime": "2026-02-14T00:00:00Z",
          "inboundMonthlyTotalApplications": 10,
          "outboundMonthlyTotalApplications": 0
        },
        "recent": {
          "updateDateTime": "2026-02-15T08:29:31Z",
          "watermarkDateTime": "2026-02-14T00:00:00Z",
          "inboundMonthlyTotalApplications": 10,
          "outboundMonthlyTotalApplications": 0
        }
      },
      "billingMetrics": null
    }
  ]
}
```
