<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# tenantGovernance resource type

Namespace: microsoft.graph

Container for Microsoft Entra Tenant Governance capabilities.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| governanceInvitations | [microsoft.graph.governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0) collection | Collection of governance invitations associated with the tenant. |
| governancePolicyTemplates | [microsoft.graph.tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-1.0) collection | Collection of governance policy templates associated with the tenant. |
| governanceRelationships | [microsoft.graph.governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-1.0) collection | Collection of governance relationships associated with the tenant. |
| governanceRequests | [microsoft.graph.governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0) collection | Collection of governance requests associated with the tenant. |
| relatedTenants | [microsoft.graph.relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0) collection | Collection of related tenants associated with the tenant. |
| settings | [microsoft.graph.tenantGovernanceSetting](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancesetting?view=graph-rest-1.0) | Settings for the tenant governance container. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tenantGovernance"
}
```
