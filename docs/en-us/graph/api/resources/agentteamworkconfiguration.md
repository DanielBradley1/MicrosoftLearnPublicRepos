<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentteamworkconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# agentTeamworkConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the per-conversation-context message notification settings that an agent uses across Teams conversation types \(group chat, channel, one-on-one chat, and meeting chat\).

This complex type is configured in the **teamworkConfiguration** property of [agentCommunicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| channelConfiguration | [agentConversationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentconversationconfiguration?view=graph-rest-beta) | The message notification settings that the agent uses in channels. |
| groupChatConfiguration | [agentConversationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentconversationconfiguration?view=graph-rest-beta) | The message notification settings that the agent uses in group chats. |
| meetingChatConfiguration | [agentConversationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentconversationconfiguration?view=graph-rest-beta) | The message notification settings that the agent uses in meeting chats. |
| oneOnOneChatConfiguration | [agentConversationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentconversationconfiguration?view=graph-rest-beta) | The message notification settings that the agent uses in one-on-one chats. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentTeamworkConfiguration",
  "groupChatConfiguration": {"@odata.type": "microsoft.graph.agentConversationConfiguration"},
  "channelConfiguration": {"@odata.type": "microsoft.graph.agentConversationConfiguration"},
  "oneOnOneChatConfiguration": {"@odata.type": "microsoft.graph.agentConversationConfiguration"},
  "meetingChatConfiguration": {"@odata.type": "microsoft.graph.agentConversationConfiguration"}
}
```
