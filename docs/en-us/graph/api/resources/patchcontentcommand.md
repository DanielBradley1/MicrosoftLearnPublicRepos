<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/patchcontentcommand?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# patchContentCommand resource type

Namespace: microsoft.graph

The changes to make to a OneNote page in a PATCH request.

## JSON representation

The following JSON representation shows the resource type., which is sent in the body of the [PATCH pages/{id}`](https://learn.microsoft.com/en-us/graph/api/page-update?view=graph-rest-1.0) request.

```json
{
  "action": "String",
  "content": "string",
  "position": "String",
  "target": "string"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | onenotePatchActionType | The action to perform on the target element. The possible values are: `replace`, `append`, `delete`, `insert`, or `prepend`. |
| content | String | A string of well-formed HTML to add to the page, and any image or file binary data. If the content contains binary data, the request must be sent using the `multipart/form-data` content type with a "Commands" part. |
| position | onenotePatchInsertPosition | The location to add the supplied content, relative to the target element. The possible values are: `after` \(default\) or `before`. |
| target | String | The element to update. Must be the `#<data-id>` or the generated `<id>` of the element, or the `body` or `title` keyword. |
