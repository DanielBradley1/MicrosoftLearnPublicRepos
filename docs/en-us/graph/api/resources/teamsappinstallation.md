<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-08 -->

# teamsAppInstallation resource type

Namespace: microsoft.graph

Represents a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) installed in a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) or the personal scope of a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). Any bots that are part of the app become part of any team or user's personal scope that the app is added to.

Note

The `id` of a **teamsAppInstallation** resource is not the same value as the `id` of the associated **teamsApp** resource.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List apps in team](https://learn.microsoft.com/en-us/graph/api/team-list-installedapps?view=graph-rest-1.0) | [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) collection | List apps installed in a team. |
| [Get app installed in team](https://learn.microsoft.com/en-us/graph/api/team-get-installedapps?view=graph-rest-1.0) | [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) | Get the specified app installed in a team. |
| [Add app to team](https://learn.microsoft.com/en-us/graph/api/team-post-installedapps?view=graph-rest-1.0) | None | Add \(install\) an app to a team. |
| [Upgrade app installed in team](https://learn.microsoft.com/en-us/graph/api/team-teamsappinstallation-upgrade?view=graph-rest-1.0) | None | Upgrade the app installed in a team to the latest version. |
| [Remove app from team](https://learn.microsoft.com/en-us/graph/api/team-delete-installedapps?view=graph-rest-1.0) | None | Remove \(uninstall\) an app from a team. |
| [List apps for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-installedapps?view=graph-rest-1.0) | [userScopeTeamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/userscopeteamsappinstallation?view=graph-rest-1.0) collection | List apps installed in the personal scope of a user. |
| [Get app installed for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-get-installedapps?view=graph-rest-1.0) | [userScopeTeamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/userscopeteamsappinstallation?view=graph-rest-1.0) | Get the specified app installed in the personal scope of a user. |
| [Add app for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-post-installedapps?view=graph-rest-1.0) |  | Add \(install\) an app in the personal scope of a user. |
| [Upgrade installed app for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-teamsappinstallation-upgrade?view=graph-rest-1.0) | None | Upgrade the app installed in the personal scope of a user to the latest version. |
| [Remove app for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-delete-installedapps?view=graph-rest-1.0) | None | Remove \(uninstall\) an app in the personal scope of a user. |
| [List apps in chat](https://learn.microsoft.com/en-us/graph/api/chat-list-installedapps?view=graph-rest-1.0) | [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) collection | List apps installed in a chat. |
| [Get app installed in chat](https://learn.microsoft.com/en-us/graph/api/chat-get-installedapps?view=graph-rest-1.0) | [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) | Get the specified app installed in a chat. |
| [Add app in chat](https://learn.microsoft.com/en-us/graph/api/chat-post-installedapps?view=graph-rest-1.0) |  | Add \(install\) an app to a chat. |
| [Upgrade app installed in chat](https://learn.microsoft.com/en-us/graph/api/chat-teamsappinstallation-upgrade?view=graph-rest-1.0) | None | Upgrade the app installed in a chat to the latest version. |
| [Remove app from chat](https://learn.microsoft.com/en-us/graph/api/chat-delete-installedapps?view=graph-rest-1.0) | None | Remove \(uninstall\) an app from a chat. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| consentedPermissionSet | [teamsAppPermissionSet](https://learn.microsoft.com/en-us/graph/api/resources/teamsapppermissionset?view=graph-rest-1.0) | The set of resource-specific permissions consented to while installing or upgrading the teamsApp. |
| id | string | A unique ID \(not the Teams app ID\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| teamsApp | [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) | The app that is installed. |
| teamsAppDefinition | [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0) | The details of this version of the app. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "consentedPermissionSet": "#microsoft.graph.teamsAppPermissionSet",
  "id": "string"
}
```

## Related content

- [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0)
- [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0)
- [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0)
- [userScopeTeamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/userscopeteamsappinstallation?view=graph-rest-1.0)
- [Teams app installation lifecycle C# sample](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/graph-app-installation-lifecycle/csharp)
- [Teams app installation lifecycle Node.js sample](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/graph-app-installation-lifecycle/nodejs)
