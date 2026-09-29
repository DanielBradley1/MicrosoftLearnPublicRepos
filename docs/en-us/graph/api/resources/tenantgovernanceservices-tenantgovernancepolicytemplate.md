<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# tenantGovernancePolicyTemplate resource type

Namespace: microsoft.graph

Represents a policy template that defines the configuration for governance relationships, including delegated administration role assignments and multi-tenant applications to provision. Policy templates are used when creating [governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0) objects and are stored as [snapshots](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relationshippolicy?view=graph-rest-1.0) in established [governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-1.0) objects.

The system provides a default policy template with the ID `default`. This template serves as a reusable configuration that is applied when governance relationships are automatically created for add-on tenants. The default template cannot be deleted.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-list-governancepolicytemplates?view=graph-rest-1.0) | [microsoft.graph.tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-1.0) collection | Get a list of the [tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-post-governancepolicytemplates?view=graph-rest-1.0) | [microsoft.graph.tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-1.0) | Create a new governance policy template. |
| [Get](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governancepolicytemplate-get?view=graph-rest-1.0) | [microsoft.graph.tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-1.0) | Read the properties of a [tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-1.0) object, including the system-provided default template. |
| [Update](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governancepolicytemplate-update?view=graph-rest-1.0) | [microsoft.graph.tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-1.0) | Update the properties of a governance policy template, including the system-provided default template. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-delete-governancepolicytemplates?view=graph-rest-1.0) | None | Delete a governance policy template. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the template was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.  <br>  <br>Supports `$filter` \(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderBy`. |
| delegatedAdministrationRoleAssignments | [microsoft.graph.delegatedAdministrationRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-delegatedadministrationroleassignment?view=graph-rest-1.0) collection | A collection of delegated administration role assignments to be applied in the governed tenant when the governance relationship is established. |
| description | String | A description of the policy template.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| displayName | String | The display name of the policy template.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governedTenantCanTerminate | Boolean | Not implemented. |
| id | String | The unique identifier for the policy template. Is `default` for the default template.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the template was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.  <br>  <br>Supports `$filter` \(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderBy`. |
| multiTenantApplicationsToProvision | [microsoft.graph.multiTenantApplicationsToProvision](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationstoprovision?view=graph-rest-1.0) collection | A collection of multi-tenant applications to be provisioned in the governed tenant when the governance relationship is established. |
| version | String | The version of the policy template. Version count increased by 1 when updated.  <br>  <br>Supports `$filter` \(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderBy`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tenantGovernancePolicyTemplate",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "governedTenantCanTerminate": "Boolean",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "version": "String",
  "multiTenantApplicationsToProvision": [
    {
      "@odata.type": "microsoft.graph.multiTenantApplicationsToProvision"
    }
  ],
  "delegatedAdministrationRoleAssignments": [
    {
      "@odata.type": "microsoft.graph.delegatedAdministrationRoleAssignment"
    }
  ]
}
```
