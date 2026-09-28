<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkloginstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkLoginStatus resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents Microsoft Teams, Skype for Business, and Exchange sign-in status for a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| exchangeConnection | [teamworkConnection](https://learn.microsoft.com/en-us/graph/api/resources/teamworkconnection?view=graph-rest-beta) | Information about the Exchange connection. |
| skypeConnection | [teamworkConnection](https://learn.microsoft.com/en-us/graph/api/resources/teamworkconnection?view=graph-rest-beta) | Information about the Skype for Business connection. |
| teamsConnection | [teamworkConnection](https://learn.microsoft.com/en-us/graph/api/resources/teamworkconnection?view=graph-rest-beta) | Information about the Teams connection. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkLoginStatus",
  "exchangeConnection": {
    "@odata.type": "microsoft.graph.teamworkConnection"
  },
  "teamsConnection": {
    "@odata.type": "microsoft.graph.teamworkConnection"
  },
  "skypeConnection": {
    "@odata.type": "microsoft.graph.teamworkConnection"
  }
}
```
