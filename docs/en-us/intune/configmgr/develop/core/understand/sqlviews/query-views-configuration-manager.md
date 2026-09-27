<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/query-views-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Query views in Configuration Manager

Configuration Manager has only one query view, **v\_Query**. It contains information about all the queries in the Configuration Manager hierarchy. The query ID, query name, comment, target class name, and the collection ID to which the query is limited, if applicable, are all listed.

The **v\_Query** view can be joined to the **v\_CollectionRuleQuery** collection view by using the **QueryID** column and to collection views by using the **LimitToCollectionID** column, which contains the same information as the **CollectionID** column in other views. It's also possible to join the query view to a security view so that the query name can be displayed when listing the class or instance permissions on the specific query object. An example is available in the section [Sample queries for queries in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-for-queries-configuration-manager).

## See also

[SQL Server views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sql-server-views-configuration-manager)
