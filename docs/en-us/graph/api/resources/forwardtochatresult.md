<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/forwardtochatresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-03-17 -->

# forwardToChatResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the individual response for each target chat ID specified in a [forward to chat](https://learn.microsoft.com/en-us/graph/api/chatmessage-forwardtochat?view=graph-rest-beta) request.

Inherits from [actionResultPart](https://learn.microsoft.com/en-us/graph/api/resources/actionresultpart?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | The error that occurred, if any, during the bulk operation. Inherited from [actionResultPart](https://learn.microsoft.com/en-us/graph/api/resources/actionresultpart?view=graph-rest-beta). |
| forwardedMessageId | String | The [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-beta) ID generated after a message is successfully forwarded to the target chat ID. |
| targetChatId | String | The target chat ID where the message was forwarded. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "forwardedMessageId": "String",
  "targetChatId": "String"
}
```

## Related content

[Forward message to a chat](https://learn.microsoft.com/en-us/graph/api/chatmessage-forwardtochat?view=graph-rest-beta)
