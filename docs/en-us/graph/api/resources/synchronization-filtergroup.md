<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-filtergroup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# filterGroup resource type

Namespace: microsoft.graph

Defines a set of clauses that an object must satisfy to be considered in scope. An object is considered in scope for the group \(the group is evaluated to `true`\) only if all the clauses of the group are evaluated to `true`. This object is configured in the **groups**, **categoryFilterGroups**, and **inputFilterGroups** properties of [filter](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-filter?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clauses | [filterClause](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-filterclause?view=graph-rest-1.0) collection | Filter clauses \(conditions\) of this group. All clauses in a group must be satisfied in order for the filter group to evaluate to `true`. |
| name | String | Human-readable name of the filter group. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "clauses": [
    {
      "@odata.type": "microsoft.graph.filterClause"
    }
  ],
  "name": "String"
}
```
