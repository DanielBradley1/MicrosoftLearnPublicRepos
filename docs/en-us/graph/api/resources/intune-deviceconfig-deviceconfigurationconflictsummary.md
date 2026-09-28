<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceConfigurationConflictSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Conflict summary for a set of device configuration policies.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceConfigurationConflictSummaries](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationconflictsummary-list?view=graph-rest-beta) | [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta) collection | List properties and relationships of the [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta) objects. |
| [Get deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationconflictsummary-get?view=graph-rest-beta) | [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta) | Read properties and relationships of the [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta) object. |
| [Create deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationconflictsummary-create?view=graph-rest-beta) | [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta) | Create a new [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta) object. |
| [Delete deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationconflictsummary-delete?view=graph-rest-beta) | None | Deletes a [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta). |
| [Update deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationconflictsummary-update?view=graph-rest-beta) | [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta) | Update the properties of a [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conflictingDeviceConfigurations | [settingSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingsource?view=graph-rest-beta) collection | The set of policies in conflict with the given setting |
| id | String | The id for this set of conflicting policies. This id is the ids of all the policies in ConflictingDeviceConfigurations in lexicographical order separated by underscores. |
| contributingSettings | String collection | The set of settings in conflict with the given policies |
| deviceCheckinsImpacted | Int32 | The count of checkins impacted by the conflicting policies and settings |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceConfigurationConflictSummary",
  "conflictingDeviceConfigurations": [
    {
      "@odata.type": "microsoft.graph.settingSource",
      "id": "String",
      "displayName": "String",
      "sourceType": "String"
    }
  ],
  "id": "String (identifier)",
  "contributingSettings": [
    "String"
  ],
  "deviceCheckinsImpacted": 1024
}
```
