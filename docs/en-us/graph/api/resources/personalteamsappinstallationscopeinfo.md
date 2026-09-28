<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/personalteamsappinstallationscopeinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# personalTeamsAppInstallationScopeInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the installation scope details when the Teams app is installed, updated, or deleted for a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta).

Inherits from [teamsAppInstallationScopeInfo](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallationscopeinfo?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| scope | teamsAppInstallationScopes | The scope in which the Teams app is updated, installed, or deleted. The possible values are: `team`, `groupChat`, `personal`, `unknownFutureValue`. Inherited from [teamsAppInstallationScopeInfo](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallationscopeinfo?view=graph-rest-beta). |
| userId | String | The ID of the user for whom the Teams app is installed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.personalTeamsAppInstallationScopeInfo",
  "scope": "String",
  "userId": "String"
}
```
