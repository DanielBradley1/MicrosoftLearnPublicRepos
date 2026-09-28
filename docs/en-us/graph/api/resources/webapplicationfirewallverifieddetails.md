<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverifieddetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# webApplicationFirewallVerifiedDetails resource type

Namespace: microsoft.graph

Represents [verification](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverificationmodel?view=graph-rest-1.0) findings and evidence for a host or domain after a verification operation with a web application firewall \(WAF\) provider.

This is an abstract type. The following types inherit from **webApplicationFirewallVerifiedDetails**:

- [cloudFlareVerifiedDetailsModel](https://learn.microsoft.com/en-us/graph/api/resources/cloudflareverifieddetailsmodel?view=graph-rest-1.0)
- [akamaiVerifiedDetailsModel](https://learn.microsoft.com/en-us/graph/api/resources/akamaiverifieddetailsmodel?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dnsConfiguration | [webApplicationFirewallDnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewalldnsconfiguration?view=graph-rest-1.0) | DNS-related details discovered during verification for the host, such as the DNS record name, record type, record value, whether the record is proxied through the provider, and whether the domain is verified. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webApplicationFirewallVerifiedDetails",
  "dnsConfiguration": {
    "@odata.type": "microsoft.graph.webApplicationFirewallDnsConfiguration"
  }
}
```
