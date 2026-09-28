<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-enrollmenttroubleshootingevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# enrollmentTroubleshootingEvent resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Event representing an enrollment failure.

Inherits from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List enrollmentTroubleshootingEvents](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-enrollmenttroubleshootingevent-list?view=graph-rest-1.0) | [enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-enrollmenttroubleshootingevent?view=graph-rest-1.0) collection | List properties and relationships of the [enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-enrollmenttroubleshootingevent?view=graph-rest-1.0) objects. |
| [Get enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-enrollmenttroubleshootingevent-get?view=graph-rest-1.0) | [enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-enrollmenttroubleshootingevent?view=graph-rest-1.0) | Read properties and relationships of the [enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-enrollmenttroubleshootingevent?view=graph-rest-1.0) object. |
| [Create enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-enrollmenttroubleshootingevent-create?view=graph-rest-1.0) | [enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-enrollmenttroubleshootingevent?view=graph-rest-1.0) | Create a new [enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-enrollmenttroubleshootingevent?view=graph-rest-1.0) object. |
| [Delete enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-enrollmenttroubleshootingevent-delete?view=graph-rest-1.0) | None | Deletes a [enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-enrollmenttroubleshootingevent?view=graph-rest-1.0). |
| [Update enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-enrollmenttroubleshootingevent-update?view=graph-rest-1.0) | [enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-enrollmenttroubleshootingevent?view=graph-rest-1.0) | Update the properties of a [enrollmentTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-enrollmenttroubleshootingevent?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | UUID for the object Inherited from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0) |
| eventDateTime | DateTimeOffset | Time when the event occurred . Inherited from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0) |
| correlationId | String | Id used for tracing the failure in the service. Inherited from [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-1.0) |
| managedDeviceIdentifier | String | Device identifier created or collected by Intune. |
| operatingSystem | String | Operating System. |
| osVersion | String | OS Version. |
| userId | String | Identifier for the user that tried to enroll the device. |
| deviceId | String | Azure AD device identifier. |
| enrollmentType | [deviceEnrollmentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-deviceenrollmenttype.md?view=graph-rest-1.0) | Type of the enrollment. The possible values are: `unknown`, `userEnrollment`, `deviceEnrollmentManager`, `appleBulkWithUser`, `appleBulkWithoutUser`, `windowsAzureADJoin`, `windowsBulkUserless`, `windowsAutoEnrollment`, `windowsBulkAzureDomainJoin`, `windowsCoManagement`. |
| failureCategory | [deviceEnrollmentFailureReason](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-deviceenrollmentfailurereason?view=graph-rest-1.0) | Highlevel failure category. The possible values are: `unknown`, `authentication`, `authorization`, `accountValidation`, `userValidation`, `deviceNotSupported`, `inMaintenance`, `badRequest`, `featureNotSupported`, `enrollmentRestrictionsEnforced`, `clientDisconnected`, `userAbandonment`. |
| failureReason | String | Detailed failure reason. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.enrollmentTroubleshootingEvent",
  "id": "String (identifier)",
  "eventDateTime": "String (timestamp)",
  "correlationId": "String",
  "managedDeviceIdentifier": "String",
  "operatingSystem": "String",
  "osVersion": "String",
  "userId": "String",
  "deviceId": "String",
  "enrollmentType": "String",
  "failureCategory": "String",
  "failureReason": "String"
}
```
