<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappautoupdatesettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# win32LobAppAutoUpdateSettings resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to perform the auto-update of an application.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| autoUpdateSupersededAppsState | [win32LobAutoUpdateSupersededAppsState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobautoupdatesupersededappsstate?view=graph-rest-1.0) | The auto-update superseded apps state setting for the app assignment. Possible values are notConfigured and enabled. Default value is notConfigured. The possible values are: `notConfigured`, `enabled`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppAutoUpdateSettings",
  "autoUpdateSupersededAppsState": "String"
}
```
