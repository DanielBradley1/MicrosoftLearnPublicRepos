<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-organizationalscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# organizationalScope resource type

Namespace: microsoft.graph.security

Represents a scope that specifies which devices are covered by a [custom detection rule's](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) [detection action](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceGroups | String collection | List of device groups to which the custom detection rule applies. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.organizationalScope",
  "deviceGroups": [
    "String"
  ]
}
```
