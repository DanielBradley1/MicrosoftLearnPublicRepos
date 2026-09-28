<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapppublishingconstraints?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# mobileAppPublishingConstraints resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for constraints that the UX need to take into consideration to guide the user experience for app creation and publishing flow.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| win32LobAppConstraints | [win32LobAppPublishingConstraints](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapppublishingconstraints?view=graph-rest-beta) | Contains properties for Win32 LOB app publishing constraints. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppPublishingConstraints",
  "win32LobAppConstraints": {
    "@odata.type": "microsoft.graph.win32LobAppPublishingConstraints",
    "maxContentFileSizeInBytes": 1024
  }
}
```
