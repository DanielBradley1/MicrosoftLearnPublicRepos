<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-crosstenantsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-16 -->

# crossTenantSummary resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A summary for cross-tenant access counts for Microsoft 365 traffic.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authTransactionCount | Int32 | The total number of authentication sessions between startDateTime and endDateTime. |
| deviceCount | Int32 | The number of unique devices that performed cross-tenant access. |
| newTenantCount | Int32 | The number of unique tenants that were accessed between endDateTime and discoveryPivotDateTime, but weren't accessed between discoveryPivotDateTime and startDateTime. |
| rarelyUsedTenantCount | Int32 | The number of tenants that are rarely used. |
| tenantCount | Int32 | The number of unique tenants that were accessed, not including the device's tenant. |
| userCount | Int32 | The number of unique users that performed cross-tenant access. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.crossTenantSummary",
  "authTransactionCount": "Integer",
  "tenantCount": "Integer",
  "newTenantCount": "Integer",
  "userCount": "Integer",
  "deviceCount": "Integer",
  "rarelyUsedTenantCount": "Integer"
}
```
