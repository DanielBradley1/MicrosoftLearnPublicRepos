<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/moveaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# moveAction resource type

Namespace: microsoft.graph

The presence of the **moveAction** resource on an [**itemActivity**](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) indicates that the activity moved an item.

> **Note:** Item activity records are currently only available on SharePoint and OneDrive for Business.

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| from | string | The name of the location the item was moved from. |
| to | string | The name of the location the item was moved to. |

## JSON representation

```json
{
  "from": "string",
  "to": "string"
}
```
