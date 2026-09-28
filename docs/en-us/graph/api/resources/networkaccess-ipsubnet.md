<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ipsubnet?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# ipSubnet resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An IP subnet is a portion of an IP network that shares a common network prefix. It is a logical subdivision of an IP network created by grouping IP addresses together based on a shared network mask. The subnet mask determines the size of the subnet and helps identify the network and host portions of an IP address.

Inherits from [microsoft.graph.networkaccess.ruleDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ruledestination?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| value | String | Defines the IP address of the subset used in a destination for a rule. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.ipSubnet",
  "value": "String"
}
```
