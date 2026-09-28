<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentityresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# importedDeviceIdentityResult resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The importedDeviceIdentityResult resource represents the result of attempting to import a device identity.

Inherits from [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List importedDeviceIdentityResults](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentityresult-list?view=graph-rest-beta) | [importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentityresult?view=graph-rest-beta) collection | List properties and relationships of the [importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentityresult?view=graph-rest-beta) objects. |
| [Get importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentityresult-get?view=graph-rest-beta) | [importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentityresult?view=graph-rest-beta) | Read properties and relationships of the [importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentityresult?view=graph-rest-beta) object. |
| [Create importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentityresult-create?view=graph-rest-beta) | [importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentityresult?view=graph-rest-beta) | Create a new [importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentityresult?view=graph-rest-beta) object. |
| [Delete importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentityresult-delete?view=graph-rest-beta) | None | Deletes a [importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentityresult?view=graph-rest-beta). |
| [Update importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentityresult-update?view=graph-rest-beta) | [importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentityresult?view=graph-rest-beta) | Update the properties of a [importedDeviceIdentityResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentityresult?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Id of the imported device identity Inherited from [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) |
| importedDeviceIdentifier | String | Imported Device Identifier Inherited from [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) |
| importedDeviceIdentityType | [importedDeviceIdentityType](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentitytype?view=graph-rest-beta) | Type of Imported Device Identity Inherited from [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta). Possible values are: `unknown`, `imei`, `serialNumber`, `manufacturerModelSerial`. |
| lastModifiedDateTime | DateTimeOffset | Last Modified DateTime of the description Inherited from [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | Created Date Time of the device Inherited from [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) |
| lastContactedDateTime | DateTimeOffset | Last Contacted Date Time of the device Inherited from [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) |
| description | String | The description of the device Inherited from [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) |
| enrollmentState | [enrollmentState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enrollmentstate?view=graph-rest-beta) | The state of the device in Intune Inherited from [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta). Possible values are: `unknown`, `enrolled`, `pendingReset`, `failed`, `notContacted`, `blocked`. |
| platform | [platform](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-platform?view=graph-rest-beta) | The platform of the Device. Inherited from [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta). Possible values are: `unknown`, `ios`, `android`, `windows`, `windowsMobile`, `macOS`, `visionOS`, `tvos`, `unknownFutureValue`. |
| status | Boolean | Status of imported device identity |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.importedDeviceIdentityResult",
  "id": "String (identifier)",
  "importedDeviceIdentifier": "String",
  "importedDeviceIdentityType": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "lastContactedDateTime": "String (timestamp)",
  "description": "String",
  "enrollmentState": "String",
  "platform": "String",
  "status": true
}
```
