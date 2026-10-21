<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/planview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# planView resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **planView** property of the [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) resource uses this type.

Plan-scoped view metadata for a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta), including the plan's category definitions.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categories | [categoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/categorydefinition?view=graph-rest-beta) collection | The collection of category definitions available in the plan. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.planView"
}
```
