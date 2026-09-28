<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/resources/copilotconversation -->
<!-- Sitemap-Last-Modified: 2025-10-17 -->

# copilotConversation resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a Copilot conversation being created or continued through the [Microsoft 365 Copilot Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/copilotroot-post-conversations).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/copilotroot-post-conversations) | `copilotConversation` | Create a new Copilot conversation. |
| [Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/copilotconversation-chat) | `copilotConversation` | Send a chat message to Copilot and receive a response synchronously. |
| [Chat over stream](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/copilotconversation-chatoverstream) | stream of `copilotConversation` | Send a chat message to Copilot and receive a streaming response. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `createdDateTime` | DateTimeOffset | The timestamp when the Copilot conversation was created. |
| `displayName` | String | The display name for the Copilot conversation. |
| `id` | String | The identifier for a Copilot conversation. This is used as a path parameter when continuing a synchronous or streamed conversation. |
| `messages` | [copilotConversationResponseMessage](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/resources/copilotconversationresponsemessage) collection | The latest turn count in the conversation when the last message was added. |
| `state` | [copilotConversationState](#copilotconversationstate-enumeration) | The Copilot conversation state. |
| `turnCount` | Int32 | The latest turn count in the conversation when the last message was added. |

### copilotConversationState enumeration

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following possible values.

| Value |
| :--- |
| `active` |
| `disengagedForRai` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotConversation",
  "id": "String",
  "createdDateTime": "DateTimeOffset",
  "displayName": "String",
  "state": "String",
  "turnCount": "Int32",
  "messages": [
    {
      "@odata.type": "#microsoft.graph.copilotConversationResponseMessage"
    }
  ]
}
```
