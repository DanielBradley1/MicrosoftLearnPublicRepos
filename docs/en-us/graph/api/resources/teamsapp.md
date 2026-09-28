<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-03 -->

# teamsApp resource type

Namespace: microsoft.graph

Represents an app in the [Microsoft Teams](https://learn.microsoft.com/en-us/graph/api/resources/teams-api-overview?view=graph-rest-1.0) app catalog.

Users can see these apps in the Microsoft Teams Store, and these apps can be installed in [teams](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) using the [Add app to team](https://learn.microsoft.com/en-us/graph/api/team-post-installedapps?view=graph-rest-1.0) method.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List apps in catalog](https://learn.microsoft.com/en-us/graph/api/appcatalogs-list-teamsapps?view=graph-rest-1.0) | [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) collection | List all the apps in the Microsoft Teams apps catalog. |
| [Publish apps to catalog](https://learn.microsoft.com/en-us/graph/api/teamsapp-publish?view=graph-rest-1.0) | [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) | Upload an app to your organization's app catalog. |
| [Update app in catalog](https://learn.microsoft.com/en-us/graph/api/teamsapp-update?view=graph-rest-1.0) | [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) | Update an app in your organization's app catalog. |
| [Delete app from catalog](https://learn.microsoft.com/en-us/graph/api/teamsapp-delete?view=graph-rest-1.0) | None | Remove an app from your organization's app catalog. |
| [Get associated bot](https://learn.microsoft.com/en-us/graph/api/teamworkbot-get?view=graph-rest-1.0) | [teamworkBot](https://learn.microsoft.com/en-us/graph/api/resources/teamworkbot?view=graph-rest-1.0) | Get the bot associated with the Teams app. |
| [List apps in channel](https://learn.microsoft.com/en-us/graph/api/channel-list-enabledapps?view=graph-rest-1.0) | [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) collection | Get a list of the [enabled apps](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) in the specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) within a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). |
| [Get app in channel](https://learn.microsoft.com/en-us/graph/api/teamsapp-get?view=graph-rest-1.0) | [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) | Get an [enabled app](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) in the specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) within a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). |
| [Add app to channel](https://learn.microsoft.com/en-us/graph/api/channel-post-enabledapps?view=graph-rest-1.0) | None | Add a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) that enables an [app](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) in the specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) within a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). |
| [Remove app from channel](https://learn.microsoft.com/en-us/graph/api/channel-delete-enabledapps?view=graph-rest-1.0) | None | Remove a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) that disables an [app](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) in the specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) within a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | string | The name of the catalog app provided by the app developer in the [Microsoft Teams zip app package](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/apps/apps-package). |
| distributionMethod | teamsAppDistributionMethod | The method of distribution for the app. Read-only. |
| externalId | string | The ID of the catalog provided by the app developer in the [Microsoft Teams zip app package](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/apps/apps-package). |
| id | string | The app ID generated for the catalog is different from the developer-provided ID found within the [Microsoft Teams zip app package](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/apps/apps-package). The **externalId** value is empty for apps with a **distributionMethod** type of `store`. When apps are published to the global store, the **id** of the app matches the **id** in the app manifest. |

### teamsAppDistributionMethod values

| Member | Description |
| :--- | :--- |
| store | The app is available to all tenants through the Microsoft Teams app store. |
| organization | The app is available only in this tenant. |
| sideloaded | The app is available only to the user or team it's installed to. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appDefinitions | [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0) collection | The details for each version of the app. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "externalId": "string",
  "displayName": "string",
  "distributionMethod": "string",
  "id": "string"
}
```

## Related content

- [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0)
- [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0)
- [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0)
- [App catalog sample \(C#\)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-appcatalog-lifecycle/csharp)
- [App catalog sample \(Node.JS\)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-appcatalog-lifecycle/nodejs)
- [Teams app catalog lifecycle C# sample](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/graph-appcatalog-lifecycle/csharp)
- [Teams app catalog lifecycle Node.js sample](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/graph-appcatalog-lifecycle/nodejs)
