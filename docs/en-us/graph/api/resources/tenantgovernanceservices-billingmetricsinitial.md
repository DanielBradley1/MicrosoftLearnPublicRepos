<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsinitial?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# billingMetricsInitial resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the initial snapshot of billing metrics captured when the [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta) was first discovered, establishing a baseline for billing account associations and associated tenant connection counts.

Inherits from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Timestamp that represents when billing metrics are initially aggregated for the related tenant. |
| foreignAssociatedTenantBillingManagementActiveCount | String | The number of foreign associated tenants with active billing management. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| foreignAssociatedTenantCount | String | The total number of foreign associated tenants. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| foreignAssociatedTenantProvisioningActiveCount | String | The number of foreign associated tenants with active provisioning. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| id | String | Unique identifier for the metrics snapshot. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| localAssociatedTenantBillingManagementActiveCount | String | The number of local associated tenants with active billing management. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| localAssociatedTenantCount | String | The total number of local associated tenants. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| localAssociatedTenantIds | Collection\(String\) | The list of local associated tenant IDs. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| localAssociatedTenantProvisioningActiveCount | String | The number of local associated tenants with active provisioning. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.billingMetricsInitial",
  "id": "String (identifier)",
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
