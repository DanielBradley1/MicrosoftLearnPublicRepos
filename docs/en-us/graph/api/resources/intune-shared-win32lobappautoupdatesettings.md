<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-win32lobappautoupdatesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# win32LobAppAutoUpdateSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to perform the auto-update of an application.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| autoUpdateSupersededApps | [win32LobAppAutoUpdateSupersededApps](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-win32lobappautoupdatesupersededapps?view=graph-rest-beta) | The auto-update superseded apps setting for the app assignment. Possible values are notConfigured and enabled. Default value is notConfigured. The possible values are: `notConfigured`, `enabled`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppAutoUpdateSettings",
  "autoUpdateSupersededApps": "String"
}
```
