<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddeviceoverview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedDeviceOverview resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Summary data for managed devices

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get managedDeviceOverview](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddeviceoverview-get?view=graph-rest-1.0) | [managedDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddeviceoverview?view=graph-rest-1.0) | Read properties and relationships of the [managedDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddeviceoverview?view=graph-rest-1.0) object. |
| [Update managedDeviceOverview](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddeviceoverview-update?view=graph-rest-1.0) | [managedDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddeviceoverview?view=graph-rest-1.0) | Update the properties of a [managedDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddeviceoverview?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the summary |
| enrolledDeviceCount | Int32 | Total enrolled device count. Does not include PC devices managed via Intune PC Agent |
| mdmEnrolledCount | Int32 | The number of devices enrolled in MDM |
| dualEnrolledDeviceCount | Int32 | The number of devices enrolled in both MDM and EAS |
| deviceOperatingSystemSummary | [deviceOperatingSystemSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceoperatingsystemsummary?view=graph-rest-1.0) | Device operating system summary. |
| deviceExchangeAccessStateSummary | [deviceExchangeAccessStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceexchangeaccessstatesummary?view=graph-rest-1.0) | Distribution of Exchange Access State in Intune |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedDeviceOverview",
  "id": "String (identifier)",
  "enrolledDeviceCount": 1024,
  "mdmEnrolledCount": 1024,
  "dualEnrolledDeviceCount": 1024,
  "deviceOperatingSystemSummary": {
    "@odata.type": "microsoft.graph.deviceOperatingSystemSummary",
    "androidCount": 1024,
    "iosCount": 1024,
    "macOSCount": 1024,
    "windowsMobileCount": 1024,
    "windowsCount": 1024,
    "unknownCount": 1024,
    "androidDedicatedCount": 1024,
    "androidDeviceAdminCount": 1024,
    "androidFullyManagedCount": 1024,
    "androidWorkProfileCount": 1024,
    "androidCorporateWorkProfileCount": 1024,
    "configMgrDeviceCount": 1024
  },
  "deviceExchangeAccessStateSummary": {
    "@odata.type": "microsoft.graph.deviceExchangeAccessStateSummary",
    "allowedDeviceCount": 1024,
    "blockedDeviceCount": 1024,
    "quarantinedDeviceCount": 1024,
    "unknownDeviceCount": 1024,
    "unavailableDeviceCount": 1024
  }
}
```
