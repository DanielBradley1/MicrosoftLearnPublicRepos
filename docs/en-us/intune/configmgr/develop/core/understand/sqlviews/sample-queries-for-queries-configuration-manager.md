<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-for-queries-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Sample queries for the query view in Configuration Manager

The following sample query demonstrates how the query view can be joined to a security view. In most cases, the **v\_Query** view won't be used in reports.

## Joining query and security views

The following query lists the query ID, query name, user name, and instance permissions for the user on the query object. The **v\_Query** view is joined to the **v\_UserInstancePermNames** security view by using the **QueryID** from **v\_Query** and **InstanceKey** from **v\_UserInstancePermNames**. Because there might be other secured objects with the same value as the **InstanceKey** \(for example, MCM00001 could be a custom query or a package\), the query also filters specifically for query objects by using the WHERE clause and an **ObjectKey** value of 7.

```sql
    SELECT Q.QueryID, Q.Name AS QueryName, UIP.UserName, UIP.PermissionName 
    FROM v_Query Q INNER JOIN v_UserInstancePermNames UIP 
    ON Q.QueryID = UIP.InstanceKey 
    WHERE UIP.ObjectKey = 7 
    ORDER BY Q.Name, UIP.UserName 
```

## See also

[Query views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/query-views-configuration-manager)
