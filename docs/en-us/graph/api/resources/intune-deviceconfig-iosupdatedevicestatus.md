<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdatedevicestatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# iosUpdateDeviceStatus resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosUpdateDeviceStatuses](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosupdatedevicestatus-list?view=graph-rest-1.0) | [iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdatedevicestatus?view=graph-rest-1.0) collection | List properties and relationships of the [iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdatedevicestatus?view=graph-rest-1.0) objects. |
| [Get iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosupdatedevicestatus-get?view=graph-rest-1.0) | [iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdatedevicestatus?view=graph-rest-1.0) | Read properties and relationships of the [iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdatedevicestatus?view=graph-rest-1.0) object. |
| [Create iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosupdatedevicestatus-create?view=graph-rest-1.0) | [iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdatedevicestatus?view=graph-rest-1.0) | Create a new [iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdatedevicestatus?view=graph-rest-1.0) object. |
| [Delete iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosupdatedevicestatus-delete?view=graph-rest-1.0) | None | Deletes a [iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdatedevicestatus?view=graph-rest-1.0). |
| [Update iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosupdatedevicestatus-update?view=graph-rest-1.0) | [iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdatedevicestatus?view=graph-rest-1.0) | Update the properties of a [iosUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdatedevicestatus?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| installStatus | [iosUpdatesInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdatesinstallstatus?view=graph-rest-1.0) | The installation status of the policy report. The possible values are: `success`, `available`, `idle`, `unknown`, `downloading`, `downloadFailed`, `downloadRequiresComputer`, `downloadInsufficientSpace`, `downloadInsufficientPower`, `downloadInsufficientNetwork`, `installing`, `installInsufficientSpace`, `installInsufficientPower`, `installPhoneCallInProgress`, `installFailed`, `notSupportedOperation`, `sharedDeviceUserLoggedInError`, `deviceOsHigherThanDesiredOsVersion`. |
| osVersion | String | The device version that is being reported. |
| deviceId | String | The device id that is being reported. |
| userId | String | The User id that is being reported. |
| deviceDisplayName | String | Device name of the DevicePolicyStatus. |
| userName | String | The User Name that is being reported |
| deviceModel | String | The device model that is being reported |
| complianceGracePeriodExpirationDateTime | DateTimeOffset | The DateTime when device compliance grace period expires |
| status | [complianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-compliancestatus?view=graph-rest-1.0) | Compliance status of the policy report. The possible values are: `unknown`, `notApplicable`, `compliant`, `remediated`, `nonCompliant`, `error`, `conflict`, `notAssigned`. |
| lastReportedDateTime | DateTimeOffset | Last modified date time of the policy report. |
| userPrincipalName | String | UserPrincipalName. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosUpdateDeviceStatus",
  "id": "String (identifier)",
  "installStatus": "String",
  "osVersion": "String",
  "deviceId": "String",
  "userId": "String",
  "deviceDisplayName": "String",
  "userName": "String",
  "deviceModel": "String",
  "complianceGracePeriodExpirationDateTime": "String (timestamp)",
  "status": "String",
  "lastReportedDateTime": "String (timestamp)",
  "userPrincipalName": "String"
}
```
