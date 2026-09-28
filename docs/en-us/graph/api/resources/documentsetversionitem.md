<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/documentsetversionitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# documentSetVersionItem resource type

Namespace: microsoft.graph

Represents an [item](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) that is a part of a captured [documentSetVersion](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| itemId | String | The unique identifier for the item. |
| title | String | The title of the item. |
| versionId | String | The version ID of the item. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.documentSetVersionItem",
  "itemId": "String",
  "title": "String",
  "versionId": "String"
}
```
