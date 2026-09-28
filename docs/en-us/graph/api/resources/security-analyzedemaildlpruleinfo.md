<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemaildlpruleinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# analyzedEmailDlpRuleInfo resource type

Namespace: microsoft.graph.security

Represents data loss prevention rules applied to the email. It's returned in the **dlpRules** property of [analyzedEmail](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name of the the data loss prevention rule. |
| ruleId | String | Unique identifier of the data loss prevention rule. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.analyzedEmailDlpRuleInfo",
  "ruleId": "String",
  "name": "String"
}
```
