<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# relatedTenant resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a tenant that has been discovered as related to the current tenant through the tenant discovery feature. Related tenants are discovered based on B2B collaboration activity, billing relationships, multi-tenant application usage, and other indicators of inter-tenant relationships.

Important

The related tenants feature must be explicitly enabled before the tenant governance APIs can be used. To enable related tenants, call the [enableRelatedTenants](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-tenantgovernancesetting-enablerelatedtenants?view=graph-rest-beta) action.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-list-relatedtenants?view=graph-rest-beta) | [microsoft.graph.relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta) collection | Get a list of the [relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-get?view=graph-rest-beta) | [microsoft.graph.relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta) | Read the properties of a [relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta) object. |
| [Refresh](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-refresh?view=graph-rest-beta) | None | Trigger a refresh operation to update the list of related tenants. |
| [Refresh status](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-refreshstatus?view=graph-rest-beta) | [microsoft.graph.relatedTenantsRefreshStatus](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenantsrefreshstatus?view=graph-rest-beta) | Check the status of a related tenants refresh operation. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the related tenant was discovered. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. |
| id | String | The Microsoft Entra tenant ID of the related tenant. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isMicrosoftInfrastructure | Boolean | Indicates whether the related tenant is a Microsoft infrastructure tenant. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appB2BSignInActivityMetrics | [microsoft.graph.b2BSignInActivityMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetrics?view=graph-rest-beta) | B2B sign-in activity metrics for this related tenant. Expanded by default. |
| b2BRegistrationMetrics | [microsoft.graph.b2bRegistrationMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetrics?view=graph-rest-beta) | B2B registration metrics for this related tenant. Expanded by default. |
| b2BSignInActivityMetrics | [microsoft.graph.b2BSignInActivityMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetrics?view=graph-rest-beta) | B2B sign-in activity metrics for this related tenant. Expanded by default. |
| billingMetrics | [microsoft.graph.billingMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetrics?view=graph-rest-beta) | Billing metrics for this related tenant. Expanded by default. |
| multiTenantApplicationMetrics | [microsoft.graph.multiTenantApplicationMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetrics?view=graph-rest-beta) | Multi-tenant application usage metrics for this related tenant. Expanded by default. |

The metrics relationships support the `$expand` query parameter. Each metrics category also exposes an **investigationHints** relationship that returns ordered, actionable guidance for drilling into the signals behind an aggregate metric. Investigation hints aren't returned by default; to retrieve them, use a nested `$expand` on the metrics relationship. For example, the following request returns the B2B registration metrics for a related tenant together with the investigation hints for those metrics:

```http
GET https://graph.microsoft.com/beta/directory/tenantGovernance/relatedTenants/{id}?$expand=b2BRegistrationMetrics($expand=investigationHints)
```

Each hint is an [investigationActionStep](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-investigationactionstep?view=graph-rest-beta) that pairs human-readable guidance with a Microsoft Graph or Azure Resource Manager URL that you can call to investigate the users, applications, sign-in activity, or billing relationships behind the count. For more information, see [investigationActionStep](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-investigationactionstep?view=graph-rest-beta).

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
