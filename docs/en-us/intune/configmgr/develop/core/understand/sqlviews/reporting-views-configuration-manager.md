<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/reporting-views-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Reporting views in Configuration Manager

Reporting in Configuration Manager uses the SQL Server Reporting Services \(SSRS\) to store and generate reports. For this reason, information about built-in and user-created reports is stored in the SQL Server Reporting Services database and not the Configuration Manager database.

You can run the following query against your Reporting Services database to retrieve a list of the built-in and user-created reports at your site.

```sql
    SELECT *
    FROM <report server name>.dbo.Catalog
    ORDER BY Name
```

For more information about the built-in reports supplied with Configuration Manager, see [List of reports in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/list-of-reports).

## See also

[SQL Server views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sql-server-views-configuration-manager)
