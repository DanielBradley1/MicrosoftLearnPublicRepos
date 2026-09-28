<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondeviceregistration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsInformationProtectionDeviceRegistration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents device registration records for Bring-Your-Own-Device\(BYOD\) Windows devices.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsInformationProtectionDeviceRegistrations](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectiondeviceregistration-list?view=graph-rest-beta) | [windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondeviceregistration?view=graph-rest-beta) collection | List properties and relationships of the [windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondeviceregistration?view=graph-rest-beta) objects. |
| [Get windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectiondeviceregistration-get?view=graph-rest-beta) | [windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondeviceregistration?view=graph-rest-beta) | Read properties and relationships of the [windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondeviceregistration?view=graph-rest-beta) object. |
| [Create windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectiondeviceregistration-create?view=graph-rest-beta) | [windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondeviceregistration?view=graph-rest-beta) | Create a new [windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondeviceregistration?view=graph-rest-beta) object. |
| [Delete windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectiondeviceregistration-delete?view=graph-rest-beta) | None | Deletes a [windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondeviceregistration?view=graph-rest-beta). |
| [Update windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectiondeviceregistration-update?view=graph-rest-beta) | [windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondeviceregistration?view=graph-rest-beta) | Update the properties of a [windowsInformationProtectionDeviceRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondeviceregistration?view=graph-rest-beta) object. |
| [wipe action](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectiondeviceregistration-wipe?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| userId | String | UserId associated with this device registration record. |
| deviceRegistrationId | String | Device identifier for this device registration record. |
| deviceName | String | Device name. |
| deviceType | String | Device type, for example, Windows laptop VS Windows phone. |
| deviceMacAddress | String | Device Mac address. |
| lastCheckInDateTime | DateTimeOffset | Last checkin time of the device. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsInformationProtectionDeviceRegistration",
  "id": "String (identifier)",
  "userId": "String",
  "deviceRegistrationId": "String",
  "deviceName": "String",
  "deviceType": "String",
  "deviceMacAddress": "String",
  "lastCheckInDateTime": "String (timestamp)"
}
```
