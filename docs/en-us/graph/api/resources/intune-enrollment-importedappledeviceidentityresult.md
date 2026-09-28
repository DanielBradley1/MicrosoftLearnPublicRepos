<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentityresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# importedAppleDeviceIdentityResult resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The importedAppleDeviceIdentityResult resource represents the result of attempting to import Apple devices identities.

Inherits from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List importedAppleDeviceIdentityResults](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedappledeviceidentityresult-list?view=graph-rest-beta) | [importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentityresult?view=graph-rest-beta) collection | List properties and relationships of the [importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentityresult?view=graph-rest-beta) objects. |
| [Get importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedappledeviceidentityresult-get?view=graph-rest-beta) | [importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentityresult?view=graph-rest-beta) | Read properties and relationships of the [importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentityresult?view=graph-rest-beta) object. |
| [Create importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedappledeviceidentityresult-create?view=graph-rest-beta) | [importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentityresult?view=graph-rest-beta) | Create a new [importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentityresult?view=graph-rest-beta) object. |
| [Delete importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedappledeviceidentityresult-delete?view=graph-rest-beta) | None | Deletes a [importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentityresult?view=graph-rest-beta). |
| [Update importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedappledeviceidentityresult-update?view=graph-rest-beta) | [importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentityresult?view=graph-rest-beta) | Update the properties of a [importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentityresult?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) |
| serialNumber | String | Device serial number Inherited from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) |
| requestedEnrollmentProfileId | String | Enrollment profile Id admin intends to apply to the device during next enrollment Inherited from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) |
| requestedEnrollmentProfileAssignmentDateTime | DateTimeOffset | The time enrollment profile was assigned to the device Inherited from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) |
| isSupervised | Boolean | Indicates if the Apple device is supervised. Inherited from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) |
| discoverySource | [discoverySource](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-discoverysource?view=graph-rest-beta) | Apple device discovery source. Inherited from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta). Possible values are: `unknown`, `adminImport`, `deviceEnrollmentProgram`. |
| isDeleted | Boolean | Indicates if the device is deleted from Apple Business Manager Inherited from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | Created Date Time of the device Inherited from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) |
| lastContactedDateTime | DateTimeOffset | Last Contacted Date Time of the device Inherited from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) |
| description | String | The description of the device Inherited from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) |
| enrollmentState | [enrollmentState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enrollmentstate?view=graph-rest-beta) | The state of the device in Intune Inherited from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta). Possible values are: `unknown`, `enrolled`, `pendingReset`, `failed`, `notContacted`, `blocked`. |
| platform | [platform](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-platform?view=graph-rest-beta) | The platform of the Device. Inherited from [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta). Possible values are: `unknown`, `ios`, `android`, `windows`, `windowsMobile`, `macOS`, `visionOS`, `tvos`, `unknownFutureValue`. |
| status | Boolean | Status of imported device identity |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.importedAppleDeviceIdentityResult",
  "id": "String (identifier)",
  "serialNumber": "String",
  "requestedEnrollmentProfileId": "String",
  "requestedEnrollmentProfileAssignmentDateTime": "String (timestamp)",
  "isSupervised": true,
  "discoverySource": "String",
  "isDeleted": true,
  "createdDateTime": "String (timestamp)",
  "lastContactedDateTime": "String (timestamp)",
  "description": "String",
  "enrollmentState": "String",
  "platform": "String",
  "status": true
}
```
