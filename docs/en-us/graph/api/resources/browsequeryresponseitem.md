<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/browsequeryresponseitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# browseQueryResponseItem resource type

Namespace: microsoft.graph

Represents the response of the [sharepointBrowseSession](https://learn.microsoft.com/en-us/graph/api/sharepointbrowsesession-browse?view=graph-rest-1.0) and [oneDriveForBusinessBrowse](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessbrowsesession-browse?view=graph-rest-1.0) APIs.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| itemKey | String | Unique identifier of the returned item. |
| itemsCount | Int32 | The count of items present within the items; for example, the count of files in a folder. |
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
  "itemKey": "String",
  "itemsCount": "Int32",
  "name": "String",
  "sizeInBytes": "String",
  "type": "String",
  "webUrl": "String"
}
```
