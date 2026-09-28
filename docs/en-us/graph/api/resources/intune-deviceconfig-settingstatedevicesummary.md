<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# settingStateDeviceSummary resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device Compilance Policy and Configuration for a Setting State summary

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List settingStateDeviceSummaries](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-settingstatedevicesummary-list?view=graph-rest-1.0) | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) collection | List properties and relationships of the [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) objects. |
| [Get settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-settingstatedevicesummary-get?view=graph-rest-1.0) | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) | Read properties and relationships of the [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) object. |
| [Create settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-settingstatedevicesummary-create?view=graph-rest-1.0) | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) | Create a new [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) object. |
| [Delete settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-settingstatedevicesummary-delete?view=graph-rest-1.0) | None | Deletes a [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0). |
| [Update settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-settingstatedevicesummary-update?view=graph-rest-1.0) | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) | Update the properties of a [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| settingName | String | Name of the setting |
| instancePath | String | Name of the InstancePath for the setting |
| unknownDeviceCount | Int32 | Device Unkown count for the setting |
| notApplicableDeviceCount | Int32 | Device Not Applicable count for the setting |
| compliantDeviceCount | Int32 | Device Compliant count for the setting |
| remediatedDeviceCount | Int32 | Device Compliant count for the setting |
| nonCompliantDeviceCount | Int32 | Device NonCompliant count for the setting |
| errorDeviceCount | Int32 | Device error count for the setting |
| conflictDeviceCount | Int32 | Device conflict error count for the setting |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.settingStateDeviceSummary",
  "id": "String (identifier)",
  "settingName": "String",
  "instancePath": "String",
  "unknownDeviceCount": 1024,
  "notApplicableDeviceCount": 1024,
  "compliantDeviceCount": 1024,
  "remediatedDeviceCount": 1024,
  "nonCompliantDeviceCount": 1024,
  "errorDeviceCount": 1024,
  "conflictDeviceCount": 1024
}
```
