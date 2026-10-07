<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# relatedTenant resource type

Namespace: microsoft.graph

Represents a tenant that has been discovered as related to the current tenant through the tenant discovery feature. Related tenants are discovered based on B2B collaboration activity, billing relationships, multi-tenant application usage, and other indicators of inter-tenant relationships.

Important

The related tenants feature must be explicitly enabled before the tenant governance APIs can be used. To enable related tenants, call the [enableRelatedTenants](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-tenantgovernancesetting-enablerelatedtenants?view=graph-rest-1.0) action.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-list-relatedtenants?view=graph-rest-1.0) | [microsoft.graph.relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0) collection | Get a list of the [relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-get?view=graph-rest-1.0) | [microsoft.graph.relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0) | Read the properties and relationships of a [relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0) object. |
| [Refresh](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-refresh?view=graph-rest-1.0) | None | Refresh the list of related tenants. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the related tenant was discovered. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. |
| id | String | The Microsoft Entra tenant ID of the related tenant. |
| isMicrosoftInfrastructure | Boolean | Indicates whether the related tenant is a Microsoft infrastructure tenant. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appB2BSignInActivityMetrics | [microsoft.graph.b2BSignInActivityMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetrics?view=graph-rest-1.0) | B2B sign-in activity metrics for this related tenant. Expanded by default. |
| b2BRegistrationMetrics | [microsoft.graph.b2bRegistrationMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetrics?view=graph-rest-1.0) | B2B registration metrics for this related tenant. Expanded by default. |
| b2BSignInActivityMetrics | [microsoft.graph.b2BSignInActivityMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetrics?view=graph-rest-1.0) | B2B sign-in activity metrics for this related tenant. Expanded by default. |
| billingMetrics | [microsoft.graph.billingMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetrics?view=graph-rest-1.0) | Billing metrics for this related tenant. Expanded by default. |
| multiTenantApplicationMetrics | [microsoft.graph.multiTenantApplicationMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetrics?view=graph-rest-1.0) | Multi-tenant application usage metrics for this related tenant. Expanded by default. |

The metrics relationships support the `$expand` query parameter.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.relatedTenant",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "isMicrosoftInfrastructure": "Boolean"
}
```
