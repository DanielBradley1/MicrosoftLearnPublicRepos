<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewalldestinationaddress?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# cloudFirewallDestinationAddress resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract base type for matching addresses in a [cloud firewall destination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewalldestinationmatching?view=graph-rest-beta). Use the `@odata.type` property to specify the concrete derived type in requests.

The following types are derived from this resource:

- [microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewalldestinationipaddress?view=graph-rest-beta)
- [microsoft.graph.networkaccess.cloudFirewallDestinationFqdnAddress](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewalldestinationfqdnaddress?view=graph-rest-beta)

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallDestinationAddress"
}
```
