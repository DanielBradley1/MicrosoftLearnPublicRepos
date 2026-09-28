<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessageviewpoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# serviceUpdateMessageViewpoint resource type

Namespace: microsoft.graph

Represents user view points data for a [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isArchived | Boolean | Indicates whether the user archived the message. |
| isFavorited | Boolean | Indicates whether the user marked the message as favorite. |
| isRead | Boolean | Indicates whether the user read the message. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serviceUpdateMessageViewpoint",
  "isRead": "Boolean",
  "isArchived": "Boolean",
  "isFavorited": "Boolean"
}
```
