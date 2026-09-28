<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/groupchatteamsappinstallationscopeinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# groupChatTeamsAppInstallationScopeInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the installation scope details when the Teams app is installed, updated, or deleted from a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-beta).

Inherits from [teamsAppInstallationScopeInfo](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallationscopeinfo?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| chatId | String | The ID of the chat where the Teams app is installed. |
| scope | teamsAppInstallationScopes | The scope in which the Teams app is installed. The possible values are: `team`, `groupChat`, `personal`, `unknownFutureValue`. Inherited from [teamsAppInstallationScopeInfo](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallationscopeinfo?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.groupChatTeamsAppInstallationScopeInfo",
  "chatId": "String",
  "scope": "String"
}
```
