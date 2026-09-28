<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailbox-import-export-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Use the mailbox import and export APIs in Microsoft Graph

The mailbox import and export APIs in Microsoft Graph allow your application to import and export contents from Exchange Online mailboxes. Mailbox contents can be accessed as a collection of [folders](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) and [items](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) in a consistent format, without the need to manage the metadata or structure of each item type individually. These items can be [exported](https://learn.microsoft.com/en-us/graph/api/mailbox-exportitems?view=graph-rest-1.0) as an opaque stream in full fidelity \(you can't change the export stream\). Full-fidelity exports ensure that when you [import](https://learn.microsoft.com/en-us/graph/api/mailbox-createimportsession?view=graph-rest-1.0) an item, Exchange recreates it with no loss of information.

These APIs support access to data in users' primary mailboxes and shared mailboxes on Exchange Online. Items can be imported to the same mailbox or a different one.

Important

The mailbox import and export APIs in Microsoft Graph aren't designed for mailbox backup and restore. For mailbox backup and restore in Microsoft 365, see [Microsoft 365 Backup](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-overview) and [Microsoft 365 Backup storage in Microsoft Graph](https://learn.microsoft.com/en-us/graph/backup-storage-concept-overview).

## How to use the mailbox import and export APIs

The following steps allow your app to systematically export and import contents from Exchange mailboxes:

1. [Get a list of mailboxes that belong to a particular user](https://learn.microsoft.com/en-us/graph/api/usersettings-list-exchange?view=graph-rest-1.0).
2. Discover the contents of the mailbox as a set of [folders](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) and [items](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0). Use the **id** property returned by [List folders](https://learn.microsoft.com/en-us/graph/api/mailbox-list-folders?view=graph-rest-1.0) as the folder identifier for mailbox import and export operations. For example, filter folders by class with `$filter=type eq 'IPF.Appointment'` to find calendar-class folders.
3. [Export items from a mailbox](https://learn.microsoft.com/en-us/graph/api/mailbox-exportitems?view=graph-rest-1.0).
4. Create or update mailbox [folders](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0).
5. [Import an item into the same or a different mailbox](https://learn.microsoft.com/en-us/graph/api/mailbox-createimportsession?view=graph-rest-1.0).

## Common use cases

| Use case | REST resource | See also |
| :--- | :--- | :--- |
| Create, get, update, or delete a mailbox folder | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) | [mailboxFolder methods](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0#methods) |
| Get one or more mailbox items | [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) | [mailboxItem methods](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0#methods) |
| Get delta for folders | [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) [mailboxFolder: delta](https://learn.microsoft.com/en-us/graph/api/mailboxfolder-delta?view=graph-rest-1.0) |  |
| Get delta for items | [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) | [mailboxItem: delta](https://learn.microsoft.com/en-us/graph/api/mailboxitem-delta?view=graph-rest-1.0) |
| Import or export mailboxes | [mailbox](https://learn.microsoft.com/en-us/graph/api/resources/mailbox?view=graph-rest-1.0) | [mailbox methods](https://learn.microsoft.com/en-us/graph/api/resources/mailbox?view=graph-rest-1.0#methods) |
| Get a list of mailboxes that belong to a user | [exchangeSettings](https://learn.microsoft.com/en-us/graph/api/resources/exchangesettings?view=graph-rest-1.0) | [List Exchange settings](https://learn.microsoft.com/en-us/graph/api/usersettings-list-exchange?view=graph-rest-1.0) |

## Next steps

Use the mailbox import and export APIs in Microsoft Graph to import and export contents from Exchange mailboxes. To learn more:

- Explore the resources and methods that are most helpful to your scenario.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).

## Related content

[Import an Exchange mailbox item using the mailbox import and export APIs](https://learn.microsoft.com/en-us/graph/import-exchange-mailbox-item)
