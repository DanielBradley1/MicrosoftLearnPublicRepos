<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosincludedapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# macOSIncludedApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties of an included .app in a MacOS app.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bundleId | String | The bundleId of the app. This maps to the CFBundleIdentifier in the app's bundle configuration. |
| bundleVersion | String | The version of the app. This maps to the CFBundleShortVersion in the app's bundle configuration. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSIncludedApp",
  "bundleId": "String",
  "bundleVersion": "String"
}
```
