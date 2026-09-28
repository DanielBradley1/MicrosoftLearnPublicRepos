<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# deviceLink resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A device link represents a single customer-premises equipment \(CPE\) at a remote network that's connected to the Global Secure Access services.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List deviceLinks](https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-list-devicelinks?view=graph-rest-beta) | [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) objects and their properties. |
| [Create deviceLink](https://learn.microsoft.com/en-us/graph/api/networkaccess-remotenetwork-post-devicelinks?view=graph-rest-beta) | None | Create a new [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) object. |
| [Get deviceLink](https://learn.microsoft.com/en-us/graph/api/networkaccess-devicelink-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) object. |
| [Delete deviceLink](https://learn.microsoft.com/en-us/graph/api/networkaccess-devicelink-delete?view=graph-rest-beta) | None | Delete a [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) object. |
| [List deviceLinks for a branchSite \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/networkaccess-branchsite-list-devicelinks?view=graph-rest-beta) | [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) objects and their properties. |
| [Create deviceLink for a branchSite \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/networkaccess-branchsite-post-devicelinks?view=graph-rest-beta) | None | Create a new [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bgpConfiguration | [microsoft.graph.networkaccess.bgpConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-bgpconfiguration?view=graph-rest-beta) | The border gateway protocol specifies the Border Gateway Protocol \(BGP\) IP address and ASN for directing traffic from a link to the edge. |
| bandwidthCapacityInMbps | Int64 | Determines the maximum allowed Mbps \(megabits per second\) bandwidth from a device link. The possible values are:`250`,`500`,`750`,`1000`. |
| deviceVendor | microsoft.graph.networkaccess.deviceVendor | Specifies the manufacturer of the deviceLink. The possible values are: `barracudaNetworks`, `checkPoint`, `ciscoMeraki`, `citrix`, `fortinet`, `hpeAruba`, `netFoundry`, `nuage`, `openSystems`, `paloAltoNetworks`, `riverbedTechnology`, `silverPeak`, `vmWareSdWan`, `versa`, `other`. |
| id | String | Identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| ipAddress | String | The public IP address of your CPE \(customer premise equipment\) device. |
| lastModifiedDateTime | DateTimeOffset | last modified time. |
| name | String | Name. |
| tunnelConfiguration | [microsoft.graph.networkaccess.tunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tunnelconfiguration?view=graph-rest-beta) | The connectivity settings, including the protocol, IPSec policy, and preshared key, are specified for establishing connectivity. |
| version | String | Version. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.deviceLink",
  "id": "String (identifier)",
  "name": "String",
  "ipAddress": "String",
  "deviceVendor": "String",
  "version": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "tunnelConfiguration": {
    "@odata.type": "microsoft.graph.networkaccess.tunnelConfiguration"
  },
  "bgpConfiguration": {
    "@odata.type": "microsoft.graph.networkaccess.bgpConfiguration"
  }
}
```
