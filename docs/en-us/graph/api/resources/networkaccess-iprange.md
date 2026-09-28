<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-iprange?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# ipRange resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An IP address range represents either a specific IP address or a range of IP addresses. It is used to define a set of network addresses or a single network endpoint within a specified range.

Inherits from [microsoft.graph.networkaccess.ruleDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ruledestination?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| beginAddress | String | Specifies the starting IP address of the IP range. |
| endAddress | String | Specifies the ending IP address of the IP range. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.ipRange",
  "beginAddress": "String",
  "endAddress": "String"
}
```
