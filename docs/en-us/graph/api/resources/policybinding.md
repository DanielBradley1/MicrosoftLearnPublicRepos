<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policybinding?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# policyBinding resource type

Namespace: microsoft.graph

Defines the user/group inclusions and exclusions for a [tenant-level policy scope](https://learn.microsoft.com/en-us/graph/api/resources/policytenantscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| exclusions | [scopeBase](https://learn.microsoft.com/en-us/graph/api/resources/scopebase?view=graph-rest-1.0) collection | Specifies the users or groups to be explicitly excluded from this policy scope. Can be null or empty. |
| inclusions | [scopeBase](https://learn.microsoft.com/en-us/graph/api/resources/scopebase?view=graph-rest-1.0) collection | Specifies the users or groups to be included in this policy scope. Often set to `tenantScope` for "All users". |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.policyBinding",
  "inclusions": [
    { "@odata.type": "microsoft.graph.scopeBase" }
  ],
  "exclusions": [
    { "@odata.type": "microsoft.graph.scopeBase" }
  ]
}
```
