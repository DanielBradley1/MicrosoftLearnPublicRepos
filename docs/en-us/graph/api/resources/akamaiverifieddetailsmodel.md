<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/akamaiverifieddetailsmodel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# akamaiVerifiedDetailsModel resource type

Namespace: microsoft.graph

Represents the details discovered when verifying a host or domain using an Akamai web application firewall \(WAF\) provider.

Inherits from [webApplicationFirewallVerifiedDetails](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverifieddetails?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeAttackGroups | [akamaiAttackGroupActionModel](https://learn.microsoft.com/en-us/graph/api/resources/akamaiattackgroupactionmodel?view=graph-rest-1.0) collection | Collection of Akamai attack groups that are currently active for the zone or host, including the action applied to each group \(for example, `deny`, `none` or `alert`\). |
| activeCustomRules | [akamaiCustomRuleModel](https://learn.microsoft.com/en-us/graph/api/resources/akamaicustomrulemodel?view=graph-rest-1.0) collection | Collection of Akamai custom rules that are currently enabled for the zone or host. Each entry includes rule metadata such as the rule identifier, friendly name, and the action taken when the rule matches traffic. |
| dnsConfiguration | [webApplicationFirewallDnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewalldnsconfiguration?view=graph-rest-1.0) | DNS-related evidence discovered during verification. Includes the record name, record type and value, whether the record is proxied through Akamai, and whether the domain is verified. Inherited from [webApplicationFirewallVerifiedDetails](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverifieddetails?view=graph-rest-1.0). |
| rapidRules | [akamaiRapidRulesModel](https://learn.microsoft.com/en-us/graph/api/resources/akamairapidrulesmodel?view=graph-rest-1.0) | Configuration for Akamai Rapid Rules, including whether Rapid Rules are enabled and the default action applied to matching traffic. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.akamaiVerifiedDetailsModel",
  "dnsConfiguration": {
    "@odata.type": "microsoft.graph.webApplicationFirewallDnsConfiguration"
  },
  "rapidRules": {
    "@odata.type": "microsoft.graph.akamaiRapidRulesModel"
  },
  "activeAttackGroups": [
    {
      "@odata.type": "microsoft.graph.akamaiAttackGroupActionModel"
    }
  ],
  "activeCustomRules": [
    {
      "@odata.type": "microsoft.graph.akamaiCustomRuleModel"
    }
  ]
}
```
