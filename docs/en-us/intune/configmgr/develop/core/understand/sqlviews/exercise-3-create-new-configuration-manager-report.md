<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/exercise-3-create-new-configuration-manager-report -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Exercise 3: Create a new Configuration Manager report

In this exercise, you'll create a simple report in Microsoft SQL Server Report Builder, and configure the report properties.

The report displays all collections that administrative users have created, and excludes the built-in collections. The results will display the collection ID and name, the last collection refresh time and the date of the last collection membership change.

## To create a new report

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then select **Reports**.
3. In the **Home** tab, in the **Create** group, select **Create Report**.
4. On the **Information** page of the Create Report Wizard, select **SQL-based Report**, and then configure the following properties:

   - **Name:** Enter **All collections created by administrative users**.
   - **Description:** Enter **Displays all collections that were created by an administrative user \(excludes built-in collections\).**
   - **Path:** Select **Browse**, and then select the **Site � General** folder to store the report.

5. Select **Next**.
6. On the **Summary** page of the Create Report Wizard, review the actions that will be taken and then select **Next**.
7. On the **Completion** page of the wizard, review any messages and then select **Close**.
8. Report Builder opens. In the **Report Data** pane, right-click **Datasets**, and then select **Add Dataset**.
9. On the **Query** page of the **Dataset Properties** dialog box, select **Use a dataset embedded in my report**.
10. In the **Data source** drop-down list, select the data source you want to use for the report. This is typically automatically generated and will begin with **AutoGen\_**.
11. Select a query type of **Text**, and then enter the following query in the **Query** field.

    ```sql
    SELECT
    v_Collections.CollectionID,
    v_Collections.CollectionName, 
    v_Collections.LastRefreshTime, 
    v_Collections.LastMemberChangeTime
    FROM
    V_Collections
    WHERE
    IsBuiltIn=0
    ```

12. Select **OK** to close the **Dataset Properties** dialog box.
13. In Report Builder, on the **Insert** tab, in the **Data Regions** group, select **Table**, and then select **Table Wizard**.
14. On the **Choose a dataset** page of the **New Table or Matrix** wizard, select **Choose an existing dataset in this report or a shared dataset**, and then select the dataset you previously created, **Dataset1**.
15. Select **Next**.
16. On the **Arrange fields** page of the **New Table or Matrix** wizard, drag **CollectionID**, **CollectionName**, **LastRefreshTime** and **LastMemberChangeTime** from the **Available fields** field to the **Values** field.
17. Select **Next**.
18. On the **Choose the layout** page of the **New Table or Matrix** wizard, select **Next**.
19. On the **Choose a style** page of the wizard, choose one of the available themes for the report, and then select **Finish**.
20. Verify that the data in the report is as expected.
21. Save and close the report in Report Builder.

The new report is now available in the Configuration Manager console.

## Next steps

Report builder includes many options to change elements of reports, including themes, column headings and more. Consult your Report Builder help for more information.

## See also

[Exercise 1: Run an existing Configuration Manager report](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/exercise-1-run-existing-configuration-manager-report)
