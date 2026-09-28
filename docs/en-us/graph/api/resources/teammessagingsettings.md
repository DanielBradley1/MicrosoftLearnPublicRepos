<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teammessagingsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamMessagingSettings resource type

Namespace: microsoft.graph

Settings to configure messaging and mentions in the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowChannelMentions | Boolean | If set to true, @channel mentions are allowed. |
| allowOwnerDeleteMessages | Boolean | If set to true, owners can delete any message. |
| allowUserDeleteMessages | Boolean | If set to true, users can delete their messages. |
| allowUserEditMessages | Boolean | If set to true, users can edit their messages. |
| allowTeamMentions | Boolean | If set to true, @team mentions are allowed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowUserEditMessages": true,
  "allowUserDeleteMessages": true,
  "allowOwnerDeleteMessages": true,
  "allowTeamMentions": true,
  "allowChannelMentions": true    
}
```
