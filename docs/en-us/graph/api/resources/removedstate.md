<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/removedstate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# removedState resource type

Namespace: microsoft.graph

Represents the reason why a [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-1.0) resource was removed from a roster.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| reason | String | The removal reason for the **participant** resource. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.removedState",
  "reason": "String"
}
```
