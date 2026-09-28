<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswebcontentfilterspecificwebsitesaccess?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosWebContentFilterSpecificWebsitesAccess resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an iOS Web Content Filter setting type, which installs URL bookmarks into iOS built-in browser. An example scenario is in the classroom where teachers would like the students to navigate websites through browser bookmarks configured on their iOS devices, and no access to other sites.

Inherits from [iosWebContentFilterBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswebcontentfilterbase?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| specificWebsitesOnly | [iosBookmark](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosbookmark?view=graph-rest-beta) collection | URL bookmarks which will be installed into built-in browser and user is only allowed to access websites through bookmarks. This collection can contain a maximum of 500 elements. |
| websiteList | [iosBookmark](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosbookmark?view=graph-rest-beta) collection | URL bookmarks which will be installed into built-in browser and user is only allowed to access websites through bookmarks. This collection can contain a maximum of 500 elements. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosWebContentFilterSpecificWebsitesAccess",
  "specificWebsitesOnly": [
    {
      "@odata.type": "microsoft.graph.iosBookmark",
      "url": "String",
      "bookmarkFolder": "String",
      "displayName": "String"
    }
  ],
  "websiteList": [
    {
      "@odata.type": "microsoft.graph.iosBookmark",
      "url": "String",
      "bookmarkFolder": "String",
      "displayName": "String"
    }
  ]
}
```
