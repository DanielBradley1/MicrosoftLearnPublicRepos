<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-mailclusterentitymapping?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# mailClusterEntityMapping resource type

Namespace: microsoft.graph.security

Represents a mapping from columns in a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) query result to a mail cluster entity that is attached to the resulting alert.

Base type: [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| queryColumn | String | Name of the detection query column that maps to the query of the alert entity. |
| sourceColumn | String | Name of the detection query column that maps to the source of the alert entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.mailClusterEntityMapping",
  "queryColumn": "String",
  "sourceColumn": "String"
}
```
