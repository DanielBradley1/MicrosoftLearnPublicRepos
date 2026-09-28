<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-28 -->

# mailboxItem resource type

Namespace: microsoft.graph

Represents an item in a [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0). Items are Exchange mailbox items like message, task, event, contact, or note.

This resource supports [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions, and updates, by providing a delta function. It also supports single-value and multi-value extended properties for filtering on custom data that isn't already exposed in the Microsoft Graph API metadata.

Inherits from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/mailboxfolder-list-items?view=graph-rest-1.0) | [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) collection | Get the [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) collection within a specified [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) in a mailbox. |
| [Get](https://learn.microsoft.com/en-us/graph/api/mailboxitem-get?view=graph-rest-1.0) | [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) | Read the properties and relationships of a [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/mailboxfolder-delete-items?view=graph-rest-1.0) | None | Delete a [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) from a [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) in a mailbox. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/mailboxitem-delta?view=graph-rest-1.0) | [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) collection | Get a set of [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) objects that were added, deleted, or updated in a specified [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0). |
| **Extended properties** |  |  |
| [Get single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0) | [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) | Get mailbox items that contain a single-value extended property by using `$expand` or `$filter`. |
| [Get multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0) | [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) | Get a mailbox item that contains a multi-value extended property by using `$expand`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| categories | String collection | The categories associated with the message. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| changeKey | String | The version of the item. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time when the item was created. The date and time information uses ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2021 is `2021-01-01T00:00:00Z`. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| id | String | The unique identifier for the item. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the item was last changed. The date and time information uses ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2021 is `2021-01-01T00:00:00Z`. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| size | Int64 | The length of the item in bytes. |
| type | String | The message class ID of the item. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of multi-value extended properties defined for the **mailboxItem**. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of single-value extended properties defined for the **mailboxItem**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mailboxItem",
  "categories": ["String"],
  "changeKey": "String",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "size": "Int64",
  "type": "String"
}
```
