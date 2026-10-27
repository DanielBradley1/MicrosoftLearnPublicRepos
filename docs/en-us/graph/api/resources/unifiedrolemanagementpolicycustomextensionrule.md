<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicycustomextensionrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# unifiedRoleManagementPolicyCustomExtensionRule resource type

Namespace: microsoft.graph

Defines a rule that associates a PIM custom extension with a role management policy. The rule controls whether the custom extension is invoked for role assignment operations targeted by the policy.

Inherits from [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-list-rules?view=graph-rest-1.0) | [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) collection | Get the rules defined for a role management policy. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyrule-get?view=graph-rest-1.0) | [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) | Retrieve a rule defined for a role management policy. |
| [Update](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyrule-update?view=graph-rest-1.0) | [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) | Update a rule defined for a role management policy. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customAttributes | String collection | The custom attributes associated with the policy rule. Read-only. |
| customExtensionId | String | The unique identifier of the [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0) associated with this rule. |
| displayName | String | The display name of the policy rule. Read-only. |
| id | String | The unique identifier for the rule. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |
| isEnabled | Boolean | Indicates whether the custom extension rule is enabled. |
| target | [unifiedRoleManagementPolicyRuleTarget](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyruletarget?view=graph-rest-1.0) | Defines the scope targeted by the role management policy rule. Inherited from [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyCustomExtensionRule",
  "id": "String (identifier)",
  "customAttributes": ["String"],
  "customExtensionId": "String",
  "displayName": "String",
  "isEnabled": "Boolean",
  "target": {
    "@odata.type": "microsoft.graph.unifiedRoleManagementPolicyRuleTarget"
  }
}
```
