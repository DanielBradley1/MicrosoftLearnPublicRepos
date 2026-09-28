<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicynotificationrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedRoleManagementPolicyNotificationRule resource type

Namespace: microsoft.graph

A type derived from the [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) resource type that defines the email notification rules for role assignments, activations, and approvals.

Inherits from [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier for the rule. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isDefaultRecipientsEnabled | Boolean | Indicates whether a default recipient will receive the notification email. |
| notificationLevel | String | The level of notification. The possible values are `None`, `Critical`, `All`. |
| notificationRecipients | String collection | The list of recipients of the email notifications. |
| notificationType | String | The type of notification. Only `Email` is supported. |
| recipientType | String | The type of recipient of the notification. The possible values are `Requestor`, `Approver`, `Admin`. |
| target | [unifiedRoleManagementPolicyRuleTarget](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyruletarget?view=graph-rest-1.0) | Defines details of the scope that's targeted by the notification rule. The details can include the principal type, the role assignment type, and actions affecting a role. Inherited from [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.unifiedRoleManagementPolicyRuleTarget"
  },
  "notificationType": "String",
  "recipientType": "String",
  "notificationLevel": "String",
  "isDefaultRecipientsEnabled": "Boolean",
  "notificationRecipients": [
    "String"
  ]
}
```
