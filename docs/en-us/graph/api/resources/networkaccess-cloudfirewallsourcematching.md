<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallsourcematching?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# cloudFirewallSourceMatching resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the [source matching criteria](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallmatchingconditions?view=graph-rest-beta) for a cloud firewall rule, including source addresses and ports. Currently, only IP address types are supported for source addresses.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addresses | [microsoft.graph.networkaccess.cloudFirewallSourceAddress](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallsourceaddress?view=graph-rest-beta) collection | The source addresses to match. An empty collection means don't filter by source addresses \(match all\). Required. |
| ports | String collection | The source ports to match, for example, `80`, `443`, `1024-2048`. An empty collection means don't filter by source ports \(match all\). Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallSourceMatching",
  "addresses": [
    {
      "@odata.type": "microsoft.graph.networkaccess.cloudFirewallSourceIpAddress"
    }
  ],
  "ports": ["String"]
}
```
