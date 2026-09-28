<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attachmentinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# attachmentInfo resource type

Namespace: microsoft.graph

Represents the attributes of an attachment.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attachmentType | attachmentType | The type of the attachment. The possible values are: `file`, `item`, `reference`. Required. |
| contentType | String | The nature of the data in the attachment. Optional. |
| name | String | The display name of the attachment. This can be a descriptive string and doesn't have to be the actual file name. Required. |
| size | Int64 | The length of the attachment in bytes. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attachmentInfo",
  "attachmentType": "String",
  "contentType": "String",
  "name": "String",
  "size": "Int64"
}
```
