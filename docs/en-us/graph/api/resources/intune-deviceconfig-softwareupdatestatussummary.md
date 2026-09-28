<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-softwareupdatestatussummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# softwareUpdateStatusSummary resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get softwareUpdateStatusSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-softwareupdatestatussummary-get?view=graph-rest-1.0) | [softwareUpdateStatusSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-softwareupdatestatussummary?view=graph-rest-1.0) | Read properties and relationships of the [softwareUpdateStatusSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-softwareupdatestatussummary?view=graph-rest-1.0) object. |
| [Update softwareUpdateStatusSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-softwareupdatestatussummary-update?view=graph-rest-1.0) | [softwareUpdateStatusSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-softwareupdatestatussummary?view=graph-rest-1.0) | Update the properties of a [softwareUpdateStatusSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-softwareupdatestatussummary?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| displayName | String | The name of the policy. |
| compliantDeviceCount | Int32 | Number of compliant devices. |
| nonCompliantDeviceCount | Int32 | Number of non compliant devices. |
| remediatedDeviceCount | Int32 | Number of remediated devices. |
| errorDeviceCount | Int32 | Number of devices had error. |
| unknownDeviceCount | Int32 | Number of unknown devices. |
| conflictDeviceCount | Int32 | Number of conflict devices. |
| notApplicableDeviceCount | Int32 | Number of not applicable devices. |
| compliantUserCount | Int32 | Number of compliant users. |
| nonCompliantUserCount | Int32 | Number of non compliant users. |
| remediatedUserCount | Int32 | Number of remediated users. |
| errorUserCount | Int32 | Number of users had error. |
| unknownUserCount | Int32 | Number of unknown users. |
| conflictUserCount | Int32 | Number of conflict users. |
| notApplicableUserCount | Int32 | Number of not applicable users. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.softwareUpdateStatusSummary",
  "id": "String (identifier)",
  "displayName": "String",
  "compliantDeviceCount": 1024,
  "nonCompliantDeviceCount": 1024,
  "remediatedDeviceCount": 1024,
  "errorDeviceCount": 1024,
  "unknownDeviceCount": 1024,
  "conflictDeviceCount": 1024,
  "notApplicableDeviceCount": 1024,
  "compliantUserCount": 1024,
  "nonCompliantUserCount": 1024,
  "remediatedUserCount": 1024,
  "errorUserCount": 1024,
  "unknownUserCount": 1024,
  "conflictUserCount": 1024,
  "notApplicableUserCount": 1024
}
```
