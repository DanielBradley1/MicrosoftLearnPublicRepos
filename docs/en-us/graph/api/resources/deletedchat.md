<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/deletedchat?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# deletedChat resource type

Namespace: microsoft.graph

Represents a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) that was deleted in Microsoft Teams.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/deletedchat-get?view=graph-rest-1.0) | [deletedChat](https://learn.microsoft.com/en-us/graph/api/resources/deletedchat?view=graph-rest-1.0) | Read the properties and relationships of a [deletedChat](https://learn.microsoft.com/en-us/graph/api/resources/deletedchat?view=graph-rest-1.0) object. |
| [Undo delete](https://learn.microsoft.com/en-us/graph/api/deletedchat-undodelete?view=graph-rest-1.0) | None | Restore a deleted chat as a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of a deleted chat. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deletedChat",
  "id": "String (identifier)"
}
```
