<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationrunsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# hardwareConfigurationRunSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for the run summary of a hardware configuration script.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get hardwareConfigurationRunSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationrunsummary-get?view=graph-rest-beta) | [hardwareConfigurationRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationrunsummary?view=graph-rest-beta) | Read properties and relationships of the [hardwareConfigurationRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationrunsummary?view=graph-rest-beta) object. |
| [Update hardwareConfigurationRunSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationrunsummary-update?view=graph-rest-beta) | [hardwareConfigurationRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationrunsummary?view=graph-rest-beta) | Update the properties of a [hardwareConfigurationRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationrunsummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the hardware configuration run summary entity. This property is read-only. |
| successfulDeviceCount | Int32 | Number of devices for which hardware configured without any issue |
| failedDeviceCount | Int32 | Number of devices for which hardware configuration found an issue |
| pendingDeviceCount | Int32 | Number of devices for which hardware configuration is in pending state |
| errorDeviceCount | Int32 | Number of devices for which hardware configuration state is error |
| notApplicableDeviceCount | Int32 | Number of devices for which hardware configuration state is not applicable |
| unknownDeviceCount | Int32 | Number of devices for which hardware configuration state is unknown |
| successfulUserCount | Int32 | Number of users for which hardware configured without any issue |
| failedUserCount | Int32 | Number of users for which hardware configuration found an issue |
| pendingUserCount | Int32 | Number of users for which hardware configuration is in pending state |
| errorUserCount | Int32 | Number of users for which hardware configuration state is error |
| notApplicableUserCount | Int32 | Number of users for which hardware configuration state is not applicable |
| unknownUserCount | Int32 | Number of users for which hardware configuration state is unknown |
| lastRunDateTime | DateTimeOffset | Last run time for the configuration across all devices |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.hardwareConfigurationRunSummary",
  "id": "String (identifier)",
  "successfulDeviceCount": 1024,
  "failedDeviceCount": 1024,
  "pendingDeviceCount": 1024,
  "errorDeviceCount": 1024,
  "notApplicableDeviceCount": 1024,
  "unknownDeviceCount": 1024,
  "successfulUserCount": 1024,
  "failedUserCount": 1024,
  "pendingUserCount": 1024,
  "errorUserCount": 1024,
  "notApplicableUserCount": 1024,
  "unknownUserCount": 1024,
  "lastRunDateTime": "String (timestamp)"
}
```
