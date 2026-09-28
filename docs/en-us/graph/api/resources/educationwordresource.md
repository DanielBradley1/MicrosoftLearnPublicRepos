<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationwordresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# educationWordResource resource type

Namespace: microsoft.graph

A subclass of [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0).

This is a Word document resource. The Word file must be uploaded in the **fileResource** directory associated with the assignment or submission.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | The display name of the user that created this object. |
| createdDateTime | DateTimeOffset | Date time the resoruce was added. |
| displayName | string | The display name of the resource. |
| fileUrl | String | Location of the file on disk. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The last user to modify the resource. |
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
