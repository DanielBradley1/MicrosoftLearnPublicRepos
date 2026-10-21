<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/taskcapability?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# taskCapability resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **capabilities** property of the [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) resource uses this type.

Server-computed, read-only capability flags indicating which optional features are enabled for a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedPriorityForTaskPersonalView | Boolean | Indicates whether assigned priority is shown in the task's personal view. |
| dependencies | Boolean | Indicates whether dependencies are enabled for the task. |
| history | Boolean | Indicates whether history tracking is enabled for the task. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.taskCapability",
  "assignedPriorityForTaskPersonalView": "Boolean",
  "dependencies": "Boolean",
  "history": "Boolean"
}
```
