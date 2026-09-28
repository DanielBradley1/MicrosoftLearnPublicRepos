<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoslaunchitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# macOSLaunchItem resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an app in the list of macOS launch items

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| path | String | Path to the launch item. |
| hide | Boolean | Whether or not to hide the item from the Users and Groups List. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSLaunchItem",
  "path": "String",
  "hide": true
}
```
