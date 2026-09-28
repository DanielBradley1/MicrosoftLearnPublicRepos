<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-08 -->

# attachment resource type

Namespace: microsoft.graph

You can add related content to a user [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0), [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), or [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) in the form of an attachment.

Events in group calendars do not support attachments.

**attachment** is the base resource for the following derived types of attachments:

- A file \([fileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/fileattachment?view=graph-rest-1.0) resource\)
- An item \(contact, event or message, represented by an [itemAttachment](https://learn.microsoft.com/en-us/graph/api/resources/itemattachment?view=graph-rest-1.0) resource\)
- A link to a file \([referenceAttachment](https://learn.microsoft.com/en-us/graph/api/resources/referenceattachment?view=graph-rest-1.0) resource\)

> **Note**: If you're attaching a file to a group post, or attaching an item to an event, message, or group post, limit the size of the attachment to 3 MB.
> 
> If you're attaching a file under 3 MB, you can [add the file attachment to a user event](https://learn.microsoft.com/en-us/graph/api/event-post-attachments?view=graph-rest-1.0), [to a message](https://learn.microsoft.com/en-us/graph/api/message-post-attachments?view=graph-rest-1.0), or [to a group post](https://learn.microsoft.com/en-us/graph/api/post-post-attachments?view=graph-rest-1.0).
> 
> If you're attaching a file between 3 MB and 150 MB to an event or message, you can [create an upload session](https://learn.microsoft.com/en-us/graph/api/attachment-createuploadsession?view=graph-rest-1.0) and iteratively upload ranges of the file to attach it. See [attach large files to Outlook messages](https://learn.microsoft.com/en-us/graph/outlook-large-attachments) for an example.

## Methods

The following methods apply to any of the derived types of attachments \(**fileAttachment**, **itemAttachment**, or **referenceAttachment**\).

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/attachment-get?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) | Read the properties, relationships, or raw contents of an attachment, attached to a user event, message, or post. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/attachment-delete?view=graph-rest-1.0) | None | Delete an attachment on an event, message, or post. |
| [Add attachment to a user event](https://learn.microsoft.com/en-us/graph/api/event-post-attachments?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) | Add a file, item, or link attachment to an event in a user calendar. This operation limits the size of the attachment you can add to under 3 MB. |
| [Add attachment to a message](https://learn.microsoft.com/en-us/graph/api/message-post-attachments?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) | Add a file, item, or link attachment to a message. This operation limits the size of the attachment you can add to under 3 MB. |
| [Create session to attach large file](https://learn.microsoft.com/en-us/graph/api/attachment-createuploadsession?view=graph-rest-1.0) | [uploadSession](https://learn.microsoft.com/en-us/graph/api/resources/uploadsession?view=graph-rest-1.0) | Create an upload session that allows an app to iteratively upload ranges of a file, so as to attach the file to the specified **message** or **event**. The file size must be between 3 MB and 150 MB. |
| [Add attachment to a post](https://learn.microsoft.com/en-us/graph/api/post-post-attachments?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) | Add a file, item, or link attachment to a post. This operation limits the size of the attachment you can add to under 3 MB. |
| [List attachments of a user event](https://learn.microsoft.com/en-us/graph/api/event-list-attachments?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) collection | Get a list of attachments for an event in a user calendar. |
| [List attachments of a message](https://learn.microsoft.com/en-us/graph/api/message-list-attachments?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) collection | Get a list of attachments for a message. |
| [List attachments of a post](https://learn.microsoft.com/en-us/graph/api/post-list-attachments?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) collection | Get a list of attachments for a post. |

## Properties

The following are the base properties of any attachment resource. Refer to the specific type of attachment \([fileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/fileattachment?view=graph-rest-1.0), [itemAttachment](https://learn.microsoft.com/en-us/graph/api/resources/itemattachment?view=graph-rest-1.0), or [referenceAttachment](https://learn.microsoft.com/en-us/graph/api/resources/referenceattachment?view=graph-rest-1.0)\) for additional properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| contentType | String | The MIME type. |
| id | String | Read-only. |
| isInline | Boolean | `true` if the attachment is an inline attachment; otherwise, `false`. |
| lastModifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| name | String | The attachment's file name. |
| size | Int32 | The length of the attachment in bytes. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "contentType": "string",
  "id": "string (identifier)",
  "isInline": true,
  "lastModifiedDateTime": "String (timestamp)",
  "name": "string",
  "size": 1024
}
```
