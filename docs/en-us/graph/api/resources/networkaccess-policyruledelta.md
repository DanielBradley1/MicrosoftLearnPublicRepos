<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyruledelta?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# policyRuleDelta resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the action for [updating the policy rule](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingpolicy-updatepolicyrules?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.networkaccess.forwardingRuleAction | Required. The possible values are: `bypass`, `forward`, `unknownFutureValue`. |
| ruleId | String | The identifier of the policy rule to update. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.policyRuleDelta",
  "ruleId": "String",
  "action": "String"
}
```
