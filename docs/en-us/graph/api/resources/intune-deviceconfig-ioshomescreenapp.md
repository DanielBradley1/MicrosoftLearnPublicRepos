<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioshomescreenapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosHomeScreenApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an icon for an app on the Home Screen

Inherits from [iosHomeScreenItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioshomescreenitem?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the app Inherited from [iosHomeScreenItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioshomescreenitem?view=graph-rest-1.0) |
| bundleID | String | BundleID of the app if isWebClip is false or the URL of a web clip if isWebClip is true. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosHomeScreenApp",
  "displayName": "String",
  "bundleID": "String"
}
```
