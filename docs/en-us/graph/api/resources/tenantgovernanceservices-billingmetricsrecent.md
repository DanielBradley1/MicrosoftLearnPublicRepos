<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsrecent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# billingMetricsRecent resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the most recent snapshot of billing metrics, showing current billing account associations and associated tenant connection counts.

Inherits from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| foreignAssociatedTenantBillingManagementActiveCount | String | The number of foreign associated tenants with active billing management. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| foreignAssociatedTenantCount | String | The total number of foreign associated tenants. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| foreignAssociatedTenantProvisioningActiveCount | String | The number of foreign associated tenants with active provisioning. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| id | String | Unique identifier for the metrics snapshot. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| localAssociatedTenantBillingManagementActiveCount | String | The number of local associated tenants with active billing management. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| localAssociatedTenantCount | String | The total number of local associated tenants. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| localAssociatedTenantIds | Collection\(String\) | The list of local associated tenant IDs. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| localAssociatedTenantProvisioningActiveCount | String | The number of local associated tenants with active provisioning. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |
| updateDateTime | DateTimeOffset | Timestamp that represents when billing metrics are aggregated and have sufficiently changed for the related tenant. |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. Inherited from [microsoft.graph.billingMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsbase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.billingMetricsRecent",
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
  "updateDateTime": "String (timestamp)"
}
```
