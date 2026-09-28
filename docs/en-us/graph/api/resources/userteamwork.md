<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# userTeamwork resource type

Namespace: microsoft.graph

Represents a container for the range of Microsoft Teams functionalities that are available per user in the tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/userteamwork-get?view=graph-rest-1.0) | [userTeamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-1.0) | Get userTeamwork settings for the specified [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0), which includes the Microsoft Teams region and the locale chosen by the user. |
| [Get all targeted messages](https://learn.microsoft.com/en-us/graph/api/userteamwork-getalltargetedmessages?view=graph-rest-1.0) | [targetedChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) collection | Get all [targeted messages](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) sent to a specific user in group chats and channels. |
| [Get all retained targeted messages](https://learn.microsoft.com/en-us/graph/api/userteamwork-getallretainedtargetedmessages?view=graph-rest-1.0) | [targetedChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) collection | Get all retained [targeted messages](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) sent to a specific user in group chats and channels. |
| [Delete targeted message](https://learn.microsoft.com/en-us/graph/api/userteamwork-deletetargetedmessage?view=graph-rest-1.0) | None | Delete a specific [targeted message](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) from a channel context. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the **userTeamwork** object. |
| locale | String | Represents the location that a user selected in Microsoft Teams and doesn't follow the Office's locale setting. A user's locale is represented by their preferred language and country or region. For example, `en-us`. The language component follows two-letter codes as defined in [ISO 639-1](https://www.iso.org/iso-639-language-code), and the country component follows two-letter codes as defined in [ISO 3166-1 alpha-2](https://www.iso.org/iso-3166-country-codes.html). |
| region | string | Represents the region of the organization or the user. For users with multigeo licenses, the property contains the user's region \(if available\). For users without multigeo licenses, the property contains the organization's region.  <br>  <br>The **region** value can be any region supported by the Teams payload. The possible values are: `Americas`, `Europe and MiddleEast`, `Asia Pacific`, `UAE`, `Australia`, `Brazil`, `Canada`, `Switzerland`, `Germany`, `France`, `India`, `Japan`, `South Korea`, `Norway`, `Singapore`, `United Kingdom`, `South Africa`, `Sweden`, `Qatar`, `Poland`, `Italy`, `Israel`, `Spain`, `Mexico`, `USGov Community Cloud`, `USGov Community Cloud High`, `USGov Department of Defense`, and `China`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| associatedTeams | [associatedTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/associatedteaminfo?view=graph-rest-1.0) collection | The list of [associatedTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/associatedteaminfo?view=graph-rest-1.0) objects that a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) is associated with. |
| installedApps | [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) collection | The apps installed in the personal scope of this user. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "locale" : "String",
  "region" : "String"
}
```

## Related content

- [teamwork resource type](https://learn.microsoft.com/en-us/graph/api/resources/teamwork?view=graph-rest-1.0)
