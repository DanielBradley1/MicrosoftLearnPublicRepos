<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingvalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationSettingValue resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Setting value

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| settingValueTemplateReference | [deviceManagementConfigurationSettingValueTemplateReference](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingvaluetemplatereference?view=graph-rest-beta) | Setting value template reference |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSettingValue",
  "settingValueTemplateReference": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
    "settingValueTemplateId": "String",
    "useTemplateDefault": true
  }
}
```
