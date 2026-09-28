<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetworkhealthevent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# remoteNetworkHealthEvent resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains information about network health, status, metrics, and operations.

This resource is an abstract type.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-logs-list-remotenetworks?view=graph-rest-beta) | [microsoft.graph.networkaccess.remotenetworkhealthevent](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetworkhealthevent?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.networkaccess.remotenetworkhealthevent](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetworkhealthevent?view=graph-rest-beta) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bgpRoutesAdvertisedCount | Int32 | The number of BGP routes advertised through tunnel. |
| createdDateTime | DateTimeOffset | The time of the original event generation in UTC. Supports `$filter` \(`ge`, `le`\) and `$orderby`. |
| description | String | The description of the event. |
| destinationIp | String | The IP address of the destination. |
| id | String | A unique identifier for each remoteNetworkHealthEvent. |
| remoteNetworkId | String | A unique identifier for each remoteNetwork site. Supports `$filter` \(`eq`\). |
| sourceIp | String | The public IP address. |
| status | microsoft.graph.networkaccess.remoteNetworkStatus | The status of the remote network. The possible values are: `tunnelDisconnected`, `tunnelConnected`, `bgpDisconnected`, `bgpConnected`, `remoteNetworkAlive`, `unknownFutureValue`. |
| sentBytes | Int64 | The number of bytes sent from the source to the destination for the connection or session. |
| receivedBytes | Int64 | The number of bytes sent from the destination to the source. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
      "id": "String (identifier)",
      "remoteNetworkId": "String (identifier)",
      "createdDateTime": "String (timestamp)",
      "status": "enum",
      "sourceIp": "String (IP address)",
      "destinationIp": "String (IP address)",
      "sentBytes": "Integer",
      "receivedBytes": "Integer",
      "description": "String",
      "bgpRoutesAdvertisedCount": "Integer"
}
```
