<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkaccountconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamworkAccountConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the account configuration for a Microsoft Teams Rooms [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| onPremisesCalendarSyncConfiguration | [teamworkOnPremisesCalendarSyncConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkonpremisescalendarsyncconfiguration?view=graph-rest-beta) | The account used to sync the calendar. |
| supportedClient | teamworkSupportedClient | The supported client for Teams Rooms devices. The possible values are: `unknown`, `skypeDefaultAndTeams`, `teamsDefaultAndSkype`, `skypeOnly`, `teamsOnly`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkAccountConfiguration",
  "onPremisesCalendarSyncConfiguration": {
    "@odata.type": "microsoft.graph.teamworkOnPremisesCalendarSyncConfiguration"
  },
  "supportedClient": "String"
}
```
