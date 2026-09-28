<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ruledestination?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-27 -->

# ruleDestination resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the list of potential destinations and destination types that the user could be accessing in the context of a network [filtering policy rule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta) or [forwarding policy rule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingrule?view=graph-rest-beta) in Global Secure Access, including IPs and FQDNs or URLs.

This is an abstract type from which the following resources are derived:

- [microsoft.graph.networkaccess.fqdn](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-fqdn?view=graph-rest-beta)
- [microsoft.graph.networkaccess.ipAddress](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ipaddress?view=graph-rest-beta)
- [microsoft.graph.networkaccess.ipRange](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-iprange?view=graph-rest-beta)
- [microsoft.graph.networkaccess.ipSubnet](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ipsubnet?view=graph-rest-beta)
- [microsoft.graph.networkaccess.url](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-url?view=graph-rest-beta)
- [microsoft.graph.networkaccess.webCategory](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategory?view=graph-rest-beta)

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.ruleDestination"
}
```
