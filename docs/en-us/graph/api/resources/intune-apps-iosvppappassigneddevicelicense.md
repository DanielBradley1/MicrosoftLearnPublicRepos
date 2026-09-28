<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosVppAppAssignedDeviceLicense resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

iOS Volume Purchase Program device license assignment. This class does not support Create, Delete, or Update.

Inherits from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosVppAppAssignedDeviceLicenses](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassigneddevicelicense-list?view=graph-rest-beta) | [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta) collection | List properties and relationships of the [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta) objects. |
| [Get iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassigneddevicelicense-get?view=graph-rest-beta) | [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta) | Read properties and relationships of the [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta) object. |
| [Create iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassigneddevicelicense-create?view=graph-rest-beta) | [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta) | Create a new [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta) object. |
| [Delete iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassigneddevicelicense-delete?view=graph-rest-beta) | None | Deletes a [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta). |
| [Update iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassigneddevicelicense-update?view=graph-rest-beta) | [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta) | Update the properties of a [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userEmailAddress | String | The user email address. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userId | String | The user ID. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userName | String | The user name. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userPrincipalName | String | The user principal name. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| managedDeviceId | String | The managed device ID. |
| deviceName | String | The device name. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosVppAppAssignedDeviceLicense",
  "id": "String (identifier)",
  "userEmailAddress": "String",
  "userId": "String",
  "userName": "String",
  "userPrincipalName": "String",
  "managedDeviceId": "String",
  "deviceName": "String"
}
```
