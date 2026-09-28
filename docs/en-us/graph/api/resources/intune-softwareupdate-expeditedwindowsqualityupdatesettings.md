<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-expeditedwindowsqualityupdatesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# expeditedWindowsQualityUpdateSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A complex type to store the expedited quality update settings such as release date and days until forced reboot.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| qualityUpdateRelease | String | The release date to identify a quality update. |
| daysUntilForcedReboot | Int32 | The number of days after installation that forced reboot will happen. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.expeditedWindowsQualityUpdateSettings",
  "qualityUpdateRelease": "String",
  "daysUntilForcedReboot": 1024
}
```
