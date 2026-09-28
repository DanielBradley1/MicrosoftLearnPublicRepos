<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmembersnotificationrecipient?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# chatMembersNotificationRecipient resource type

Namespace: microsoft.graph

Represents the recipient of a notification sent in a Microsoft Teams activity feed. The recipient consists of the chat members.

Inherits from [teamworkNotificationRecipient](https://learn.microsoft.com/en-us/graph/api/resources/teamworknotificationrecipient?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| chatId | String | The unique identifier for the chat whose members should receive the notifications. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.chatMembersNotificationRecipient",
  "chatId": "String"
}
```
