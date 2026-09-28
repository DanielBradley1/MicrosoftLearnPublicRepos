<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# remoteNetwork resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A remote network represents a location such as a branch office where customer premises equipment \(CPE\) is connected to the nearest deployment of Global Secure Access service though IPsec tunnels.

Inherits from [microsoft.graph.networkaccess.baseEntity](https://learn.microsoft.com/en-us/graph/api/resources/baseentity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-list-remotenetworks?view=graph-rest-beta) | [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-post-remotenetworks?view=graph-rest-beta) | [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) | Create a new [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) | Update the properties of a [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-delete-remotenetworks?view=graph-rest-beta) | None | Delete a [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier for the remote network. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | last modified time. |
| name | String | Name. Inherited from [microsoft.graph.networkaccess.baseEntity](https://learn.microsoft.com/en-us/graph/api/resources/baseentity?view=graph-rest-beta). |
| region | microsoft.graph.networkaccess.region | Specify the region closest to your remote network. The possible value are: `eastUS`, `eastUS2`, `westUS`, `westUS2`, `westUS3`, `centralUS`, `northCentralUS`, `southCentralUS`, `northEurope`, `westEurope`, `franceCentral`, `germanyWestCentral`, `switzerlandNorth`, `ukSouth`, `canadaEast`, `canadaCentral`, `southAfricaWest`, `southAfricaNorth`, `uaeNorth`, `australiaEast`, `westCentralUS`, `centralIndia`, `southEastAsia`, `swedenCentral`, `southIndia`, `australiaSouthEast`, `koreaCentral`, `koreaSouth`, `polandCentral`, `brazilSouth`, `japanEast`, `japanWest`, `koreaSouth`, `italyNorth`, `franceSouth`, `israelCentral`, `unknownFutureValue`. |
| version | String | Remote network version. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| connectivityConfiguration | [microsoft.graph.networkaccess.remoteNetworkConnectivityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetworkconnectivityconfiguration?view=graph-rest-beta) collection | Specifies the connectivity details of all device links associated with a remote network. |
| deviceLinks | [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) collection | Each unique CPE device associated with a remote network is specified. Supports `$expand`. |
| forwardingProfiles | [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) collection | Each forwarding profile associated with a remote network is specified. Supports `$expand` and `$select`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.remoteNetwork",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "name": "String",
  "region": "microsoft.graph.networkaccess.region",
  "version": "String",
}
```
