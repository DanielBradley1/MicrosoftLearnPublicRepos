<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teaminfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamInfo resource type

Namespace: microsoft.graph

Represents a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) with basic information.

Base type of [associatedTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/associatedteaminfo?view=graph-rest-1.0) and [sharedWithChannelTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). |
| id | String | The unique identifier for the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). Read-only. |
| tenantId | String | The ID of the Microsoft Entra tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamInfo",
  "displayName": "String",
  "id": "String (identifier)",
  "tenantId": "String"
}
```
