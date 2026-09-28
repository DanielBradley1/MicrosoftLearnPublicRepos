<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementattachment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# serviceAnnouncementAttachment resource type

Namespace: microsoft.graph

Represents an attachment associated with a [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0) object.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/serviceannouncementattachment-get?view=graph-rest-1.0) | [serviceAnnouncementAttachment](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementattachment?view=graph-rest-1.0) | Read the properties and relationships of a [serviceAnnouncementAttachment](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementattachment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | Stream | The attachment content. |
| contentType | String | The content type of the attachment. |
| id | String | The attachment ID. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the attachment was last modified. |
| name | String | The attachment name. |
| size | Int32 | The size in bytes of the attachment. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serviceAnnouncementAttachment",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "name": "String",
  "contentType": "String",
  "size": "Integer",
  "isInline": "Boolean",
  "content": "Stream"
}
```
