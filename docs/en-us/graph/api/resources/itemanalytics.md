<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itemanalytics?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# itemAnalytics resource type

Namespace: microsoft.graph

The **itemAnalytics** resource provides analytics about activities that took place on an item. This resource is currently only available on SharePoint and OneDrive for Business.

You can also use the [getActivitiesByInterval](https://learn.microsoft.com/en-us/graph/api/itemactivitystat-getactivitybyinterval?view=graph-rest-1.0) API to retrieve analytics over a custom time range or interval.

> **Note:** The **itemAnalytics** resource is not yet available in all [national deployments](https://learn.microsoft.com/en-us/graph/deployments).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allTime | [itemActivityStat](https://learn.microsoft.com/en-us/graph/api/resources/itemactivitystat?view=graph-rest-1.0) | Analytics over the item's lifespan. |
| lastSevenDays | [itemActivityStat](https://learn.microsoft.com/en-us/graph/api/resources/itemactivitystat?view=graph-rest-1.0) | Analytics for the last seven days. |

## JSON representation

```json
{
  "allTime": {"@odata.type": "microsoft.graph.itemActivityStat"},
  "lastSevenDays": {"@odata.type": "microsoft.graph.itemActivityStat"}
}
```
