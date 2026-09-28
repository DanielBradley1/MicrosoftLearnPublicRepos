<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itemattachment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-08 -->

# itemAttachment resource type

Namespace: microsoft.graph

A contact, event, or message that's attached to a user [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0), [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), or [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0).

Derived from [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/attachment-get?view=graph-rest-1.0) | [itemAttachment](https://learn.microsoft.com/en-us/graph/api/resources/itemattachment?view=graph-rest-1.0) | Read the properties, relationships, or raw contents of an itemAttachment object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/attachment-delete?view=graph-rest-1.0) | None | Delete itemAttachment object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentType | String | The content type of the attachment. Returned as `null` by default, when not set explicitly. Optional. |
| id | String | The attachment ID. |
| isInline | Boolean | Set to true if the attachment is inline, such as an embedded image within the body of the item. |
| lastModifiedDateTime | DateTimeOffset | The last time and date that the attachment was modified. |
| name | String | The display name of the attachment. |
| size | Int32 | The size in bytes of the attachment. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| item | [OutlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0) | The attached message or event. Navigation property. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "contentType": "string",
  "id": "string (identifier)",
  "isInline": true,
  "lastModifiedDateTime": "String (timestamp)",
  "name": "string",
  "size": 1024,
  "item": { "@odata.type": "microsoft.graph.outlookItem" }
}
```
