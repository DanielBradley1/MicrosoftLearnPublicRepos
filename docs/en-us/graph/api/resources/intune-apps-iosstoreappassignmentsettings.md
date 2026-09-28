<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosstoreappassignmentsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# iosStoreAppAssignmentSettings resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to assign an iOS Store mobile app to a group.

Inherits from [mobileAppAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignmentsettings?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| vpnConfigurationId | String | This is the unique identifier \(Id\) of the VPN Configuration to apply to the app. |
| uninstallOnDeviceRemoval | Boolean | When TRUE, indicates that the app should be uninstalled when the device is removed from Intune. When FALSE, indicates that the app will not be uninstalled when the device is removed from Intune. By default, property is set to null which internally is treated as TRUE. |
| isRemovable | Boolean | When TRUE, indicates that the app can be uninstalled by the user. When FALSE, indicates that the app cannot be uninstalled by the user. By default, this property is set to null which internally is treated as TRUE. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosStoreAppAssignmentSettings",
  "vpnConfigurationId": "String",
  "uninstallOnDeviceRemoval": true,
  "isRemovable": true
}
```
