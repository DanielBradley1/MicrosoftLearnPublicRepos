<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosdevicetype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosDeviceType resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties of the possible iOS device types the mobile app can run on.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| iPad | Boolean | Whether the app should run on iPads. |
| iPhoneAndIPod | Boolean | Whether the app should run on iPhones and iPods. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosDeviceType",
  "iPad": true,
  "iPhoneAndIPod": true
}
```
