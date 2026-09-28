<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# securityBaselineTemplate resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The security baseline template of the account

Inherits from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List securityBaselineTemplates](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinetemplate-list?view=graph-rest-beta) | [securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate?view=graph-rest-beta) collection | List properties and relationships of the [securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate?view=graph-rest-beta) objects. |
| [Get securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinetemplate-get?view=graph-rest-beta) | [securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate?view=graph-rest-beta) | Read properties and relationships of the [securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate?view=graph-rest-beta) object. |
| [Create securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinetemplate-create?view=graph-rest-beta) | [securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate?view=graph-rest-beta) | Create a new [securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate?view=graph-rest-beta) object. |
| [Delete securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinetemplate-delete?view=graph-rest-beta) | None | Deletes a [securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate?view=graph-rest-beta). |
| [Update securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinetemplate-update?view=graph-rest-beta) | [securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate?view=graph-rest-beta) | Update the properties of a [securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The template ID Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| displayName | String | The template's display name Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| description | String | The template's description Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| versionInfo | String | The template's version information Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| isDeprecated | Boolean | The template is deprecated or not. Intents cannot be created from a deprecated template. Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| intentCount | Int32 | Number of Intents created from this template. Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| templateType | [deviceManagementTemplateType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatetype?view=graph-rest-beta) | The template's type. Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta). Possible values are: `securityBaseline`, `specializedDevices`, `advancedThreatProtectionSecurityBaseline`, `deviceConfiguration`, `custom`, `securityTemplate`, `microsoftEdgeSecurityBaseline`, `microsoftOffice365ProPlusSecurityBaseline`, `deviceCompliance`, `deviceConfigurationForOffice365`, `cloudPC`, `firewallSharedSettings`. |
| platformType | [policyPlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-policyplatformtype?view=graph-rest-beta) | The template's platform. Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta). Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `windows10XProfile`, `linux`, `all`. |
| templateSubtype | [deviceManagementTemplateSubtype](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesubtype?view=graph-rest-beta) | The template's subtype. Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta). Possible values are: `none`, `firewall`, `diskEncryption`, `attackSurfaceReduction`, `endpointDetectionReponse`, `accountProtection`, `antivirus`, `firewallSharedAppList`, `firewallSharedIpList`, `firewallSharedPortlist`. |
| publishedDateTime | DateTimeOffset | When the template was published Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| settings | [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) collection | Collection of all settings this template has Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| categories | [deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory?view=graph-rest-beta) collection | Collection of setting categories within the template Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| migratableTo | [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) collection | Collection of templates this template can migrate to Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| deviceStateSummary | [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) | The security baseline device state summary |
| deviceStates | [securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinedevicestate?view=graph-rest-beta) collection | The security baseline device states |
| categoryDeviceStateSummaries | [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta) collection | The security baseline per category device state summary |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.securityBaselineTemplate",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "versionInfo": "String",
  "isDeprecated": true,
  "intentCount": 1024,
  "templateType": "String",
  "platformType": "String",
  "templateSubtype": "String",
  "publishedDateTime": "String (timestamp)"
}
```
