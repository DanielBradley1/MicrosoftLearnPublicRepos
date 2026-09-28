<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamguestsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamGuestSettings resource type

Namespace: microsoft.graph

Settings to configure whether guests can create, update, or delete channels in the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowCreateUpdateChannels | Boolean | If set to true, guests can add and update channels. |
| allowDeleteChannels | Boolean | If set to true, guests can delete channels. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowCreateUpdateChannels": true,
  "allowDeleteChannels": true
}
```
