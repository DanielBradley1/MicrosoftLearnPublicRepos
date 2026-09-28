<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# deviceComplianceUserStatus resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceComplianceUserStatuses](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceuserstatus-list?view=graph-rest-1.0) | [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-1.0) collection | List properties and relationships of the [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-1.0) objects. |
| [Get deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceuserstatus-get?view=graph-rest-1.0) | [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-1.0) | Read properties and relationships of the [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-1.0) object. |
| [Create deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceuserstatus-create?view=graph-rest-1.0) | [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-1.0) | Create a new [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-1.0) object. |
| [Delete deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceuserstatus-delete?view=graph-rest-1.0) | None | Deletes a [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-1.0). |
| [Update deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceuserstatus-update?view=graph-rest-1.0) | [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-1.0) | Update the properties of a [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| userDisplayName | String | User name of the DevicePolicyStatus. |
| devicesCount | Int32 | Devices count for that user. |
| status | [complianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-compliancestatus?view=graph-rest-1.0) | Compliance status of the policy report. The possible values are: `unknown`, `notApplicable`, `compliant`, `remediated`, `nonCompliant`, `error`, `conflict`, `notAssigned`. |
| lastReportedDateTime | DateTimeOffset | Last modified date time of the policy report. |
| userPrincipalName | String | UserPrincipalName. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceComplianceUserStatus",
  "id": "String (identifier)",
  "userDisplayName": "String",
  "devicesCount": 1024,
  "status": "String",
  "lastReportedDateTime": "String (timestamp)",
  "userPrincipalName": "String"
}
```
