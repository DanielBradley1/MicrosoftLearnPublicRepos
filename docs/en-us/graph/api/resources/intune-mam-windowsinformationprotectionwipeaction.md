<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsInformationProtectionWipeAction resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents wipe requests issued by tenant admin for Bring-Your-Own-Device\(BYOD\) Windows devices.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsInformationProtectionWipeActions](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectionwipeaction-list?view=graph-rest-beta) | [windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction?view=graph-rest-beta) collection | List properties and relationships of the [windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction?view=graph-rest-beta) objects. |
| [Get windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectionwipeaction-get?view=graph-rest-beta) | [windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction?view=graph-rest-beta) | Read properties and relationships of the [windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction?view=graph-rest-beta) object. |
| [Create windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectionwipeaction-create?view=graph-rest-beta) | [windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction?view=graph-rest-beta) | Create a new [windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction?view=graph-rest-beta) object. |
| [Delete windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectionwipeaction-delete?view=graph-rest-beta) | None | Deletes a [windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction?view=graph-rest-beta). |
| [Update windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectionwipeaction-update?view=graph-rest-beta) | [windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction?view=graph-rest-beta) | Update the properties of a [windowsInformationProtectionWipeAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionwipeaction?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| status | [actionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-actionstate?view=graph-rest-beta) | Wipe action status. Possible values are: `none`, `pending`, `canceled`, `active`, `done`, `failed`, `notSupported`. |
| targetedUserId | String | The UserId being targeted by this wipe action. |
| targetedDeviceRegistrationId | String | The DeviceRegistrationId being targeted by this wipe action. |
| targetedDeviceName | String | Targeted device name. |
| targetedDeviceMacAddress | String | Targeted device Mac address. |
| lastCheckInDateTime | DateTimeOffset | Last checkin time of the device that was targeted by this wipe action. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsInformationProtectionWipeAction",
  "id": "String (identifier)",
  "status": "String",
  "targetedUserId": "String",
  "targetedDeviceRegistrationId": "String",
  "targetedDeviceName": "String",
  "targetedDeviceMacAddress": "String",
  "lastCheckInDateTime": "String (timestamp)"
}
```
