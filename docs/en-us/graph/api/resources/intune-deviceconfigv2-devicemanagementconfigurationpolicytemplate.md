<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-12 -->

# deviceManagementConfigurationPolicyTemplate resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device Management Configuration Policy Template

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementConfigurationPolicyTemplates](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate-list?view=graph-rest-beta) | [deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate?view=graph-rest-beta) objects. |
| [Get deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate-get?view=graph-rest-beta) | [deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate?view=graph-rest-beta) object. |
| [Create deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate-create?view=graph-rest-beta) | [deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate?view=graph-rest-beta) | Create a new [deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate?view=graph-rest-beta) object. |
| [Delete deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate?view=graph-rest-beta). |
| [Update deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate-update?view=graph-rest-beta) | [deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate?view=graph-rest-beta) | Update the properties of a [deviceManagementConfigurationPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the template document, composed of BaseId and Version. Automatically generated. |
| baseId | String | Template base identifier |
| version | Int32 | Template version. Valid values 1 to 2147483647. This property is read-only. |
| displayName | String | Template display name |
| description | String | Template description |
| displayVersion | String | Description of template version |
| lifecycleState | [deviceManagementTemplateLifecycleState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementtemplatelifecyclestate?view=graph-rest-beta) | Indicate current lifecycle state of template. The possible values are: `invalid`, `draft`, `active`, `superseded`, `deprecated`, `retired`. |
| platforms | [deviceManagementConfigurationPlatforms](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationplatforms?view=graph-rest-beta) | Platforms for this template. The possible values are: `none`, `android`, `iOS`, `macOS`, `windows10X`, `windows10`, `linux`, `unknownFutureValue`, `androidEnterprise`, `aosp`, `visionOS`, `tvOS`. |
| technologies | [deviceManagementConfigurationTechnologies](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationtechnologies?view=graph-rest-beta) | Technologies for this template. The possible values are: `none`, `mdm`, `windows10XManagement`, `configManager`, `appleRemoteManagement`, `microsoftSense`, `exchangeOnline`, `mobileApplicationManagement`, `linuxMdm`, `extensibility`, `enrollment`, `endpointPrivilegeManagement`, `unknownFutureValue`, `windowsOsRecovery`, `android`. |
| templateFamily | [deviceManagementConfigurationTemplateFamily](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationtemplatefamily?view=graph-rest-beta) | TemplateFamily for this template. The possible values are: `none`, `endpointSecurityAntivirus`, `endpointSecurityDiskEncryption`, `endpointSecurityFirewall`, `endpointSecurityEndpointDetectionAndResponse`, `endpointSecurityAttackSurfaceReduction`, `endpointSecurityAccountProtection`, `endpointSecurityApplicationControl`, `endpointSecurityEndpointPrivilegeManagement`, `enrollmentConfiguration`, `appQuietTime`, `baseline`, `unknownFutureValue`, `deviceConfigurationScripts`, `deviceConfigurationPolicies`, `windowsOsRecoveryPolicies`, `companyPortal`. |
| allowUnmanagedSettings | Boolean | Allow unmanaged setting templates |
| settingTemplateCount | Int32 | Number of setting templates. Valid values 0 to 2147483647. This property is read-only. |
| disableEntraGroupPolicyAssignment | Boolean | Indicates whether assignments to Entra security groups is disabled |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| settingTemplates | [deviceManagementConfigurationSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingtemplate?view=graph-rest-beta) collection | Setting templates |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationPolicyTemplate",
  "id": "String (identifier)",
  "baseId": "String",
  "version": 1024,
  "displayName": "String",
  "description": "String",
  "displayVersion": "String",
  "lifecycleState": "String",
  "platforms": "String",
  "technologies": "String",
  "templateFamily": "String",
  "allowUnmanagedSettings": true,
  "settingTemplateCount": 1024,
  "disableEntraGroupPolicyAssignment": true
}
```
