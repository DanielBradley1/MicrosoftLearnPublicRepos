<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macoslobappassignmentsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# macOsLobAppAssignmentSettings resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to assign a macOS LOB app to a group.

Inherits from [mobileAppAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignmentsettings?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| uninstallOnDeviceRemoval | Boolean | When TRUE, indicates that the app should be uninstalled when the device is removed from Intune. When FALSE, indicates that the app will not be uninstalled when the device is removed from Intune. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOsLobAppAssignmentSettings",
  "uninstallOnDeviceRemoval": true
}
```
