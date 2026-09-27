<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/frequently-asked-questions -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Frequently asked questions about diagnostics and usage data

*Applies to: Configuration Manager \(current branch\)*

This article provides answers to frequently asked questions about diagnostic and usage data in Configuration Manager.

## Can I turn off diagnostic and usage data?

To help manage when the site sends data, use the service connection point in offline mode. Then use the service connection tool to manually send data. For more information, see the following articles:

- [About the service connection point](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point)
- [Use the service connection tool](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/use-the-service-connection-tool)

To support new versions of Windows and cloud services like Microsoft Intune, you need to update the current branch of Configuration Manager on a regular basis. Microsoft requires at least the basic level of diagnostic and usage data. This data is used to keep the product up to date, improve the update experience, and improve the quality and security of the product.

No data is sent to the service when the service connection point is in offline mode. When you switch to online mode or use the service connection tool, it sends data to the service to check for updates.

You can also choose the level of data that Configuration Manager collects. For more information, see [Levels of diagnostic usage data](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/levels-overview).

## What is the data retention period?

Microsoft stores Configuration Manager diagnostic and usage data for one year.

## Is diagnostics and usage data sent when setup runs?

No. Diagnostics and usage data is only sent after the site is installed and operational.

## How frequently is the data sent?

The SQL Server stored procedures run every seven days from the date you installed the site.

- In online mode, the service connection point uploads the data after the queries run.
- In offline mode, you use the service connection tool to upload the data. \(The data isn't initially available for offline use until seven days after you install the site.\)

## Can the data be used to form a network map?

No. This data doesn't include any network details, such as IP addresses or detailed geographic information. For more information, see [Diagnostic and usage data for supported versions](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection).

The data does include time zone information from each site. This information can provide insight into the broad geolocation and global dispersion of sites in a hierarchy.

## Can you see data in custom SQL Server tables?

No. Configuration Manager collects diagnostics and usage data via SQL Server stored procedures. These stored procedures run against default product tables in the database. All of these SQL Server tables are prefixed with **TEL\_**. As part of the SQL Server schema detection query, all table names are hashed for comparison against the known defaults. This behavior determines that custom tables exist in the database. The presence of custom tables informs Microsoft that you extended the database schema from the default. It doesn't include any of the data stored within those tables.

## Can you see other databases?

No. The stored procedures to collect data are limited to the Configuration Manager site database. Microsoft can't see the names of other databases, or any data in other databases.

## Is any data sent to other integrated cloud services?

Yes, when you integrate those services with Configuration Manager. As part of the interaction with any cloud service, Configuration Manager sends some data to that service. This data is specific to that cloud service, and separate from Configuration Manager diagnostics and usage data. For more information on the specific data used in the interaction with another cloud service, see the documentation for that service.

For example, the following cloud services are a part of Microsoft Intune family of products:

- [Tenant attach data collection](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/data-collection)
- [Endpoint analytics data collection](https://learn.microsoft.com/en-us/intune/endpoint-analytics/ref-data-collection)
- [Privacy and personal data in Intune](https://learn.microsoft.com/en-us/mem/intune-service/protect/privacy-personal-data)
- [Windows Autopilot requirements](https://learn.microsoft.com/en-us/windows/deployment/windows-autopilot/windows-autopilot-requirements)

## Does Configuration Manager collect any personal data?

No. Configuration doesn't collect or transmit any personal data or customer data. It's an on-premises product that you directly deploy, manage, and operate. The diagnostics and usage data that Microsoft collects improves the installation experience, quality, and security of future releases.

For more information about Configuration Manager data, see [Levels of diagnostic usage data](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/levels-overview).
