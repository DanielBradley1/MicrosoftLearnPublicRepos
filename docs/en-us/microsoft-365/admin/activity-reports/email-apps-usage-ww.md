<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/email-apps-usage-ww?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# Exchange email app usage report

The Exchange email app usage report provides details about how many email apps connect to Exchange Online. You can view the version information of Outlook apps that users are using. This information helps you follow up with those users who are using unsupported versions to install supported versions of Outlook.

For general information about usage reports in the Microsoft 365 admin center, and to see a list of all available reports, see [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide).

## View the Exchange email app usage report in the Microsoft 365 admin center

For information about the roles needed to view usage reports, see "Before you begin" in [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#before-you-begin)

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the navigation menu, select **Reports**. If you don't see **Reports**, select **Show all**, and then select **Reports**.
3. Select [Usage](https://go.microsoft.com/fwlink/p/?linkid=2074756).
4. On the **Usage** page, under **Reports**, select **Exchange**, and then select the **Email app usage** tab.

## Interpret the Exchange email app usage report

The report displays trends over the last 7, 30, 90, or 180 days. However, if you select a particular day in the report, the table shows data for up to 28 days from the current date, not the date the report generated. The data in each report usually covers up to the last 24 to 48 hours.

[![Screenshot of the Exchange email app usage report showing connected apps and Outlook versions in Microsoft 365.](https://learn.microsoft.com/en-us/microsoft-365/media/email-apps-report.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/email-apps-report.png?view=o365-worldwide#lightbox)

The **Users** chart shows the number of unique users that connected to Exchange Online by using any email app. The Y axis is the total count of unique users that connected to an app on any day of the reporting period. The X axis is the number of unique users that used the app for that reporting period.

The **Apps** chart shows the number of unique users by app over the selected time period. The Y axis is the total count of unique users who used a specific app during the reporting period. The X axis is the list of apps in your organization.

The **Versions** chart shows the number of unique users for each version of Outlook in Windows. The Y axis is the total count of unique users using a specific version of Outlook desktop. If the report can't resolve the version number of Outlook, the quantity shows as **Undetermined**. The X axis is the list of apps in your organization.

You can filter the series you see on the charts by selecting an item in the legend. You might not see all the items in the list in the columns until you add them.

To add or remove columns from the report, select **Choose columns**.

[![Screenshot of the Exchange Email apps usage report column options.](https://learn.microsoft.com/en-us/microsoft-365/media/041bd6ff-27e8-409d-9608-282edcfa2316.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/041bd6ff-27e8-409d-9608-282edcfa2316.png?view=o365-worldwide#lightbox)

To export the report data into an Excel .csv file, select **Export**. This action exports the usage data of all users and enables you to do simple sorting, filtering, and searching for further analysis.

The following table contains definitions of the metrics available in the report.

| Metric | Definition |
| :--- | :--- |
| Username | The name of the email app's owner. |
| Last activity date | The latest date the user read or sent an email message. |
| Mac mail, Mac Outlook, Outlook, Outlook mobile, and Outlook on the web | Examples of email apps you might have in your organization. |

Note

By default, user-specific information like usernames, display names, groups, and sites is hidden in usage reports. To learn how to display this information in usage reports, see [Show user, group, or site details in usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#show-user-group-or-site-details-in-usage-reports).
