<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingvaluetemplatereference?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationSettingValueTemplateReference resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Setting value template reference information

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| settingValueTemplateId | String | Setting value template id |
| useTemplateDefault | Boolean | Indicates whether to update policy setting value to match template setting default value |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
  "settingValueTemplateId": "String",
  "useTemplateDefault": true
}
```
