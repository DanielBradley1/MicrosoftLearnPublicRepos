<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceexchangeaccessstatesummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceExchangeAccessStateSummary resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device Exchange Access State summary

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedDeviceCount | Int32 | Total count of devices with Exchange Access State: Allowed. |
| blockedDeviceCount | Int32 | Total count of devices with Exchange Access State: Blocked. |
| quarantinedDeviceCount | Int32 | Total count of devices with Exchange Access State: Quarantined. |
| unknownDeviceCount | Int32 | Total count of devices with Exchange Access State: Unknown. |
| unavailableDeviceCount | Int32 | Total count of devices for which no Exchange Access State could be found. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceExchangeAccessStateSummary",
  "allowedDeviceCount": 1024,
  "blockedDeviceCount": 1024,
  "quarantinedDeviceCount": 1024,
  "unknownDeviceCount": 1024,
  "unavailableDeviceCount": 1024
}
```
