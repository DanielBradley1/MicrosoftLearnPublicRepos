<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsDriverUpdateProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Driver Update Profile

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsDriverUpdateProfiles](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofile-list?view=graph-rest-beta) | [windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofile?view=graph-rest-beta) collection | List properties and relationships of the [windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofile?view=graph-rest-beta) objects. |
| [Get windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofile-get?view=graph-rest-beta) | [windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofile?view=graph-rest-beta) | Read properties and relationships of the [windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofile?view=graph-rest-beta) object. |
| [Create windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofile-create?view=graph-rest-beta) | [windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofile?view=graph-rest-beta) | Create a new [windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofile?view=graph-rest-beta) object. |
| [Delete windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofile-delete?view=graph-rest-beta) | None | Deletes a [windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofile?view=graph-rest-beta). |
| [Update windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofile-update?view=graph-rest-beta) | [windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofile?view=graph-rest-beta) | Update the properties of a [windowsDriverUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofile?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofile-assign?view=graph-rest-beta) | None |  |
| [executeAction action](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofile-executeaction?view=graph-rest-beta) | [bulkDriverActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-bulkdriveractionresult?view=graph-rest-beta) |  |
| [syncInventory action](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofile-syncinventory?view=graph-rest-beta) | None | Sync the driver inventory of a WindowsDriverUpdateProfile. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The Intune policy id. |
| displayName | String | The display name for the profile. |
| description | String | The description of the profile which is specified by the user. |
| approvalType | [driverUpdateProfileApprovalType](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-driverupdateprofileapprovaltype?view=graph-rest-beta) | Driver update profile approval type. For example, manual or automatic approval. Possible values are: `manual`, `automatic`. |
| deviceReporting | Int32 | Number of devices reporting for this profile |
| newUpdates | Int32 | Number of new driver updates available for this profile. |
| deploymentDeferralInDays | Int32 | Deployment deferral settings in days, only applicable when ApprovalType is set to automatic approval. |
| createdDateTime | DateTimeOffset | The date time that the profile was created. |
| lastModifiedDateTime | DateTimeOffset | The date time that the profile was last modified. |
| roleScopeTagIds | String collection | List of Scope Tags for this Driver Update entity. |
| inventorySyncStatus | [windowsDriverUpdateProfileInventorySyncStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofileinventorysyncstatus?view=graph-rest-beta) | Driver inventory sync status for this profile. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofileassignment?view=graph-rest-beta) collection | The list of group assignments of the profile. |
| driverInventories | [windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateinventory?view=graph-rest-beta) collection | Driver inventories for this profile. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsDriverUpdateProfile",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "approvalType": "String",
  "deviceReporting": 1024,
  "newUpdates": 1024,
  "deploymentDeferralInDays": 1024,
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
  "inventorySyncStatus": {
    "@odata.type": "microsoft.graph.windowsDriverUpdateProfileInventorySyncStatus",
    "lastSuccessfulSyncDateTime": "String (timestamp)",
    "driverInventorySyncState": "String"
  }
}
```
