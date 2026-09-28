<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsminimumoperatingsystem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsMinimumOperatingSystem resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The minimum operating system required for a Windows mobile app.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| v8\_0 | Boolean | Windows version 8.0 or later. |
| v8\_1 | Boolean | Windows version 8.1 or later. |
| v10\_0 | Boolean | Windows version 10.0 or later. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsMinimumOperatingSystem",
  "v8_0": true,
  "v8_1": true,
  "v10_0": true
}
```
