<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teammembersettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamMemberSettings resource type

Namespace: microsoft.graph

Settings to configure whether members can perform certain actions, for example, create channels and add bots, in the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowAddRemoveApps | Boolean | If set to true, members can add and remove apps. |
| allowCreatePrivateChannels | Boolean | If set to true, members can add and update private channels. |
| allowCreateUpdateChannels | Boolean | If set to true, members can add and update channels. |
| allowCreateUpdateRemoveConnectors | Boolean | If set to true, members can add, update, and remove connectors. |
| allowCreateUpdateRemoveTabs | Boolean | If set to true, members can add, update, and remove tabs. |
| allowDeleteChannels | Boolean | If set to true, members can delete channels. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowCreatePrivateChannels": true,
  "allowCreateUpdateChannels": true,
  "allowDeleteChannels": true,
  "allowAddRemoveApps": true,
  "allowCreateUpdateRemoveTabs": true,
  "allowCreateUpdateRemoveConnectors": true
}
```
