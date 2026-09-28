<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemailexchangetransportruleinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# analyzedEmailExchangeTransportRuleInfo resource type

Namespace: microsoft.graph.security

Represents mail flow rules in Exchange Online. It's returned in the **exchangeTransportRules** property of [analyzedEmail](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name of the Exchange transport rules \(ETRs\) that are part of the email. |
| ruleId | String | The ETR rule ID. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.analyzedEmailExchangeTransportRuleInfo",
  "ruleId": "String",
  "name": "String"
}
```
