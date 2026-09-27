<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-server -->
<!-- Sitemap-Last-Modified: 2024-12-04 -->

# Removed and deprecated for Configuration Manager site servers

*Applies to: Configuration Manager \(current branch\)*

This article describes products and operating systems that are removed from support for Configuration Manager site servers, or will be removed in a future update \(deprecated\). It provides early notice about future changes that might affect your use of Configuration Manager.

This information may change in the future. It might not include each deprecated feature, product, or OS.

## Client OS

| Operating systems | Deprecation first announced | Support removed |
| --- | --- | --- |
| Windows 10 22H2 | Oct 2021 | Version 2509 |

## Server OS

| Operating systems | Deprecation first announced | Support removed |
| --- | --- | --- |
| Windows Server 2008 R2 with SP1 | July 2015 | Version 1702 |
| Windows Server 2008 with SP2 | July 2015 | Version 1511 |

## SQL Server

| SQL Server versions | Deprecation first announced | Support removed |
| --- | --- | --- |
| Sql Server 2014 | Oct 2024 | Version 2409 |
| SQL Server 2012 | July 2021 | The first release after July 1, 2022 |
| SQL Server 2008 R2 | July 2015 | Version 1702 |
| SQL Server 2008 | July 2015 | Version 1511 |

If you need to upgrade your version of SQL Server, we recommend the following methods, from easy to more complex:

1. [Upgrade SQL Server in-place](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/upgrade-on-premises-infrastructure#upgrade-sql-server) \(recommended\).
2. Install a new version of SQL Server on a new computer. Then to point your site server at the new SQL Server, [use the database move option](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/modify-your-infrastructure#bkmk_dbconfig) of Configuration Manager setup.
3. Use [backup and recovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/backup-and-recovery).

Note

Make sure to also upgrade versions of SQL Server Express at secondary sites.

## Next steps

For more information, see the following articles:

- [Removed and deprecated](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated)
- [Microsoft Support Lifecycle](https://learn.microsoft.com/en-us/lifecycle)
- [Support for current branch versions of Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/current-branch-versions-supported)
