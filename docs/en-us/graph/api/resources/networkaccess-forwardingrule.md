<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# forwardingRule resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A forwarding rule is utilized to selectively forward traffic to the Global Secure Access services based on specific requirements or preferences.

This is an abstract type from which the [m365ForwardingRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-m365forwardingrule?view=graph-rest-beta) and [privateAccessForwardingRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-privateaccessforwardingrule?view=graph-rest-beta) resource types are derived.

Inherits from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.networkaccess.forwardingRuleAction | The action to apply to traffic. The possible values are: `bypass`, `forward`, `unknownFutureValue`. |
| destinations | [microsoft.graph.networkaccess.ruleDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ruledestination?view=graph-rest-beta) collection | Destinations maintain a list of potential destinations and destination types that the user may access within the context of a network filtering policy. This includes IP addresses and fully qualified domain names \(FQDNs\)/URLs. |
| id | String | Identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| name | String | Name. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). |
| ruleType | microsoft.graph.networkaccess.networkDestinationType | The network destination type used by a URL filtering policy is defined, which can include types such as IP \(Internet Protocol\) or FQDN \(Fully Qualified Domain Name\). The possible values are: `url`, `fqdn`, `ipAddress`, `ipRange`, `ipSubnet`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.forwardingRule",
  "id": "String (identifier)",
  "name": "String",
  "ruleType": "String",
  "action": "String",
  "destinations": [
    {
      "@odata.type": "microsoft.graph.networkaccess.webCategory"
    }
  ]
}
```
