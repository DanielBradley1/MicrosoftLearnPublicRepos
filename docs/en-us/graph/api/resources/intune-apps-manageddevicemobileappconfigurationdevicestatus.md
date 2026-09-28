<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedDeviceMobileAppConfigurationDeviceStatus resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties, inherited properties and actions for an MDM mobile app configuration status for a device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedDeviceMobileAppConfigurationDeviceStatuses](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationdevicestatus-list?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-1.0) collection | List properties and relationships of the [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-1.0) objects. |
| [Get managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationdevicestatus-get?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-1.0) | Read properties and relationships of the [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-1.0) object. |
| [Create managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationdevicestatus-create?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-1.0) | Create a new [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-1.0) object. |
| [Delete managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationdevicestatus-delete?view=graph-rest-1.0) | None | Deletes a [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-1.0). |
| [Update managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationdevicestatus-update?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-1.0) | Update the properties of a [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-1.0) object. |

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
  "@odata.type": "#microsoft.graph.managedDeviceMobileAppConfigurationDeviceStatus",
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
