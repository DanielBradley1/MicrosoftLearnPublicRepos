<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingoptions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# forwardingOptions resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

ForwardingOptions object includes the skipDnsLookupState settings, which determine whether DNS lookup will be performed at the client. This setting allows Microsoft 365 traffic to be forwarded directly to Azure Front Door. Alternatively, DNS resolution can be conducted at the Edge. This operation provides control over the traffic flow and DNS resolution strategy within the network infrastructure.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingoptions-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.forwardingOptions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingoptions?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.networkaccess.forwardingOptions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingoptions?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingoptions-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.forwardingOptions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingoptions?view=graph-rest-beta) | Update the properties of a [microsoft.graph.networkaccess.forwardingOptions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingoptions?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| skipDnsLookupState | microsoft.graph.networkaccess.status | Dns lookup options. The possible values are: `enabled`, `disabled`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.forwardingOptions",
  "id": "String (identifier)",
  "skipDnsLookupState": "String"
}
```
