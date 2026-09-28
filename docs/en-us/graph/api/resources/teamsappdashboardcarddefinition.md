<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsappdashboardcarddefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# teamsAppDashBoardCardDefinition resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the dashboard cards details of a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentSource | [teamsAppDashboardCardContentSource](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdashboardcardcontentsource?view=graph-rest-beta) | The configuration for the source of the card content. Required. |
| defaultSize | [teamsAppDashboardCardSize](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdashboardcarddefinition?view=graph-rest-beta#teamsappdashboardcardsize-values) | The size of the card. The possible values are: `medium`, `large`, `unknownFutureValue`. Required. |
| description | String | The description for the card. Required. |
| displayName | String | The name of the card. Required. |
| icon | [teamsAppDashboardCardIcon](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdashboardcardicon?view=graph-rest-beta) | Configuration for the display of the icon in the card picker. If neither this nor any of its properties \(**iconUrl** and **officeUIFabricIconName**\) are specified, the color icon of the app is used. Optional. |
| id | String | The unique ID for the card. Must be unique inside the app. Required. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| pickerGroupId | String | ID for the group in the card picker. Required. |

### teamsAppDashboardCardSize values

| Member | Description |
| :--- | :--- |
| medium | Renders a medium-sized dashboard card. |
| large | Renders a large-sized dashboard card. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAppDashboardCardDefinition",
  "contentSource": {"@odata.type": "microsoft.graph.teamsAppDashboardCardContentSource"},
  "defaultSize": "String",
  "description": "String",
  "displayName": "String",
  "icon": {"@odata.type": "microsoft.graph.teamsAppDashboardCardIcon"},
  "id": "String (identifier)",
  "pickerGroupId": "String"
}
```
