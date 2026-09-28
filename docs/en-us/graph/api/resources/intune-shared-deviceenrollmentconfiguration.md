<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceEnrollmentConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The Base Class of Device Enrollment Configuration

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceEnrollmentConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-shared-deviceenrollmentconfiguration-list?view=graph-rest-beta) | [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) objects. |
| [Get deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-shared-deviceenrollmentconfiguration-get?view=graph-rest-beta) | [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) | Read properties and relationships of the [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) object. |
| **Onboarding** |  |  |
| [setPriority action](https://learn.microsoft.com/en-us/graph/api/intune-shared-deviceenrollmentconfiguration-setpriority?view=graph-rest-beta) | None |  |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-shared-deviceenrollmentconfiguration-assign?view=graph-rest-beta) | None |  |
| **Policy Set** |  |  |
| [hasPayloadLinks action](https://learn.microsoft.com/en-us/graph/api/intune-shared-deviceenrollmentconfiguration-haspayloadlinks?view=graph-rest-beta) | [hasPayloadLinkResultItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-haspayloadlinkresultitem?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the account |
| displayName | String | The display name of the device enrollment configuration |
| description | String | The description of the device enrollment configuration |
| priority | Int32 | Priority is used when a user exists in multiple groups that are assigned enrollment configuration. Users are subject only to the configuration with the lowest priority value. |
| createdDateTime | DateTimeOffset | Created date time in UTC of the device enrollment configuration |
| lastModifiedDateTime | DateTimeOffset | Last modified date time in UTC of the device enrollment configuration |
| version | Int32 | The version of the device enrollment configuration |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| **Onboarding** |  |  |
| assignments | [enrollmentConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-enrollmentconfigurationassignment?view=graph-rest-beta) collection | The list of group assignments for the device configuration profile |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceEnrollmentConfiguration",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "priority": 1024,
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "version": 1024
}
```
