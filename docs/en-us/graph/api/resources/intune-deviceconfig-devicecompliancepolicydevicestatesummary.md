<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicydevicestatesummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# deviceCompliancePolicyDeviceStateSummary resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceCompliancePolicyDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecompliancepolicydevicestatesummary-get?view=graph-rest-1.0) | [deviceCompliancePolicyDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicydevicestatesummary?view=graph-rest-1.0) | Read properties and relationships of the [deviceCompliancePolicyDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicydevicestatesummary?view=graph-rest-1.0) object. |
| [Update deviceCompliancePolicyDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecompliancepolicydevicestatesummary-update?view=graph-rest-1.0) | [deviceCompliancePolicyDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicydevicestatesummary?view=graph-rest-1.0) | Update the properties of a [deviceCompliancePolicyDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicydevicestatesummary?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inGracePeriodCount | Int32 | Number of devices that are in grace period |
| configManagerCount | Int32 | Number of devices that have compliance managed by System Center Configuration Manager |
| id | String | Key of the entity. |
| unknownDeviceCount | Int32 | Number of unknown devices |
| notApplicableDeviceCount | Int32 | Number of not applicable devices |
| compliantDeviceCount | Int32 | Number of compliant devices |
| remediatedDeviceCount | Int32 | Number of remediated devices |
| nonCompliantDeviceCount | Int32 | Number of NonCompliant devices |
| errorDeviceCount | Int32 | Number of error devices |
| conflictDeviceCount | Int32 | Number of conflict devices |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceCompliancePolicyDeviceStateSummary",
  "inGracePeriodCount": 1024,
  "configManagerCount": 1024,
  "id": "String (identifier)",
  "unknownDeviceCount": 1024,
  "notApplicableDeviceCount": 1024,
  "compliantDeviceCount": 1024,
  "remediatedDeviceCount": 1024,
  "nonCompliantDeviceCount": 1024,
  "errorDeviceCount": 1024,
  "conflictDeviceCount": 1024
}
```
