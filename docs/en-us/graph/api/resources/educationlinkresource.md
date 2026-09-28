<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationlinkresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# educationLinkResource resource type

Namespace: microsoft.graph

A subclass of [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0).

This resource is a link and doesn't have any other data associated with it.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | The display name of the user that created this object. |
| createdDateTime | DateTimeOffset | Date time the resource was added. |
| displayName | string | The display name of the resource. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The last user to modify the resource. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the resource was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| link | String | URL to the resource. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdBy": "String (User)",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "lastModifiedBy": "String (User)",
  "lastModifiedDateTime": "String (timestamp)",
  "link": "String",
}
```
