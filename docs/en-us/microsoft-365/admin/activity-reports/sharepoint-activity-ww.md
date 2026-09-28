<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/sharepoint-activity-ww?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-15 -->

# SharePoint Activity report

The SharePoint Activity report provides details about the activity of every licensed SharePoint user by looking at their interaction with files. The report helps you understand the level of collaboration by showing the number of files shared.

For general information about usage reports in the Microsoft 365 admin center, and to see a list of all available reports, see [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide).

## View the SharePoint activity report in the Microsoft 365 admin center

For information about the roles needed to view usage reports, see "Before you begin" in [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#before-you-begin)

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the navigation menu, select **Reports**. If you don't see **Reports**, select **Show all**, and then select **Reports**.
3. Select [Usage](https://go.microsoft.com/fwlink/p/?linkid=2074756).
4. On the **Usage** page, under **Reports**, select **SharePoint**.
5. On the report page, select the **Activity** tab.

## Interpret the SharePoint Activity report

The report displays trends over the last 7, 30, 90, or 180 days. However, if you select a particular day in the report, the table shows data for up to 28 days from the current date, not the date the report generated.

[![Screenshot of the SharePoint activity report.](https://learn.microsoft.com/en-us/microsoft-365/media/5a0a96f-0e4f-4fb9-8baa-3262275b3d1f.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/5a0a96f-0e4f-4fb9-8baa-3262275b3d1f.png?view=o365-worldwide#lightbox)

To add or remove columns from the report, select **Choose columns**.

[![Screenshot of the columns available for the SharePoint activity report.](https://learn.microsoft.com/en-us/microsoft-365/media/3c396cd1-9701-4712-8eaa-eb7bba702aa8.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/3c396cd1-9701-4712-8eaa-eb7bba702aa8.png?view=o365-worldwide#lightbox)

To export the report data into an Excel .csv file, select **Export**. This action exports the usage data of all users and enables you to do simple sorting, filtering, and searching for further analysis.

The following table contains definitions of the metrics available in the report.

| Metric | Definition |
| :--- | :--- |
| Username | The email address of the user who performed the activity on the SharePoint Site. |
| Last activity date \(UTC\) | The latest date a file activity was performed or a page was visited for the selected date range. To see activity that occurred on a specific date, select the date directly in the chart. |
| Files viewed or edited | The number of files that the user uploaded, downloaded, modified, or viewed. |
| Files synced | The number of files that are synced from a user's local device to the SharePoint site. |
| Files shared internally | The count of files that are shared with users within the organization, or with users within groups \(that might include external users\). |
| Files shared externally | The number of files that are shared with users outside of the organization. |
| Pages visited | The visits to unique pages by the user. |
| Deleted | This value indicates that the user's license was removed.  <br>  <br>**NOTE:** Activity for a deleted user still displays in the report as long as the user was licensed at some time during the selected time period. The Deleted column helps you to note that the user might no longer be active, but contributed to the data in the report. |
| Deleted date | The date when the user's license was removed. |
| Product assigned | The Microsoft 365 products that are licensed to the user. |

Note

By default, user-specific information like usernames, display names, groups, and sites is hidden in usage reports. To learn how to display this information in usage reports, see [Show user, group, or site details in usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#show-user-group-or-site-details-in-usage-reports).
