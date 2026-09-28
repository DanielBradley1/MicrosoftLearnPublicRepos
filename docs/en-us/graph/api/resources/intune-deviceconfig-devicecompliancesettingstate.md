<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancesettingstate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceComplianceSettingState resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device compliance setting State for a given device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceComplianceSettingStates](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecompliancesettingstate-list?view=graph-rest-1.0) | [deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancesettingstate?view=graph-rest-1.0) collection | List properties and relationships of the [deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancesettingstate?view=graph-rest-1.0) objects. |
| [Get deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecompliancesettingstate-get?view=graph-rest-1.0) | [deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancesettingstate?view=graph-rest-1.0) | Read properties and relationships of the [deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancesettingstate?view=graph-rest-1.0) object. |
| [Create deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecompliancesettingstate-create?view=graph-rest-1.0) | [deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancesettingstate?view=graph-rest-1.0) | Create a new [deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancesettingstate?view=graph-rest-1.0) object. |
| [Delete deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecompliancesettingstate-delete?view=graph-rest-1.0) | None | Deletes a [deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancesettingstate?view=graph-rest-1.0). |
| [Update deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecompliancesettingstate-update?view=graph-rest-1.0) | [deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancesettingstate?view=graph-rest-1.0) | Update the properties of a [deviceComplianceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancesettingstate?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity |
| setting | String | The setting class name and property name. |
| settingName | String | The Setting Name that is being reported |
| deviceId | String | The Device Id that is being reported |
| deviceName | String | The Device Name that is being reported |
| userId | String | The user Id that is being reported |
| userEmail | String | The User email address that is being reported |
| userName | String | The User Name that is being reported |
| userPrincipalName | String | The User PrincipalName that is being reported |
| deviceModel | String | The device model that is being reported |
| state | [complianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-compliancestatus?view=graph-rest-1.0) | The compliance state of the setting. The possible values are: `unknown`, `notApplicable`, `compliant`, `remediated`, `nonCompliant`, `error`, `conflict`, `notAssigned`. |
| complianceGracePeriodExpirationDateTime | DateTimeOffset | The DateTime when device compliance grace period expires |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceComplianceSettingState",
  "id": "String (identifier)",
  "setting": "String",
  "settingName": "String",
  "deviceId": "String",
  "deviceName": "String",
  "userId": "String",
  "userEmail": "String",
  "userName": "String",
  "userPrincipalName": "String",
  "deviceModel": "String",
  "state": "String",
  "complianceGracePeriodExpirationDateTime": "String (timestamp)"
}
```
