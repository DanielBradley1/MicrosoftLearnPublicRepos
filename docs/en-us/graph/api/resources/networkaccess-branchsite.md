<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# branchSite resource type \(deprecated\)

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

Deprecated and to be retired soon. Use the [remoteNetwork resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) and its associated methods instead.

A branch connects the Customer Premises Equipment \(CPE\) to the Global Secure Access services edge network.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-list-branches?view=graph-rest-beta) | [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-post-branches?view=graph-rest-beta) | [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta) | Create a new [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-branchsite-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-branchsite-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta) | Update the properties of a [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-branchsite-delete?view=graph-rest-beta) | None | Delete a [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchsite?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bandwidthCapacity | Int64 | Determines the maximum allowed Mbps \(megabits per second\) bandwidth from a branch site. The possible values are:`250`,`500`,`750`,`1000`. |
| connectivityState | microsoft.graph.networkaccess.connectivityState | Determines the branch site status. The possible values are: `pending`, `connected`, `inactive`, `error`. |
| id | String | Identifier for the branch. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | last modified time. |
| name | String | Name. |
| region | microsoft.graph.networkaccess.region | Specify the region closest to your remote network. The possible value are: `eastUS`, `eastUS2`, `westUS`, `westUS2`, `westUS3`, `centralUS`, `northCentralUS`, `southCentralUS`, `northEurope`, `westEurope`, `franceCentral`, `germanyWestCentral`, `switzerlandNorth`, `ukSouth`, `canadaEast`, `canadaCentral`, `southAfricaWest`, `southAfricaNorth`, `uaeNorth`, `australiaEast`, `westCentralUS`, `centralIndia`, `southEastAsia`, `swedenCentral`, `southIndia`, `australiaSouthEast`, `koreaCentral`, `koreaSouth`, `polandCentral`, `brazilSouth`, `japanEast`, `japanWest`, `koreaSouth`, `italyNorth`, `franceSouth`, `israelCentral`, `unknownFutureValue`. |
| version | String | The branch version. |
| country \(deprecated\) | String | The branch site is created in the specified country. **DO NOT USE.** |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| connectivityConfiguration | [microsoft.graph.networkaccess.branchConnectivityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchconnectivityconfiguration?view=graph-rest-beta) collection | Specifies the connectivity details of all device links associated with a branch. |
| deviceLinks | [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) collection | Each unique CPE device associated with a branch is specified. Supports `$expand`. |
| forwardingProfiles | [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) collection | Each forwarding profile associated with a branch site is specified. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.branchSite",
  "id": "String (identifier)",
  "name": "String",
  "country": "String",
  "region": "String",
  "connectivityState": "String",
  "bandwidthCapacity": "Integer",
  "version": "String",
  "lastModifiedDateTime": "String (timestamp)"
}
```
