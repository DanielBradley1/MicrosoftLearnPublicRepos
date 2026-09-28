<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailbox?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# mailbox resource type

Namespace: microsoft.graph

Represents a user's mailbox.

Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create import session](https://learn.microsoft.com/en-us/graph/api/mailbox-createimportsession?view=graph-rest-1.0) | [mailboxItemImportSession](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitemimportsession?view=graph-rest-1.0) | Create a session to [import an Exchange mailbox item](https://learn.microsoft.com/en-us/graph/import-exchange-mailbox-item). |
| [Export items](https://learn.microsoft.com/en-us/graph/api/mailbox-exportitems?view=graph-rest-1.0) | [exportItemResponse](https://learn.microsoft.com/en-us/graph/api/resources/exportitemresponse?view=graph-rest-1.0) collection | Export Exchange [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) objects in full-fidelity. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and time when this object was deleted. Always `null` when the object isn't deleted. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |
| id | String | The unique identifier for the **mailbox**. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| folders | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) collection | The collection of folders in the mailbox. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mailbox",
  "deletedDateTime": "String (timestamp)",
  "id": "String (identifier)"
}
```
