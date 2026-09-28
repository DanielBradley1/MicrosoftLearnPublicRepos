<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-macosdevicelocaladminaccountdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# macOSDeviceLocalAdminAccountDetail resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Properties related to macOS-specific configured and Intune-managed local administrator account

Inherits from [deviceLocalAdminAccountDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelocaladminaccountdetail?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| passwordLastRotationDateTime | DateTimeOffset | The last rotation date and time of the local admin account password. Read-only. Inherited from [deviceLocalAdminAccountDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelocaladminaccountdetail?view=graph-rest-beta) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSDeviceLocalAdminAccountDetail",
  "passwordLastRotationDateTime": "String (timestamp)"
}
```
