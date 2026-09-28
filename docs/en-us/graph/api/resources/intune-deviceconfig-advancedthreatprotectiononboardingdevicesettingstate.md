<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# advancedThreatProtectionOnboardingDeviceSettingState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

ATP onboarding State for a given device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List advancedThreatProtectionOnboardingDeviceSettingStates](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate-list?view=graph-rest-beta) | [advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate?view=graph-rest-beta) collection | List properties and relationships of the [advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate?view=graph-rest-beta) objects. |
| [Get advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate-get?view=graph-rest-beta) | [advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate?view=graph-rest-beta) | Read properties and relationships of the [advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate?view=graph-rest-beta) object. |
| [Create advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate-create?view=graph-rest-beta) | [advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate?view=graph-rest-beta) | Create a new [advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate?view=graph-rest-beta) object. |
| [Delete advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate-delete?view=graph-rest-beta) | None | Deletes a [advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate?view=graph-rest-beta). |
| [Update advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate-update?view=graph-rest-beta) | [advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate?view=graph-rest-beta) | Update the properties of a [advancedThreatProtectionOnboardingDeviceSettingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-advancedthreatprotectiononboardingdevicesettingstate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity |
| platformType | [deviceType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicetype?view=graph-rest-beta) | Device platform type. Possible values are: `desktop`, `windowsRT`, `winMO6`, `nokia`, `windowsPhone`, `mac`, `winCE`, `winEmbedded`, `iPhone`, `iPad`, `iPod`, `android`, `iSocConsumer`, `unix`, `macMDM`, `holoLens`, `surfaceHub`, `androidForWork`, `androidEnterprise`, `windows10x`, `androidnGMS`, `chromeOS`, `linux`, `visionOS`, `tvOS`, `blackberry`, `palm`, `unknown`, `cloudPC`. |
| setting | String | The setting class name and property name. |
| settingName | String | The Setting Name that is being reported |
| deviceId | String | The Device Id that is being reported |
| deviceName | String | The Device Name that is being reported |
| userId | String | The user Id that is being reported |
| userEmail | String | The User email address that is being reported |
| userName | String | The User Name that is being reported |
| userPrincipalName | String | The User PrincipalName that is being reported |
| deviceModel | String | The device model that is being reported |
| state | [complianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-compliancestatus?view=graph-rest-beta) | The compliance state of the setting. Possible values are: `unknown`, `notApplicable`, `compliant`, `remediated`, `nonCompliant`, `error`, `conflict`, `notAssigned`. |
| complianceGracePeriodExpirationDateTime | DateTimeOffset | The DateTime when device compliance grace period expires |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.advancedThreatProtectionOnboardingDeviceSettingState",
  "id": "String (identifier)",
  "platformType": "String",
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
