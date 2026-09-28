<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallationscopeinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# teamsAppInstallationScopeInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents the details of the scope where the Teams app is installed.

Base type of [groupChatTeamsAppInstallationScopeInfo](https://learn.microsoft.com/en-us/graph/api/resources/groupchatteamsappinstallationscopeinfo?view=graph-rest-beta), [personalTeamsAppInstallationScopeInfo](https://learn.microsoft.com/en-us/graph/api/resources/personalteamsappinstallationscopeinfo?view=graph-rest-beta), and [teamTeamsAppInstallationScopeInfo](https://learn.microsoft.com/en-us/graph/api/resources/teamteamsappinstallationscopeinfo?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| scope | teamsAppInstallationScopes | The scope in which the Teams app is installed. The possible values are: `team`, `groupChat`, `personal`, `unknownFutureValue`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAppInstallationScopeInfo",
  "scope": "String"
}
```
