<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioshomescreenpage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosHomeScreenPage resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A page containing apps, folders, and web clips on the Home Screen.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the page |
| icons | [iosHomeScreenItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioshomescreenitem?view=graph-rest-1.0) collection | A list of apps, folders, and web clips to appear on a page. This collection can contain a maximum of 500 elements. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosHomeScreenPage",
  "displayName": "String",
  "icons": [
    {
      "@odata.type": "microsoft.graph.iosHomeScreenFolder",
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
  ]
}
```
