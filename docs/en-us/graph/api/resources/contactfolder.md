<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-19 -->

# contactFolder resource type

Namespace: microsoft.graph

A folder that contains contacts.

This resource supports using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions, and updates, by providing a [delta](https://learn.microsoft.com/en-us/graph/api/contactfolder-delta?view=graph-rest-1.0) function.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get contact folder](https://learn.microsoft.com/en-us/graph/api/contactfolder-get?view=graph-rest-1.0) | [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0) | Get a contact folder by using the contact folder ID. |
| [Update contact folder](https://learn.microsoft.com/en-us/graph/api/contactfolder-update?view=graph-rest-1.0) | [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0) | Update **contactFolder** object. |
| [Delete contact folder](https://learn.microsoft.com/en-us/graph/api/contactfolder-delete?view=graph-rest-1.0) | None | Delete a **contactFolder** object. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/contactfolder-permanentdelete?view=graph-rest-1.0) | None | Permanently delete a contact folder and remove its items from the user's mailbox. |
| [List child folders](https://learn.microsoft.com/en-us/graph/api/contactfolder-list-childfolders?view=graph-rest-1.0) | [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0) collection | Get a collection of child folders under the specified contact folder. |
| [Create child folder](https://learn.microsoft.com/en-us/graph/api/contactfolder-post-childfolders?view=graph-rest-1.0) | [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0) | Create a new **contactFolder** as a child of a specified folder. |
| [Get contact delta](https://learn.microsoft.com/en-us/graph/api/contact-delta?view=graph-rest-1.0) | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) collection | Get a set of contact folders that have been added, deleted, or removed from the user's mailbox. |
| [List contacts in folder](https://learn.microsoft.com/en-us/graph/api/contactfolder-list-contacts?view=graph-rest-1.0) | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) collection | Get a contact collection from the default contacts folder of the signed-in user \(`.../me/contacts`\), or from the specified contact folder. |
| [Create contact in folder](https://learn.microsoft.com/en-us/graph/api/contactfolder-post-contacts?view=graph-rest-1.0) | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Add a contact to the root contacts folder or the `contacts` endpoint of another contact folder. |
| [Create single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-post-singlevalueextendedproperties?view=graph-rest-1.0) | [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0) | Create one or more single-value extended properties in a new or existing **contactFolder**. |
| [Get single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0) | [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0) | Get **contactFolders** that contain a single-value extended property by using `$expand` or `$filter`. |
| [Create multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-post-multivalueextendedproperties?view=graph-rest-1.0) | [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0) | Create one or more multi-value extended properties in a new or existing **contactFolder**. |
| [Get multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0) | [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0) | Get a **contactFolder** that contains a multi-value extended property by using `$expand`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The folder's display name. |
| id | String | Unique identifier of the contact folder. Read-only. |
| parentFolderId | String | The ID of the folder's parent folder. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| childFolders | [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0) collection | The collection of child folders in the folder. Navigation property. Read-only. Nullable. |
| contacts | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) collection | The contacts in the folder. Navigation property. Read-only. Nullable. |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of multi-value extended properties defined for the **contactFolder**. Read-only. Nullable. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of single-value extended properties defined for the **contactFolder**. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "string",
  "id": "string (identifier)",
  "parentFolderId": "string"
}
```

## Related content

- [Use delta query to track changes in Microsoft Graph data](https://learn.microsoft.com/en-us/graph/delta-query-overview)
- [Get incremental changes to messages in a folder](https://learn.microsoft.com/en-us/graph/delta-query-messages)
