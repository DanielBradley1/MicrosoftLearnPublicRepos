<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# securityConfigurationTask resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A security configuration task.

Inherits from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List securityConfigurationTasks](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-securityconfigurationtask-list?view=graph-rest-beta) | [securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask?view=graph-rest-beta) collection | List properties and relationships of the [securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask?view=graph-rest-beta) objects. |
| [Get securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-securityconfigurationtask-get?view=graph-rest-beta) | [securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask?view=graph-rest-beta) | Read properties and relationships of the [securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask?view=graph-rest-beta) object. |
| [Create securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-securityconfigurationtask-create?view=graph-rest-beta) | [securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask?view=graph-rest-beta) | Create a new [securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask?view=graph-rest-beta) object. |
| [Delete securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-securityconfigurationtask-delete?view=graph-rest-beta) | None | Deletes a [securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask?view=graph-rest-beta). |
| [Update securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-securityconfigurationtask-update?view=graph-rest-beta) | [securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask?view=graph-rest-beta) | Update the properties of a [securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The entity key. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| displayName | String | The name. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| description | String | The description. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The created date. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| dueDateTime | DateTimeOffset | The due date. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| category | [deviceAppManagementTaskCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskcategory?view=graph-rest-beta) | The category. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta). Possible values are: `unknown`, `advancedThreatProtection`. |
| priority | [deviceAppManagementTaskPriority](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskpriority?view=graph-rest-beta) | The priority. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta). Possible values are: `none`, `high`, `low`. |
| creator | String | The email address of the creator. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| creatorNotes | String | Notes from the creator. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| assignedTo | String | The name or email of the admin this task is assigned to. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| status | [deviceAppManagementTaskStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskstatus?view=graph-rest-beta) | The status. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta). Possible values are: `unknown`, `pending`, `active`, `completed`, `rejected`. |
| endpointSecurityPolicy | [endpointSecurityConfigurationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-endpointsecurityconfigurationtype?view=graph-rest-beta) | The endpoint security policy type. Possible values are: `unknown`, `antivirus`, `diskEncryption`, `firewall`, `endpointDetectionAndResponse`, `attackSurfaceReduction`, `accountProtection`. |
| applicablePlatform | [endpointSecurityConfigurationApplicablePlatform](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-endpointsecurityconfigurationapplicableplatform?view=graph-rest-beta) | The applicable platform. Possible values are: `unknown`, `macOS`, `windows10AndLater`, `windows10AndWindowsServer`. |
| endpointSecurityPolicyProfile | [endpointSecurityConfigurationProfileType](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-endpointsecurityconfigurationprofiletype?view=graph-rest-beta) | The endpoint security policy profile. Possible values are: `unknown`, `antivirus`, `windowsSecurity`, `bitLocker`, `fileVault`, `firewall`, `firewallRules`, `endpointDetectionAndResponse`, `deviceControl`, `appAndBrowserIsolation`, `exploitProtection`, `webProtection`, `applicationControl`, `attackSurfaceReductionRules`, `accountProtection`. |
| insights | String | Information about the mitigation. |
| managedDeviceCount | Int32 | The number of vulnerable devices. |
| intendedSettings | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-keyvaluepair?view=graph-rest-beta) collection | The intended settings and their values. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| managedDevices | [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta) collection | The vulnerable managed devices. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.securityConfigurationTask",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "dueDateTime": "String (timestamp)",
  "category": "String",
  "priority": "String",
  "creator": "String",
  "creatorNotes": "String",
  "assignedTo": "String",
  "status": "String",
  "endpointSecurityPolicy": "String",
  "applicablePlatform": "String",
  "endpointSecurityPolicyProfile": "String",
  "insights": "String",
  "managedDeviceCount": 1024,
  "intendedSettings": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "String",
      "value": "String"
    }
  ]
}
```
