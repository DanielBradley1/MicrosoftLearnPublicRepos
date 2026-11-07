<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-securitygroupentitymapping?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# securityGroupEntityMapping resource type

Namespace: microsoft.graph.security

Represents a mapping from columns in a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) query result to a security group entity that is attached to the resulting alert.

Base type: [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| distinguishedNameColumn | String | Name of the detection query column that maps to the distinguished name of the alert entity. |
| objectIdColumn | String | Name of the detection query column that maps to the object ID of the alert entity. |
| sidColumn | String | Name of the detection query column that maps to the security identifier \(SID\) of the alert entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.securityGroupEntityMapping",
  "distinguishedNameColumn": "String",
  "objectIdColumn": "String",
  "sidColumn": "String"
}
```
