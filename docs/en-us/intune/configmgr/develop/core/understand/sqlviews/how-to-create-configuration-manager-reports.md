<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/how-to-create-configuration-manager-reports -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to create Configuration Manager reports

You can create two types of reports directly from the Configuration Manager console:

- **Model-based report** � Allows you to create a report based on a Reporting Services model and select the attributes to be included with Report Builder.
- **SQL-based report** � Allows you to create a traditional report based directly off the database views by using SQL statements and stored procedures.

## To create a new model-based report

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then select **Reports**.
3. In the **Home** tab, in the **Create** group, select **Create Report**.
4. On the **Information** page of the Create Report Wizard, configure the following settings:

   - **Type:** Select **Model-based Report** to create a report in Report Builder by using a Reporting Services model.
   - **Name:** Specify a name for the report.
   - **Description:** Specify a description for the report.
   - **Server:** Displays the name of the report server on which you are creating this report.
   - **Path:** Select **Browse** to specify a folder in which you want to store the report.

5. On the **Model Selection** page of the wizard, select an available model in the list that you use to create this report. When you select the report model, the Preview section displays the SQL Server views and entities that are made available by the selected report model.
6. On the **Summary** page of the wizard, review the settings. Select **Previous** to change the settings or select **Next** to create the report.
7. On the **Completion** page of the wizard, select **Close** to exit the wizard, Report Builder now opens where you can configure the report settings. Enter your user account and password if you are prompted, and then select **OK**. If Report Builder is not installed on the computer, you are prompted to install it. Select **Run** to install Report Builder, which is required to modify and create reports.
8. In Report Builder, create the report layout, select data in the available SQL Server views, add parameters to the report, and so on. For more information about using Report Builder to create a new report, see the Report Builder Help.
9. Select **Run** to run your report. Verify that the report provides the information that you expect. Select **Design** to return to the Design view to modify the report, if needed.
10. Select **Save** to save the report to the report server. You can run and modify the new report in the **Reports** node in the **Monitoring** workspace.

## To create a new SQL-based report

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then select **Reports**.
3. In the **Home** tab, in the **Create** group, select **Create Report**.
4. On the **Information** page of the Create Report Wizard, configure the following settings:

   - **Type:** Select **SQL-based Report** to create a report in Report Builder by using SQL statements.
   - **Name:** Specify a name for the report.
   - **Description:** Specify a description for the report.
   - **Server:** Displays the name of the report server on which you are creating this report.
   - **Path:** Select **Browse** to specify a folder in which you want to store the report.

5. On the **Summary** page of the wizard, review the settings. Select **Previous** to change the settings or select **Next** to create the report.
6. On the **Completion** page of the wizard, select **Close** to exit the wizard, Report Builder now opens where you can configure the report settings. Enter your user account and password if you are prompted, and then select **OK**. If Report Builder is not installed on the computer, you are prompted to install it. Select **Run** to install Report Builder, which is required to modify and create reports.
7. In Microsoft Report Builder, create the report layout, select data in the available SQL Server views and add parameters to the report, and so on. For more information about using Report Builder to create a new report, see the Report Builder Help.
8. Select **Run** to run your report. Verify that the report provides the information that you expect. Select **Design** to return to the Design view to modify the report, if needed.
9. Select **Save** to save the report to the report server. You can run and modify the new report in the **Reports** node in the **Monitoring** workspace.

## See also

[How to run Configuration Manager reports](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/how-to-run-configuration-manager-reports)
