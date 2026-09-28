<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/akamairapidrulesmodel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# akamaiRapidRulesModel resource type

Namespace: microsoft.graph

Represents the configuration for Akamai Rapid Rules in a web application firewall \(WAF\) integration, as defined in the **rapidRules** property of the [akamaiVerifiedDetailsModel object](https://learn.microsoft.com/en-us/graph/api/resources/akamaiverifieddetailsmodel?view=graph-rest-1.0). Rapid Rules are pre-configured rulesets designed to quickly address emerging threats. This resource describes whether Rapid Rules are enabled and the default action applied to traffic that matches these rules.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultAction | String | The default action Akamai applies to traffic that matches Rapid Rules. Common values include `deny`, `none` or `alert`. |
| isEnabled | Boolean | Indicates whether Akamai Rapid Rules are enabled for the WAF integration. If true, Rapid Rules are active and applied to incoming traffic. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.akamaiRapidRulesModel",
  "isEnabled": "Boolean",
  "defaultAction": "String"
}
```
