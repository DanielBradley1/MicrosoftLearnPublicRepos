<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-19 -->

# mailboxFolder resource type

Namespace: microsoft.graph

Represents a folder in a user's mailbox, such as inbox, drafts, or other user created folders. Folders can contain various mailbox items like messages, events, contacts, other Outlook items, and child folders.

This resource supports [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions, and updates, by providing a [delta](https://learn.microsoft.com/en-us/graph/api/mailboxfolder-delta?view=graph-rest-1.0) function. It also supports [single-value and multi-value extended properties](https://learn.microsoft.com/en-us/graph/api/resources/extended-properties-overview?view=graph-rest-1.0) for storing and accessing custom data that isn't already exposed in the Microsoft Graph API metadata.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/mailbox-list-folders?view=graph-rest-1.0) | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) collection | Get all the [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) objects in the specified mailbox, including any search folders. |
| [Create](https://learn.microsoft.com/en-us/graph/api/mailbox-post-folders?view=graph-rest-1.0) | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) | Create a new [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) or child **mailboxFolder** in a user's mailbox. |
| [Get](https://learn.microsoft.com/en-us/graph/api/mailboxfolder-get?view=graph-rest-1.0) | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) | Read the properties and relationships of a [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/mailboxfolder-update?view=graph-rest-1.0) | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) | Update [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) properties such as the **displayName** within a mailbox. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/mailbox-delete-folders?view=graph-rest-1.0) | None | Delete a [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) or a child **mailboxFolder** within a mailbox. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/mailboxfolder-delta?view=graph-rest-1.0) | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) collection | Get a set of [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) objects that were added, deleted, or removed from the user's mailbox. |
| [List child mailbox folders](https://learn.microsoft.com/en-us/graph/api/mailboxfolder-list-childfolders?view=graph-rest-1.0) | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) collection | Get the [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) collection under the specified **mailboxFolder** in a mailbox. |
| [List items in folder](https://learn.microsoft.com/en-us/graph/api/mailboxfolder-list-items?view=graph-rest-1.0) | [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) collection | Get the [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) collection within a specified [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) in a mailbox. |
| [Delete item in folder](https://learn.microsoft.com/en-us/graph/api/mailboxfolder-delete-items?view=graph-rest-1.0) | None | Delete a [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) from a [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) in a mailbox. |
| **Extended properties** |  |  |
| [Create single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-post-singlevalueextendedproperties?view=graph-rest-1.0) | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) | Create one or more single-value extended properties in a new or existing mailbox folder. |
| [Get single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0) | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) | Get mailbox folders that contain a single-value extended property by using `$expand` or `$filter`. |
| [Create multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-post-multivalueextendedproperties?view=graph-rest-1.0) | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) | Create one or more multi-value extended properties in a new or existing mailbox folder. |
| [Get multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0) | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) | Get a mailbox folder that contains a multi-value extended property by using `$expand`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| childFolderCount | Int32 | The number of immediate child folders in the current folder. |
| displayName | String | The display name of the folder. |
| id | String | The unique identifier for the folder. |
| parentFolderId | String | The unique identifier for the parent folder of this folder. |
| totalItemCount | Int32 | The number of items in the folder. |
| type | String | Describes the folder class type. |
| wellKnownName | String | The locale-independent well-known name of the folder for folders created by Outlook, such as `inbox`, `sentitems`, `drafts`, `deleteditems`, or `archive`. For user-created folders, the value is `null`. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| childFolders | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) collection | The collection of child folders in this folder. |
| items | [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) collection | The collection of items in this folder. |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of multi-value extended properties defined for the **mailboxFolder**. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of single-value extended properties defined for the **mailboxFolder**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mailboxFolder",
  "displayName": "String",
  "childFolderCount": "Int32",
  "id": "String (identifier)",
  "parentFolderId": "String",
  "totalItemCount": "Int32",
  "wellKnownName": "String",
  "type": "String"
}
```
