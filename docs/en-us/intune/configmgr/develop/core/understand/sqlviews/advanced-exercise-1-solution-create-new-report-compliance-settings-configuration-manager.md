<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-1-solution-create-new-report-compliance-settings-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Advanced exercise 1 solution: Create a new report for compliance settings in Configuration Manager

Use the following procedure to create the report in [Advanced exercise 1: Create a new report for compliance settings in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-1-create-new-report-compliance-settings-configuration-manager).

Note

Depending on your experience at creating SQL Server reports, there are numerous paths you can use to create a report. You can use your preferred method of creating reports if you prefer.

## To create the status of configuration baselines deployed to a specified computer report

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then select **Reports**.
3. In the **Home** tab, in the **Create** group, select **Create Report**.
4. On the **Information** page of the Create Report Wizard, select **SQL-based Report**, and then supply the following information:

   - **Name:** Enter **Status of configuration baselines deployed to a specified computer**.
   - **Description:** Enter **Displays the name and description of the configuration baselines that are deployed to a specific computer and whether the computer returns compliant or noncompliant for the configuration baseline**.
   - **Server:** This field is automatically entered. Ensure that it matches the name of your Reporting Server.
   - **Path:** Select **Browse** to select the folder in which the new report will be stored. For this exercise, select **Compliance and Settings Management**.

5. To continue, select **Next**.
6. On the **Summary** page of the Create Report Wizard, review the information and then select **Next**.
7. On the **Completion** page of the Create Report Wizard, review the actions that were taken, and then select **Close**. Report Builder now opens to allow you to construct the report.
8. Next, you must create the datasets that this report will use to return results for the report. This report uses two datasets. The first of these is used to list computer names that can be selected to use as a basis for the report. The second contains the SQL statements for the report itself.

   In the **Report Data** pane, right-click **Datasets** and then select **Add Dataset**.
9. On the **Query** page of the **Dataset Properties** dialog box, supply a name for the dataset, or use the default name, and then select **Use a dataset embedded in my report**.
10. In the **Data source** drop-down list, select the data source you want to use for the report. This is typically automatically generated and will begin with **AutoGen\_**.
11. Select a query type of **Text**, and then enter the following query in the **Query** field.

    ```sql
    SELECT DISTINCT SYS.Netbios_Name0
    ��from v_R_System SYS WHERE SYS.Client0=1
    ��ORDER By SYS.Netbios_Name0
    ```

12. Select **OK** to close the **Dataset Properties** dialog box. The new dataset, named by default **DataSet1** is now displayed in the **Datasets** node of the **Report Data** pane.

    You have now created the query that the report parameter will use to return the available client names from which you can choose to run the report.
13. Next create the parameter that the report will use to let you select the computer that will be reported on.

    In the **Report Data** pane, right-click **Parameters**, and then select **Add Parameter**.
14. On the **General** page of the **Report Parameter Properties** dialog box, change the value in the **Prompt** field to read **Computer name**.
15. On the **Available Values** page of the **Report Parameter Properties** dialog box, select **Get values from a query**.
16. Select the following values:

    - **Dataset:** Choose **DataSet1**
    - **Value field:** Choose **Netbios\_Name0**
    - **Label field:** Choose **Netbios\_Name0**

17. Select **OK** to close the **Report Parameter Properties** dialog box. The new parameter **ReportParameter1** is displayed in the **Parameters** node of the **Report Data** pane.
18. At this point, run the report to check the parameter is working correctly. On the **Home** tab, in the **Views** group, select **Run**.
19. Verify that the **Computer name** field is shown. When you select this field, you should see all Windows client computers in the drop-down list.
20. On the **Home** tab, in the **Views** group, select **Design** to return to the design view.
21. Now, you must create the main dataset for the report.

    In the **Report Data** pane, right-click **Datasets** and then select **Add Dataset**.
22. On the **Query** page of the **Dataset Properties** dialog box, supply a name for the dataset, or use the default name, and then select **Use a dataset embedded in my report**.
23. In the **Data source** drop-down list, select the data source you want to use for the report. This is typically automatically generated and will begin with **AutoGen\_**.
24. Select a query type of **Text**, and then enter the following query in the **Query** field.

    ```sql
    SELECT v_CICurrentComplianceStatus.ComplianceState,
      v_LocalizedCIProperties.DisplayName, v_LocalizedCIProperties.Description, v_R_System.Netbios_Name0
    FROM v_CICurrentComplianceStatus INNER JOIN v_R_System ON
      v_CICurrentComplianceStatus.ResourceID = v_R_System.ResourceID
    INNER JOIN v_ConfigurationItems ON
      v_CICurrentComplianceStatus.CI_ID = v_ConfigurationItems.CI_ID
    INNER JOIN v_LocalizedCIProperties ON
      v_CICurrentComplianceStatus.CI_ID = v_LocalizedCIProperties.CI_ID
    WHERE (v_ConfigurationItems.CIType_ID = 2)
    ```

25. Select **OK** to close the **Dataset Properties** dialog box.
26. On the **Insert** tab, in the **Data Regions** group, select **Table**, and then select **Table Wizard**.
27. On the **New Table or Matrix** page of the wizard, select **Choose an existing dataset in this report or a shared dataset**, select **DataSet2** and then select **Next**.
28. On the **Arrange fields** page of the wizard, drag **ComplianceState**, **DisplayName**, **Description** and **Netbios\_Name0** from the **Available fields** pane, to the **Values** pane.
29. Select **Next** to see a preview of your report, and then select **Next** again.
30. On the **Choose a style** page of the wizard, choose one of the available themes for the report, and then select **Finish**.
31. On the **Home** tab, in the **Views** group, select **Run**.
32. In the **Computer name** field, select a computer from the drop-down list, and then select **View Report**.
33. Verify that the data in the report is as expected.
34. Save and close the report in Report Builder.

The new report is now available in the Configuration Manager console.

## Next steps

Report builder includes many options to change elements of reports, including themes, column headings and more. Consult your Report Builder help for more information.

## See also

[Advanced exercise 1: Create a new report for compliance settings in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-1-create-new-report-compliance-settings-configuration-manager)
