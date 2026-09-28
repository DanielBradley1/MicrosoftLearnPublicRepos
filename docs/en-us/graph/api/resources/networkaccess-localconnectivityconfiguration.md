<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-localconnectivityconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-10 -->

# localConnectivityConfiguration resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies the Microsoft end of the tunnel configuration for a device link.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| asn | Int32 | Specifies ASN of one end of IPSec tunnel \(local or peer\). |
| bgpAddress | String | Specifies BGP IPv4 address of one end of IPSec tunnel \(local or peer\). |
| endpoint | String | Specifies public IPv4 address of one end of IPSec tunnel \(local or peer\). |
| region | microsoft.graph.networkaccess.region | Specify the region closest to your remote network. Not applicable for peer configuration. The possible value are: `eastUS`, `eastUS2`, `westUS`, `westUS2`, `westUS3`, `centralUS`, `northCentralUS`, `southCentralUS`, `northEurope`, `westEurope`, `franceCentral`, `germanyWestCentral`, `switzerlandNorth`, `ukSouth`, `canadaEast`, `canadaCentral`, `southAfricaWest`, `southAfricaNorth`, `uaeNorth`, `australiaEast`, `westCentralUS`, `centralIndia`, `southEastAsia`, `swedenCentral`, `southIndia`, `australiaSouthEast`, `koreaCentral`, `koreaSouth`, `polandCentral`, `brazilSouth`, `japanEast`, `japanWest`, `koreaSouth`, `italyNorth`, `franceSouth`, `israelCentral`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.localConnectivityConfiguration",
  "endpoint": "String",
  "asn": "Integer",
  "bgpAddress": "String",
  "region": "String"
}
```
