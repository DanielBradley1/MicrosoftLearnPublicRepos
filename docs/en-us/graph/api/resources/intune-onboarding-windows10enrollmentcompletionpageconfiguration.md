<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windows10enrollmentcompletionpageconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# windows10EnrollmentCompletionPageConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows 10 Enrollment Status Page Configuration

Inherits from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windows10EnrollmentCompletionPageConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-windows10enrollmentcompletionpageconfiguration-list?view=graph-rest-1.0) | [windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windows10enrollmentcompletionpageconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windows10enrollmentcompletionpageconfiguration?view=graph-rest-1.0) objects. |
| [Get windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-windows10enrollmentcompletionpageconfiguration-get?view=graph-rest-1.0) | [windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windows10enrollmentcompletionpageconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windows10enrollmentcompletionpageconfiguration?view=graph-rest-1.0) object. |
| [Create windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-windows10enrollmentcompletionpageconfiguration-create?view=graph-rest-1.0) | [windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windows10enrollmentcompletionpageconfiguration?view=graph-rest-1.0) | Create a new [windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windows10enrollmentcompletionpageconfiguration?view=graph-rest-1.0) object. |
| [Delete windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-windows10enrollmentcompletionpageconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windows10enrollmentcompletionpageconfiguration?view=graph-rest-1.0). |
| [Update windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-windows10enrollmentcompletionpageconfiguration-update?view=graph-rest-1.0) | [windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windows10enrollmentcompletionpageconfiguration?view=graph-rest-1.0) | Update the properties of a [windows10EnrollmentCompletionPageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windows10enrollmentcompletionpageconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the account Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| displayName | String | The display name of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| description | String | The description of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| priority | Int32 | Priority is used when a user exists in multiple groups that are assigned enrollment configuration. Users are subject only to the configuration with the lowest priority value. Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | Created date time in UTC of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | Last modified date time in UTC of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| version | Int32 | The version of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |
| allowNonBlockingAppInstallation | Boolean | When TRUE, ESP \(Enrollment Status Page\) installs all required apps targeted during technician phase and ignores any failures for non-blocking apps. When FALSE, ESP fails on any error during app install. The default is false. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-1.0) collection | The list of group assignments for the device configuration profile Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfiguration?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windows10EnrollmentCompletionPageConfiguration",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "priority": 1024,
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "version": 1024,
  "allowNonBlockingAppInstallation": true
}
```
