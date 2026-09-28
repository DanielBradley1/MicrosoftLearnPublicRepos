<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsAutopilotSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The windowsAutopilotSettings resource represents a Windows Autopilot Account to sync data with Windows device data sync service.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get windowsAutopilotSettings](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotsettings-get?view=graph-rest-beta) | [windowsAutopilotSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotsettings?view=graph-rest-beta) | Read properties and relationships of the [windowsAutopilotSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotsettings?view=graph-rest-beta) object. |
| [Update windowsAutopilotSettings](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotsettings-update?view=graph-rest-beta) | [windowsAutopilotSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotsettings?view=graph-rest-beta) | Update the properties of a [windowsAutopilotSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotsettings?view=graph-rest-beta) object. |
| [sync action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotsettings-sync?view=graph-rest-beta) | None | Initiates a sync of all AutoPilot registered devices from Store for Business and other portals. If the sync successful, this action returns a 204 No Content response code. If a sync is already in progress, the action returns a 409 Conflict response code. If this sync action is called within 10 minutes of the previous sync, the action returns a 429 Too Many Requests response code. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object |
| lastSyncDateTime | DateTimeOffset | Last data sync date time with DDS service. |
| lastManualSyncTriggerDateTime | DateTimeOffset | Last data sync date time with DDS service. |
| syncStatus | [windowsAutopilotSyncStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotsyncstatus?view=graph-rest-beta) | Indicates the status of sync with Device data sync \(DDS\) service. Possible values are: `unknown`, `inProgress`, `completed`, `failed`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsAutopilotSettings",
  "id": "String (identifier)",
  "lastSyncDateTime": "String (timestamp)",
  "lastManualSyncTriggerDateTime": "String (timestamp)",
  "syncStatus": "String"
}
```
