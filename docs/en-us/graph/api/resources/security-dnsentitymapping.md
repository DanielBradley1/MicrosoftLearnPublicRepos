<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-dnsentitymapping?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# dnsEntityMapping resource type

Namespace: microsoft.graph.security

Represents a mapping from columns in a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) query result to a DNS entity that is attached to the resulting alert.

Base type: [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| domainNameColumn | String | Name of the detection query column that maps to the domain name of the alert entity. |
| hostIpAddressColumn | String | Name of the detection query column that maps to the host IP address of the alert entity. |
| serverIpColumn | String | Name of the detection query column that maps to the server IP address of the alert entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.dnsEntityMapping",
  "domainNameColumn": "String",
  "hostIpAddressColumn": "String",
  "serverIpColumn": "String"
}
```
