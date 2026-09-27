<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/software-metering-views-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Software metering views in Configuration Manager

The software metering views contain information such as the software metering rules that are created in the Configuration Manager hierarchy, which files to meter, the products in which the files belong, the users that have used the metered files, and more. Several of the status and status summarizer views also provide information about file usage. Most often, the software metering views can be joined to other views by using the **FileID** and **ResourceID** columns.

The following sections provide detailed information about software metering views and software metering status views.

## Software metering views

The software metering views are described in this section.

### v\_GS\_SoftwareUsageData

Lists the Configuration Manager client computers, by resource ID, that have used metered files. The view contains the start time, end time, user name, file ID, file name, file description, file version, file size, product name, product version, and more. The view can be joined to other views by using the **ResourceID**, **FileID**, and **UserName** columns.

### v\_MeterData

Lists all software metering data, including the meter data ID, time span for the data, file ID, resource ID, user ID, and more. The view can be joined to other views by using the **FileID**, **ResourceID**, and **MeteredUserID** columns.

### v\_MeteredFiles

Lists all files that are configured in the software metering rules and metered on clients. The view contains the software metering rule ID, security key, product name, site code, file name, file version, metered file ID, metered product ID, and more. The view can be joined to other views by using the **RuleID**, **SecurityKey**, **MeteredProductID**, and **MeteredFileID** columns.

### v\_MeteredProductRule

Lists all software metering rules that have been configured in the Configuration Manager site hierarchy. The view contains the software metering rule ID, security key, product name, file name, file version, site code, and more. The view can be joined to other views by using the **RuleID** and **SecurityKey** columns.

### v\_MeteredUser

Lists all users who have used metered files. The view contains the metered user ID, full user name \(domain\\user name\), domain, and user name. The view can be joined to other views by using the **MeteredUserID** and **FullName** columns.

### v\_MeterRuleInstallBase

Lists all metered files for system resources that match files by FileID that are also in software inventory. The view contains the rule ID, product name, metered file ID, and resource ID. The view can be joined to other views by using the **RuleID**, **MeteredFileID**, and **ResourceID** columns.

## Software metering status views

The software metering status views contain status summary information about the file usage for metered files. For more information about the status views, see [Status and Alert Views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/status-alert-views-configuration-manager). The status views that contain software metering information are described in this section.

### v\_FileUsageSummary

Lists software metering summary status information for file usage by site. The view can be joined to other views by using the **FileID** column.

### v\_FileUsageSummaryIntervals

Lists software metering summary interval information for file usage. It is unlikely that this view will be joined to other views.

### v\_MonthlyUsageSummary

Lists the Configuration Manager client computers, by resource ID, and the usage summary for metered files, as well as the logged-on user name, usage time, and time of last usage. The view can be joined to other views by using the **ResourceID**, **FileID**, and **MeteredUserID** columns.

## See also

[SQL Server views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sql-server-views-configuration-manager)
