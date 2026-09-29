<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsinitial?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# billingMetricsInitial resource type

Namespace: microsoft.graph

Represents the initial snapshot of billing metrics captured when the [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0) was first discovered, establishing a baseline for billing account associations and associated tenant connection counts.

Inherits from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Timestamp that represents when billing metrics are initially aggregated for the related tenant. |
| foreignAssociatedTenantBillingManagementActiveCount | String | The number of foreign associated tenants with active billing management. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-1.0). |
| foreignAssociatedTenantCount | String | The total number of foreign associated tenants. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-1.0). |
| foreignAssociatedTenantProvisioningActiveCount | String | The number of foreign associated tenants with active provisioning. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-1.0). |
| localAssociatedTenantBillingManagementActiveCount | String | The number of local associated tenants with active billing management. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-1.0). |
| localAssociatedTenantCount | String | The total number of local associated tenants. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-1.0). |
| localAssociatedTenantIds | Collection\(String\) | The list of local associated tenant IDs. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-1.0). |
| localAssociatedTenantProvisioningActiveCount | String | The number of local associated tenants with active provisioning. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-1.0). |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.billingMetricsInitial",
  "watermarkDateTime": "String (timestamp)",
  "localAssociatedTenantCount": "String",
  "localAssociatedTenantBillingManagementActiveCount": "String",
  "localAssociatedTenantProvisioningActiveCount": "String",
  "localAssociatedTenantIds": [
    "String"
  ],
  "foreignAssociatedTenantCount": "String",
  "foreignAssociatedTenantBillingManagementActiveCount": "String",
  "foreignAssociatedTenantProvisioningActiveCount": "String",
  "createdDateTime": "String (timestamp)"
}
```
