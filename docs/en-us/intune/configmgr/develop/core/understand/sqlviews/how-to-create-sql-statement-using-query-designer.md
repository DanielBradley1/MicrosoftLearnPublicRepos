<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/how-to-create-sql-statement-using-query-designer -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to create a SQL statement by using query designer

Query Designer in SQL Server can help you to more easily write SQL queries that can be used in your Configuration Manager reports. Use the following procedures to create Configuration Manager report queries using Query Designer.

## To create a new SQL query in query designer

1. Start Microsoft SQL Server Management Studio.
2. Navigate to *<Computer Name>*�**\\ Databases \\**�*<Configuration Manager database name>*�**\\ Views\*\*.
3. Right-click **Views** and then select **New View**.
4. In the **Add Table** dialog box, select the **Views** tab and then select the views that you want to include in the SQL query.

   Note

   You can select multiple views by holding down the CTRL key.
5. In the design view of query designer, select the columns you want to appear in the report. If you are querying multiple views, you can join these by selecting a column in one view and dragging this over to the same column in another view.
6. Select **Execute SQL** to test the query and see the results.
7. When you are happy with the results returned by the query, copy and paste it from query designer to be used to create your report in Report Builder.

## See also

[SQL statement reference for Configuration Manager reports](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sql-statement-reference-configuration-manager-reports)
