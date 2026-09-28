<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10teamgeneralconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# windows10TeamGeneralConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the windows10TeamGeneralConfiguration resource.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windows10TeamGeneralConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10teamgeneralconfiguration-list?view=graph-rest-1.0) | [windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10teamgeneralconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10teamgeneralconfiguration?view=graph-rest-1.0) objects. |
| [Get windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10teamgeneralconfiguration-get?view=graph-rest-1.0) | [windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10teamgeneralconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10teamgeneralconfiguration?view=graph-rest-1.0) object. |
| [Create windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10teamgeneralconfiguration-create?view=graph-rest-1.0) | [windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10teamgeneralconfiguration?view=graph-rest-1.0) | Create a new [windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10teamgeneralconfiguration?view=graph-rest-1.0) object. |
| [Delete windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10teamgeneralconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10teamgeneralconfiguration?view=graph-rest-1.0). |
| [Update windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10teamgeneralconfiguration-update?view=graph-rest-1.0) | [windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10teamgeneralconfiguration?view=graph-rest-1.0) | Update the properties of a [windows10TeamGeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10teamgeneralconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| azureOperationalInsightsBlockTelemetry | Boolean | Indicates whether or not to Block Azure Operational Insights. |
| azureOperationalInsightsWorkspaceId | String | The Azure Operational Insights workspace id. |
| azureOperationalInsightsWorkspaceKey | String | The Azure Operational Insights Workspace key. |
| connectAppBlockAutoLaunch | Boolean | Specifies whether to automatically launch the Connect app whenever a projection is initiated. |
| maintenanceWindowBlocked | Boolean | Indicates whether or not to Block setting a maintenance window for device updates. |
| maintenanceWindowDurationInHours | Int32 | Maintenance window duration for device updates. Valid values 0 to 5 |
| maintenanceWindowStartTime | TimeOfDay | Maintenance window start time for device updates. |
| miracastChannel | [miracastChannel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-miracastchannel?view=graph-rest-1.0) | The channel. The possible values are: `userDefined`, `one`, `two`, `three`, `four`, `five`, `six`, `seven`, `eight`, `nine`, `ten`, `eleven`, `thirtySix`, `forty`, `fortyFour`, `fortyEight`, `oneHundredFortyNine`, `oneHundredFiftyThree`, `oneHundredFiftySeven`, `oneHundredSixtyOne`, `oneHundredSixtyFive`. |
| miracastBlocked | Boolean | Indicates whether or not to Block wireless projection. |
| miracastRequirePin | Boolean | Indicates whether or not to require a pin for wireless projection. |
| settingsBlockMyMeetingsAndFiles | Boolean | Specifies whether to disable the "My meetings and files" feature in the Start menu, which shows the signed-in user's meetings and files from Office 365. |
| settingsBlockSessionResume | Boolean | Specifies whether to allow the ability to resume a session when the session times out. |
| settingsBlockSigninSuggestions | Boolean | Specifies whether to disable auto-populating of the sign-in dialog with invitees from scheduled meetings. |
| settingsDefaultVolume | Int32 | Specifies the default volume value for a new session. Permitted values are 0-100. The default is 45. Valid values 0 to 100 |
| settingsScreenTimeoutInMinutes | Int32 | Specifies the number of minutes until the Hub screen turns off. |
| settingsSessionTimeoutInMinutes | Int32 | Specifies the number of minutes until the session times out. |
| settingsSleepTimeoutInMinutes | Int32 | Specifies the number of minutes until the Hub enters sleep mode. |
| welcomeScreenBlockAutomaticWakeUp | Boolean | Indicates whether or not to Block the welcome screen from waking up automatically when someone enters the room. |
| welcomeScreenBackgroundImageUrl | String | The welcome screen background image URL. The URL must use the HTTPS protocol and return a PNG image. |
| welcomeScreenMeetingInformation | [welcomeScreenMeetingInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-welcomescreenmeetinginformation?view=graph-rest-1.0) | The welcome screen meeting information shown. The possible values are: `userDefined`, `showOrganizerAndTimeOnly`, `showOrganizerAndTimeAndSubject`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0) collection | The list of assignments for the device configuration profile. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| deviceStatuses | [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0) collection | Device configuration installation status by device. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| userStatuses | [deviceConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatus?view=graph-rest-1.0) collection | Device configuration installation status by user. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| deviceStatusOverview | [deviceConfigurationDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdeviceoverview?view=graph-rest-1.0) | Device Configuration devices status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| userStatusOverview | [deviceConfigurationUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuseroverview?view=graph-rest-1.0) | Device Configuration users status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| deviceSettingStateSummaries | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) collection | Device Configuration Setting State Device Summary Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windows10TeamGeneralConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "azureOperationalInsightsBlockTelemetry": true,
  "azureOperationalInsightsWorkspaceId": "String",
  "azureOperationalInsightsWorkspaceKey": "String",
  "connectAppBlockAutoLaunch": true,
  "maintenanceWindowBlocked": true,
  "maintenanceWindowDurationInHours": 1024,
  "maintenanceWindowStartTime": "String (time of day)",
  "miracastChannel": "String",
  "miracastBlocked": true,
  "miracastRequirePin": true,
  "settingsBlockMyMeetingsAndFiles": true,
  "settingsBlockSessionResume": true,
  "settingsBlockSigninSuggestions": true,
  "settingsDefaultVolume": 1024,
  "settingsScreenTimeoutInMinutes": 1024,
  "settingsSessionTimeoutInMinutes": 1024,
  "settingsSleepTimeoutInMinutes": 1024,
  "welcomeScreenBlockAutomaticWakeUp": true,
  "welcomeScreenBackgroundImageUrl": "String",
  "welcomeScreenMeetingInformation": "String"
}
```
