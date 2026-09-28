<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswebcontentfilterautofilter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosWebContentFilterAutoFilter resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an iOS Web Content Filter setting type, which enables iOS automatic filter feature and allows for additional URL access control. When constructed with no property values, the iOS device will enable the automatic filter regardless.

Inherits from [iosWebContentFilterBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswebcontentfilterbase?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedUrls | String collection | Additional URLs allowed for access |
| blockedUrls | String collection | Additional URLs blocked for access |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosWebContentFilterAutoFilter",
  "allowedUrls": [
    "String"
  ],
  "blockedUrls": [
    "String"
  ]
}
```
