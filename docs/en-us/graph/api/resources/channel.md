<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-16 -->

# channel resource type

Namespace: microsoft.graph

[Teams](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) are made up of channels, which are the conversations you have with your teammates. Each channel is dedicated to a specific topic, department, or project. Channels are where the work actually gets done - where text, audio, and video conversations open to the whole team happen, where files are shared, and where tabs are added.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List channels](https://learn.microsoft.com/en-us/graph/api/channel-list?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | Get the list of channels in a team. |
| [List incoming channels](https://learn.microsoft.com/en-us/graph/api/team-list-incomingchannels?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | Get the list of incoming [channels](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) \(channels shared with a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0)\). |
| [List all channels](https://learn.microsoft.com/en-us/graph/api/team-list-allchannels?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | Get the list of [channels](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) either in a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) or shared with a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) \(incoming channels\). |
| [Create channel](https://learn.microsoft.com/en-us/graph/api/channel-post?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) | Create a new channel by including the display name and description. |
| [Get channel](https://learn.microsoft.com/en-us/graph/api/channel-get?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) | Read properties and relationships of the channel. |
| [Get primary channel](https://learn.microsoft.com/en-us/graph/api/team-get-primarychannel?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) | The general channel for the team. |
| [Update channel](https://learn.microsoft.com/en-us/graph/api/channel-patch?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) | Update properties of the channel. |
| [Delete channel](https://learn.microsoft.com/en-us/graph/api/channel-delete?view=graph-rest-1.0) | None | Delete a channel. |
| [List channel messages](https://learn.microsoft.com/en-us/graph/api/channel-list-messages?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Get messages in a channel |
| [Get all channel messages](https://learn.microsoft.com/en-us/graph/api/channel-getallmessages?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | Get all messages from all channels that a user is a participant in. |
| [Get all retained channel messages](https://learn.microsoft.com/en-us/graph/api/channel-getallretainedmessages?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) collection | Get all retained [messages](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) across all [channels](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) in a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). |
| [Create channel message post](https://learn.microsoft.com/en-us/graph/api/channel-post-messages?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Send a message to a channel. |
| [Create reply to channel message post](https://learn.microsoft.com/en-us/graph/api/chatmessage-post-replies?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Reply to a message in a channel. |
| [Get files folder](https://learn.microsoft.com/en-us/graph/api/channel-get-filesfolder?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | Retrieves the details of the SharePoint folder where the files for the channel are stored. |
| [List tabs](https://learn.microsoft.com/en-us/graph/api/channel-list-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | Lists tabs pinned to a channel. |
| [List channel members](https://learn.microsoft.com/en-us/graph/api/channel-list-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get a list of [members](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) in a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0), including direct members of standard, private, and shared channels. |
| [List all members](https://learn.microsoft.com/en-us/graph/api/channel-list-allmembers?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get a list of all [members](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) in a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0). |
| [Add channel member](https://learn.microsoft.com/en-us/graph/api/channel-post-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) | Add a member to a channel. Only supported for channels with a **membershipType** of `private` or `shared`. |
| [Get channel member](https://learn.microsoft.com/en-us/graph/api/channel-get-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get a member in a channel. |
| [Archive channel](https://learn.microsoft.com/en-us/graph/api/channel-archive?view=graph-rest-1.0) | None | Archive a channel in a team. |
| [Unarchive channel](https://learn.microsoft.com/en-us/graph/api/channel-unarchive?view=graph-rest-1.0) | None | Restore an archived channel in a team. |
| [Update channel member's role](https://learn.microsoft.com/en-us/graph/api/channel-update-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) | Update the properties of a member of the channel. Only supported for channels with a **membershipType** of `private` or `shared`. |
| [Remove channel member](https://learn.microsoft.com/en-us/graph/api/channel-delete-members?view=graph-rest-1.0) | None | Delete a member from a channel. Only supported for channels with a **membershipType** of `private` or `shared`. |
| [Start migration](https://learn.microsoft.com/en-us/graph/api/channel-startmigration?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) | Start the migration of external messages by enabling migration mode in an existing [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0). |
| [Complete migration](https://learn.microsoft.com/en-us/graph/api/channel-completemigration?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) | Complete migration on existing [channels](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) or new channels. |
| [List tabs in channel](https://learn.microsoft.com/en-us/graph/api/channel-list-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | List tabs pinned to a channel. |
| [Add tab to channel](https://learn.microsoft.com/en-us/graph/api/channel-post-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | Add \(pin\) a tab to a channel. |
| [Get tab in channel](https://learn.microsoft.com/en-us/graph/api/channel-get-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | Get a specific tab pinned to a channel. |
| [Update tab in channel](https://learn.microsoft.com/en-us/graph/api/channel-patch-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | Updates the properties of a tab in a channel. |
| [Remove tab from channel](https://learn.microsoft.com/en-us/graph/api/channel-delete-tabs?view=graph-rest-1.0) | None | Remove \(unpin\) a tab from a channel. |
| [List apps in channel](https://learn.microsoft.com/en-us/graph/api/channel-list-enabledapps?view=graph-rest-1.0) | [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) collection | Get a list of the [enabled apps](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) in the specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) within a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). |
| [Get app in channel](https://learn.microsoft.com/en-us/graph/api/teamsapp-get?view=graph-rest-1.0) | [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) | Get an [enabled app](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) in the specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) within a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). |
| [Add app to channel](https://learn.microsoft.com/en-us/graph/api/channel-post-enabledapps?view=graph-rest-1.0) | None | Add a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) that enables an [app](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) in the specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) within a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). |
| [Remove app from channel](https://learn.microsoft.com/en-us/graph/api/channel-delete-enabledapps?view=graph-rest-1.0) | None | Remove a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) that disables an [app](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) in the specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) within a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). |
| [Provision channel email address](https://learn.microsoft.com/en-us/graph/api/channel-provisionemail?view=graph-rest-1.0) | [provisionChannelEmailResult](https://learn.microsoft.com/en-us/graph/api/resources/provisionchannelemailresult?view=graph-rest-1.0) | Provision an email address for the channel. |
| [Remove channel email address](https://learn.microsoft.com/en-us/graph/api/channel-removeemail?view=graph-rest-1.0) | None | Remove the email address of the channel. |
| [Remove incoming channel](https://learn.microsoft.com/en-us/graph/api/team-delete-incomingchannels?view=graph-rest-1.0) | None | Remove an incoming [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) \(a **channel** shared with a **team**\) from a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). |
| [List teams sharing a channel](https://learn.microsoft.com/en-us/graph/api/sharedwithchannelteaminfo-list?view=graph-rest-1.0) | [sharedWithChannelTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0) collection | Get the list of [teams](https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0) that has been shared a specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0). |
| [Get team sharing a channel](https://learn.microsoft.com/en-us/graph/api/sharedwithchannelteaminfo-get?view=graph-rest-1.0) | [sharedWithChannelTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0) | Get a [team](https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0) which has been shared a specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0). |
| [Unshare channel with team](https://learn.microsoft.com/en-us/graph/api/sharedwithchannelteaminfo-delete?view=graph-rest-1.0) | None | Unshare a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) with a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) by deleting the corresponding [sharedWithChannelTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0) resource. |
| [List allowed members](https://learn.microsoft.com/en-us/graph/api/sharedwithchannelteaminfo-list-allowedmembers?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get the list of [conversationMembers](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) who can access a shared [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0). |
| [Check user access](https://learn.microsoft.com/en-us/graph/api/channel-doesuserhaveaccess?view=graph-rest-1.0) | Boolean | Determine whether a [user](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-1.0) has access to a shared [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | dateTimeOffset | Read-only. Timestamp at which the channel was created. |
| description | String | Optional textual description for the channel. |
| displayName | String | Channel name as it will appear to the user in Microsoft Teams. The maximum length is 50 characters. |
| email | String | The email address for sending messages to the channel. Read-only. |
| id | String | The channel's unique identifier. Read-only. |
| isArchived | Boolean | Indicates whether the channel is archived. Read-only. |
| isFavoriteByDefault | Boolean | Indicates whether the channel should be marked as recommended for all members of the team to show in their channel list. **Note:** All recommended channels automatically show in the channels list for education and frontline worker users. The property can only be set programmatically via the [Create team](https://learn.microsoft.com/en-us/graph/api/team-post?view=graph-rest-1.0) method. The default value is `false`. |
| layoutType | [channelLayoutType](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0#channellayouttype-values) | The layout type of the channel. It can be set during creation and updated later. The possible values are: `post`, `chat`, `unknownFutureValue`. The default value is `post`. Channels with the `post` layout use a traditional post‑reply conversation format, and channels with the chat layout provide a chat‑like threading experience similar to group chats. |
| membershipType | [channelMembershipType](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0#channelmembershiptype-values) | The type of the channel. Can be set during creation and can't be changed. The possible values are: `standard`, `private`, `unknownFutureValue`, `shared`. The default value is `standard`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `shared`. |
| migrationMode | [migrationMode](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0#migrationmode-values) | Indicates whether a channel is in migration mode. This value is `null` for channels that never entered migration mode. The possible values are: `inProgress`, `completed`, `unknownFutureValue`. |
| originalCreatedDateTime | dateTimeOffset | Timestamp of the original creation time for the channel. The value is `null` if the channel never entered migration mode. |
| tenantId | string | The ID of the Microsoft Entra tenant. |
| webUrl | String | A hyperlink that will go to the channel in Microsoft Teams. This is the URL that you get when you right-click a channel in Microsoft Teams and select Get link to channel. This URL should be treated as an opaque blob, and not parsed. Read-only. |
| summary | [channelSummary](https://learn.microsoft.com/en-us/graph/api/resources/channelsummary?view=graph-rest-1.0) | Contains summary information about the channel, including number of owners, members, guests, and an indicator for members from other tenants. The **summary** property will only be returned if it is specified in the `$select` clause of the [Get channel](https://learn.microsoft.com/en-us/graph/api/channel-get?view=graph-rest-1.0) method. |

### channelMembershipType values

| Member | Description |
| :--- | :--- |
| standard | Channel inherits the list of members of the parent team. |
| private | Channel can have members that are a subset of all the members on the parent team. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |
| shared | Members can be directly added to the channel without adding them to the team. |

### migrationMode values

| Member | Description |
| :--- | :--- |
| inProgress | The channel or chat entered migration mode. |
| completed | The channel or chat is out of migration mode. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### channelLayoutType values

| Member | Description |
| :--- | :--- |
| post | Traditional post-reply conversation format. Posts are displayed in a structured format with replies nested under the original post. Represents the default layout type. |
| chat | Chat-like threading experience similar to group chats. Messages are displayed in a continuous flow with support for threaded conversations on specific topics. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### Instance attributes

Instance attributes are properties with special behaviors. These properties are temporary and either a\) define behavior the service should perform or b\) provide short-term property values, like a download URL for an item that expires.

| Property name | Type | Description |
| :--- | :--- | :--- |
| @microsoft.graph.channelCreationMode | string | Indicates that the channel is in migration state and is currently being used for migration purposes. It accepts one value: `migration`. |

> **Note**: `channelCreationMode` is an enum that takes the value `migration`.

For a POST request example, see [Request \(create channel in migration state\)](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/import-messages/import-external-messages-to-teams#request-create-a-team-in-migration-state).

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| allMembers | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | A collection of membership records associated with the channel, including both direct and indirect members of shared channels. |
| enabledApps | [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) collection | A collection of enabled apps in the channel. |
| [filesFolder](https://learn.microsoft.com/en-us/graph/api/channel-get-filesfolder?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | Metadata for the location where the channel's files are stored. |
| members | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | A collection of membership records associated with the channel. |
| messages | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) collection | A collection of all the messages in the channel. A navigation property. Nullable. |
| operations | [teamsAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0) collection | The async operations that ran or are running on this team. |
| sharedWithTeams | [sharedWithChannelTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0) collection | A collection of teams with which a channel is shared. |
| tabs | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) collection | A collection of all the tabs in the channel. A navigation property. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "email": "String",
  "id": "String (identifier)",
  "isArchived": "Boolean",
  "isFavoriteByDefault": "Boolean",
  "layoutType": "String",
  "membershipType": "String",
  "migrationMode": "String",
  "originalCreatedDateTime": "String (timestamp)",
  "webUrl": "String"
}
```

## Related content

- [Channel lifecycle C# sample](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/graph-channel-lifecycle/csharp)
- [Channel lifecycle Node.js sample](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/graph-channel-lifecycle/nodejs)
