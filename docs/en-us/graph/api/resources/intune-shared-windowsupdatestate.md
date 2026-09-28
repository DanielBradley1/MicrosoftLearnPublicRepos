<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsUpdateState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsUpdateStates](https://learn.microsoft.com/en-us/graph/api/intune-shared-windowsupdatestate-list?view=graph-rest-beta) | [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta) collection | List properties and relationships of the [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta) objects. |
| [Get windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/intune-shared-windowsupdatestate-get?view=graph-rest-beta) | [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta) | Read properties and relationships of the [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta) object. |
| [Create windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/intune-shared-windowsupdatestate-create?view=graph-rest-beta) | [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta) | Create a new [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta) object. |
| [Delete windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/intune-shared-windowsupdatestate-delete?view=graph-rest-beta) | None | Deletes a [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta). |
| [Update windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/intune-shared-windowsupdatestate-update?view=graph-rest-beta) | [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta) | Update the properties of a [windowsUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | This is Id of the entity. |
| deviceId | String | The id of the device. |
| userId | String | The id of the user. |
| deviceDisplayName | String | Device display name. |
| userPrincipalName | String | User principal name. |
| status | [windowsUpdateStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsupdatestatus.md?view=graph-rest-beta) | Windows udpate status. The possible values are: `upToDate`, `pendingInstallation`, `pendingReboot`, `failed`. |
| qualityUpdateVersion | String | The Quality Update Version of the device. |
| featureUpdateVersion | String | The current feature update version of the device. |
| lastScanDateTime | DateTimeOffset | The date time that the Windows Update Agent did a successful scan. |
| lastSyncDateTime | DateTimeOffset | Last date time that the device sync with with Microsoft Intune. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdateState",
  "id": "String (identifier)",
  "deviceId": "String",
  "userId": "String",
  "deviceDisplayName": "String",
  "userPrincipalName": "String",
  "status": "String",
  "qualityUpdateVersion": "String",
  "featureUpdateVersion": "String",
  "lastScanDateTime": "String (timestamp)",
  "lastSyncDateTime": "String (timestamp)"
}
```
