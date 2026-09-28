<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewalldestinationmatching?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# cloudFirewallDestinationMatching resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the destination matching criteria for a [cloud firewall rule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta), including destination addresses, ports, and protocols.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addresses | [microsoft.graph.networkaccess.cloudFirewallDestinationAddress](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewalldestinationaddress?view=graph-rest-beta) collection | The destination addresses to match. An empty collection means don't filter by destination addresses \(match all\). Required. |
| ports | String collection | The destination ports to match, for example, `80`, `443`, `1024-2048`. An empty collection means don't filter by destination ports \(match all\). Required. |
| protocols | microsoft.graph.networkaccess.cloudFirewallProtocol | The network protocols to match. This is a flagged enumeration that allows multiple values to be selected simultaneously, for example, `tcp, udp`. An empty collection means don't filter by protocol \(match all\). The possible values are: `tcp`, `udp`, `unknownFutureValue`. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallDestinationMatching",
  "addresses": [
    {
      "@odata.type": "microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress"
    }
  ],
  "ports": ["String"],
  "protocols": "String"
}
```
