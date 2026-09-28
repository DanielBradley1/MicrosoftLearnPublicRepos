<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruledevicemode?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# deviceManagementApplicabilityRuleDeviceMode resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceMode | [windows10DeviceModeType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10devicemodetype?view=graph-rest-beta) | Applicability rule for device mode. Possible values are: `standardConfiguration`, `sModeConfiguration`. |
| name | String | Name for object. |
| ruleType | [deviceManagementApplicabilityRuleType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruletype?view=graph-rest-beta) | Applicability Rule type. Possible values are: `include`, `exclude`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementApplicabilityRuleDeviceMode",
  "deviceMode": "String",
  "name": "String",
  "ruleType": "String"
}
```
