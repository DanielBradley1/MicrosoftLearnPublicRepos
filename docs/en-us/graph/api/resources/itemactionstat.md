<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itemactionstat?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# itemActionStat resource type

Namespace: microsoft.graph

The **itemActionStat** resource provides aggregate details about an action over a period of time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionCount | Int32 | The number of times the action took place. Read-only. |
| actorCount | Int32 | The number of distinct actors that performed the action. Read-only. |

## JSON representation

```json
{
  "actionCount": 123,
  "actorCount": 60
}
```
