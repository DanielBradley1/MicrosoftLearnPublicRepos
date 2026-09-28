<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-m365forwardingrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# m365ForwardingRule resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the rule or criteria used to direct and route specific Microsoft 365 traffic through the Global Secure Access services.

Inherits from [microsoft.graph.networkaccess.forwardingRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingrule?view=graph-rest-beta).

## Methods

None.

For API operations for managing forward rules, see [policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.networkaccess.forwardingRuleAction | The action applies to traffic. The possible values are: `bypass`, `forward`. |
| category | microsoft.graph.networkaccess.forwardingCategory | Defines the category of Office 365 traffic used by a forwarding rule for Microsoft 365 traffic \(for example, optimized traffic\). The possible values are: `default`, `optimized`, `allow`. |
| destinations | [microsoft.graph.networkaccess.ruleDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ruledestination?view=graph-rest-beta) collection | destinations à Maintains the list of potential destinations and destination types that the user could be accessing in the context of a forwarding policy, including IPs and FQDNs/URLs Inherited from [microsoft.graph.networkaccess.forwardingRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingrule?view=graph-rest-beta). |
| ID | String | Identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| name | String | Name. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). |
| ports | String collection | The port\(s\) used by a forwarding rule for Microsoft 365 traffic are specified to determine the specific network port\(s\) through which the Microsoft 365 traffic is directed and forwarded. |
| protocol | microsoft.graph.networkaccess.networkingProtocol | Defines the networking protocol type used by a forwarding rule for Microsoft 365 traffic. The possible values are: `ip`, `icmp`, `igmp`, `ggp`, `ipv4`, `tcp`, `pup`, `udp`, `idp`, `ipv6`, `ipv6RoutingHeader`, `ipv6FragmentHeader`, `ipSecEncapsulatingSecurityPayload`, `ipSecAuthenticationHeader`, `icmpV6`, `ipv6NoNextHeader`, `ipv6DestinationOptions`, `nd`, `raw`, `ipx`, `spx`, `spxII` |
| ruleType | microsoft.graph.networkaccess.networkDestinationType | Destination Type. Inherited from [microsoft.graph.networkaccess.forwardingRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingrule?view=graph-rest-beta). The possible values are: `url`, `fqdn`, `ipAddress`, `ipRange`, `ipSubnet`, `webCategory`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.m365ForwardingRule",
  "id": "String (identifier)",
  "name": "String",
  "ruleType": "String",
  "action": "String",
  "destinations": [
    {
      "@odata.type": "microsoft.graph.networkaccess.webCategory"
    }
  ],
  "protocol": "String",
  "ports": [
    "String"
  ],
  "category": "String"
}
```
