<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ipv4cidrrange?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# iPv4CidrRange resource type

Namespace: microsoft.graph

Represents an IPv4 range using the Classless inter-domain routing \(CIDR\) notation.

Inherits from [ipRange](https://learn.microsoft.com/en-us/graph/api/resources/iprange?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cidrAddress | String | IPv4 address in CIDR notation. Not nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.iPv4CidrRange",  
  "cidrAddress": "String"
}
```
