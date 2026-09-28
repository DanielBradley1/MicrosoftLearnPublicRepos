<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallsourceaddress?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# cloudFirewallSourceAddress resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract base type for [cloud firewall source addresses](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallsourcematching?view=graph-rest-beta). Use the `@odata.type` property to specify the concrete derived type in requests. Currently, only IP address types are supported for sources.

The following type is derived from this resource:

- [microsoft.graph.networkaccess.cloudFirewallSourceIpAddress](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallsourceipaddress?view=graph-rest-beta)

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallSourceAddress"
}
```
