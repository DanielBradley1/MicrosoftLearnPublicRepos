<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudflareverifieddetailsmodel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# cloudFlareVerifiedDetailsModel resource type

Namespace: microsoft.graph

Represents the details discovered when verifying a host or domain using a Cloudflare web application firewall \(WAF\) provider.

Inherits from [webApplicationFirewallVerifiedDetails](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverifieddetails?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dnsConfiguration | [webApplicationFirewallDnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewalldnsconfiguration?view=graph-rest-1.0) | DNS-related evidence discovered during verification. Inherited from [webApplicationFirewallVerifiedDetails](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverifieddetails?view=graph-rest-1.0). |
| enabledCustomRules | [cloudFlareRuleModel](https://learn.microsoft.com/en-us/graph/api/resources/cloudflarerulemodel?view=graph-rest-1.0) collection | Collection of Cloudflare custom rules that are currently enabled for the zone or host. |
| enabledRecommendedRulesets | [cloudFlareRulesetModel](https://learn.microsoft.com/en-us/graph/api/resources/cloudflarerulesetmodel?view=graph-rest-1.0) collection | Collection of Cloudflare recommended rulesets that are enabled for the zone or host. |
| zoneId | String | Cloudflare-assigned identifier for the DNS zone associated with the verified host \(for example, the Cloudflare Zone ID\). This ID is used to correlate verification details with the Cloudflare account and to perform configuration operations via the provider's API. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudFlareVerifiedDetailsModel",
  "dnsConfiguration": {
    "@odata.type": "microsoft.graph.webApplicationFirewallDnsConfiguration"
  },
  "zoneId": "String",
  "enabledRecommendedRulesets": [
    {
      "@odata.type": "microsoft.graph.cloudFlareRulesetModel"
    }
  ],
  "enabledCustomRules": [
    {
      "@odata.type": "microsoft.graph.cloudFlareRuleModel"
    }
  ]
}
```
