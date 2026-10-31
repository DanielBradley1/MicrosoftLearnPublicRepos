<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyplan?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# conditionalAccessPolicyPlan resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Conditional Access policy plan that groups shared conditions and related rules into a single policy configuration. The shared conditions apply to every rule in the plan, while each rule defines scenario-specific conditions and enforcement controls.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-list-plans?view=graph-rest-beta) | [conditionalAccessPolicyPlan](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyplan?view=graph-rest-beta) collection | Retrieve a list of Conditional Access policy plans. |
| [Create](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-post-plans?view=graph-rest-beta) | [conditionalAccessPolicyPlan](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyplan?view=graph-rest-beta) | Create a Conditional Access policy plan. |
| [Get](https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicyplan-get?view=graph-rest-beta) | [conditionalAccessPolicyPlan](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyplan?view=graph-rest-beta) | Retrieve a Conditional Access policy plan. |
| [Update](https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicyplan-update?view=graph-rest-beta) | [conditionalAccessPolicyPlan](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyplan?view=graph-rest-beta) | Update a Conditional Access policy plan. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-delete-plans?view=graph-rest-beta) | None | Delete a Conditional Access policy plan. |
| [List rules](https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicyplan-list-rules?view=graph-rest-beta) | [conditionalAccessPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrule?view=graph-rest-beta) collection | Retrieve the rules contained in the Conditional Access policy plan. |
| [Create rule](https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicyplan-post-rules?view=graph-rest-beta) | [conditionalAccessPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrule?view=graph-rest-beta) | Create a rule in the Conditional Access policy plan. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time the plan was created, in UTC. Read-only. |
| description | String | A free-text description of the plan's purpose and scope. |
| displayName | String | The administrator-defined display name for the plan. |
| id | String | The unique identifier for the plan. Read-only. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| modifiedDateTime | DateTimeOffset | The date and time the plan was last modified, in UTC. Read-only. |
| owners | String collection | The IDs of users and groups recorded as metadata owners of the plan. Does not grant any role or permission to the plan. |
| sharedConditions | [conditionalAccessConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessconditionset?view=graph-rest-beta) | The conditions that apply to every rule in the plan. During evaluation, these conditions are combined with each rule's **conditions** property; rules can add conditions but can't remove plan-level conditions. |
| tags | String collection | The administrator-defined tags used to categorize and organize the plan. |
| templateId | String | The identifier of the Microsoft-managed template from which the plan was created. The value is `null` for custom plans. |
| version | Int32 | The version number of the plan. The service increments this value each time the plan is updated. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| rules | [conditionalAccessPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrule?view=graph-rest-beta) collection | The unordered collection of rules contained in the plan. Each rule defines scenario-specific conditions and enforcement controls. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessPolicyPlan",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "owners": [
    "String"
  ],
  "tags": [
    "String"
  ],
  "version": "Integer",
  "templateId": "String",
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "sharedConditions": {
    "@odata.type": "microsoft.graph.conditionalAccessConditionSet"
  },
  "rules": [
    {
      "@odata.type": "microsoft.graph.conditionalAccessPolicyRule"
    }
  ]
}
```
