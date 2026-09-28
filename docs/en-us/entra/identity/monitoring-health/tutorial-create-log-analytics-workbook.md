<!-- Source: https://learn.microsoft.com/en-us/entra/identity/monitoring-health/tutorial-create-log-analytics-workbook -->
<!-- Sitemap-Last-Modified: 2025-04-14 -->

# Tutorial: Create a custom workbook for Microsoft Entra ID

In this tutorial, you learn how to:

- Create a custom workbook
- Add a query to an existing workbook template

## Prerequisites

To analyze activity logs with Log Analytics, you need the following roles and requirements:

- [Microsoft Entra monitoring and health licensing](https://learn.microsoft.com/en-us/entra/fundamentals/licensing#microsoft-entra-monitoring-and-health)
- [Access to create a Log Analytics workspace](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/manage-access)
- The appropriate role for Azure Monitor:

  - Monitoring Reader
  - Log Analytics Reader
  - Monitoring Contributor
  - Log Analytics Contributor

- The appropriate role for Microsoft Entra ID:

  - Reports Reader
  - Security Reader
  - Global Reader
  - Security Administrator

If you haven't already created a Log Analytics workspace, complete the [Configure Log Analytics workspace](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/tutorial-configure-log-analytics-workspace) tutorial.

## Create a custom workbook

In addition to querying the data with Kusto Query Language \(KQL\), you can create a custom workbook for further analysis and alerting. The least privileged role to create or update a workbook is the **Security Administrator** role.

1. Browse to **Entra ID** > **Monitoring & health** > **Workbooks**.
2. In the **Quickstart** section, select **Empty**.

   ![Screenshot of the blank workbook in the Quick start section.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/tutorial-create-log-analytics-workbook/quick-start.png)

3. From the **Add** menu, select **Add text**.

   ![Screenshot of the Add text menu option.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/tutorial-create-log-analytics-workbook/add-text.png)

4. In the textbox, enter `# Client apps used in the past week` and select **Done Editing**.

   ![Screenshot shows the text and the Done Editing button.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/tutorial-create-log-analytics-workbook/workbook-text.png)

5. Below the text window, open the **Add** menu and select **Add query**.

   ![Screenshot of the Add query menu option.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/tutorial-create-log-analytics-workbook/add-query.png)

6. In the query textbox, enter: `SigninLogs | where TimeGenerated > ago(7d) | project TimeGenerated, UserDisplayName, ClientAppUsed | summarize count() by ClientAppUsed`
7. Select **Run Query**.

   ![Screenshot shows the Run Query button.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/tutorial-create-log-analytics-workbook/run-workbook-query.png)

8. In the toolbar, from the **Visualization** menu select **Pie chart**.

   ![Screenshot showing the Pie chart menu option.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/tutorial-create-log-analytics-workbook/pie-chart.png)

9. Select **Done Editing** at the top of the page.
10. Select the **Save** icon to save your workbook.
11. In the dialog box that appears, enter a title, select a Resource group, and select **Apply**.

## Add a query to a workbook template

You can add Kusto queries to your workbook. The example is based on a query that shows the distribution of successful and failed sign-ins with applied Conditional Access policies. The least privileged role to create or update a workbook is the **Security Administrator** role.

1. Browse to **Entra ID** > **Monitoring & health** > **Workbooks**.
2. In the **Conditional Access** section, select **Conditional Access Insights and Reporting**.

   ![Screenshot shows the Conditional Access Insights and Reporting option.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/tutorial-create-log-analytics-workbook/conditional-access-template.png)

3. In the toolbar, select **Edit**.

   ![Screenshot shows the Edit button.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/tutorial-create-log-analytics-workbook/edit-workbook-template.png)

4. In the toolbar, select the three dots next to the Edit button, then **Add**, and then **Add query**.

   ![Add workbook query](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/tutorial-create-log-analytics-workbook/add-custom-workbook-query.png)

5. In the query textbox, enter: `SigninLogs | where TimeGenerated > ago(20d) | where ConditionalAccessPolicies != "[]" | summarize dcount(UserDisplayName) by bin(TimeGenerated, 1d), ConditionalAccessStatus`
6. Select **Run Query**.

   ![Screenshot shows the Run Query button to run this query.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/tutorial-create-log-analytics-workbook/run-workbook-insights-query.png)

7. From the **Time Range** menu, select **Set in query**.
8. From the **Visualization** menu, select **Bar chart**.
9. Select **Advanced Settings**.

   ![Screenshot of the time range, visualization, and advanced setting options.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/tutorial-create-log-analytics-workbook/select-query-options.png)

10. In the **Chart title** field, enter `Conditional Access status over the last 20 days` and select **Done Editing**.

    ![Set chart title](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/tutorial-create-log-analytics-workbook/set-chart-title.png)

Your Conditional Access success and failure chart displays a color-coded snapshot of your tenant.

## Related content

- [Configure Log Analytics workspace](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/tutorial-configure-log-analytics-workspace)
- [Configure diagnostic settings](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-configure-diagnostic-settings)
- [Integrate activity logs with Log Analytics](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-integrate-activity-logs-with-azure-monitor-logs)
