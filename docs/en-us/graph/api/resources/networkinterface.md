<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkinterface?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# networkInterface resource type

Namespace: microsoft.graph

Represents a Network Interface Card \(NIC\) associated with this host.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description of the NIC \(for example, Ethernet adapter, Wireless LAN adapter Local Area Connection, and so on\). |
| ipV4Address | String | Last IPv4 address associated with this NIC. |
| ipV6Address | String | Last Public \(also known as global\) IPv6 address associated with this NIC. |
| localIpV6Address | String | Last local \(link-local or site-local\) IPv6 address associated with this NIC. |
| macAddress | String | MAC address of the NIC on this host. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String",
  "ipV4Address": "String",
  "ipV6Address": "String",
  "localIpV6Address": "String",
  "macAddress": "String"
}
```
