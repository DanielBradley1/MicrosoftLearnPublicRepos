<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-discoveredapplicationsegmentreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-04-11 -->

# discoveredApplicationSegmentReport resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a report about application segments detected in network traffic through Global Secure Access services.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessType | microsoft.graph.networkaccess.accessType | The type of access used to connect to this application segment. The possible values are: `quickAccess`, `privateAccess`, `unknownFutureValue`, `appAccess`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `appAccess`. |
| deviceCount | Int32 | The number of unique devices that have accessed this application segment. |
| discoveredApplicationSegmentId | String | The unique identifier for this discovered application segment. |
| firstAccessDateTime | DateTimeOffset | The date and time when this application segment was first accessed. |
| fqdn | String | The fully qualified domain name associated with this application segment. |
| ip | String | The IP address associated with this application segment. |
| lastAccessDateTime | DateTimeOffset | The date and time when this application segment was last accessed. |
| port | Int32 | The port number used to access this application segment. |
| totalBytesReceived | Int64 | The total number of bytes received from this application segment. |
| totalBytesSent | Int64 | The total number of bytes sent to this application segment. |
| transactionCount | Int32 | The number of transactions recorded for this application segment. |
| transportProtocol | microsoft.graph.networkaccess.networkingProtocol | The transport protocol used to access this application segment. The possible values are: `ip`, `icmp`, `igmp`, `ggp`, `ipv4`, `tcp`, `pup`, `udp`, `idp`, `ipv6`, `ipv6RoutingHeader`, `ipv6FragmentHeader`, `ipSecEncapsulatingSecurityPayload`, `ipSecAuthenticationHeader`, `icmpV6`, `ipv6NoNextHeader`, `ipv6DestinationOptions`, `nd`, `raw`, `ipx`, `spx`, `spxII`, `unknownFutureValue`. |
| userCount | Int32 | The number of unique users who have accessed this application segment. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.discoveredApplicationSegmentReport",
  "discoveredApplicationSegmentId": "String",
  "fqdn": "String",
  "ip": "String",
  "port": "Integer",
  "transportProtocol": "String",
  "accessType": "String",
  "firstAccessDateTime": "String (timestamp)",
  "lastAccessDateTime": "String (timestamp)",
  "transactionCount": "Integer",
  "userCount": "Integer",
  "deviceCount": "Integer",
  "totalBytesSent": "Integer",
  "totalBytesReceived": "Integer"
}
```
