<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioshomescreenfolder?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosHomeScreenFolder resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A folder containing pages of apps and web clips on the Home Screen.

Inherits from [iosHomeScreenItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioshomescreenitem?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the app Inherited from [iosHomeScreenItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioshomescreenitem?view=graph-rest-1.0) |
| pages | [iosHomeScreenFolderPage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioshomescreenfolderpage?view=graph-rest-1.0) collection | Pages of Home Screen Layout Icons which must be applications or web clips. This collection can contain a maximum of 500 elements. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosHomeScreenFolder",
  "displayName": "String",
  "pages": [
    {
      "@odata.type": "microsoft.graph.iosHomeScreenFolderPage",
      "displayName": "String",
      "apps": [
        {
          "@odata.type": "microsoft.graph.iosHomeScreenApp",
          "displayName": "String",
          "bundleID": "String"
        }
      ]
    }
  ]
}
```
