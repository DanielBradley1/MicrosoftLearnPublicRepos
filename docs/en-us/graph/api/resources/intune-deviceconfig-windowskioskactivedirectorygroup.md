<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskactivedirectorygroup?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsKioskActiveDirectoryGroup resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The class used to identify an Azure Directory group for the kiosk configuration

Inherits from [windowsKioskUser](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskuser?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| groupName | String | The name of the AD group that will be locked to this kiosk configuration |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsKioskActiveDirectoryGroup",
  "groupName": "String"
}
```
