<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsappdashboardcardbotconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# teamsAppDashboardCardBotConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the bot configuration for a dashboard card in a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| botId | String | The ID \(usually a GUID\) of the bot associated with the specific [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-beta). This is a unique app ID for the bot as registered with the Bot Framework. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAppDashboardCardBotConfiguration",
  "botId": "String"
}
```
