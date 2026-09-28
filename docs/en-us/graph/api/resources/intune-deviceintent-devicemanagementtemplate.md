<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementTemplate resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that represents a defined collection of device settings

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementTemplates](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplate-list?view=graph-rest-beta) | [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) objects. |
| [Get deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplate-get?view=graph-rest-beta) | [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) object. |
| [Create deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplate-create?view=graph-rest-beta) | [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) | Create a new [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) object. |
| [Delete deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplate-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta). |
| [Update deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplate-update?view=graph-rest-beta) | [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) | Update the properties of a [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) object. |
| [createInstance action](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplate-createinstance?view=graph-rest-beta) | [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta) |  |
| [compare function](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplate-compare?view=graph-rest-beta) | [deviceManagementSettingComparison](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcomparison?view=graph-rest-beta) collection |  |
| [importOffice365DeviceConfigurationPolicies action](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementtemplate-importoffice365deviceconfigurationpolicies?view=graph-rest-beta) | [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The template ID |
| displayName | String | The template's display name |
| description | String | The template's description |
| versionInfo | String | The template's version information |
| isDeprecated | Boolean | The template is deprecated or not. Intents cannot be created from a deprecated template. |
| intentCount | Int32 | Number of Intents created from this template. |
| templateType | [deviceManagementTemplateType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatetype?view=graph-rest-beta) | The template's type. Possible values are: `securityBaseline`, `specializedDevices`, `advancedThreatProtectionSecurityBaseline`, `deviceConfiguration`, `custom`, `securityTemplate`, `microsoftEdgeSecurityBaseline`, `microsoftOffice365ProPlusSecurityBaseline`, `deviceCompliance`, `deviceConfigurationForOffice365`, `cloudPC`, `firewallSharedSettings`. |
| platformType | [policyPlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-policyplatformtype?view=graph-rest-beta) | The template's platform. Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `windows10XProfile`, `linux`, `all`. |
| templateSubtype | [deviceManagementTemplateSubtype](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesubtype?view=graph-rest-beta) | The template's subtype. Possible values are: `none`, `firewall`, `diskEncryption`, `attackSurfaceReduction`, `endpointDetectionReponse`, `accountProtection`, `antivirus`, `firewallSharedAppList`, `firewallSharedIpList`, `firewallSharedPortlist`. |
| publishedDateTime | DateTimeOffset | When the template was published |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| settings | [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) collection | Collection of all settings this template has |
| categories | [deviceManagementTemplateSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesettingcategory?view=graph-rest-beta) collection | Collection of setting categories within the template |
| migratableTo | [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) collection | Collection of templates this template can migrate to |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementTemplate",
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
