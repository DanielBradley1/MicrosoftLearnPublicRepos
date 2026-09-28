<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-peerconnectivityconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# peerConnectivityConfiguration resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies the customer's end of the tunnel configuration for a device link.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| asn | Int32 | Specifies ASN of one end of IPSec tunnel \(local or peer\). |
| bgpAddress | String | Specifies BGP IPv4 address of one end of IPSec tunnel \(local or peer\). |
| endpoint | String | Specifies public IPv4 address of one end of IPSec tunnel \(local or peer\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.peerConnectivityConfiguration",
  "endpoint": "String",
  "asn": "Integer",
  "bgpAddress": "String"
}
```
