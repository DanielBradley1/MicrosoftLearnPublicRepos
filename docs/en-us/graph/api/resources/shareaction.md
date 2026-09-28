<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/shareaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# shareAction resource type

Namespace: microsoft.graph

The **shareAction** resource provides information about an [activity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) that shared an item.

> **Note:** Item activity records are currently only available on SharePoint and OneDrive for Business.

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| recipients | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) collection | The identities the item was shared with in this action. |

## JSON representation

```json
{
  "recipients": [{"@odata.type": "microsoft.graph.identitySet"}]
}
```
