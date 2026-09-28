<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10secureassessmentconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-13 -->

# windows10SecureAssessmentConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the secureAssessment resource.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windows10SecureAssessmentConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10secureassessmentconfiguration-list?view=graph-rest-1.0) | [windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10secureassessmentconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10secureassessmentconfiguration?view=graph-rest-1.0) objects. |
| [Get windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10secureassessmentconfiguration-get?view=graph-rest-1.0) | [windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10secureassessmentconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10secureassessmentconfiguration?view=graph-rest-1.0) object. |
| [Create windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10secureassessmentconfiguration-create?view=graph-rest-1.0) | [windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10secureassessmentconfiguration?view=graph-rest-1.0) | Create a new [windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10secureassessmentconfiguration?view=graph-rest-1.0) object. |
| [Delete windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10secureassessmentconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10secureassessmentconfiguration?view=graph-rest-1.0). |
| [Update windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10secureassessmentconfiguration-update?view=graph-rest-1.0) | [windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10secureassessmentconfiguration?view=graph-rest-1.0) | Update the properties of a [windows10SecureAssessmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10secureassessmentconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| launchUri | String | Url link to an assessment that's automatically loaded when the secure assessment browser is launched. It has to be a valid Url \(http\[s\]://msdn.microsoft.com/\). |
| configurationAccount | String | The account used to configure the Windows device for taking the test. The user can be a domain account \(domain\\user\), an AAD account \(username@tenant.com\) or a local account \(username\). |
| allowPrinting | Boolean | Indicates whether or not to allow the app from printing during the test. |
| allowScreenCapture | Boolean | Indicates whether or not to allow screen capture capability during a test. |
| allowTextSuggestion | Boolean | Indicates whether or not to allow text suggestions during the test. |

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
  "@odata.type": "#microsoft.graph.windows10SecureAssessmentConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "launchUri": "String",
  "configurationAccount": "String",
  "allowPrinting": true,
  "allowScreenCapture": true,
  "allowTextSuggestion": true
}
```
