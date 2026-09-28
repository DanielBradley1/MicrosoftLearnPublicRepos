<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallmatchingconditions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# cloudFirewallMatchingConditions resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the conditions that network traffic must match for a [cloud firewall rule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta) to apply. All specified conditions use "AND" logic between properties, meaning all specified criteria must be met. Within collections, items use "OR" logic, meaning any one value in the collection can match. At least one of the **sources** or **destinations** properties must have a value.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| destinations | [microsoft.graph.networkaccess.cloudFirewallDestinationMatching](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewalldestinationmatching?view=graph-rest-beta) | Destination address, port, and protocol matching criteria. `null` means don't match on destination. Optional. |
| sources | [microsoft.graph.networkaccess.cloudFirewallSourceMatching](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallsourcematching?view=graph-rest-beta) | Source address and port matching criteria. `null` means don't match on source. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallMatchingConditions",
  "sources": {
    "@odata.type": "microsoft.graph.networkaccess.cloudFirewallSourceMatching"
  },
  "destinations": {
    "@odata.type": "microsoft.graph.networkaccess.cloudFirewallDestinationMatching"
  }
}
```
