<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowsrestoredeviceenrollmentconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsRestoreDeviceEnrollmentConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Indicates the configuration is of type Windows Restore which refers to the tenant level Windows Backup and Restore settings a user receives during OOBE Windows enrollment

Inherits from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsRestoreDeviceEnrollmentConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-windowsrestoredeviceenrollmentconfiguration-list?view=graph-rest-beta) | [windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowsrestoredeviceenrollmentconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowsrestoredeviceenrollmentconfiguration?view=graph-rest-beta) objects. |
| [Get windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-windowsrestoredeviceenrollmentconfiguration-get?view=graph-rest-beta) | [windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowsrestoredeviceenrollmentconfiguration?view=graph-rest-beta) | Read properties and relationships of the [windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowsrestoredeviceenrollmentconfiguration?view=graph-rest-beta) object. |
| [Create windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-windowsrestoredeviceenrollmentconfiguration-create?view=graph-rest-beta) | [windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowsrestoredeviceenrollmentconfiguration?view=graph-rest-beta) | Create a new [windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowsrestoredeviceenrollmentconfiguration?view=graph-rest-beta) object. |
| [Delete windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-windowsrestoredeviceenrollmentconfiguration-delete?view=graph-rest-beta) | None | Deletes a [windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowsrestoredeviceenrollmentconfiguration?view=graph-rest-beta). |
| [Update windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-windowsrestoredeviceenrollmentconfiguration-update?view=graph-rest-beta) | [windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowsrestoredeviceenrollmentconfiguration?view=graph-rest-beta) | Update the properties of a [windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowsrestoredeviceenrollmentconfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the account Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| displayName | String | The display name of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| description | String | The description of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| priority | Int32 | Priority is used when a user exists in multiple groups that are assigned enrollment configuration. Users are subject only to the configuration with the lowest priority value. Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | Created date time in UTC of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | Last modified date time in UTC of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| version | Int32 | The version of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| roleScopeTagIds | String collection | Optional role scope tags for the enrollment restrictions. Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| deviceEnrollmentConfigurationType | [deviceEnrollmentConfigurationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfigurationtype?view=graph-rest-beta) | Support for Enrollment Configuration Type Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta). Possible values are: `unknown`, `limit`, `platformRestrictions`, `windowsHelloForBusiness`, `defaultLimit`, `defaultPlatformRestrictions`, `defaultWindowsHelloForBusiness`, `defaultWindows10EnrollmentCompletionPageConfiguration`, `windows10EnrollmentCompletionPageConfiguration`, `deviceComanagementAuthorityConfiguration`, `singlePlatformRestriction`, `unknownFutureValue`, `enrollmentNotificationsConfiguration`, `windowsRestore`. |
| state | [enablement](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enablement?view=graph-rest-beta) | Indicates the configuration state of the Windows Restore setting. Possible values are 'notConfigured', 'enabled', and 'disabled'. Default is: notConfigured. This is a tenant level default setting that is not targetable. This property's value is applied during Enrollment. Possible values are: `notConfigured`, `enabled`, `disabled`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-beta) collection | The list of group assignments for the device configuration profile Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsRestoreDeviceEnrollmentConfiguration",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "priority": 1024,
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "version": 1024,
  "roleScopeTagIds": [
    "String"
  ],
  "deviceEnrollmentConfigurationType": "String",
  "state": "String"
}
```
