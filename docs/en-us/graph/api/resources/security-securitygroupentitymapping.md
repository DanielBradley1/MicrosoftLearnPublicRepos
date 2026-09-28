<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-securitygroupentitymapping?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# securityGroupEntityMapping resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a mapping from columns in a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) query result to a security group entity that is attached to the resulting alert.

Base type: [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-beta).

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
