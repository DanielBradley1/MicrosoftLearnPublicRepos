<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-privateaccessforwardingrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# privateAccessForwardingRule resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A private access forwarding rule is a rule within a network configuration that enables the forwarding or routing of network traffic for private access.

Inherits from [microsoft.graph.networkaccess.forwardingRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingrule?view=graph-rest-beta).

## Methods

None.

For API operations for managing forward rules, see [policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.networkaccess.forwardingRuleAction | The action applies to traffic. The possible values are: `bypass`, `forward`. |
| destinations | [microsoft.graph.networkaccess.ruleDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ruledestination?view=graph-rest-beta) collection | maintains the list of potential destinations and destination types that the user could be accessing in the context of a forwarding policy, including IPs and FQDNs/URLs Inherited from [microsoft.graph.networkaccess.forwardingRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingrule?view=graph-rest-beta). |
| id | String | Identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| name | String | Name. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). |
| ruleType | microsoft.graph.networkaccess.networkDestinationType | Destination Type. Inherited from [microsoft.graph.networkaccess.forwardingRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingrule?view=graph-rest-beta). The possible values are: `url`, `fqdn`, `ipAddress`, `ipRange`, `ipSubnet` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.privateAccessForwardingRule",
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
