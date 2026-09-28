<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-18 -->

# team resource type

Namespace: microsoft.graph

A team in Microsoft Teams is a collection of [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) objects. A channel represents a topic, and therefore a logical isolation of discussion, within a team.

Every team is associated with a [Microsoft 365 group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). The group has the same ID as the team - for example, `/groups/{id}/team` is the same as `/teams/{id}`. For more information about working with groups and members in teams, see [Use the Microsoft Graph REST API to work with Microsoft Teams](https://learn.microsoft.com/en-us/graph/api/resources/teams-api-overview?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/team-post?view=graph-rest-1.0) | [teamsAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0) | Create a team from scratch. |
| [Create team from group](https://learn.microsoft.com/en-us/graph/api/team-put-teams?view=graph-rest-1.0) | [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) | Create a new team, or add a team to an existing Microsoft 365 group. |
| [Get](https://learn.microsoft.com/en-us/graph/api/team-get?view=graph-rest-1.0) | [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) | Retrieve the properties and relationships of the specified team. |
| [Update](https://learn.microsoft.com/en-us/graph/api/team-update?view=graph-rest-1.0) | [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) | Update the properties of the specified team. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/group-delete?view=graph-rest-1.0) | None | Delete the team and its associated group. |
| [List members](https://learn.microsoft.com/en-us/graph/api/team-list-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get the list of members in the team. |
| [Add member](https://learn.microsoft.com/en-us/graph/api/team-post-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) | Add a new member to the team. |
| [Add members in bulk](https://learn.microsoft.com/en-us/graph/api/conversationmembers-add?view=graph-rest-1.0) | [actionResultPart](https://learn.microsoft.com/en-us/graph/api/resources/actionresultpart?view=graph-rest-1.0) collection | Add multiple members to the team in a single request. |
| [Get member](https://learn.microsoft.com/en-us/graph/api/team-get-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get a member in the team. |
| [Get primary channel](https://learn.microsoft.com/en-us/graph/api/team-get-primarychannel?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) | The general channel for the team. |
| [Update member](https://learn.microsoft.com/en-us/graph/api/team-update-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) | Change a member to an owner or back to a regular member. |
| [Remove member](https://learn.microsoft.com/en-us/graph/api/team-delete-members?view=graph-rest-1.0) | None | Remove an existing member from the team. |
| [Remove members in bulk](https://learn.microsoft.com/en-us/graph/api/conversationmember-remove?view=graph-rest-1.0) | [actionResultPart](https://learn.microsoft.com/en-us/graph/api/resources/actionresultpart?view=graph-rest-1.0) collection | Remove multiple members from a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) in a single request. |
| [Archive team](https://learn.microsoft.com/en-us/graph/api/team-archive?view=graph-rest-1.0) | [teamsAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0) | Put the team in a read-only state. |
| [Unarchive team](https://learn.microsoft.com/en-us/graph/api/team-unarchive?view=graph-rest-1.0) | [teamsAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0) | Restore the team to a read-write state. |
| [Clone team](https://learn.microsoft.com/en-us/graph/api/team-clone?view=graph-rest-1.0) | [teamsAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0) | Copy the team and its associated group. |
| [List your teams](https://learn.microsoft.com/en-us/graph/api/user-list-joinedteams?view=graph-rest-1.0) | [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) collection | List the teams you're a member of. |
| [List your associated teams](https://learn.microsoft.com/en-us/graph/api/associatedteaminfo-list?view=graph-rest-1.0) | [associatedTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/associatedteaminfo?view=graph-rest-1.0) collection | Get the list of [teams](https://learn.microsoft.com/en-us/graph/api/resources/associatedteaminfo?view=graph-rest-1.0) in Microsoft Teams that a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) is associated with. |
| [List all teams in an organization](https://learn.microsoft.com/en-us/graph/api/teams-list?view=graph-rest-1.0) | [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) collection | List all teams in an organization. |
| [Complete migration for team](https://learn.microsoft.com/en-us/graph/api/team-completemigration?view=graph-rest-1.0) | [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) | Removes migration mode from the team and makes the team available to users to post and read messages. |
| [List all channels](https://learn.microsoft.com/en-us/graph/api/team-list-allchannels?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | Get the list of [channels](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) either in this [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) or shared with this [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) \(incoming channels\). |
| [List channels](https://learn.microsoft.com/en-us/graph/api/channel-list?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | Get the list of [channels](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) in a **team**. |
| [List incoming channels](https://learn.microsoft.com/en-us/graph/api/team-list-incomingchannels?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | Get the list of incoming [channels](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) \(channels shared with a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0)\). |
| [Remove incoming channel](https://learn.microsoft.com/en-us/graph/api/team-delete-incomingchannels?view=graph-rest-1.0) | None | Remove an incoming [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) \(a **channel** shared with a **team**\) from a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). |
| [List apps in team](https://learn.microsoft.com/en-us/graph/api/team-list-installedapps?view=graph-rest-1.0) | [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) collection | List apps installed in a team. |
| [Add app to team](https://learn.microsoft.com/en-us/graph/api/team-post-installedapps?view=graph-rest-1.0) | None | Add \(install\) an app to a team. |
| [Get app installed in team](https://learn.microsoft.com/en-us/graph/api/team-get-installedapps?view=graph-rest-1.0) | [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) | Get the specified app installed in a team. |
| [Upgrade app installed in team](https://learn.microsoft.com/en-us/graph/api/team-teamsappinstallation-upgrade?view=graph-rest-1.0) | None | Upgrade the app installed in a team to the latest version. |
| [Remove app from team](https://learn.microsoft.com/en-us/graph/api/team-delete-installedapps?view=graph-rest-1.0) | None | Remove \(uninstall\) an app from a team. |
| [List permission grants](https://learn.microsoft.com/en-us/graph/api/team-list-permissiongrants?view=graph-rest-1.0) | [resourceSpecificPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant?view=graph-rest-1.0) collection | List permissions that were granted to apps to access the team. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | The unique identifier of the team. The group has the same ID as the team. This property is read-only, and is inherited from the base entity type. |
| classification | string | An optional label. Typically describes the data or business sensitivity of the team. Must match one of a preconfigured set in the tenant's directory. |
| classSettings | [teamClassSettings](https://learn.microsoft.com/en-us/graph/api/resources/teamclasssettings?view=graph-rest-1.0) | Configure settings of a class. Available only when the team represents a class. |
| createdDateTime | dateTimeOffset | Timestamp at which the team was created. |
| description | string | An optional description for the team. Maximum length: 1,024 characters. |
| displayName | string | The name of the team. |
| firstChannelName | String | The name of the first channel in the team. This is an optional property, only used during team creation and isn't returned in methods to get and list teams. |
| funSettings | [teamFunSettings](https://learn.microsoft.com/en-us/graph/api/resources/teamfunsettings?view=graph-rest-1.0) | Settings to configure use of Giphy, memes, and stickers in the team. |
| guestSettings | [teamGuestSettings](https://learn.microsoft.com/en-us/graph/api/resources/teamguestsettings?view=graph-rest-1.0) | Settings to configure whether guests can create, update, or delete channels in the team. |
| internalId | string | A unique ID for the team that was used in a few places such as the audit log/[Office 365 Management Activity API](https://learn.microsoft.com/en-us/office/office-365-management-api/office-365-management-activity-api-reference). |
| isArchived | Boolean | Whether this team is in read-only mode. |
| memberSettings | [teamMemberSettings](https://learn.microsoft.com/en-us/graph/api/resources/teammembersettings?view=graph-rest-1.0) | Settings to configure whether members can perform certain actions, for example, create channels and add bots, in the team. |
| messagingSettings | [teamMessagingSettings](https://learn.microsoft.com/en-us/graph/api/resources/teammessagingsettings?view=graph-rest-1.0) | Settings to configure messaging and mentions in the team. |
| specialization | [teamSpecialization](https://learn.microsoft.com/en-us/graph/api/resources/teamspecialization?view=graph-rest-1.0) | Optional. Indicates whether the team is intended for a particular use case. Each team specialization has access to unique behaviors and experiences targeted to its use case. |
| summary | [teamSummary](https://learn.microsoft.com/en-us/graph/api/resources/teamsummary?view=graph-rest-1.0) | Contains summary information about the team, including number of owners, members, and guests. |
| tenantId | string | The ID of the Microsoft Entra tenant. |
| visibility | [teamVisibilityType](https://learn.microsoft.com/en-us/graph/api/resources/teamvisibilitytype?view=graph-rest-1.0) | The visibility of the group and team. Defaults to Public. |
| webUrl | string \(readonly\) | A hyperlink that goes to the team in the Microsoft Teams client. You get this URL when you right-click a team in the Microsoft Teams client and select **Get link to team**. This URL should be treated as an opaque blob, and not parsed. |

### Instance attributes

Instance attributes are properties with special behaviors. These properties are temporary. They either define behavior the service should perform or provide short-term property values, such as a download URL for an item that expires.

| Property name | Type | Description |
| :--- | :--- | :--- |
| @microsoft.graph.teamCreationMode | string | Indicates that the team is in migration state and is currently being used for migration purposes. It accepts one value: `migration`. **Note**: In the future, Microsoft might require you or your customers to pay extra fees based on the amount of data imported. |

For a POST request example, see [Request \(create team in migration state\)](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/import-messages/import-external-messages-to-teams).

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| allChannels | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | List of channels either hosted in or shared with the team \(incoming channels\). |
| channels | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | The collection of channels and messages associated with the team. |
| incomingChannels | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | List of [channels](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) shared with the team. |
| installedApps | [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) collection | The apps installed in this team. |
| members | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Members and owners of the team. |
| operations | [teamsAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0) collection | The async operations that ran or are running on this team. |
| photo | [profilePhoto](https://learn.microsoft.com/en-us/graph/api/resources/profilephoto?view=graph-rest-1.0) | The profile photo for the team. |
| [primaryChannel](https://learn.microsoft.com/en-us/graph/api/team-get-primarychannel?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) | The general channel for the team. |
| schedule | [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) | The schedule of shifts for this team. |
| tags | [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) collection | The tags associated with the team. |
| template | [teamsTemplate](https://learn.microsoft.com/en-us/graph/api/resources/teamstemplate?view=graph-rest-1.0) | The template this team was created from. See [available templates](https://learn.microsoft.com/en-us/MicrosoftTeams/get-started-with-teams-templates). |
| permissionGrants | [resourceSpecificPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant?view=graph-rest-1.0) collection | A collection of permissions granted to apps to access the team. |

## JSON representation

The following JSON representation shows the resource type.

> **Note:** If the team is of type class, a **classSettings** property is applied on the team.

```json
{
  "classSettings": {"@odata.type": "microsoft.graph.teamClassSettings"},
  "classification": "String",
  "createdDateTime": "DateTimeOffset",
  "description": "String",
  "displayName": "String",
  "firstChannelName": "String",
  "funSettings": {"@odata.type": "microsoft.graph.teamFunSettings"},
  "guestSettings": {"@odata.type": "microsoft.graph.teamGuestSettings"},
  "internalId": "String",
  "isArchived": "Boolean",
  "memberSettings": {"@odata.type": "microsoft.graph.teamMemberSettings"},
  "messagingSettings": {"@odata.type": "microsoft.graph.teamMessagingSettings"},
  "specialization": "String",
  "tenantId": "String",
  "visibility": "String",
  "webUrl": "String (URL)"
}
```

## Related content

- [Use the Microsoft Graph API to work with Microsoft Teams](https://learn.microsoft.com/en-us/graph/api/resources/teams-api-overview?view=graph-rest-1.0)
- [Creating a group with a team](https://learn.microsoft.com/en-us/graph/teams-create-group-and-team)
- [List all teams](https://learn.microsoft.com/en-us/graph/teams-list-all-teams)
