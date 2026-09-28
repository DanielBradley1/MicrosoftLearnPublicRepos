<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itemactivitystat?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# itemActivityStat resource type

Namespace: microsoft.graph

The **itemActivityStat** resource provides information about activities that took place within an interval of time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| access | [itemActionStat](https://learn.microsoft.com/en-us/graph/api/resources/itemactionstat?view=graph-rest-1.0) | Statistics about the **access** actions in this interval. Read-only. |
| create | [itemActionStat](https://learn.microsoft.com/en-us/graph/api/resources/itemactionstat?view=graph-rest-1.0) | Statistics about the **create** actions in this interval. Read-only. |
| delete | [itemActionStat](https://learn.microsoft.com/en-us/graph/api/resources/itemactionstat?view=graph-rest-1.0) | Statistics about the **delete** actions in this interval. Read-only. |
| edit | [itemActionStat](https://learn.microsoft.com/en-us/graph/api/resources/itemactionstat?view=graph-rest-1.0) | Statistics about the **edit** actions in this interval. Read-only. |
| endDateTime | DateTimeOffset | When the interval ends. Read-only. |
| incompleteData | [incompleteData](https://learn.microsoft.com/en-us/graph/api/resources/incompletedata?view=graph-rest-1.0) | Indicates that the statistics in this interval are based on incomplete data. Read-only. |
| isTrending | Boolean | Indicates whether the item is "trending." Read-only. |
| move | [itemActionStat](https://learn.microsoft.com/en-us/graph/api/resources/itemactionstat?view=graph-rest-1.0) | Statistics about the **move** actions in this interval. Read-only. |
| startDateTime | DateTimeOffset | When the interval starts. Read-only. |

## Relationships

| Relationship name | Type | Description |
| :--- | :--- | :--- |
| activities | [itemActivity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) collection | Exposes the **itemActivities** represented in this **itemActivityStat** resource. |

## JSON representation

```json
{
  "activities": [{"@odata.type": "microsoft.graph.itemActivity"}],
  "incompleteData": {"@odata.type": "microsoft.graph.incompleteData"},
  "isTrending": true,
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "create": {"@odata.type": "microsoft.graph.itemActionStat"},
  "delete": {"@odata.type": "microsoft.graph.itemActionStat"},
  "edit": {"@odata.type": "microsoft.graph.itemActionStat"},
  "move": {"@odata.type": "microsoft.graph.itemActionStat"},
  "access": {"@odata.type": "microsoft.graph.itemActionStat"}
}
```
