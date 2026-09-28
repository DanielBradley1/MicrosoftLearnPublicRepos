<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# itemBody resource type

Namespace: microsoft.graph

Represents properties of the body of an item, such as a message, event or group post.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | The content of the item. |
| contentType | bodyType | The type of the content. Possible values are `text` and `html`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "content": "string",
  "contentType": "String"
}
```
