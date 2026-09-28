<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsappdashboardcardcontentsource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# teamsAppDashboardCardContentSource resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a configuration for the source of the dashboard card content in a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| botConfiguration | [teamsAppDashboardCardBotConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdashboardcardbotconfiguration?view=graph-rest-beta) | The configuration for the bot source. Required if **sourceType** is set to `bot`. |
| sourceType | [teamsAppDashboardCardSourceType](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdashboardcardcontentsource?view=graph-rest-beta#teamsappdashboardcardsourcetype-values) | Represents the type of source that powers the content of the dashboard card. The possible values are: `bot`, `unknownFutureValue`. |

### teamsAppDashboardCardSourceType values

| Member | Description |
| :--- | :--- |
| bot | Dashboard card source type as a bot. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAppDashboardCardContentSource",
  "botConfiguration": {"@odata.type": "microsoft.graph.teamsAppDashboardCardBotConfiguration"},
  "sourceType": "String"
}
```
