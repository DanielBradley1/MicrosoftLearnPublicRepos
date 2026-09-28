<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/pendingoperations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# pendingOperations resource type

Namespace: microsoft.graph

Indicates that one or more operations that might affect the state of the **driveItem** are pending completion.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| **pendingContentUpdate** | [pendingContentUpdate](https://learn.microsoft.com/en-us/graph/api/resources/pendingcontentupdate?view=graph-rest-1.0) | A property that indicates that an operation that might update the binary content of a file is pending completion. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "pendingContentUpdate": {"@odata.type": "microsoft.graph.pendingContentUpdate"}
}
```
