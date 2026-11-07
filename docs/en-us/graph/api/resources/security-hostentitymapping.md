<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hostentitymapping?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# hostEntityMapping resource type

Namespace: microsoft.graph.security

Represents a mapping from columns in a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) query result to a host entity that is attached to the resulting alert.

Base type: [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceIdColumn | String | Name of the detection query column that maps to the device ID of the alert entity. |
| dnsDomainColumn | String | Name of the detection query column that maps to the DNS domain of the alert entity. |
| nameColumn | String | Name of the detection query column that maps to the name of the alert entity. |
| netBiosNameColumn | String | Name of the detection query column that maps to the NetBIOS name of the alert entity. |
| ntDomainColumn | String | Name of the detection query column that maps to the NT domain of the alert entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hostEntityMapping",
  "deviceIdColumn": "String",
  "dnsDomainColumn": "String",
  "nameColumn": "String",
  "netBiosNameColumn": "String",
  "ntDomainColumn": "String"
}
```
