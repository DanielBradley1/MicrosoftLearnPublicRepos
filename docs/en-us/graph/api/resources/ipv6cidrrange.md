<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ipv6cidrrange?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# iPv6CidrRange resource type

Namespace: microsoft.graph

Represents an IPv6 range using the Classless inter-domain routing \(CIDR\) notation.

Inherits from [ipRange](https://learn.microsoft.com/en-us/graph/api/resources/iprange?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cidrAddress | String | IPv6 address in CIDR notation. Not nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.iPv6CidrRange", 
  "cidrAddress": "String"
}
```
