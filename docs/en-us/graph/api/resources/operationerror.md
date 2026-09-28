<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/operationerror?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# operationError resource type

Namespace: microsoft.graph

Describes errors in [teamsAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0).

## operationError Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | string \(readonly\) | Operation error code. |
| message | string \(readonly\) | Operation error message. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "code": "TeamUnavailable",
    "message": "The team was not found."
}
```
