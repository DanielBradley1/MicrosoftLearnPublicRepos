<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# billingMetricsBase resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

This is an abstract base type and does not appear directly in API responses. Use the concrete types [billingMetricsInitial](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsinitial?view=graph-rest-beta) or [billingMetricsRecent](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsrecent?view=graph-rest-beta).

Abstract base type that defines common properties for billing metrics.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| foreignAssociatedTenantBillingManagementActiveCount | String | The number of foreign associated tenants with active billing management. |
| foreignAssociatedTenantCount | String | The total number of foreign associated tenants. |
| foreignAssociatedTenantProvisioningActiveCount | String | The number of foreign associated tenants with active provisioning. |
| id | String | Unique identifier for the metrics snapshot. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| localAssociatedTenantBillingManagementActiveCount | String | The number of local associated tenants with active billing management. |
| localAssociatedTenantCount | String | The total number of local associated tenants. |
| localAssociatedTenantIds | Collection\(String\) | The list of local associated tenant IDs. |
| localAssociatedTenantProvisioningActiveCount | String | The number of local associated tenants with active provisioning. |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

Note

This abstract type is not returned in API responses. See concrete implementations.

```json
{
  "@odata.type": "#microsoft.graph.billingMetricsBase",
  "id": "String (identifier)",
  "watermarkDateTime": "String (timestamp)",
  "localAssociatedTenantCount": "String",
  "localAssociatedTenantBillingManagementActiveCount": "String",
  "localAssociatedTenantProvisioningActiveCount": "String",
  "localAssociatedTenantIds": ["String"],
  "foreignAssociatedTenantCount": "String",
  "foreignAssociatedTenantBillingManagementActiveCount": "String",
  "foreignAssociatedTenantProvisioningActiveCount": "String"
}
```
