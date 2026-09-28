<!-- Source: https://learn.microsoft.com/en-us/graph/api/chatmessage-unsetreaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# chatMessage: unsetReaction

Namespace: microsoft.graph

Unset a reaction to a single [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) or a [chat message reply](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) in a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) or a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

### Permissions for channel

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | ChannelMessage.Send |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | Not supported. |

### Permissions for chat

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | Chat.ReadWrite, ChatMessage.Send |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | Not supported. |

## HTTP request

To unset a reaction to a **chatMessage** in a **channel**:

```http
POST /teams/{teamsId}/channels/{channelId}/messages/{chatMessageId}/unsetReaction
POST /teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}/unsetReaction
```

To unset a reaction to a **chatMessage** in a **chat**:

```http
POST /chats/{chatId}/messages/{chatMessageId}/unsetReaction
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply the **reactionType** as unicode.

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Example 1: Unset a reaction to a chat message

#### Request

```http
POST https://graph.microsoft.com/v1.0/chats/chatId/messages/messageId/unsetReaction
{
  "reactionType": "💘"
}
```

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: Unset a reaction to a message in a channel

#### Request

```http
POST https://graph.microsoft.com/v1.0/teams/teamsid/channels/channelId/messages/messageId/unsetReaction
{
  "reactionType": "💘"
}
```

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 3: Unset a reaction to a message reply

#### Request

```http
POST https://graph.microsoft.com/v1.0/teams/teamsid/channels/channelId/messages/messageId/replies/replyId/unsetReaction
{
  "reactionType": "💘"
}
```

#### Response

```http
HTTP/1.1 204 No Content
```
