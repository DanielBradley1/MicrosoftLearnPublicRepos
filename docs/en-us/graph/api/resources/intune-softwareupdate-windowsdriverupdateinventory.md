<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateinventory?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsDriverUpdateInventory resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A new entity to represent driver inventories.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsDriverUpdateInventories](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateinventory-list?view=graph-rest-beta) | [windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateinventory?view=graph-rest-beta) collection | List properties and relationships of the [windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateinventory?view=graph-rest-beta) objects. |
| [Get windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateinventory-get?view=graph-rest-beta) | [windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateinventory?view=graph-rest-beta) | Read properties and relationships of the [windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateinventory?view=graph-rest-beta) object. |
| [Create windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateinventory-create?view=graph-rest-beta) | [windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateinventory?view=graph-rest-beta) | Create a new [windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateinventory?view=graph-rest-beta) object. |
| [Delete windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateinventory-delete?view=graph-rest-beta) | None | Deletes a [windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateinventory?view=graph-rest-beta). |
| [Update windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateinventory-update?view=graph-rest-beta) | [windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateinventory?view=graph-rest-beta) | Update the properties of a [windowsDriverUpdateInventory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateinventory?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The id of the driver. |
| name | String | The name of the driver. |
| version | String | The version of the driver. |
| manufacturer | String | The manufacturer of the driver. |
| releaseDateTime | DateTimeOffset | The release date time of the driver. |
| driverClass | String | The class of the driver. |
| applicableDeviceCount | Int32 | The number of devices for which this driver is applicable. |
| approvalStatus | [driverApprovalStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-driverapprovalstatus?view=graph-rest-beta) | The approval status for this driver. Possible values are: `needsReview`, `declined`, `approved`, `suspended`. |
| category | [driverCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-drivercategory?view=graph-rest-beta) | The category for this driver. Possible values are: `recommended`, `previouslyApproved`, `other`. |
| deployDateTime | DateTimeOffset | The date time when a driver should be deployed if approvalStatus is approved. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsDriverUpdateInventory",
  "id": "String (identifier)",
  "name": "String",
  "version": "String",
  "manufacturer": "String",
  "releaseDateTime": "String (timestamp)",
  "driverClass": "String",
  "applicableDeviceCount": 1024,
  "approvalStatus": "String",
  "category": "String",
  "deployDateTime": "String (timestamp)"
}
```
