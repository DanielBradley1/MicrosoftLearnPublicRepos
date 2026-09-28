<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# deviceConfigurationDeviceStatus resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Support for this Entity is being deprecated starting May 2026 & will no longer be supported.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceConfigurationDeviceStatuses](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationdevicestatus-list?view=graph-rest-1.0) | [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0) collection | List properties and relationships of the [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0) objects. |
| [Get deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationdevicestatus-get?view=graph-rest-1.0) | [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0) | Read properties and relationships of the [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0) object. |
| [Create deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationdevicestatus-create?view=graph-rest-1.0) | [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0) | Create a new [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0) object. |
| [Delete deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationdevicestatus-delete?view=graph-rest-1.0) | None | Deletes a [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0). |
| [Update deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationdevicestatus-update?view=graph-rest-1.0) | [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0) | Update the properties of a [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| deviceDisplayName | String | Device name of the DevicePolicyStatus. |
| userName | String | The User Name that is being reported |
| deviceModel | String | The device model that is being reported |
| complianceGracePeriodExpirationDateTime | DateTimeOffset | The DateTime when device compliance grace period expires |
| status | [complianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-compliancestatus?view=graph-rest-1.0) | Compliance status of the policy report. The possible values are: `unknown`, `notApplicable`, `compliant`, `remediated`, `nonCompliant`, `error`, `conflict`, `notAssigned`. |
| lastReportedDateTime | DateTimeOffset | Last modified date time of the policy report. |
| userPrincipalName | String | UserPrincipalName. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceConfigurationDeviceStatus",
  "id": "String (identifier)",
  "deviceDisplayName": "String",
  "userName": "String",
  "deviceModel": "String",
  "complianceGracePeriodExpirationDateTime": "String (timestamp)",
  "status": "String",
  "lastReportedDateTime": "String (timestamp)",
  "userPrincipalName": "String"
}
```
