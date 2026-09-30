<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-delegatedadministrationroleassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# delegatedAdministrationRoleAssignment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a role assignment configuration for delegated administration in a governance relationship. Specifies which security group in the governing tenant should be assigned which roles in the governed tenant. This resource is defined in the \*\*delegatedAdministrationRoleAssignment \*\* property of [governancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| groupDisplayName | String | The display name of the security group referenced by the **group** navigation property. Server-populated and read-only; returns `null` if the referenced group has been deleted. |
| roleTemplates | [microsoft.graph.roleTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-roletemplate?view=graph-rest-beta) collection | A collection of role templates that define the roles to be assigned to the group in the governed tenant. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| group | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) | The security group in the governing tenant that will receive the role assignments in the governed tenant. This group must be role-assignable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.delegatedAdministrationRoleAssignment",
  "groupDisplayName": "String",
  "roleTemplates": [
    {
      "@odata.type": "microsoft.graph.roleTemplate"
    }
  ]
}
```
