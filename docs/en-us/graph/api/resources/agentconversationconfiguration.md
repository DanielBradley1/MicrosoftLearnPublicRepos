<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentconversationconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# agentConversationConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the message notification settings for an agent within a specific Teams conversation context.

This complex type is used by the **channelConfiguration**, **groupChatConfiguration**, **meetingChatConfiguration**, and **oneOnOneChatConfiguration** properties of [agentTeamworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentteamworkconfiguration?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| messageNotificationMode | [agentMessageNotificationMode](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#agentmessagenotificationmode-values) | Controls which messages in the conversation context the agent is notified about. The possible values are: `atMentionedMessagesOnly`, `allMessages`, `unknownFutureValue`. Not nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentConversationConfiguration",
  "messageNotificationMode": "String"
}
```
