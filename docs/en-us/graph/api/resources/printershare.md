<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-03 -->

# printerShare resource type

Namespace: microsoft.graph

Represents a printer that is intended to be discoverable by users and printing applications.

Inherits from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/print-list-shares?view=graph-rest-1.0) | [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) collection | Get a list of printer shares in the tenant. |
| [Get](https://learn.microsoft.com/en-us/graph/api/printershare-get?view=graph-rest-1.0) | [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) | Read properties and relationships of a **printerShare** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/printershare-update?view=graph-rest-1.0) | [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) | Update a **printerShare** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/printershare-delete?view=graph-rest-1.0) | None | Unshare a printer. |
| [List jobs for a printer share](https://learn.microsoft.com/en-us/graph/api/printershare-list-jobs?view=graph-rest-1.0) | [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) collection | Get a list of print jobs that are queued for processing by the printerShare. |
| [Create job for a printer share](https://learn.microsoft.com/en-us/graph/api/printershare-post-jobs?view=graph-rest-1.0) | [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) | Create a new print job for the printerShare. To start printing the job, use [start](https://learn.microsoft.com/en-us/graph/api/printjob-start?view=graph-rest-1.0). |
| [List allowed users](https://learn.microsoft.com/en-us/graph/api/printershare-list-allowedusers?view=graph-rest-1.0) | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) collection | Retrieve a list of users who have been granted access to submit print jobs to the associated printer share. |
| [Create allowed user](https://learn.microsoft.com/en-us/graph/api/printershare-post-allowedusers?view=graph-rest-1.0) | None | Grant the specified user access to submit print jobs to the associated printer share. |
| [Delete allowed user](https://learn.microsoft.com/en-us/graph/api/printershare-delete-alloweduser?view=graph-rest-1.0) | None | Revoke printer share access from the specified user. |
| [List allowed groups](https://learn.microsoft.com/en-us/graph/api/printershare-list-allowedgroups?view=graph-rest-1.0) | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) collection | Retrieve a list of groups that have been granted access to submit print jobs to the associated printer share. |
| [Create allowed group](https://learn.microsoft.com/en-us/graph/api/printershare-post-allowedgroups?view=graph-rest-1.0) | None | Grant the specified group access to submit print jobs to the associated printer share. |
| [Delete allowed group](https://learn.microsoft.com/en-us/graph/api/printershare-delete-allowedgroup?view=graph-rest-1.0) | None | Revoke printer share access from the specified group. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowAllUsers | Boolean | If true, all users and groups will be granted access to this printer share. This supersedes the allow lists defined by the **allowedUsers** and **allowedGroups** navigation properties. |
| capabilities | [printerCapabilities](https://learn.microsoft.com/en-us/graph/api/resources/printercapabilities?view=graph-rest-1.0) | The capabilities of the printer associated with this printer share. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The DateTimeOffset when the printer share was created. Read-only. |
| defaults | [printerDefaults](https://learn.microsoft.com/en-us/graph/api/resources/printerdefaults?view=graph-rest-1.0) | The default print settings of the printer associated with this printer share. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| displayName | String | The name of the printer share that print clients should display. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| id | String | The printerShare's identifier. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). Read-only. |
| isAcceptingJobs | Boolean | Whether the printer associated with this printer share is currently accepting new print jobs. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| location | [printerLocation](https://learn.microsoft.com/en-us/graph/api/resources/printerlocation?view=graph-rest-1.0) | The physical and/or organizational location of the printer associated with this printer share. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| manufacturer | String | The manufacturer reported by the printer associated with this printer share. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). Read-only. |
| model | String | The model name reported by the printer associated with this printer share. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). Read-only. |
| status | [printerStatus](https://learn.microsoft.com/en-us/graph/api/resources/printerstatus?view=graph-rest-1.0) | The processing status, including any errors, of the printer associated with this printer share.Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). Read-only. |
| viewPoint | [printerShareViewpoint](https://learn.microsoft.com/en-us/graph/api/resources/printershareviewpoint?view=graph-rest-1.0) | Additional data for a printer share as viewed by the signed-in user. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| printer | [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) | The printer that this printer share is related to. |
| allowedUsers | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) collection | The users who have access to print using the printer. |
| allowedGroups | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | The groups whose users have access to print using the printer. |
| jobs | [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) collection | The list of jobs that are queued for printing by the printer associated with this printer share. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printerShare",
  "id": "String (identifier)",
  "displayName": "String",
  "manufacturer": "String",
  "model": "String",
  "isAcceptingJobs": "Boolean",
  "defaults": {
    "@odata.type": "microsoft.graph.printerDefaults"
  },
  "location": {
    "@odata.type": "microsoft.graph.printerLocation"
  },
  "capabilities": {
    "@odata.type": "microsoft.graph.printerCapabilities"
  },
  "status": {
    "@odata.type": "microsoft.graph.printerStatus"
  },
  "allowAllUsers": "Boolean",
  "createdDateTime": "String (timestamp)",
  "viewPoint": {"@odata.type": "microsoft.graph.printerShareViewpoint"}
}
```
