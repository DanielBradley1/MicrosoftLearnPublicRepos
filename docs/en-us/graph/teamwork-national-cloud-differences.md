<!-- Source: https://learn.microsoft.com/en-us/graph/teamwork-national-cloud-differences -->
<!-- Sitemap-Last-Modified: 2025-05-08 -->

# Microsoft Teams API implementation differences in national clouds

This article describes Microsoft Teams API implementation differences between the Microsoft Graph global endpoint and the national clouds.

For general information about national cloud availability for Microsoft Graph APIs, see [National cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

## Implementation differences in Microsoft Graph for US Government cloud

This section describes implementation differences in the Microsoft Graph for US Government for all the available environments.

| API | Details |
| :--- | :--- |
| **Apps** |  |
| [List apps installed for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-installedapps) | Not supported in application context in the GCC High and DOD environments. |
| [Install app for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-post-installedapps) | Not supported in application context in the GCC High and DOD environments. |
| [Get app installed for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-get-installedapps) | Not supported in the application context in the GCC High and DOD environments. |
| [Get chat between user and app](https://learn.microsoft.com/en-us/graph/api/userscopeteamsappinstallation-get-chat) | Not supported in application context in the GCC High and DOD environments. |
| [Upgrade installed app for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-teamsappinstallation-upgrade) | Not supported in application context in the GCC High and DOD environments. |
| [Uninstall app for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-delete-installedapps) | Not supported in application context in the GCC High and DOD environments. |
| **Channels** |  |
| [Provision Email address](https://learn.microsoft.com/en-us/graph/api/channel-provisionemail) | Not supported. |
| [Channels](https://learn.microsoft.com/en-us/graph/api/resources/channel) | All channel-based APIs aren't supported in the context of shared channels. |
| **Chats** |  |
| [Get chat](https://learn.microsoft.com/en-us/graph/api/chat-get) | Chats with meetings associated with them aren't supported in application context in the GCC High and DOD environments. |
| [List chats](https://learn.microsoft.com/en-us/graph/api/chat-list) | The `OrderBy` OData query parameter is not supported. |
| **Meeting AI insights** |  |
| [List AI insights](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api-reference/onlinemeeting-list-aiinsights) | Not supported. |
| [Get AI insight](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api-reference/callaiinsight-get) | Not supported. |
| **Meeting recordings** |  |
| [Get delta by organizer](https://learn.microsoft.com/en-us/graph/api/callrecording-delta) | Not supported. |
| [List recordings by organizer](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-getallrecordings) | Not supported. |
| **Meeting transcripts** |  |
| [Get delta by organizer](https://learn.microsoft.com/en-us/graph/api/calltranscript-delta) | Not supported. |
| [List transcripts by organizer](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-getalltranscripts) | Not supported. |
| **Messages** |  |
| [Soft delete a message](https://learn.microsoft.com/en-us/graph/api/chatmessage-softdelete) | Not supported in the GCC High and DOD Environments. |
| [List messages in a chat](https://learn.microsoft.com/en-us/graph/api/chat-list-messages) | The `OrderBy` OData query parameter isn't supported in the GCC environment. |

## Implementation differences in Microsoft Graph for Microsoft Graph China operated by 21Vianet

This section describes implementation differences in the Microsoft Graph for the Microsoft Graph China operated by 21Vianet.

| API | Details |
| :--- | :--- |
| **Apps** |  |
| [Apps in Microsoft Teams app catalog](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp) | APIs to create, update, or delete apps in the catalog aren't supported. |
| [App installation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation) | APIs to manage app installation aren't supported in any scope. |
| [Resource-specific permission grant](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant) | APIs to list resource-specific permission grants aren't supported in any scope. |
| **Activity Feed** |  |
| [Activity Feed notifications](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) | APIs to send activity feed notifications aren't supported in any scope. |
| **Tabs** |  |
| [Tabs](https://learn.microsoft.com/en-us/graph/api/resources/teamstab) | APIs to manage tabs in chat and channels aren't supported. |
| **Channel** |  |
| [Channel](https://learn.microsoft.com/en-us/graph/api/resources/channel) | Channel APIs aren't supported in the context of shared channels, which are channels with a **channelMembershipType** value of `shared`. |
| **Chat** |  |
| [List chats](https://learn.microsoft.com/en-us/graph/api/chat-list) | The `OrderBy` OData query parameter isn't supported. |
| **Messaging** |  |
| [Export content](https://learn.microsoft.com/en-us/microsoftteams/export-teams-content) | APIs to export chat and channel messages aren't supported. |
| **Team Membership** |  |
| Membership | Membership APIs to add and delete guests aren't supported. |
| **Change notifications** |  |
| [Change notifications](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview) | Change notifications aren't supported for Microsoft Teams resources. |
| **Meeting AI insights** |  |
| [List AI insights](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api-reference/onlinemeeting-list-aiinsights) | Not supported. |
| [Get AI insight](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api-reference/callaiinsight-get) | Not supported. |
| **Meeting transcripts** |  |
| [List transcripts](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-list-transcripts) | Not supported. |
| [Get transcript](https://learn.microsoft.com/en-us/graph/api/calltranscript-get) | Not supported. |
| [Get delta by organizer](https://learn.microsoft.com/en-us/graph/api/calltranscript-delta) | Not supported. |
| [List transcripts by organizer](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-getalltranscripts) | Not supported. |
| **HostedContent** |  |
| [Hosted Content](https://learn.microsoft.com/en-us/graph/api/chatmessagehostedcontent-get) | APIs to manage hosted content aren't supported in application context. |
