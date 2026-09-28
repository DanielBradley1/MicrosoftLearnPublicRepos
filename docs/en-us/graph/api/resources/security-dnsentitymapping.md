<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-dnsentitymapping?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# dnsEntityMapping resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a mapping from columns in a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) query result to a DNS entity that is attached to the resulting alert.

Base type: [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-beta).

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
