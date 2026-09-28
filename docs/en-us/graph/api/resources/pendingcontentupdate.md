<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/pendingcontentupdate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# pendingContentUpdate resource type

Namespace: microsoft.graph

Indicates that an operation that might affect the binary content of the **driveItem** is pending completion.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| **queuedDateTime** | DateTimeOffset | Date and time the pending binary operation was queued in UTC time. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "queuedDateTime": "String (timestamp)"
}
```
