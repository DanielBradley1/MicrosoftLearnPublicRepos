<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewalldestinationipaddress?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# cloudFirewallDestinationIpAddress resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies destination addresses using IP addresses for cloud firewall rule matching. Supports IPv4, IPv6, CIDR notation, and IP ranges.

Inherits from [microsoft.graph.networkaccess.cloudFirewallDestinationAddress](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewalldestinationaddress?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| values | String collection | A collection of IP addresses. Supports IPv4, IPv6, CIDR notation \(for example, `192.168.0.0/16`\), and IP ranges \(for example, `172.16.0.0-172.16.255.255`\). The collection must not be empty. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress",
  "values": [
    "String"
  ]
}
```
