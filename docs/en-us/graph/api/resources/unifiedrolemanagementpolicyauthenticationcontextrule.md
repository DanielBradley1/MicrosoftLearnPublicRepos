<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyauthenticationcontextrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# unifiedRoleManagementPolicyAuthenticationContextRule resource type

Namespace: microsoft.graph

A type derived from the [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) resource type that defines the authentication context rule for the conditional access policy associated with a role management policy.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| claimValue | String | The value of the authentication context claim. |
| id | String | Identifier for the rule. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnabled | Boolean | Determines whether this rule is enabled. |
| target | [unifiedRoleManagementPolicyRuleTarget](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyruletarget?view=graph-rest-1.0) | Defines details of the scope that the enablement rule targets. The details can include the principal type, the role assignment type, and actions affecting a role. Inherited from [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.unifiedRoleManagementPolicyRuleTarget"
  },
  "isEnabled": "Boolean",
  "claimValue": "String"
}
```
