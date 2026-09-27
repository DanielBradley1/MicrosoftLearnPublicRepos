<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/diagnostics-and-usage-data -->
<!-- Sitemap-Last-Modified: 2026-06-04 -->

# Diagnostics and usage data for Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

Configuration Manager collects diagnostics and usage data about itself, which is used by Microsoft to improve the installation experience, quality, and security of future releases. With version 2509, no further changes or updates are planned for diagnostic and usage data collection.

Each Configuration Manager hierarchy enables diagnostics and usage data. It consists of SQL Server queries that run on a weekly basis on each primary site and at the central administration site \(CAS\). When the hierarchy uses a CAS, child primary sites replicate their data to that CAS. At the top-level site of your hierarchy, the [service connection point](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point) submits this information when it checks for updates. If the service connection point is in offline mode, you transfer the information by using the [service connection tool](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/use-the-service-connection-tool).

Note

Configuration Manager collects data only from the site's SQL Server database, and it doesn't collect data directly from clients or site servers.

For more information, see the [Microsoft privacy statement](https://privacy.microsoft.com/privacystatement).

Next, learn about how Microsoft uses the diagnostics and usage data that Configuration Manager collects:

[How Microsoft uses diagnostics and usage data](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-used)

Tip

The **ConfigurationManager** PowerShell module also collects usage data. For more information, see [Configuration Manager cmdlet library privacy statement](https://learn.microsoft.com/en-us/powershell/sccm/privacy-statement).

Some of the tools that are included with Configuration Manager collect usage data. For more information, see [Diagnostic usage data for tools](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/tools).
