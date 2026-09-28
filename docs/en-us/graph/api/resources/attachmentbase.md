<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attachmentbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# attachmentBase resource type

Namespace: microsoft.graph

Represents an abstract base type for an attachment. You can add related content to a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) in the form of an attachment.

Base type of [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentType | String | The MIME type. |
| id | String | Unique identifier for the attachment. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| name | String | The display name of the attachment. This doesn't need to be the actual file name. |
| size | Int32 | The length of the attachment in bytes. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attachmentBase",
  "contentType": "String",  
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "name": "String",
  "size": "Int32"
}
```
