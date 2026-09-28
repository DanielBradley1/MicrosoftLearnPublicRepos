<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/planner?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# planner resource type

Namespace: microsoft.graph

The **planner** resource is the entry point for the Planner object model. It returns a singleton **planner** resource. It doesn't contain any usable properties.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create bucket](https://learn.microsoft.com/en-us/graph/api/planner-post-buckets?view=graph-rest-1.0) | [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-1.0) | Create a new **plannerBucket** by posting to the buckets collection. |
| [Create plan](https://learn.microsoft.com/en-us/graph/api/planner-post-plans?view=graph-rest-1.0) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) | Create a new **plannerPlan** by posting to the plans collection. |
| [Create task](https://learn.microsoft.com/en-us/graph/api/planner-post-tasks?view=graph-rest-1.0) | [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) | Create a new **plannerTask** by posting to the tasks collection. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| buckets | [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-1.0) collection | Read-only. Nullable. Returns a collection of the specified buckets |
| plans | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) collection | Read-only. Nullable. Returns a collection of the specified plans |
| tasks | [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) collection | Read-only. Nullable. Returns a collection of the specified tasks |

## JSON representation

The following JSON representation shows the resource type.

```json
{
}
```

## Example

The **planner** resource is available at the root of the graph.

```http
GET https://graph.microsoft.com/v1.0/planner
```

```http
HTTP/1.1 200 OK
Content-type: application/json

{
}
```
