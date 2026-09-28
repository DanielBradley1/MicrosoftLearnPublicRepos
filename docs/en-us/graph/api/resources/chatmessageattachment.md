<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessageattachment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-31 -->

# chatMessageAttachment resource type

Namespace: microsoft.graph

Represents an attachment to a chat message entity.

An entity of type **chatMessageAttachment** is returned as part of the [Get channel messages](https://learn.microsoft.com/en-us/graph/api/channel-list-messages?view=graph-rest-1.0) API, as a part of [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) entity.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | string | The content of the attachment. If the attachment is a [rich card](https://learn.microsoft.com/en-us/microsoftteams/platform/task-modules-and-cards/cards/cards-reference), set the property to the rich card object. This property and contentUrl are mutually exclusive. |
| contentType | string | The media type of the content attachment. The possible values are:  <br><br><br>- `reference`: The attachment is a link to another file. Populate the **contentURL** with the link to the object.<br>- `forwardedMessageReference`: The attachment is a reference to a forwarded message. Populate the **content** with the original message context.<br>- Any **contentType** that is supported by the Bot Framework's [Attachment object](https://learn.microsoft.com/en-us/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?#attachment-object).<br>- `application/vnd.microsoft.card.codesnippet`: A code snippet.<br>- `application/vnd.microsoft.card.announcement`: An announcement header. |
| contentUrl | string | The URL for the content of the attachment. |
| id | string | Read-only. The unique ID of the attachment. |
| name | string | The name of the attachment. |
| teamsAppId | string | The ID of the Teams app that is associated with the attachment. The property is used to attribute a Teams message card to the specified app. |
| thumbnailUrl | string | The URL to a thumbnail image that the channel can use if it supports using an alternative, smaller form of **content** or **contentUrl**. For example, if you set **contentType** to application/word and set **contentUrl** to the location of the Word document, you might include a thumbnail image that represents the document. The channel could display the thumbnail image instead of the document. When the user selects the image, the channel would open the document. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "content": "string",
  "contentType": "string",
  "contentUrl": "string",
  "id": "string (identifier)",
  "name": "string",
  "teamsAppId": "string",
  "thumbnailUrl": "string"
}
```
