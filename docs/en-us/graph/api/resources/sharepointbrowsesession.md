<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointbrowsesession?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-11 -->

# sharePointBrowseSession resource type

Namespace: microsoft.graph

Represents a browse session created on a restore point of a backed-up SharePoint site.

Inherits from [browseSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/browsesessionbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-sharepointbrowsesessions?view=graph-rest-1.0) | [sharePointBrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointbrowsesession?view=graph-rest-1.0) | Create a new sharePointBrowseSession object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/sharepointbrowsesession-get?view=graph-rest-1.0) | [sharePointBrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointbrowsesession?view=graph-rest-1.0) | Read the properties and relationships of [sharePointBrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointbrowsesession?view=graph-rest-1.0) object. |
| [List](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-sharepointbrowsesessions?view=graph-rest-1.0) | [sharePointBrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointbrowsesession?view=graph-rest-1.0) collection | Get a list of the sharePointBrowseSession objects and their properties. |
| [browse](https://learn.microsoft.com/en-us/graph/api/sharepointbrowsesession-browse?view=graph-rest-1.0) | [browseQueryResponseItem](https://learn.microsoft.com/en-us/graph/api/resources/browsequeryresponseitem?view=graph-rest-1.0) collection | Allow client to browse files and folder present within a [BrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/browsesessionbase?view=graph-rest-1.0) |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| backupSizeInBytes | String | The size of the backup in bytes. |
| createdDateTime | DateTimeOffset | The time of the creation of the browse session. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Contains the error details if the browse session creation fails. |
| expirationDateTime | DateTimeOffset | The time after which the browse session is deleted automatically. |
| id | String | The unique identifier of the browse session. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| restorePointDateTime | DateTimeOffset | The date time of the restore point on which browse session is created. |
| siteId | String | Id of the backed-up SharePoint site. |
| status | browseSessionStatus | The status of the browse session. The possible values are: `creating`, `created`, `failed`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointBrowseSession",
  "id": "String (identifier)",
  "status": "String",
  "createdDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "restorePointDateTime": "String (timestamp)",
  "backupSizeInBytes": "String",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "siteId": "String"
}
```
