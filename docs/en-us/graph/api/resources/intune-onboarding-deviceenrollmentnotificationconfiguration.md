<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentnotificationconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# deviceEnrollmentNotificationConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Enrollment Notification Configuration which is used to send notification

Inherits from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceEnrollmentNotificationConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentnotificationconfiguration-list?view=graph-rest-beta) | [deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentnotificationconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentnotificationconfiguration?view=graph-rest-beta) objects. |
| [Get deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentnotificationconfiguration-get?view=graph-rest-beta) | [deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentnotificationconfiguration?view=graph-rest-beta) | Read properties and relationships of the [deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentnotificationconfiguration?view=graph-rest-beta) object. |
| [Create deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentnotificationconfiguration-create?view=graph-rest-beta) | [deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentnotificationconfiguration?view=graph-rest-beta) | Create a new [deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentnotificationconfiguration?view=graph-rest-beta) object. |
| [Delete deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentnotificationconfiguration-delete?view=graph-rest-beta) | None | Deletes a [deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentnotificationconfiguration?view=graph-rest-beta). |
| [Update deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-deviceenrollmentnotificationconfiguration-update?view=graph-rest-beta) | [deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentnotificationconfiguration?view=graph-rest-beta) | Update the properties of a [deviceEnrollmentNotificationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentnotificationconfiguration?view=graph-rest-beta) object. |

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
| platformType | [enrollmentRestrictionPlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentrestrictionplatformtype?view=graph-rest-beta) | Platform type of the Enrollment Notification. Possible values are: `allPlatforms`, `ios`, `windows`, `windowsPhone`, `android`, `androidForWork`, `mac`, `linux`, `unknownFutureValue`. |
| templateType | [enrollmentNotificationTemplateType](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentnotificationtemplatetype?view=graph-rest-beta) | Template type of the Enrollment Notification. Possible values are: `email`, `push`, `unknownFutureValue`. |
| notificationMessageTemplateId | Guid | Notification Message Template Id |
| notificationTemplates | String collection | The list of notification data - <TemplateType>\_<NotificationMessageTemplateId> |
| brandingOptions | [enrollmentNotificationBrandingOptions](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentnotificationbrandingoptions?view=graph-rest-beta) | Branding Options for the Enrollment Notification. Possible values are: `none`, `includeCompanyLogo`, `includeCompanyName`, `includeContactInformation`, `includeCompanyPortalLink`, `includeDeviceDetails`, `unknownFutureValue`. |
| defaultLocale | String | DefaultLocale for the Enrollment Notification |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-beta) collection | The list of group assignments for the device configuration profile Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceEnrollmentNotificationConfiguration",
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
  "platformType": "String",
  "templateType": "String",
  "notificationMessageTemplateId": "Guid",
  "notificationTemplates": [
    "String"
  ],
  "brandingOptions": "String",
  "defaultLocale": "String"
}
```
