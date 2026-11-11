<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-07 -->

# teamworkChannelTag resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a tag owned by a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-beta) in Microsoft Teams. Use channel tags to group users within a channel and mention them together.

Channel tags are separate from team-owned [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-beta) objects. Use the team that hosts the channel when managing channel tags, including for shared channels. Treat tag IDs as opaque identifiers and use them unchanged with the channel that owns the tag. Team tag IDs and channel tag IDs aren't interchangeable.

Channel tags support standard, private, and shared channels, except the **General** channel. The **General** channel doesn't have a separate channel tag collection with its own tags. Use [List teamworkTags](https://learn.microsoft.com/en-us/graph/api/teamworktag-list?view=graph-rest-beta) and [Create teamworkTag](https://learn.microsoft.com/en-us/graph/api/teamworktag-post?view=graph-rest-beta) to manage tags for the **General** channel.

Inherits from [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/channel-list-tags?view=graph-rest-beta) | [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) collection | Get a list of the [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) objects owned by the specified channel. |
| [Create](https://learn.microsoft.com/en-us/graph/api/channel-post-tags?view=graph-rest-beta) | [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) | Create a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) owned by a channel and assign its initial members. |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-get?view=graph-rest-beta) | [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) | Get the properties of a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) owned by the specified channel. |
| [Update](https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-update?view=graph-rest-beta) | [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) | Update the display name or description of a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) owned by the specified channel. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-delete?view=graph-rest-beta) | None | Delete a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) owned by the specified channel. |
| Channel tag membership |  |  |
| [List members](https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-list-members?view=graph-rest-beta) | [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) collection | Get the [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) objects assigned to a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) owned by the specified channel. |
| [Create member](https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-post-members?view=graph-rest-beta) | [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) | Create a [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) object, which assigns a user to a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) owned by the specified channel. |
| [Get member](https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-get-members?view=graph-rest-beta) | [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) | Get a [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) of a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) owned by the specified channel. |
| [Delete member](https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-delete-members?view=graph-rest-beta) | None | Delete a [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) from a [teamworkChannelTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworkchanneltag?view=graph-rest-beta) owned by the specified channel. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| channelId | String | The identifier of the channel that owns the tag. Read-only. |
| description | String | The description of the tag as it appears in Microsoft Teams. Inherited from [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-beta). |
| displayName | String | The name of the tag as it appears in Microsoft Teams. The maximum length is 40 characters. Supports `$filter` \(`eq`\). Inherited from [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-beta). |
| id | String | The identifier of the tag. Read-only. Inherited from [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-beta). |
| memberCount | Int32 | The number of users assigned to the tag. Read-only. Inherited from [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-beta). |
| tagType | [teamworkTagType](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-beta#teamworktagtype-values) | The type of tag. Supports a subset of the members of the **teamworkTagType** enumeration. Channel tags support only the `standard` member. Inherited from [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-beta). |
| teamId | String | The identifier of the team that hosts the owning channel. Read-only. Inherited from [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| members | [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-beta) collection | The users assigned to the tag. Inherited from [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-beta). Use the [List channel tag members](https://learn.microsoft.com/en-us/graph/api/teamworkchanneltag-list-members?view=graph-rest-beta) operation to get this collection. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkChannelTag",
  "id": "String (identifier)",
  "teamId": "String",
  "displayName": "String",
  "description": "String",
  "memberCount": "Int32",
  "tagType": "String",
  "channelId": "String"
}
```
