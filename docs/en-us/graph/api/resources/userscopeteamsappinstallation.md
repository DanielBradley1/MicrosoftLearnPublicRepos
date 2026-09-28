<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userscopeteamsappinstallation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# userScopeTeamsAppInstallation resource type

Namespace: microsoft.graph

Represents a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) installed in the personal scope of a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). Any bots that are part of the app will become part of a user's personal scope that the app is added to. This type inherits from [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0).

Note

The `id` of a **teamsAppInstallation** resource is not the same value as the `id` of the associated **teamsApp** resource.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List apps for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-installedapps?view=graph-rest-1.0) | [userScopeTeamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/userscopeteamsappinstallation?view=graph-rest-1.0) collection | List apps installed in the personal scope of a user. |
| [Get app installed for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-get-installedapps?view=graph-rest-1.0) | [userScopeTeamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/userscopeteamsappinstallation?view=graph-rest-1.0) | List the specified app installed in the personal scope of a user. |
| [Add app for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-post-installedapps?view=graph-rest-1.0) | None | Add \(install\) an app in the personal scope of a user. |
| [Remove app for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-delete-installedapps?view=graph-rest-1.0) | None | Remove \(uninstall\) an app in the personal scope of a user. |
| [Upgrade installed app for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-teamsappinstallation-upgrade?view=graph-rest-1.0) | None | Upgrade to the latest version of the app installed in the personal scope of a user. |
| [Get chat between user and app](https://learn.microsoft.com/en-us/graph/api/userscopeteamsappinstallation-get-chat?view=graph-rest-1.0) | [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) | List one-on-one chats between a user and the app. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | A unique ID \(not the Teams app ID\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| chat | [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) | The chat between the user and Teams app. |
| teamsApp | [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) | The app that is installed. |
| teamsAppDefinition | [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0) | The details of this version of the app. |

## JSON representation

```json
{
  "id": "string"
}
```

## Related content

- [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0)
- [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0)
- [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0)
