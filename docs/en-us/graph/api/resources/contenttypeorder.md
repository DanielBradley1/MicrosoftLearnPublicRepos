<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contenttypeorder?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# contentTypeOrder resource type

Namespace: microsoft.graph

Specifies in which order the [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) appears in the selection UI.

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| default | Boolean | Indicates whether this is the default content type |
| position | Int32 | Specifies the position in which the content type appears in the selection UI. |

## JSON representation

The following is a JSON representation of the resource.

```json
{
  "default": "Boolean",
  "position": "Int32"
}
```
