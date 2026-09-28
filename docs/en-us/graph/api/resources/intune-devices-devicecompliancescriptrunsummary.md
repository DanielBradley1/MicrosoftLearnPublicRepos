<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptrunsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceComplianceScriptRunSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for the run summary of a device management script.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceComplianceScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescriptrunsummary-get?view=graph-rest-beta) | [deviceComplianceScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptrunsummary?view=graph-rest-beta) | Read properties and relationships of the [deviceComplianceScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptrunsummary?view=graph-rest-beta) object. |
| [Update deviceComplianceScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescriptrunsummary-update?view=graph-rest-beta) | [deviceComplianceScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptrunsummary?view=graph-rest-beta) | Update the properties of a [deviceComplianceScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptrunsummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the device compliance script run summary entity. This property is read-only. |
| noIssueDetectedDeviceCount | Int32 | Number of devices for which the detection script did not find an issue and the device is healthy. Valid values -2147483648 to 2147483647 |
| issueDetectedDeviceCount | Int32 | Number of devices for which the detection script found an issue. Valid values -2147483648 to 2147483647 |
| detectionScriptErrorDeviceCount | Int32 | Number of devices on which the detection script execution encountered an error and did not complete. Valid values -2147483648 to 2147483647 |
| detectionScriptPendingDeviceCount | Int32 | Number of devices which have not yet run the latest version of the device compliance script. Valid values -2147483648 to 2147483647 |
| lastScriptRunDateTime | DateTimeOffset | Last run time for the script across all devices |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceComplianceScriptRunSummary",
  "id": "String (identifier)",
  "noIssueDetectedDeviceCount": 1024,
  "issueDetectedDeviceCount": 1024,
  "detectionScriptErrorDeviceCount": 1024,
  "detectionScriptPendingDeviceCount": 1024,
  "lastScriptRunDateTime": "String (timestamp)"
}
```
