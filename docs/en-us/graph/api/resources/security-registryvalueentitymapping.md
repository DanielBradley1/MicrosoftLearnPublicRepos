<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-registryvalueentitymapping?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# registryValueEntityMapping resource type

Namespace: microsoft.graph.security

Represents a mapping from columns in a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) query result to a registry value entity that is attached to the resulting alert.

Base type: [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| keyColumn | String | Name of the detection query column that maps to the registry key of the alert entity. |
| valueNameColumn | String | Name of the detection query column that maps to the value name of the alert entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.registryValueEntityMapping",
  "keyColumn": "String",
  "valueNameColumn": "String"
}
```
