<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapppublishingconstraints?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# win32LobAppPublishingConstraints resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for Win32 LOB app publishing constraints.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| maxContentFileSizeInBytes | Int64 | Indicates the maximum Win32 LOB content file size in bytes that can be uploaded. Valid values 0 to 42949672960 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppPublishingConstraints",
  "maxContentFileSizeInBytes": 1024
}
```
