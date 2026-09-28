<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/evaluatedynamicmembershipresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# evaluateDynamicMembershipResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the result of membership evaluation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| membershipRule | String | If a group ID is provided, the value is the membership rule for the group. If a group ID isn't provided, the value is the membership rule that was provided as a parameter. For more information, see [Dynamic membership rules for groups in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership). |
| membershipRuleEvaluationDetails | [expressionEvaluationDetails](https://learn.microsoft.com/en-us/graph/api/resources/expressionevaluationdetails?view=graph-rest-beta) | Provides a detailed analysis of the membership evaluation result. |
| membershipRuleEvaluationResult | Boolean | The value is `true` if the user or device is a member of the group. The value can also be `true` if a membership rule was provided and the user or device passes the rule evaluation; otherwise `false`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "membershipRule": "String",
  "membershipRuleEvaluationDetails": {
    "@odata.type": "microsoft.graph.expressionEvaluationDetails"
  },
  "membershipRuleEvaluationResult": true
}
```
