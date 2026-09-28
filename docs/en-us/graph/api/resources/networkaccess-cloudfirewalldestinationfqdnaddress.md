<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewalldestinationfqdnaddress?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# cloudFirewallDestinationFqdnAddress resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a collection of fully qualified domain names \(FQDNs\) for destination address matching in [cloud firewall rules](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta).

Inherits from [microsoft.graph.networkaccess.cloudFirewallDestinationAddress](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewalldestinationaddress?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| values | String collection | A collection of FQDNs for destination address matching \(for example, `example.com`, `api.contoso.com`\). Empty collections are not allowed. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallDestinationFqdnAddress",
  "values": [
    "String"
  ]
}
```
