<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/visio-activity?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# Visio Activity report

The Visio Activity report provides insight into the activity of every Visio user in your organization.

For general information about usage reports in the Microsoft 365 admin center, and to see a list of all available reports, see [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide).

## View the Visio Activity report in the Microsoft 365 admin center

For information about the roles needed to view usage reports, see "Before you begin" in [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#before-you-begin)

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the navigation menu, select **Reports**. If you don't see **Reports**, select **Show all**, and then select **Reports**.
3. Select [Usage](https://go.microsoft.com/fwlink/p/?linkid=2074756).
4. On the **Usage** page, under **Reports**, select **Visio**.

## Interpret the Visio Activity report

The report displays trends over the last 7, 30, 90, or 180 days. If you select a particular day in the report, the per-user data table updates to display users' usage for that day.

Note

The Visio report currently becomes available within 72 hours. Microsoft is working to reduce the latency to 48 hours like other reports.

[![Screenshot of the Visio activity report.](https://learn.microsoft.com/en-us/microsoft-365/media/visio-activity-charts.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/visio-activity-charts.png?view=o365-worldwide#lightbox)

- **Active users** Shows the daily active users on each day over time. This metric includes Visio for the web and Visio desktop app usage.
- **Platforms** Shows the daily active users on each day over time, broken down by platform: Web and Desktop.
- **Platforms \(total users\)** Shows the aggregated active users for the selected time window, broken down by platform: Web and Desktop.

To export the report data into an Excel .csv file, select **Export**. This action exports the usage data of all users and enables you to do simple sorting, filtering, and searching for further analysis.

### Visio licensed usage

Use this report to filter for Visio licensed usage. Each of the charts includes a filter to select the user segment.

- **All users** Shows the usage for Visio licensed users, including Visio Plan 1 and Visio Plan 2, and seeded usage, such as using Visio that comes as part of a Microsoft 365 commercial subscription.
- **Visio licensed users** Shows the usage for Visio licensed users only, including Visio Plan 1 and Visio Plan 2.

[![Licensed users filter for the Visio activity report in Microsoft 365.](https://learn.microsoft.com/en-us/microsoft-365/media/visio-license-filter.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/visio-license-filter.png?view=o365-worldwide#lightbox)

Note

[Learn more about Visio seeded capabilities](https://www.microsoft.com/microsoft-365/visio/visio-in-microsoft-365), and about [Visio plans and pricing](https://www.microsoft.com/microsoft-365/visio/microsoft-visio-plans-and-pricing-compare-visio-options?rtc=1&activetab=tabs%3aprimaryr1).

### User details table

The report includes a table that shows the user details with active usage in your environment during the selected time window.

The following table contains definitions of the metrics available in the report.

| Metric | Definition |
| --- | --- |
| User name | The user principal name |
| Display name | The full name of the user |
| Last activity date | The latest date the user in that row had activity in Visio, including any of the activities in the summary reports |
| Desktop | This metric indicates whether that user used the Visio desktop app at least once during the selected time window |
| Web | This metric indicates whether that user used Visio for the web at least once during the selected time window |

Note

By default, user-specific information like usernames, display names, groups, and sites is hidden in usage reports. To learn how to display this information in usage reports, see [Show user, group, or site details in usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#show-user-group-or-site-details-in-usage-reports).
