<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-processentitymapping?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# processEntityMapping resource type

Namespace: microsoft.graph.security

Represents a mapping from columns in a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) query result to a process entity that is attached to the resulting alert.

Base type: [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| sha1Column | String | Name of the detection query column that maps to the SHA-1 hash of the alert entity. |
| sha256Column | String | Name of the detection query column that maps to the SHA-256 hash of the alert entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.processEntityMapping",
  "sha1Column": "String",
  "sha256Column": "String"
}
```
