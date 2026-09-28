<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnssecurednsserver?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-09 -->

# windowsZtdnsSecureDnsServer resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Trusted DNS server configuration for Zero Trust DNS

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name assigned to the trusted server entry |
| dnsOverHttpsConfiguration | [windowsZtdnsSecureDnsServerDnsOverHttpsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnssecurednsserverdnsoverhttpsconfiguration?view=graph-rest-beta) | DNS over HTTPS \(DoH\) configuration settings for the secure DNS server |
| dnsOverTlsConfiguration | [windowsZtdnsSecureDnsServerDnsOverTlsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnssecurednsserverdnsovertlsconfiguration?view=graph-rest-beta) | DNS over TLS \(DoT\) configuration settings for the secure DNS server |
| ipAddress | String | IP address of a trusted DNS server for ZTDNS \(IPv4 or IPv6\) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsZtdnsSecureDnsServer",
  "displayName": "String",
  "dnsOverHttpsConfiguration": {
    "@odata.type": "microsoft.graph.windowsZtdnsSecureDnsServerDnsOverHttpsConfiguration",
    "httpsPort": 1024,
    "queryUrl": "String"
  },
  "dnsOverTlsConfiguration": {
    "@odata.type": "microsoft.graph.windowsZtdnsSecureDnsServerDnsOverTlsConfiguration",
    "certificateSubjectName": "String",
    "tlsPort": 1024
  },
  "ipAddress": "String"
}
```
