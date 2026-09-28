<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsecretsettingvalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationSecretSettingValue resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Graph model for a secret setting value

Inherits from [deviceManagementConfigurationSimpleSettingValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsimplesettingvalue?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| settingValueTemplateReference | [deviceManagementConfigurationSettingValueTemplateReference](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingvaluetemplatereference?view=graph-rest-beta) | Setting value template reference Inherited from [deviceManagementConfigurationSettingValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingvalue?view=graph-rest-beta) |
| value | String | Value of the secret setting. |
| valueState | [deviceManagementConfigurationSecretSettingValueState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsecretsettingvaluestate?view=graph-rest-beta) | Gets or sets a value indicating the encryption state of the Value property. The possible values are: `invalid`, `notEncrypted`, `encryptedValueToken`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSecretSettingValue",
  "settingValueTemplateReference": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
    "settingValueTemplateId": "String",
    "useTemplateDefault": true
  },
  "value": "String",
  "valueState": "String"
}
```
