<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingmapping?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicySettingMapping resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The Group Policy setting to MDM/Intune mapping.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicySettingMappings](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicysettingmapping-list?view=graph-rest-beta) | [groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingmapping?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingmapping?view=graph-rest-beta) objects. |
| [Get groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicysettingmapping-get?view=graph-rest-beta) | [groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingmapping?view=graph-rest-beta) | Read properties and relationships of the [groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingmapping?view=graph-rest-beta) object. |
| [Create groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicysettingmapping-create?view=graph-rest-beta) | [groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingmapping?view=graph-rest-beta) | Create a new [groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingmapping?view=graph-rest-beta) object. |
| [Delete groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicysettingmapping-delete?view=graph-rest-beta) | None | Deletes a [groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingmapping?view=graph-rest-beta). |
| [Update groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicysettingmapping-update?view=graph-rest-beta) | [groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingmapping?view=graph-rest-beta) | Update the properties of a [groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingmapping?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String |  |
| parentId | String | Parent Id of the group policy setting. |
| childIdList | String collection | List of Child Ids of the group policy setting. |
| settingName | String | The name of this group policy setting. |
| settingValue | String | The value of this group policy setting. |
| settingValueType | String | The value type of this group policy setting. |
| settingDisplayName | String | The display name of this group policy setting. |
| settingDisplayValue | String | The display value of this group policy setting. |
| settingDisplayValueType | String | The display value type of this group policy setting. |
| settingValueDisplayUnits | String | The display units of this group policy setting value |
| settingCategory | String | The category the group policy setting is in. |
| mdmCspName | String | The CSP name this group policy setting maps to. |
| mdmSettingUri | String | The MDM CSP URI this group policy setting maps to. |
| mdmMinimumOSVersion | Int32 | The minimum OS version this mdm setting supports. |
| settingType | [groupPolicySettingType](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingtype?view=graph-rest-beta) | The setting type \(security or admx\) of the Group Policy. Possible values are: `unknown`, `policy`, `account`, `securityOptions`, `userRightsAssignment`, `auditSetting`, `windowsFirewallSettings`, `appLockerRuleCollection`, `dataSourcesSettings`, `devicesSettings`, `driveMapSettings`, `environmentVariables`, `filesSettings`, `folderOptions`, `folders`, `iniFiles`, `internetOptions`, `localUsersAndGroups`, `networkOptions`, `networkShares`, `ntServices`, `powerOptions`, `printers`, `regionalOptionsSettings`, `registrySettings`, `scheduledTasks`, `shortcutSettings`, `startMenuSettings`. |
| isMdmSupported | Boolean | Indicates if the setting is supported by Intune or not |
| mdmSupportedState | [mdmSupportedState](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-mdmsupportedstate?view=graph-rest-beta) | Indicates if the setting is supported in Mdm or not. Possible values are: `unknown`, `supported`, `unsupported`, `deprecated`. |
| settingScope | [groupPolicySettingScope](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingscope?view=graph-rest-beta) | The scope of the setting. Possible values are: `unknown`, `device`, `user`. |
| intuneSettingUriList | String collection | The list of Intune Setting URIs this group policy setting maps to |
| intuneSettingDefinitionId | String | The Intune Setting Definition Id |
| admxSettingDefinitionId | String | Admx Group Policy Id |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicySettingMapping",
  "id": "String (identifier)",
  "parentId": "String",
  "childIdList": [
    "String"
  ],
  "settingName": "String",
  "settingValue": "String",
  "settingValueType": "String",
  "settingDisplayName": "String",
  "settingDisplayValue": "String",
  "settingDisplayValueType": "String",
  "settingValueDisplayUnits": "String",
  "settingCategory": "String",
  "mdmCspName": "String",
  "mdmSettingUri": "String",
  "mdmMinimumOSVersion": 1024,
  "settingType": "String",
  "isMdmSupported": true,
  "mdmSupportedState": "String",
  "settingScope": "String",
  "intuneSettingUriList": [
    "String"
  ],
  "intuneSettingDefinitionId": "String",
  "admxSettingDefinitionId": "String"
}
```
