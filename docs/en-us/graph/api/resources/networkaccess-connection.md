<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-04 -->

# connection resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

In Global Secure Access \(GSA\) a connection represents multiple [networkAccessTraffic](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-networkaccesstraffic?view=graph-rest-beta) occurring and sharing single connection ID. Provides information about network connections including source and destination details, traffic statistics, and connection status.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-logs-list-connections?view=graph-rest-beta) | [microsoft.graph.networkaccess.connection](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connection?view=graph-rest-beta) collection | Get a list of the connection objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-connection-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.connection](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connection?view=graph-rest-beta) | Read the properties and relationships of a connection object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agentVersion | String | The version of the client that initiated the connection. |
| applicationSnapshot | [microsoft.graph.networkaccess.applicationSnapshot](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-applicationsnapshot?view=graph-rest-beta) | **appId** \(or client ID\) of the destination Microsoft Entra application. |
| createdDateTime | DateTimeOffset | The time the connection was created. |
| crossTenantAccessType | microsoft.graph.networkaccess.crossTenantAccessType | Cross tenant access details, for B2B scenarios. The possible values are: `none`, `b2bCollaboration`, `unknownFutureValue`. |
| destinationFqdn | String | The destination FQDN of the connection. |
| destinationIp | String | The destination IP of the connection. |
| destinationPort | Int32 | The destination port of the connection. |
| deviceCategory | microsoft.graph.networkaccess.deviceCategory | The category of the device. The possible values are: `client`, `branch`, `unknownFutureValue`, `remoteNetwork`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `remoteNetwork`. |
| deviceId | String | The DeviceID. |
| deviceJoinType | microsoft.graph.networkaccess.deviceJoinType | Device registration type, for BYOD scenarios. The possible values are: `none`, `microsoftEntraJoined`, `microsoftEntraRegistered`, `unknownFutureValue`. |
| deviceOperatingSystem | String | The device operating system type. |
| deviceOperatingSystemVersion | String | The device operating system version. |
| endDateTime | DateTimeOffset | The time the connection was terminated. |
| homeTenantId | String | The identifier of the home tenant, for Entra B2B scenarios. |
| id | String | The unique identifier for the connection. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| initiatingProcessName | String | The process initiating the traffic connection. |
| lastUpdateDateTime | DateTimeOffset | When the connection was last updated. |
| networkProtocol | microsoft.graph.networkaccess.networkingProtocol | The network protocol of the connection. The possible values are: `ip`, `icmp`, `igmp`, `ggp`, `ipv4`, `tcp`, `pup`, `udp`, `idp`, `ipv6`, `ipv6RoutingHeader`, `ipv6FragmentHeader`, `ipSecEncapsulatingSecurityPayload`, `ipSecAuthenticationHeader`, `icmpV6`, `ipv6NoNextHeader`, `ipv6DestinationOptions`, `nd`, `raw`, `ipx`, `spx`, `spxII`, `unknownFutureValue`. |
| popProcessingRegion | String | The Point-of-Presence processing region of the traffic. |
| privateAccessDetails | [microsoft.graph.networkaccess.privateAccessDetails](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-privateaccessdetails?view=graph-rest-beta) | Private access details. |
| receivedBytes | Int64 | Accumulative bytes received. |
| sentBytes | Int64 | Accumulative bytes sent. |
| sourceIp | String | The source IP of the connection. |
| sourcePort | Int32 | The source port of the connection. |
| status | microsoft.graph.networkaccess.connectionStatus | Status of the connection. The possible values are: `open`, `active`, `closed`, `unknownFutureValue`. |
| tenantId | String | The ID of the tenant where the connection was initiated. |
| trafficType | microsoft.graph.networkaccess.trafficType | The type of traffic. The possible values are: `internet`, `private`, `microsoft365`, `all`, `unknownFutureValue`, `microsoft`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `microsoft`. |
| transactionBlockCount | Int32 | The number of blocked transactions belonging to the connection. |
| transactionCount | Int32 | The number of transactions belonging to the connection. |
| transportProtocol | microsoft.graph.networkaccess.networkingProtocol | The transport protocol of the connection. The possible values are: `ip`, `icmp`, `igmp`, `ggp`, `ipv4`, `tcp`, `pup`, `udp`, `idp`, `ipv6`, `ipv6RoutingHeader`, `ipv6FragmentHeader`, `ipSecEncapsulatingSecurityPayload`, `ipSecAuthenticationHeader`, `icmpV6`, `ipv6NoNextHeader`, `ipv6DestinationOptions`, `nd`, `raw`, `ipx`, `spx`, `spxII`, `unknownFutureValue`. |
| userId | String | The user ID. |
| userPrincipalName | String | The principal name of the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.connection",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "tenantId": "String",
  "lastUpdateDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "status": "String",
  "trafficType": "String",
  "transactionCount": "Integer",
  "transactionBlockCount": "Integer",
  "sentBytes": "Integer",
  "receivedBytes": "Integer",
  "destinationIp": "String",
  "destinationPort": "Integer",
  "destinationFqdn": "String",
  "userId": "String",
  "sourceIp": "String",
  "sourcePort": "Integer",
  "initiatingProcessName": "String",
  "deviceId": "String",
  "deviceOperatingSystem": "String",
  "deviceOperatingSystemVersion": "String",
  "agentVersion": "String",
  "applicationSnapshot": {
    "@odata.type": "microsoft.graph.networkaccess.applicationSnapshot"
  },
  "privateAccessDetails": {
    "@odata.type": "microsoft.graph.networkaccess.privateAccessDetails"
  },
  "deviceCategory": "String",
  "userPrincipalName": "String",
  "transportProtocol": "String",
  "networkProtocol": "String",
  "popProcessingRegion": "String",
  "homeTenantId": "String",
  "crossTenantAccessType": "String",
  "deviceJoinType": "String"
}
```
