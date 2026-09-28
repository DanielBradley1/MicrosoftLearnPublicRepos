<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosgeneraldeviceconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-13 -->

# macOSGeneralDeviceConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the macOSGeneralDeviceConfiguration resource.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSGeneralDeviceConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosgeneraldeviceconfiguration-list?view=graph-rest-1.0) | [macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosgeneraldeviceconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosgeneraldeviceconfiguration?view=graph-rest-1.0) objects. |
| [Get macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosgeneraldeviceconfiguration-get?view=graph-rest-1.0) | [macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosgeneraldeviceconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosgeneraldeviceconfiguration?view=graph-rest-1.0) object. |
| [Create macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosgeneraldeviceconfiguration-create?view=graph-rest-1.0) | [macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosgeneraldeviceconfiguration?view=graph-rest-1.0) | Create a new [macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosgeneraldeviceconfiguration?view=graph-rest-1.0) object. |
| [Delete macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosgeneraldeviceconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosgeneraldeviceconfiguration?view=graph-rest-1.0). |
| [Update macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosgeneraldeviceconfiguration-update?view=graph-rest-1.0) | [macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosgeneraldeviceconfiguration?view=graph-rest-1.0) | Update the properties of a [macOSGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosgeneraldeviceconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| compliantAppsList | [appListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applistitem?view=graph-rest-1.0) collection | List of apps in the compliance \(either allow list or block list, controlled by CompliantAppListType\). This collection can contain a maximum of 10000 elements. |
| compliantAppListType | [appListType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applisttype?view=graph-rest-1.0) | List that is in the CompliantAppsList. The possible values are: `none`, `appsInListCompliant`, `appsNotInListCompliant`. |
| emailInDomainSuffixes | String collection | An email address lacking a suffix that matches any of these strings will be considered out-of-domain. |
| passwordBlockSimple | Boolean | Block simple passwords. |
| passwordExpirationDays | Int32 | Number of days before the password expires. |
| passwordMinimumCharacterSetCount | Int32 | Number of character sets a password must contain. Valid values 0 to 4 |
| passwordMinimumLength | Int32 | Minimum length of passwords. |
| passwordMinutesOfInactivityBeforeLock | Int32 | Minutes of inactivity required before a password is required. |
| passwordMinutesOfInactivityBeforeScreenTimeout | Int32 | Minutes of inactivity required before the screen times out. |
| passwordPreviousPasswordBlockCount | Int32 | Number of previous passwords to block. |
| passwordRequiredType | [requiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-requiredpasswordtype?view=graph-rest-1.0) | Type of password that is required. The possible values are: `deviceDefault`, `alphanumeric`, `numeric`. |
| passwordRequired | Boolean | Whether or not to require a password. |

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
  "@odata.type": "#microsoft.graph.macOSGeneralDeviceConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
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
  "emailInDomainSuffixes": [
    "String"
  ],
  "passwordBlockSimple": true,
  "passwordExpirationDays": 1024,
  "passwordMinimumCharacterSetCount": 1024,
  "passwordMinimumLength": 1024,
  "passwordMinutesOfInactivityBeforeLock": 1024,
  "passwordMinutesOfInactivityBeforeScreenTimeout": 1024,
  "passwordPreviousPasswordBlockCount": 1024,
  "passwordRequiredType": "String",
  "passwordRequired": true
}
```
