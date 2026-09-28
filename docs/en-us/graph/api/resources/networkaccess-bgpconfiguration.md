<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-bgpconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# bgpConfiguration resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The border gateway protocol \(BGP\) specifies the IP address and ASN to route traffic from a link to the edge.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ipAddress | String | Specifies the BGP IP address. |
| localIpAddress | String | Specifies the BGP IP address of peer \(Microsoft, in this case\). |
| peerIpAddress | String | Specifies the BGP IP address of customer's on-premise VPN router configuration. |
| asn | Int32 | Specifies the ASN of the BGP. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.bgpConfiguration",
  "ipAddress": "String",
  "asn": "Integer"
}
```
