<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationmediaresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# educationMediaResource resource type

Namespace: microsoft.graph

Represents a media file resource for an [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0). Inherits from [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0).

Upload these files to the **fileResource** directory associated with the assignment or submission.

The following file types are media resources: `webm`, `mkv`, `avi`, `wmv`, `mp4`, `m4v`, `mpg`, `mpeg`, `m2v`, `jpg`, `png`, `gif`, `bmp`, `heic`, `jpeg`, `psd`, `mp3` and `m4a`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | The display name of the user that created this resource. |
| createdDateTime | DateTimeOffset | Date time the resoruce was added. |
| displayName | string | The display name of the user who added resource. |
| fileUrl | String | Location of the file on shared point folder. Required |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The last user to modify the resource |
| lastModifiedDateTime | DateTimeOffset | The date and time when the resource was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdBy": "String (User)",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "fileUrl": "String",
  "lastModifiedBy": "String (User)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
