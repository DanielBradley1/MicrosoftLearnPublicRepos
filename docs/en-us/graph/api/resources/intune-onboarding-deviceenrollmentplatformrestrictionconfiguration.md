<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceEnrollmentPlatformRestrictionConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device Enrollment Configuration that restricts the types of devices a user can enroll for a single platform

Inherits from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceEnrollmentPlatformRestrictionConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration-list?view=graph-rest-beta) | [deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration?view=graph-rest-beta) objects. |
| [Get deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration-get?view=graph-rest-beta) | [deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration?view=graph-rest-beta) | Read properties and relationships of the [deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration?view=graph-rest-beta) object. |
| [Create deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration-create?view=graph-rest-beta) | [deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration?view=graph-rest-beta) | Create a new [deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration?view=graph-rest-beta) object. |
| [Delete deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration-delete?view=graph-rest-beta) | None | Deletes a [deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration?view=graph-rest-beta). |
| [Update deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration-update?view=graph-rest-beta) | [deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration?view=graph-rest-beta) | Update the properties of a [deviceEnrollmentPlatformRestrictionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestrictionconfiguration?view=graph-rest-beta) object. |

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
| platformRestriction | [deviceEnrollmentPlatformRestriction](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentplatformrestriction?view=graph-rest-beta) | Restrictions based on platform, platform operating system version, and device ownership |
| platformType | [enrollmentRestrictionPlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentrestrictionplatformtype?view=graph-rest-beta) | Type of platform for which this restriction applies. Possible values are: `allPlatforms`, `ios`, `windows`, `windowsPhone`, `android`, `androidForWork`, `mac`, `linux`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-beta) collection | The list of group assignments for the device configuration profile Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceEnrollmentPlatformRestrictionConfiguration",
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
  "platformRestriction": {
    "@odata.type": "microsoft.graph.deviceEnrollmentPlatformRestriction",
    "platformBlocked": true,
    "personalDeviceEnrollmentBlocked": true,
    "osMinimumVersion": "String",
    "osMaximumVersion": "String",
    "blockedManufacturers": [
      "String"
    ],
    "blockedSkus": [
      "String"
    ]
  },
  "platformType": "String"
}
```
