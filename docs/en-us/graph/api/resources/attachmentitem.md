<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attachmentitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# attachmentItem resource type

Namespace: microsoft.graph

Represents attributes of an item to be attached.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attachmentType | String | The type of attachment. The possible values are: `file`, `item`, `reference`. Required. |
| contentId | String | The CID or Content-Id of the attachment for referencing for the in-line attachments using the `<img src="cid:contentId">` tag in HTML messages. Optional. |
| contentType | String | The nature of the data in the attachment. Optional. |
| isInline | Boolean | `true` if the attachment is an inline attachment; otherwise, `false`. Optional. |
| name | String | The display name of the attachment. This can be a descriptive string and doesn't have to be the actual file name. Required. |
| size | Int64 | The length of the attachment in bytes. Required. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "attachmentType": "String",
  "contentId": "String",
  "contentType": "String",
  "isInline": true,
  "name": "String",
  "size": 1024
}
```
