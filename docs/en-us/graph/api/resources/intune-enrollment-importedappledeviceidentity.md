<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# importedAppleDeviceIdentity resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The importedAppleDeviceIdentity resource represents the imported device identity of an Apple device .

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List importedAppleDeviceIdentities](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedappledeviceidentity-list?view=graph-rest-beta) | [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) collection | List properties and relationships of the [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) objects. |
| [Get importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedappledeviceidentity-get?view=graph-rest-beta) | [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) | Read properties and relationships of the [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) object. |
| [Create importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedappledeviceidentity-create?view=graph-rest-beta) | [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) | Create a new [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) object. |
| [Delete importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedappledeviceidentity-delete?view=graph-rest-beta) | None | Deletes a [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta). |
| [Update importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedappledeviceidentity-update?view=graph-rest-beta) | [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) | Update the properties of a [importedAppleDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentity?view=graph-rest-beta) object. |
| [importAppleDeviceIdentityList action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedappledeviceidentity-importappledeviceidentitylist?view=graph-rest-beta) | [importedAppleDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedappledeviceidentityresult?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| serialNumber | String | Device serial number |
| requestedEnrollmentProfileId | String | Enrollment profile Id admin intends to apply to the device during next enrollment |
| requestedEnrollmentProfileAssignmentDateTime | DateTimeOffset | The time enrollment profile was assigned to the device |
| isSupervised | Boolean | Indicates if the Apple device is supervised. |
| discoverySource | [discoverySource](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-discoverysource?view=graph-rest-beta) | Apple device discovery source. Possible values are: `unknown`, `adminImport`, `deviceEnrollmentProgram`. |
| isDeleted | Boolean | Indicates if the device is deleted from Apple Business Manager |
| createdDateTime | DateTimeOffset | Created Date Time of the device |
| lastContactedDateTime | DateTimeOffset | Last Contacted Date Time of the device |
| description | String | The description of the device |
| enrollmentState | [enrollmentState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enrollmentstate?view=graph-rest-beta) | The state of the device in Intune. Possible values are: `unknown`, `enrolled`, `pendingReset`, `failed`, `notContacted`, `blocked`. |
| platform | [platform](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-platform?view=graph-rest-beta) | The platform of the Device. Possible values are: `unknown`, `ios`, `android`, `windows`, `windowsMobile`, `macOS`, `visionOS`, `tvos`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.importedAppleDeviceIdentity",
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
  "platform": "String"
}
```
