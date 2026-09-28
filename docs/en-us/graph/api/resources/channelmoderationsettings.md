<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/channelmoderationsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# channelModerationSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

In Microsoft Teams, team owners can turn on moderation for a channel to control who can start new posts and reply to posts in that channel. For example, owners might want to do the following:

- Use a channel for announcements only.
- Use a channel for discussions in a class team where only the teacher can start new discussions.
- Use a channel for livesite issues where new posts can be started by connectors.

By default, moderation is `OFF`, which means that the usual channel settings apply to team owners and team members, with additional control to allow only team members or everyone including guests to start a new channel post. Setting channel moderation to `ON` allows only moderators to start new posts, with additional control for team members.

To support channel moderation settings via Microsoft Graph APIs:

- Team members should be able to query channel moderation settings.
- Team owners should be able to set channel moderation settings.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowNewMessageFromBots | Boolean | Indicates whether bots are allowed to post messages. |
| allowNewMessageFromConnectors | Boolean | Indicates whether connectors are allowed to post messages. |
| replyRestriction | replyRestriction | Indicates who is allowed to reply to the teams channel. The possible values are: `everyone`, `authorAndModerators`, `unknownFutureValue`. |
| userNewMessageRestriction | userNewMessageRestriction | Indicates who is allowed to post messages to teams channel. The possible values are: `everyone`, `everyoneExceptGuests`, `moderators`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.channelModerationSettings",
  "userNewMessageRestriction": "String",
  "replyRestriction": "String",
  "allowNewMessageFromBots": "Boolean",
  "allowNewMessageFromConnectors": "Boolean"
}
```

## Related content

- To modify moderation settings of a channel, see example 2 in [Update channel](https://learn.microsoft.com/en-us/graph/api/channel-patch?view=graph-rest-beta).
