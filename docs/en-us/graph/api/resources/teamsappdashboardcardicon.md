<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsappdashboardcardicon?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# teamsAppDashboardCardIcon resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a configuration for the icon of a dashboard card in a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| iconUrl | String | The icon for the card, displayed in the toolbox and card bar, is represented as a URL. The preferred size for raster images is 28x28 pixels. If this property has a value, the **officeFabricIconFontName** property is ignored. |
| officeUIFabricIconName | String | The friendly name of the Office UI Fabric/Fluent UI icon for the card that is used when the **iconUrl** property isn't specified. For example, `"officeUIFabricIconName": "Search"`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAppDashboardCardIcon",
  "iconUrl": "String",
  "officeUIFabricIconName": "String"
}
```
