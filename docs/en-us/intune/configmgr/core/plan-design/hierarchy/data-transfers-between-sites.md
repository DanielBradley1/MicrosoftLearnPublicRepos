<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/data-transfers-between-sites -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Data transfers between sites

*Applies to: Configuration Manager \(current branch\)*

Configuration Manager uses *file-based replication* and *database replication* to transfer different types of information between sites. Learn about how Configuration Manager moves data between sites, and how you can manage the transfer of data across your network.

## Types of replication

### File-based replication

Configuration Manager uses file-based replication to transfer file-based data between sites in your hierarchy. This data includes applications and packages that you want to deploy to distribution points in child sites. It also handles unprocessed discovery data records that the site transfers to its parent site and then processes.

For more information, see [File-based replication](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/file-based-replication).

### Database replication

Configuration Manager database replication uses SQL Server to transfer data. It uses this method to merge changes in its site database with the information from the database at other sites in the hierarchy.

For more information, see [Database replication](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/database-replication).

For help with troubleshooting SQL Server replication, see [Troubleshoot SQL Server replication](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/replication/overview).

## See also

[Monitor replication](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/monitor-replication)
