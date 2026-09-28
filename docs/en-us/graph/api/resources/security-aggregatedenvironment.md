<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-aggregatedenvironment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-20 -->

# aggregatedEnvironment resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents grouped [environments](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) by type within a specific [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta). These aggregations provide a quick summary of how many environments of each type are attached to a zone.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| count | Int32 | Number of environments of this type. |
| kind | String | Environment type. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.aggregatedEnvironment",
  "count": "Int32",
  "kind": "String (identifier)"
}
```
