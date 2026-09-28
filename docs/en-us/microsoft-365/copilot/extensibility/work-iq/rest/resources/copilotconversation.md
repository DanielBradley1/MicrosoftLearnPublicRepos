<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversation -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Work IQ - copilotConversation resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications isn't supported.

Represents a Copilot conversation being created or continued through the [Work IQ Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotroot-post-conversations).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotroot-post-conversations) | `copilotConversation` | Create a new Copilot conversation. |
| [Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotconversation-chat) | `copilotConversation` | Send a chat message to Copilot and receive a response synchronously. |
| [Chat over stream](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotconversation-chatoverstream) | stream of `copilotConversation` | Send a chat message to Copilot and receive a streaming response. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `agentId` | String | The unique identifier of the agent associated with the conversation. |
| `createdDateTime` | DateTimeOffset | The date and time when the conversation was created. |
| `displayName` | String | The display name of the conversation. |
| `id` | String | The unique identifier of the conversation. This is used as a path parameter when continuing a synchronous or streamed conversation. |
| `state` | [copilotConversationState](#copilotconversationstate-enumeration) | The state of the conversation. |
| `turnCount` | Int32 | The number of turns in the conversation. |

### copilotConversationState enumeration

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following possible values.

| Value |
| :--- |
| `active` |
| `disengagedForRai` |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `messages` | [copilotConversationResponseMessage](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversationresponsemessage) collection | The ordered list of messages in the conversation. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotConversation",
  "id": "String",
  "agentId": "String",
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
