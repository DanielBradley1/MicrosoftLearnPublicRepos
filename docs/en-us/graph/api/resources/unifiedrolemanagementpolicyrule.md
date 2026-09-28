<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-13 -->

# unifiedRoleManagementPolicyRule resource type

Namespace: microsoft.graph

An abstract type that defines the rules or settings associated with role management policies. This abstract type is inherited by the following resources that define the various types of rules and their settings associated with role management policies.

- [unifiedRoleManagementPolicyApprovalRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyapprovalrule?view=graph-rest-1.0)
- [unifiedRoleManagementPolicyAuthenticationContextRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyauthenticationcontextrule?view=graph-rest-1.0)
- [unifiedRoleManagementPolicyEnablementRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyenablementrule?view=graph-rest-1.0)
- [unifiedRoleManagementPolicyExpirationRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyexpirationrule?view=graph-rest-1.0)
- [unifiedRoleManagementPolicyNotificationRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicynotificationrule?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-list-rules?view=graph-rest-1.0) | [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) collection | Get a list of the [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyrule-get?view=graph-rest-1.0) | [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) | Read the properties and relationships of an [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyrule-update?view=graph-rest-1.0) | [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) | Update the properties of an [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier for the rule. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |
| target | [unifiedRoleManagementPolicyRuleTarget](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyruletarget?view=graph-rest-1.0) | Defines details of scope that's targeted by role management policy rule. The details can include the principal type, the role assignment type, and actions affecting a role. Supports `$filter` \(`eq`, `ne`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyRule",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.unifiedRoleManagementPolicyRuleTarget"
  }
}
```
