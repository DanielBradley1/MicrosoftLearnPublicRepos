<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# tenantGovernance resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Container for Microsoft Entra Tenant Governance capabilities.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | A unique identifier for the tenant governance container. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| governanceInvitations | [microsoft.graph.governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-beta) collection | Collection of governance invitations associated with the tenant. |
| governancePolicyTemplates | [microsoft.graph.tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-beta) collection | Collection of governance policy templates associated with the tenant. |
| governanceRelationships | [microsoft.graph.governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-beta) collection | Collection of governance relationships associated with the tenant. |
| governanceRequests | [microsoft.graph.governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-beta) collection | Collection of governance requests associated with the tenant. |
| relatedTenants | [microsoft.graph.relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta) collection | Collection of related tenants associated with the tenant. |
| settings | [microsoft.graph.tenantGovernanceSetting](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancesetting?view=graph-rest-beta) | Settings for the tenant governance container. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tenantGovernance",
  "id": "String (identifier)"
}
```
