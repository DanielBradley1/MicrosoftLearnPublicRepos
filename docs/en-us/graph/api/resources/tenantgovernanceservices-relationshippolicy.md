<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relationshippolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# relationshipPolicy resource type

Namespace: microsoft.graph

Represents a snapshot of governance policy configuration that is stored in a [governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-1.0) or [governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0). This snapshot preserves the policy state at the time the relationship was created or requested.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| delegatedAdministrationRoleAssignments | [microsoft.graph.delegatedAdministrationRoleAssignmentSnapshot](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-delegatedadministrationroleassignmentsnapshot?view=graph-rest-1.0) collection | A snapshot of the delegated administration role assignments configured in this policy. |
| governedTenantCanTerminate | Boolean | Indicates whether the governed tenant can terminate the relationship. |
| multiTenantApplicationsToProvision | [microsoft.graph.multiTenantApplicationsToProvisionSnapshot](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationstoprovisionsnapshot?view=graph-rest-1.0) collection | A snapshot of the multi-tenant applications to be provisioned in the governed tenant. |
| policyId | String | The identifier of the source policy template from which this snapshot was created. |
| version | Int32 | The version of the source policy template from which this snapshot was created. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.relationshipPolicy",
  "policyId": "String",
  "version": "Int32",
  "governedTenantCanTerminate": "Boolean",
  "multiTenantApplicationsToProvision": [
    {
      "@odata.type": "microsoft.graph.multiTenantApplicationsToProvisionSnapshot"
    }
  ],
  "delegatedAdministrationRoleAssignments": [
    {
      "@odata.type": "microsoft.graph.delegatedAdministrationRoleAssignmentSnapshot"
    }
  ]
}
```
