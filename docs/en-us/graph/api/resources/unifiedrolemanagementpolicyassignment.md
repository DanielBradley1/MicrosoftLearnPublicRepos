<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedRoleManagementPolicyAssignment resource type

Namespace: microsoft.graph

The assignment of a role management policy to a [role definition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/policyroot-list-rolemanagementpolicyassignments?view=graph-rest-1.0) | [unifiedRoleManagementPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyassignment?view=graph-rest-1.0) collection | Get the details of all role management policy assignments including the policies and rules associated with the Microsoft Entra role. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyassignment-get?view=graph-rest-1.0) | [unifiedRoleManagementPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyassignment?view=graph-rest-1.0) | Read the properties and relationships of an [unifiedRoleManagementPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the policy assignment. The ID is typically a concatenation of the **unifiedRoleManagementPolicy** ID and the **roleDefinitionId** separated by an underscore. |
| policyId | String | The id of the policy. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| roleDefinitionId | String | For Microsoft Entra roles policy, it's the identifier of the [role definition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object where the policy applies. For PIM for Groups membership and ownership, it's either `member` or `owner`. Supports $filter \(`eq`\). |
| scopeId | String | The identifier of the scope where the policy is assigned. Can be `/` for the tenant or a group ID. Required. |
| scopeType | String | The type of the scope where the policy is assigned. One of `Directory`, `DirectoryRole`, `Group`. Required. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policy | [unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicy?view=graph-rest-1.0) | The policy that's associated with a policy assignment. Supports `$expand` and a nested `$expand` of the **rules** and **effectiveRules** relationships for the policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyAssignment",
  "id": "String (identifier)",
  "policyId": "String",
  "scopeId": "String",
  "scopeType": "String",
  "roleDefinitionId": "String"
}
```
