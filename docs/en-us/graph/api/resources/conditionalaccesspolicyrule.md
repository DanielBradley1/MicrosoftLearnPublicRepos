<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# conditionalAccessPolicyRule resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a rule in a Conditional Access policy plan. The rule defines scenario-specific conditions and enforcement controls that are combined with the parent plan's shared conditions during evaluation.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicyplan-list-rules?view=graph-rest-beta) | [conditionalAccessPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrule?view=graph-rest-beta) collection | Retrieve the rules in a Conditional Access policy plan. |
| [Create](https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicyplan-post-rules?view=graph-rest-beta) | [conditionalAccessPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrule?view=graph-rest-beta) | Create a rule in a Conditional Access policy plan. |
| [Get](https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicyrule-get?view=graph-rest-beta) | [conditionalAccessPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrule?view=graph-rest-beta) | Retrieve a rule in a Conditional Access policy plan. |
| [Update](https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicyrule-update?view=graph-rest-beta) | [conditionalAccessPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrule?view=graph-rest-beta) | Update a rule in a Conditional Access policy plan. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicyplan-delete-rules?view=graph-rest-beta) | None | Delete a rule from a Conditional Access policy plan. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conditions | [conditionalAccessConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessconditionset?view=graph-rest-beta) | The conditions specific to the rule. During evaluation, these conditions are combined with the parent plan's **sharedConditions** property to determine the rule's effective targeting. |
| controls | [conditionalAccessPolicyRuleControls](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrulecontrols?view=graph-rest-beta) | The grant and session controls enforced when the rule's effective conditions are met. |
| description | String | A free-text description of the rule's purpose. |
| displayName | String | The administrator-defined display name for the rule. |
| id | String | The unique identifier for the rule. Read-only. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| state | [conditionalAccessPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#conditionalaccesspolicystate-values) | The state of the rule. The possible values are: `enabled`, `disabled`, `enabledForReportingButNotEnforced`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessPolicyRule",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "state": "String",
  "conditions": {
    "@odata.type": "microsoft.graph.conditionalAccessConditionSet"
  },
  "controls": {
    "@odata.type": "microsoft.graph.conditionalAccessPolicyRuleControls"
  }
}
```
