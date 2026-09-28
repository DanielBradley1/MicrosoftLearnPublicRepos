<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangedeviceclass?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# deviceManagementExchangeDeviceClass resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device Class in Exchange.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name of the device class which will be impacted by this rule. |
| type | [deviceManagementExchangeAccessRuleType](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeaccessruletype?view=graph-rest-beta) | Type of device which is impacted by this rule e.g. Model, Family. Possible values are: `family`, `model`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementExchangeDeviceClass",
  "name": "String",
  "type": "String"
}
```
