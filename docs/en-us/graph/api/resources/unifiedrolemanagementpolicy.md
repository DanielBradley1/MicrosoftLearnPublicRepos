<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedRoleManagementPolicy resource type

Namespace: microsoft.graph

Specifies the various policies associated with scopes and roles. For policies that apply to Azure RBAC, use the [Azure REST PIM API for role management policies](https://learn.microsoft.com/en-us/rest/api/authorization/role-management-policies).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/policyroot-list-rolemanagementpolicies?view=graph-rest-1.0) | [unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicy?view=graph-rest-1.0) collection | Get role management policies and their details. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-get?view=graph-rest-1.0) | [unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicy?view=graph-rest-1.0) | Retrieve the details of a role management policy. |
| [Update](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-update?view=graph-rest-1.0) | [unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicy?view=graph-rest-1.0) | Update a role management policy. |
| [List rules](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-list-rules?view=graph-rest-1.0) | [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) collection | Get the rules defined for a role management policy. |
| [Get rule](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyrule-get?view=graph-rest-1.0) | [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) | Retrieve a rule defined for a role management policy. |
| [Update rule](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyrule-update?view=graph-rest-1.0) | [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) | Update a rule defined for a role management policy. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description for the policy. |
| displayName | String | Display name for the policy. |
| id | String | Unique identifier for the policy. |
| isOrganizationDefault | Boolean | This can only be set to `true` for a single tenant-wide policy which will apply to all scopes and roles. Set the scopeId to `/` and scopeType to `Directory`. Supports `$filter` \(`eq`, `ne`\). |
| lastModifiedBy | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | The identity who last modified the role setting. |
| lastModifiedDateTime | DateTimeOffset | The time when the role setting was last modified. |
| scopeId | String | The identifier of the scope where the policy is created. Can be `/` for the tenant or a group ID. Required. |
| scopeType | String | The type of the scope where the policy is created. One of `Directory`, `DirectoryRole`, `Group`. Required. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| effectiveRules | [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) collection | The list of effective rules like approval rules and expiration rules evaluated based on inherited referenced rules. For example, if there is a tenant-wide policy to enforce enabling an approval rule, the effective rule will be to enable approval even if the policy has a rule to disable approval. Supports `$expand`. |
| rules | [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) collection | The collection of rules like approval rules and expiration rules. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicy",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "isOrganizationDefault": "Boolean",
  "scopeId": "String",
  "scopeType": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identity"
  }
}
```
