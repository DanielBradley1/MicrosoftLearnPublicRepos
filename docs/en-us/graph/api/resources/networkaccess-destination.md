<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-destination?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# destination resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A unique network destination.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceCount | Int32 | The number of unique devices that were seen. |
| fqdn | String | The fully qualified domain name \(FQDN\) of the destination. |
| ip | String | The internet protocol \(IP\) used to access the destination. |
| lastAccessDateTime | DateTimeOffset | The most recent access DateTime. |
| networkingProtocol | microsoft.graph.networkaccess.networkingProtocol | The set of communication rules and conventions that govern data transmission between devices in a network. The possible values are: `ip`, `icmp`, `igmp`, `ggp`, `ipv4`, `tcp`, `pup`, `udp`, `idp`, `ipv6`, `ipv6RoutingHeader`, `ipv6FragmentHeader`, `ipSecEncapsulatingSecurityPayload`, `ipSecAuthenticationHeader`, `icmpV6`, `ipv6NoNextHeader`, `ipv6DestinationOptions`, `nd`, `raw`, `ipx`, `spx`, and `spxII`. |
| port | Int32 | The numeric identifier that is associated with a specific endpoint in a network. |
| trafficType | microsoft.graph.networkaccess.trafficType | The traffic classification. The possible values are `internet`, `private`, `microsoft365`, and `all`. |
| transactionCount | Int32 | The number of transactions. |
| userCount | Int32 | The number of unique Microsoft Entra ID users that were seen. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.destination",
  "fqdn": "String",
  "ip": "String",
  "port": "Integer",
  "networkingProtocol": "String",
  "trafficType": "String",
  "lastAccessDateTime": "String (timestamp)",
  "transactionCount": "Integer",
  "userCount": "Integer",
  "deviceCount": "Integer"
}
```
