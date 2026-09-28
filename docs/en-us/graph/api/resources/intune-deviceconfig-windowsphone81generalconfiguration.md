<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81generalconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# windowsPhone81GeneralConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the windowsPhone81GeneralConfiguration resource.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsPhone81GeneralConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81generalconfiguration-list?view=graph-rest-1.0) | [windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81generalconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81generalconfiguration?view=graph-rest-1.0) objects. |
| [Get windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81generalconfiguration-get?view=graph-rest-1.0) | [windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81generalconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81generalconfiguration?view=graph-rest-1.0) object. |
| [Create windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81generalconfiguration-create?view=graph-rest-1.0) | [windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81generalconfiguration?view=graph-rest-1.0) | Create a new [windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81generalconfiguration?view=graph-rest-1.0) object. |
| [Delete windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81generalconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81generalconfiguration?view=graph-rest-1.0). |
| [Update windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81generalconfiguration-update?view=graph-rest-1.0) | [windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81generalconfiguration?view=graph-rest-1.0) | Update the properties of a [windowsPhone81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81generalconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| applyOnlyToWindowsPhone81 | Boolean | Value indicating whether this policy only applies to Windows Phone 8.1. This property is read-only. |
| appsBlockCopyPaste | Boolean | Indicates whether or not to block copy paste. |
| bluetoothBlocked | Boolean | Indicates whether or not to block bluetooth. |
| cameraBlocked | Boolean | Indicates whether or not to block camera. |
| cellularBlockWifiTethering | Boolean | Indicates whether or not to block Wi-Fi tethering. Has no impact if Wi-Fi is blocked. |
| compliantAppsList | [appListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applistitem?view=graph-rest-1.0) collection | List of apps in the compliance \(either allow list or block list, controlled by CompliantAppListType\). This collection can contain a maximum of 10000 elements. |
| compliantAppListType | [appListType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applisttype?view=graph-rest-1.0) | List that is in the AppComplianceList. The possible values are: `none`, `appsInListCompliant`, `appsNotInListCompliant`. |
| diagnosticDataBlockSubmission | Boolean | Indicates whether or not to block diagnostic data submission. |
| emailBlockAddingAccounts | Boolean | Indicates whether or not to block custom email accounts. |
| locationServicesBlocked | Boolean | Indicates whether or not to block location services. |
| microsoftAccountBlocked | Boolean | Indicates whether or not to block using a Microsoft Account. |
| nfcBlocked | Boolean | Indicates whether or not to block Near-Field Communication. |
| passwordBlockSimple | Boolean | Indicates whether or not to block syncing the calendar. |
| passwordExpirationDays | Int32 | Number of days before the password expires. |
| passwordMinimumLength | Int32 | Minimum length of passwords. |
| passwordMinutesOfInactivityBeforeScreenTimeout | Int32 | Minutes of inactivity before screen timeout. |
| passwordMinimumCharacterSetCount | Int32 | Number of character sets a password must contain. |
| passwordPreviousPasswordBlockCount | Int32 | Number of previous passwords to block. Valid values 0 to 24 |
| passwordSignInFailureCountBeforeFactoryReset | Int32 | Number of sign in failures allowed before factory reset. |
| passwordRequiredType | [requiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-requiredpasswordtype?view=graph-rest-1.0) | Password type that is required. The possible values are: `deviceDefault`, `alphanumeric`, `numeric`. |
| passwordRequired | Boolean | Indicates whether or not to require a password. |
| screenCaptureBlocked | Boolean | Indicates whether or not to block screenshots. |
| storageBlockRemovableStorage | Boolean | Indicates whether or not to block removable storage. |
| storageRequireEncryption | Boolean | Indicates whether or not to require encryption. |
| webBrowserBlocked | Boolean | Indicates whether or not to block the web browser. |
| wifiBlocked | Boolean | Indicates whether or not to block Wi-Fi. |
| wifiBlockAutomaticConnectHotspots | Boolean | Indicates whether or not to block automatically connecting to Wi-Fi hotspots. Has no impact if Wi-Fi is blocked. |
| wifiBlockHotspotReporting | Boolean | Indicates whether or not to block Wi-Fi hotspot reporting. Has no impact if Wi-Fi is blocked. |
| windowsStoreBlocked | Boolean | Indicates whether or not to block the Windows Store. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0) collection | The list of assignments for the device configuration profile. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| deviceStatuses | [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0) collection | Device configuration installation status by device. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| userStatuses | [deviceConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatus?view=graph-rest-1.0) collection | Device configuration installation status by user. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| deviceStatusOverview | [deviceConfigurationDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdeviceoverview?view=graph-rest-1.0) | Device Configuration devices status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| userStatusOverview | [deviceConfigurationUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuseroverview?view=graph-rest-1.0) | Device Configuration users status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| deviceSettingStateSummaries | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) collection | Device Configuration Setting State Device Summary Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsPhone81GeneralConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "applyOnlyToWindowsPhone81": true,
  "appsBlockCopyPaste": true,
  "bluetoothBlocked": true,
  "cameraBlocked": true,
  "cellularBlockWifiTethering": true,
  "compliantAppsList": [
    {
      "@odata.type": "microsoft.graph.appListItem",
      "name": "String",
      "publisher": "String",
      "appStoreUrl": "String",
      "appId": "String"
    }
  ],
  "compliantAppListType": "String",
  "diagnosticDataBlockSubmission": true,
  "emailBlockAddingAccounts": true,
  "locationServicesBlocked": true,
  "microsoftAccountBlocked": true,
  "nfcBlocked": true,
  "passwordBlockSimple": true,
  "passwordExpirationDays": 1024,
  "passwordMinimumLength": 1024,
  "passwordMinutesOfInactivityBeforeScreenTimeout": 1024,
  "passwordMinimumCharacterSetCount": 1024,
  "passwordPreviousPasswordBlockCount": 1024,
  "passwordSignInFailureCountBeforeFactoryReset": 1024,
  "passwordRequiredType": "String",
  "passwordRequired": true,
  "screenCaptureBlocked": true,
  "storageBlockRemovableStorage": true,
  "storageRequireEncryption": true,
  "webBrowserBlocked": true,
  "wifiBlocked": true,
  "wifiBlockAutomaticConnectHotspots": true,
  "wifiBlockHotspotReporting": true,
  "windowsStoreBlocked": true
}
```
