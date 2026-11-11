<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/browsequeryresponseitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-07 -->

# browseQueryResponseItem resource type

Namespace: microsoft.graph

Represents the response of the [sharepointBrowseSession](https://learn.microsoft.com/en-us/graph/api/sharepointbrowsesession-browse?view=graph-rest-1.0) and [oneDriveForBusinessBrowse](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessbrowsesession-browse?view=graph-rest-1.0) APIs.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the user or application that created the item. Returned only when **type** is `file` or `folder`. |
| createdDateTime | DateTimeOffset | The date and time when the item was created. Returned only when **type** is `file` or `folder`. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. |
| itemKey | String | Unique identifier of the returned item. |
| itemsCount | Int32 | The count of items present within the items; for example, the count of files in a folder. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the user or application that last modified the item. Returned only when **type** is `file` or `folder`. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the item was last modified. Returned only when **type** is `file` or `folder`. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. |
| name | String | The name of the item. |
| sizeInBytes | String | The size of the item in bytes. |
| type | browseQueryResponseItemType | The type of the item. The possible values are: `none`, `site`, `documentLibrary`, `folder`, `file`, `unknownFutureValue`. |
| webUrl | String | The web URL of the item. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.browseQueryResponseItem",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "itemKey": "String",
  "itemsCount": "Int32",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "name": "String",
  "sizeInBytes": "String",
  "type": "String",
  "webUrl": "String"
}
```
