<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# conditionalAccessPolicy resource type

Namespace: microsoft.graph

Represents a Microsoft Entra Conditional Access policy. Conditional access policies are custom rules that define an access scenario. For more information, see the [Conditional access documentation](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-list-policies?view=graph-rest-1.0) | [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0) collection | Get all of the conditionalAccessPolicies objects in the organization. |
| [Create](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-post-policies?view=graph-rest-1.0) | [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0) | Create a new conditionalAccessPolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicy-get?view=graph-rest-1.0) | [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0) | Read properties and relationships of a conditionalAccessPolicy object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicy-update?view=graph-rest-1.0) | [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0) | Update a conditionalAccessPolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/conditionalaccesspolicy-delete?view=graph-rest-1.0) | None | Delete a conditionalAccessPolicy object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conditions | [conditionalAccessConditionSet](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessconditionset?view=graph-rest-1.0) | Specifies the rules that must be met for the policy to apply. Required. |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| displayName | String | Specifies a display name for the conditionalAccessPolicy object. |
| grantControls | [conditionalAccessGrantControls](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessgrantcontrols?view=graph-rest-1.0) | Specifies the grant controls that must be fulfilled to pass the policy. |
| id | String | Specifies the identifier of a conditionalAccessPolicy object. Read-only. |
| modifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| sessionControls | [conditionalAccessSessionControls](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssessioncontrols?view=graph-rest-1.0) | Specifies the session controls that are enforced after sign-in. |
| state | conditionalAccessPolicyState | Specifies the state of the conditionalAccessPolicy object. The possible values are: `enabled`, `disabled`, `enabledForReportingButNotEnforced`. Required. |
| templateId | String | Specifies the unique identifier of a [Conditional Access template](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0). Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "conditions": {"@odata.type": "microsoft.graph.conditionalAccessConditionSet"},
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "grantControls": {"@odata.type": "microsoft.graph.conditionalAccessGrantControls"},
  "id": "String (identifier)",
  "modifiedDateTime": "String (timestamp)",
  "sessionControls": {"@odata.type": "microsoft.graph.conditionalAccessSessionControls"},
  "state": "string"
}
```
