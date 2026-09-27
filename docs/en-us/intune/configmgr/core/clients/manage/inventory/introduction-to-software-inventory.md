<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/inventory/introduction-to-software-inventory -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Introduction to software inventory in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

Use software inventory to collect information about files on client devices. Software inventory can also collect files from client devices and store them on the site server. Software inventory is collected when you select the **Enable software inventory on clients** setting in client settings. You can also schedule the operation in client settings.

After you enable software inventory and the clients run a software inventory cycle, the client sends the information to a management point in the client's site. The management point then forwards the inventory information to the Configuration Manager site server, which stores the information in the site database.

There are a few ways to view software inventory data:

- [Create queries](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/create-queries) that return devices with specified files.
- Create [query-based collections](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/introduction-to-collections) that include devices with specified files.
- [Run reports](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/introduction-to-reporting) that provide details about files on devices.
- Use [Resource Explorer](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory) to examine detailed information about the files that were inventoried and collected from client devices.

When software inventory runs on a client device, the first report is a full inventory. Subsequent reports contain only delta inventory information. The site server processes delta information in the order received. If delta information for a client is missing, the site server rejects further delta information and directs the client to run a full inventory.

Configuration Manager can discover dual-boot computers but only returns inventory information from the operating system that's active at the time of inventory.
