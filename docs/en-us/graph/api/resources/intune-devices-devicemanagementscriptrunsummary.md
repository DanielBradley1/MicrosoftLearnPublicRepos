<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptrunsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementScriptRunSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for the run summary of a device management script.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceManagementScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptrunsummary-get?view=graph-rest-beta) | [deviceManagementScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptrunsummary?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptrunsummary?view=graph-rest-beta) object. |
| [Update deviceManagementScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptrunsummary-update?view=graph-rest-beta) | [deviceManagementScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptrunsummary?view=graph-rest-beta) | Update the properties of a [deviceManagementScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptrunsummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the device management script run summary entity. This property is read-only. |
| successDeviceCount | Int32 | Success device count. |
| errorDeviceCount | Int32 | Error device count. |
| successUserCount | Int32 | Success user count. |
| errorUserCount | Int32 | Error user count. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementScriptRunSummary",
  "id": "String (identifier)",
  "successDeviceCount": 1024,
  "errorDeviceCount": 1024,
  "successUserCount": 1024,
  "errorUserCount": 1024
}
```
