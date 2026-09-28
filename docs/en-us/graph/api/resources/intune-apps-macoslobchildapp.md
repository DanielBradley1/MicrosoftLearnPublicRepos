<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macoslobchildapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# macOSLobChildApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties of a macOS .app in the package

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bundleId | String | The bundleId of the app. |
| buildNumber | String | The build number of the app. |
| versionNumber | String | The version number of the app. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSLobChildApp",
  "bundleId": "String",
  "buildNumber": "String",
  "versionNumber": "String"
}
```
