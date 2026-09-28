<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/channelmembersnotificationrecipient?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# channelMembersNotificationRecipient resource type

Namespace: microsoft.graph

Represents the recipient of a notification sent in a Microsoft Teams activity feed. The recipient consists of the channel members.

Inherits from [teamworkNotificationRecipient](https://learn.microsoft.com/en-us/graph/api/resources/teamworknotificationrecipient?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| channelId | String | The unique identifier for the channel whose members should receive the notification. |
| teamId | String | The unique identifier for the team under which the channel resides. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.channelMembersNotificationRecipient",
  "channelId": "String",
  "teamId": "String"
}
```
