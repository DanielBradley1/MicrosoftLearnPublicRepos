<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudflarerulemodel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# cloudFlareRuleModel resource type

Namespace: microsoft.graph

Represents a Cloudflare WAF rule configuration or mapping that is known to the integration, as defined in the **enabledCustomRules** property of the [cloudFlareVerifiedDetailsModel object](https://learn.microsoft.com/en-us/graph/api/resources/cloudflareverifieddetailsmodel?view=graph-rest-1.0). This resource captures metadata about the rule and the action Cloudflare takes when the rule matches traffic.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | String | The action Cloudflare applies when the rule matches traffic. Common values include `Managed Challenge`, `Interactive Challenge`, `Log`, `Block`, `JS Challenge`, or `Skip`. |
| name | String | Friendly name for the rule, used in UIs or logs to help administrators identify the rule. |
| ruleId | String | Unique identifier assigned to the rule by Cloudflare or the integration. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudFlareRuleModel",
  "ruleId": "String",
  "name": "String",
  "action": "String"
}
```
