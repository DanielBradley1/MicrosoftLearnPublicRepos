<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewalldnsconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# webApplicationFirewallDnsConfiguration resource type

Namespace: microsoft.graph

Represents DNS configuration for a domain used by a web application firewall \(WAF\) provider, returned in the **dnsConfiguration** property of the [webApplicationFirewallVerifiedDetails](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverifieddetails?view=graph-rest-1.0) resource or its subtypes.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isDomainVerified | Boolean | Indicates whether the domain owning this DNS record has been verified by the WAF provider. |
| isProxied | Boolean | Indicates whether traffic for this DNS record is proxied through the WAF provider's network \(for example, using a CDN or reverse proxy\). |
| name | String | The DNS record name \(for example, `www.contoso.com` or `contoso.com`\). This is the host or zone name to which the configuration applies. |
| recordType | webApplicationFirewallDnsRecordType | Type of DNS record used for verification or routing. The possible values are: `cname`, `unknownFutureValue`. |
| value | String | The value of the DNS record. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webApplicationFirewallDnsConfiguration",
  "name": "String",
  "isProxied": "Boolean",
  "recordType": "String",
  "value": "String",
  "isDomainVerified": "Boolean"
}
```
