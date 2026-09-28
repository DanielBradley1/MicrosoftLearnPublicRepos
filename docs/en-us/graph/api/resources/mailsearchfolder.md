<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailsearchfolder?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-07 -->

# mailSearchFolder resource type

Namespace: microsoft.graph

A **mailSearchFolder** is a virtual folder in the user's mailbox that contains all the email items matching specified search criteria. **mailSearchFolder** inherits from [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0). Search folders can be created in any folder in a user's Exchange Online mailbox. However, for a search folder to appear in Outlook clients, the required location differs by client:

- In **Outlook for Windows**, the folder must be created under **WellKnownFolderName.SearchFolders**.
- In **Outlook on the web** and **New Outlook for Windows**, the folder must be created under **SearchFoldersView**.

## Search folder lifecycle

Search folders created by your application can be deleted by Exchange Online for one of the following reasons:

1. Search folders expire after 45 days of no usage.
2. There are limits on the number of search folders that can be created per source folder. When this limit is breached, older search folders are deleted to make way for new ones.

When a search folder is deleted, your app should create a new search folder resource and use the same.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create mail search folder](https://learn.microsoft.com/en-us/graph/api/mailsearchfolder-post?view=graph-rest-1.0) | [mailSearchFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailsearchfolder?view=graph-rest-1.0) | Create a search folder in this user's mailbox. |
| [List child folders](https://learn.microsoft.com/en-us/graph/api/mailfolder-list-childfolders?view=graph-rest-1.0) | [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0) collection | List all the folders in this user's mailbox, including search folders. |
| [Get mail search folder](https://learn.microsoft.com/en-us/graph/api/mailfolder-get?view=graph-rest-1.0) | [mailSearchFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailsearchfolder?view=graph-rest-1.0) | Get the specified search folder. |
| [Update mail search folder](https://learn.microsoft.com/en-us/graph/api/mailsearchfolder-update?view=graph-rest-1.0) | [mailSearchFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailsearchfolder?view=graph-rest-1.0) | Update the specified search folder. |
| [Delete mail search folder](https://learn.microsoft.com/en-us/graph/api/mailfolder-delete?view=graph-rest-1.0) | None | Delete the specified search folder. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/mailsearchfolder-permanentdelete?view=graph-rest-1.0) | None | Permanently delete a mail search folder and remove its items from the user's mailbox. |
| [List messages in folder](https://learn.microsoft.com/en-us/graph/api/mailfolder-list-messages?view=graph-rest-1.0) | [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) collection | List all the messages in the specified search folder. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| filterQuery | String | The OData query to filter the messages. |
| includeNestedFolders | Boolean | Indicates how the mailbox folder hierarchy should be traversed in the search. `true` means that a deep search should be done to include child folders in the hierarchy of each folder explicitly specified in **sourceFolderIds**. `false` means a shallow search of only each of the folders explicitly specified in **sourceFolderIds**. |
| isSupported | Boolean | Indicates whether a search folder is editable using REST APIs. |
| sourceFolderIds | String collection | The mailbox folders that should be mined. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isSupported": true,
  "includeNestedFolders": true,
  "sourceFolderIds": ["string"],
  "filterQuery": "string"
}
```
