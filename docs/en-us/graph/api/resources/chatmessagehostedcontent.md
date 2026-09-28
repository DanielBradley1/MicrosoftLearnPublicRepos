<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessagehostedcontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# chatMessageHostedContent resource type

Namespace: microsoft.graph

Represents Teams content hosted in a chat message, such as images or code snippets. [File attachments](https://learn.microsoft.com/en-us/graph/api/resources/chatmessageattachment?view=graph-rest-1.0) aren't hosted content; they're stored in SharePoint or OneDrive.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List hosted content](https://learn.microsoft.com/en-us/graph/api/chatmessage-list-hostedcontents?view=graph-rest-1.0) | [chatMessageHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagehostedcontent?view=graph-rest-1.0) collection | Retrieve the list of **chatMessageHostedContent** for a message. |
| [Get hosted content](https://learn.microsoft.com/en-us/graph/api/chatmessagehostedcontent-get?view=graph-rest-1.0) | [chatMessageHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagehostedcontent?view=graph-rest-1.0) | Read the properties and relationships of a **chatMessageHostedContent** object. |

## Properties

chatMessageHostedContent derives from [teamworkHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/teamworkhostedcontent?view=graph-rest-1.0)

| Property | Type | Description |
| :--- | :--- | :--- |
| contentBytes | Edm.Binary | Write-only. When posting new chat message hosted content, represents the bytes of the payload and are represented as a base64 encoded string. |
| contentType | String | Write-only. When posting new chat message hosted content, represents the type of content, such as image/png. |
| id | String | Read-only. Represents the chat message hosted content identifier. |

### Instance attributes

Instance attributes are properties with special behaviors. These properties are temporary and either define behavior the service should perform or provide short-term property values, like a download URL for an item that expires.

| Property name | Type | Description |
| :--- | :--- | :--- |
| @microsoft.graph.temporaryId | string | Write-only. Represents the temporaryId for the hosted content while posting a message to refer to the hosted content in **chatMessage** resource being sent. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@microsoft.graph.temporaryId": "String (identifier)",
  "contentBytes": "String (binary)",
  "contentType": "String",
  "id": "String (identifier)"
}
```
