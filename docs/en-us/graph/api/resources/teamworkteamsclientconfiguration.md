<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkteamsclientconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkTeamsClientConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents configuration details for the Microsoft Teams client running on a Microsoft Teams Rooms [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountConfiguration | [teamworkAccountConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkaccountconfiguration?view=graph-rest-beta) | The configuration of the Microsoft Teams client user account for a device. |
| featuresConfiguration | [teamworkFeaturesConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkfeaturesconfiguration?view=graph-rest-beta) | The configuration of Microsoft Teams client features for a device. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkTeamsClientConfiguration",
  "accountConfiguration": {
    "@odata.type": "microsoft.graph.teamworkAccountConfiguration"
  },
  "featuresConfiguration": {
    "@odata.type": "microsoft.graph.teamworkFeaturesConfiguration"
  }
}
```
