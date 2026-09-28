<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicemobileappconfigurationsettingstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedDeviceMobileAppConfigurationSettingState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Managed Device Mobile App Configuration Setting State for a given device.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| setting | String | The setting that is being reported |
| settingName | String | Localized/user friendly setting name that is being reported |
| instanceDisplayName | String | Name of setting instance that is being reported. |
| state | [complianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-compliancestatus?view=graph-rest-beta) | The compliance state of the setting. Possible values are: `unknown`, `notApplicable`, `compliant`, `remediated`, `nonCompliant`, `error`, `conflict`, `notAssigned`. |
| errorCode | Int64 | Error code for the setting |
| errorDescription | String | Error description |
| userId | String | UserId |
| userName | String | UserName |
| userEmail | String | UserEmail |
| userPrincipalName | String | UserPrincipalName. |
| sources | [settingSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingsource?view=graph-rest-beta) collection | Contributing policies |
| currentValue | String | Current value of setting on device |
| settingInstanceId | String | SettingInstanceId |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedDeviceMobileAppConfigurationSettingState",
  "setting": "String",
  "settingName": "String",
  "instanceDisplayName": "String",
  "state": "String",
  "errorCode": 1024,
  "errorDescription": "String",
  "userId": "String",
  "userName": "String",
  "userEmail": "String",
  "userPrincipalName": "String",
  "sources": [
    {
      "@odata.type": "microsoft.graph.settingSource",
      "id": "String",
      "displayName": "String",
      "sourceType": "String"
    }
  ],
  "currentValue": "String",
  "settingInstanceId": "String"
}
```
