<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationstringsettingvaluetemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationStringSettingValueTemplate resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

String Setting Value Template

Inherits from [deviceManagementConfigurationSimpleSettingValueTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsimplesettingvaluetemplate?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| settingValueTemplateId | String | Setting Value Template Id Inherited from [deviceManagementConfigurationSimpleSettingValueTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsimplesettingvaluetemplate?view=graph-rest-beta) |
| defaultValue | [deviceManagementConfigurationStringSettingValueDefaultTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationstringsettingvaluedefaulttemplate?view=graph-rest-beta) | String Setting Value Default Template. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationStringSettingValueTemplate",
  "settingValueTemplateId": "String",
  "defaultValue": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationStringSettingValueConstantDefaultTemplate",
    "constantValue": "String"
  }
}
```
