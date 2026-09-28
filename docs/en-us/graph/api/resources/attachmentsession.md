<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attachmentsession?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# attachmentSession resource type

Namespace: microsoft.graph

Represents a resource that uploads large attachments to a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | Stream | The content streams that are uploaded. |
| expirationDateTime | DateTimeOffset | The date and time in UTC when the upload session will expire. The complete file must be uploaded before this expiration time is reached. |
| id | String | Unique identifier for the attachment session. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| nextExpectedRanges | String collection | Indicates a single value `{start}` that represents the location in the file where the next upload should begin. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attachmentSession",
  "content": "Stream",
  "expirationDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "nextExpectedRanges": [
    "String"
  ]
}
```
