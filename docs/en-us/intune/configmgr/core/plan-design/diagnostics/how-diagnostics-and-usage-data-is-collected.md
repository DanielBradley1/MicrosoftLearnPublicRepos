<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-collected -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How Configuration Manager collects diagnostics and usage data

*Applies to: Configuration Manager \(current branch\)*

To collect diagnostics and usage data for Configuration Manager, each primary site runs SQL Server queries on a weekly basis. In a multi-site hierarchy, the data is replicated to the central administration site.

At the top-level site of a hierarchy, the service connection point submits this information when it checks for updates. The mode of the service connection point determines how the data is transferred:

- **Online**: Once a week, the service connection point automatically sends diagnostics and usage data to the cloud service.
- **Offline**: You manually transfer diagnostics and usage data with the [service connection tool](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/use-the-service-connection-tool).

For more information, see [About the service connection point](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point).

Next, you can view diagnostic and usage data to confirm that your Configuration Manager hierarchy contains no sensitive information:

[How to view diagnostics and usage data](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/view-diagnostics-and-usage-data)

Tip

The **ConfigurationManager** PowerShell module also collects usage data. For more information, see [Configuration Manager cmdlet library privacy statement](https://learn.microsoft.com/en-us/powershell/sccm/privacy-statement).

Some of the tools that are included with Configuration Manager collect usage data. For more information, see [Diagnostic usage data for tools](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/tools).
