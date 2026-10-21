<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/taskplanview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# taskPlanView resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **planView** property of the [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) resource uses this type.

Task view metadata scoped to a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta), such as the category IDs applied to a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) within that plan.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appliedCategoryIds | String collection | IDs of the categories applied to the task within this plan. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.taskPlanView",
  "appliedCategoryIds": [
    "String"
  ]
}
```
