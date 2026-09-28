<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicesettingstatesummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementIntentDeviceSettingStateSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that represents device setting state summary for an intent

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementIntentDeviceSettingStateSummaries](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicesettingstatesummary-list?view=graph-rest-beta) | [deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicesettingstatesummary?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicesettingstatesummary?view=graph-rest-beta) objects. |
| [Get deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicesettingstatesummary-get?view=graph-rest-beta) | [deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicesettingstatesummary?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicesettingstatesummary?view=graph-rest-beta) object. |
| [Create deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicesettingstatesummary-create?view=graph-rest-beta) | [deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicesettingstatesummary?view=graph-rest-beta) | Create a new [deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicesettingstatesummary?view=graph-rest-beta) object. |
| [Delete deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicesettingstatesummary-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicesettingstatesummary?view=graph-rest-beta). |
| [Update deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicesettingstatesummary-update?view=graph-rest-beta) | [deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicesettingstatesummary?view=graph-rest-beta) | Update the properties of a [deviceManagementIntentDeviceSettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicesettingstatesummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID |
| settingName | String | Name of a setting |
| compliantCount | Int32 | Number of compliant devices |
| conflictCount | Int32 | Number of devices in conflict |
| errorCount | Int32 | Number of error devices |
| nonCompliantCount | Int32 | Number of non compliant devices |
| notApplicableCount | Int32 | Number of not applicable devices |
| remediatedCount | Int32 | Number of remediated devices |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementIntentDeviceSettingStateSummary",
  "id": "String (identifier)",
  "settingName": "String",
  "compliantCount": 1024,
  "conflictCount": 1024,
  "errorCount": 1024,
  "nonCompliantCount": 1024,
  "notApplicableCount": 1024,
  "remediatedCount": 1024
}
```
