<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-16 -->

# outlookItem resource type

Namespace: microsoft.graph

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| categories | String collection | The categories associated with the item |
| changeKey | String | Identifies the version of the item. Every time the item is changed, changeKey changes as well. This allows Exchange to apply changes to the correct version of the object. Read-only. |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| id | String | Read-only. |
| lastModifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "categories": ["string"],
  "changeKey": "string",
  "createdDateTime": "String (timestamp)",
  "id": "string (identifier)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
