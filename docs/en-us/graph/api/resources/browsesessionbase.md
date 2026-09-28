<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/browsesessionbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-11 -->

# browseSessionBase resource type

Namespace: microsoft.graph

An abstract entity that represents a browse session created on a specific restore point. A browse session can be created only for SharePoint and OneDrive for work or school. Only *fastRestore* points are supported to create a browse session. A browse session is a short-lived entity and is deleted automatically.

Base type of [oneDriveForBusinessBrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessbrowsesession?view=graph-rest-1.0) and [sharePointBrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointbrowsesession?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-browsesessions?view=graph-rest-1.0) | [browseSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/browsesessionbase?view=graph-rest-1.0) collection | Get a list of the [browseSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/browsesessionbase?view=graph-rest-1.0) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| backupSizeInBytes | String | The size of the backup in bytes. |
| createdDateTime | DateTimeOffset | The date and time when the browse session was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Contains the error details if the browse session creation fails. |
| expirationDateTime | DateTimeOffset | The date and time after which the browse session is deleted automatically. |
| id | String | The unique identifier of the browse session. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| restorePointDateTime | DateTimeOffset | The date and time of the restore point on which the browse session is created. |
| status | browseSessionStatus | The status of the browse session. The possible values are: `creating`, `created`, `failed`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.browseSessionBase",
  "backupSizeInBytes": "String",
  "createdDateTime": "String (timestamp)",
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "expirationDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "restorePointDateTime": "String (timestamp)",
  "status": "String"
}
```
