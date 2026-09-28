<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationuserstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# hardwareConfigurationUserState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for User state of the hardware configuration

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List hardwareConfigurationUserStates](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationuserstate-list?view=graph-rest-beta) | [hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationuserstate?view=graph-rest-beta) collection | List properties and relationships of the [hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationuserstate?view=graph-rest-beta) objects. |
| [Get hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationuserstate-get?view=graph-rest-beta) | [hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationuserstate?view=graph-rest-beta) | Read properties and relationships of the [hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationuserstate?view=graph-rest-beta) object. |
| [Create hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationuserstate-create?view=graph-rest-beta) | [hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationuserstate?view=graph-rest-beta) | Create a new [hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationuserstate?view=graph-rest-beta) object. |
| [Delete hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationuserstate-delete?view=graph-rest-beta) | None | Deletes a [hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationuserstate?view=graph-rest-beta). |
| [Update hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwareconfigurationuserstate-update?view=graph-rest-beta) | [hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationuserstate?view=graph-rest-beta) | Update the properties of a [hardwareConfigurationUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwareconfigurationuserstate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the hardware configuration script user state entity. This property is read-only. |
| upn | String | User Principal Name \(UPN\). |
| userEmail | String | User Email address. |
| userName | String | User name |
| lastStateUpdateDateTime | DateTimeOffset | Last timestamp when the hardware configuration executed |
| successfulDeviceCount | Int32 | Success device count for specific user. |
| failedDeviceCount | Int32 | Failed device count for specific user. |
| pendingDeviceCount | Int32 | Pending device count for specific user. |
| errorDeviceCount | Int32 | Error device count for specific user. |
| notApplicableDeviceCount | Int32 | Not applicable device count for specific user. |
| unknownDeviceCount | Int32 | Unknown device count for specific user. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.hardwareConfigurationUserState",
  "id": "String (identifier)",
  "upn": "String",
  "userEmail": "String",
  "userName": "String",
  "lastStateUpdateDateTime": "String (timestamp)",
  "successfulDeviceCount": 1024,
  "failedDeviceCount": 1024,
  "pendingDeviceCount": 1024,
  "errorDeviceCount": 1024,
  "notApplicableDeviceCount": 1024,
  "unknownDeviceCount": 1024
}
```
