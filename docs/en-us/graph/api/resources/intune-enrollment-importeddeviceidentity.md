<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# importedDeviceIdentity resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The importedDeviceIdentity resource represents a unique hardware identity of a device that has been pre-staged for pre-enrollment configuration.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List importedDeviceIdentities](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentity-list?view=graph-rest-beta) | [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) collection | List properties and relationships of the [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) objects. |
| [Get importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentity-get?view=graph-rest-beta) | [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) | Read properties and relationships of the [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) object. |
| [Create importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentity-create?view=graph-rest-beta) | [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) | Create a new [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) object. |
| [Delete importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentity-delete?view=graph-rest-beta) | None | Deletes a [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta). |
| [Update importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentity-update?view=graph-rest-beta) | [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) | Update the properties of a [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) object. |
| [importDeviceIdentityList action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentity-importdeviceidentitylist?view=graph-rest-beta) | [importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentityresult?view=graph-rest-beta) collection |  |
| [searchExistingIdentities action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentity-searchexistingidentities?view=graph-rest-beta) | [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Id of the imported device identity |
| importedDeviceIdentifier | String | Imported Device Identifier |
| importedDeviceIdentityType | [importedDeviceIdentityType](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentitytype?view=graph-rest-beta) | Type of Imported Device Identity. Possible values are: `unknown`, `imei`, `serialNumber`, `manufacturerModelSerial`. |
| lastModifiedDateTime | DateTimeOffset | Last Modified DateTime of the description |
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
  "@odata.type": "#microsoft.graph.importedDeviceIdentity",
  "id": "String (identifier)",
  "importedDeviceIdentifier": "String",
  "importedDeviceIdentityType": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "lastContactedDateTime": "String (timestamp)",
  "description": "String",
  "enrollmentState": "String",
  "platform": "String"
}
```
