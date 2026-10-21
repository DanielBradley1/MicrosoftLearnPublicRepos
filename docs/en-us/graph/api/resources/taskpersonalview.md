<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/taskpersonalview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# taskPersonalView resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **personalView** property of the [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) resource uses this type.

Per-user personal view metadata for a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta), such as whether the task is on the user's My Day view.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isOnMyDay | Boolean | Indicates whether the task is included in the user's My Day view. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.taskPersonalView",
  "isOnMyDay": "Boolean"
}
```
