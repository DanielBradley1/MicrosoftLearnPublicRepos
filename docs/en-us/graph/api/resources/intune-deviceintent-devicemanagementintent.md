<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementIntent resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that represents an intent to apply settings to a device

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementIntents](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintent-list?view=graph-rest-beta) | [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta) objects. |
| [Get deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintent-get?view=graph-rest-beta) | [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta) object. |
| [Create deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintent-create?view=graph-rest-beta) | [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta) | Create a new [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta) object. |
| [Delete deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintent-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta). |
| [Update deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintent-update?view=graph-rest-beta) | [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta) | Update the properties of a [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta) object. |
| [updateSettings action](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintent-updatesettings?view=graph-rest-beta) | None |  |
| [migrateToTemplate action](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintent-migratetotemplate?view=graph-rest-beta) | None |  |
| [createCopy action](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintent-createcopy?view=graph-rest-beta) | [deviceManagementIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintent?view=graph-rest-beta) |  |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintent-assign?view=graph-rest-beta) | None |  |
| [compare function](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintent-compare?view=graph-rest-beta) | [deviceManagementSettingComparison](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingcomparison?view=graph-rest-beta) collection |  |
| [getCustomizedSettings function](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintent-getcustomizedsettings?view=graph-rest-beta) | [deviceManagementIntentCustomizedSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentcustomizedsetting?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The intent ID |
| displayName | String | The user given display name |
| description | String | The user given description |
| isAssigned | Boolean | Signifies whether or not the intent is assigned to users |
| isMigratingToConfigurationPolicy | Boolean | Signifies whether or not the intent is being migrated to the configurationPolicies endpoint |
| lastModifiedDateTime | DateTimeOffset | When the intent was last modified |
| templateId | String | The ID of the template this intent was created from \(if any\) |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| settings | [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) collection | Collection of all settings to be applied |
| categories | [deviceManagementIntentSettingCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentsettingcategory?view=graph-rest-beta) collection | Collection of setting categories within the intent |
| assignments | [deviceManagementIntentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentassignment?view=graph-rest-beta) collection | Collection of assignments |
| deviceSettingStateSummaries | [deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicesettingstatesummary?view=graph-rest-beta) collection | Collection of settings and their states and counts of devices that belong to corresponding state for all settings within the intent |
| deviceStates | [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta) collection | Collection of states of all devices that the intent is applied to |
| userStates | [deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstate?view=graph-rest-beta) collection | Collection of states of all users that the intent is applied to |
| deviceStateSummary | [deviceManagementIntentDeviceStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestatesummary?view=graph-rest-beta) | A summary of device states and counts of devices that belong to corresponding state for all devices that the intent is applied to |
| userStateSummary | [deviceManagementIntentUserStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstatesummary?view=graph-rest-beta) | A summary of user states and counts of users that belong to corresponding state for all users that the intent is applied to |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementIntent",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "isAssigned": true,
  "isMigratingToConfigurationPolicy": true,
  "lastModifiedDateTime": "String (timestamp)",
  "templateId": "String",
  "roleScopeTagIds": [
    "String"
  ]
}
```
