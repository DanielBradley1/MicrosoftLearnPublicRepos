<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/project-activity?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Project Activity report

Use the Project Activity report to quickly answer three questions:

- Who is actively using Project?
- Which client are they using \(web or desktop\)?
- How much project and task activity is happening?

To jump to details, go to [View the Project Activity report in the Microsoft 365 admin center](#view-the-project-activity-report-in-the-microsoft-365-admin-center) or [User activity table](#user-activity-table).

For general information about usage reports in the Microsoft 365 admin center, and to see a list of all available reports, see [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide).

## View the Project Activity report in the Microsoft 365 admin center

For information about the roles needed to view usage reports, see "Before you begin" in [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#before-you-begin)

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the navigation menu, select **Reports**. If you don't see **Reports**, select **Show all**, and then select **Reports**.
3. Select [Usage](https://go.microsoft.com/fwlink/p/?linkid=2074756).
4. On the **Usage** page, under **Reports**, select **Project**.

## Interpret the Project Activity report

Use the Project Activity report to see the activity and usage of Project in your organization.

Use the report timeline to analyze usage over **7, 30, 90, or 180 days**.

- Selecting a specific day updates the per-user table for that day.
- Daily drill-down is available only for the most recent **28 days**.

[![Screenshot of the Microsoft Project activity report.](https://learn.microsoft.com/en-us/microsoft-365/media/project-activity.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/project-activity.png?view=o365-worldwide#lightbox)

The Project activity report contains four summary charts. Start with **Active users** for adoption trends, then use **Project Activity** and **Task activity** for deeper engagement signals:

- **Active users** - Shows the daily active users on each day over time. Currently, this chart includes only Project for the Web and Project Online desktop client.
- **Active users \(by client\)** - Shows the daily active users on each day over time, broken out by client \(Project for the Web vs. Project Online desktop client\).
- **Project Activity** - Shows the number of daily sessions of Project over time, for each client \(Project for the Web and Project Online desktop client\).
- **Task activity** - Shows the daily number of tasks created or edited over time in Project for the Web

The report also has a table that shows activity for each Project user in your environment.

To add or remove columns from the report, select **Choose columns**.

[![Screenshot of the Project activity report column options.](https://learn.microsoft.com/en-us/microsoft-365/media/project-activity-columns.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/project-activity-columns.png?view=o365-worldwide#lightbox)

To export the report data into an Excel .csv file, select **Export**. This action exports the usage data of all users and enables you to do simple sorting, filtering, and searching for further analysis.

### Privacy settings affect on the dashboard

If users or admins set their privacy settings to **Neither**, the **Project activity** chart for the Project Online desktop client doesn't show accurate metrics. The numbers are undercounted. For more information on privacy settings, see [Use policy settings to manage privacy controls for Microsoft 365 Apps for enterprise](https://learn.microsoft.com/en-us/deployoffice/privacy/manage-privacy-controls).

### User activity table

The following table contains definitions of the metrics available in the report.

| Metric | Definition |
| :--- | :--- |
| User name | The user's principal name. |
| Display name | The full name of the user. |
| Last activity date | The latest date the user in that row had activity in Project, including any of the activities in the summary reports. |
| Projects visited \(Desktop\) | The number of projects opened by the user in the Project Online desktop client during the time range selected in the top right of the page. |
| Projects visited \(Web\) | The number of projects visited by the user in Project for the Web during the time range selected in the top right of the page. |
| Tasks created \(Web\) | The number of tasks created by the user in Project for the Web during the time range selected in the top right of the page. |
| Tasks edited \(Web\) | The number of tasks edited by the user in Project for the Web during the time range selected in the top right of the page. |
| Other | This value is true if the user performed an activity in Project Online desktop client or in Project for the Web \(that isn't covered by the other columns\) during the time range selected at the top of the page. If the user didn't perform any activity during this time, this value is false. |

Note

By default, user-specific information like usernames, display names, groups, and sites is hidden in usage reports. To learn how to display this information in usage reports, see [Show user, group, or site details in usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#show-user-group-or-site-details-in-usage-reports).
