<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationfileresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# educationFileResource resource type

Namespace: microsoft.graph

A subclass of [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0) that represents a file object that is associated with the assignment or submission.

In this case, the file isn't one of the special files \(Word, Excel, and so on\) but is a file that does not have special handling within the system. The file resource must be stored in the **resourceFolder** that is associated with the assignment or submission this resource is attached to.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | The display name of the user that created this object. |
| createdDateTime | DateTimeOffset | Date time the resoruce was added. |
| displayName | string | The display name of the resource. |
| fileUrl | String | Location on disk of the file resource. |
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
