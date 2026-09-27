<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/tools -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Diagnostic usage data for tools

*Applies to: Configuration Manager \(current branch\)*

Some of the tools that are included with Configuration Manager collect usage data. Microsoft uses this data to improve the quality of these tools, and better understand customer usage. Microsoft collects data for the following Configuration Manager tools:

- Client tools
- Server tools
- Support Center
- CMTrace

For more general information about these tools, see [Configuration Manager Tools](https://learn.microsoft.com/en-us/intune/configmgr/core/support/tools).

Note

The **ConfigurationManager** PowerShell module also collects usage data. For more information, see [Configuration Manager cmdlet library privacy statement](https://learn.microsoft.com/en-us/powershell/sccm/privacy-statement).

The following data is collected for these tools:

- Version
- Start and stop times to calculate duration of use

Because these tools can run on any Windows device, they all use the Windows diagnostic data channel. They don't rely on Configuration Manager diagnostic data collection. The device on which the tool runs needs to be configured for at least **Optional** diagnostic data. If you configure the device for any other setting, Windows won't collect data for these Configuration Manager tools. For more information on these Windows diagnostic data levels, see the following articles:

- [Windows 10, version 1709 and newer optional diagnostic data](https://learn.microsoft.com/en-us/windows/privacy/windows-diagnostic-data)
- [Configure Windows diagnostic data in your organization](https://learn.microsoft.com/en-us/windows/privacy/configure-windows-diagnostic-data-in-your-organization)

Next, see the frequently asked questions about diagnostic and usage data for Configuration Manager:

[Frequently asked questions](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/frequently-asked-questions)
