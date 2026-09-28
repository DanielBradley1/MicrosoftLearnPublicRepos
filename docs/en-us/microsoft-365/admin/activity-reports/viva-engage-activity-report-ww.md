<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/viva-engage-activity-report-ww?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Viva Engage Activity report

The Viva Engage Activity report helps you understand the level of engagement of your organization with Viva Engage by looking at the number of unique users who use Viva Engage to post, like, or read a message and the amount of activity generated across the organization.

For general information about usage reports in the Microsoft 365 admin center, and to see a list of all available reports, see [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide).

## View the Viva Engage Activity report in the Microsoft 365 admin center

For information about the roles needed to view usage reports, see "Before you begin" in [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#before-you-begin)

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the navigation menu, select **Reports**. If you don't see **Reports**, select **Show all**, and then select **Reports**.
3. Select [Usage](https://go.microsoft.com/fwlink/p/?linkid=2074756).
4. On the **Usage** page, under **Reports**, select **Viva Engage**.
5. On the report page, select the **Activity** tab.

## Interpret the Viva Engage Activity report

The report displays trends over the last 7, 30, 90, or 180 days. However, if you select a particular day in the report, the table shows data for up to 28 days from the current date, not the date the report generated.

[![Screenshot of the Microsoft Viva Engage activity report.](https://learn.microsoft.com/en-us/microsoft-365/media/9b251183-c2b3-430c-ab2d-58bf11e7e3ae.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/9b251183-c2b3-430c-ab2d-58bf11e7e3ae.png?view=o365-worldwide#lightbox)

To add or remove columns from the report, select **Choose columns**.

[![Screenshot of the Viva Engage activity report column options.](https://learn.microsoft.com/en-us/microsoft-365/media/7ef6351d-f7e9-4504-913d-2c2df9062bf6.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/7ef6351d-f7e9-4504-913d-2c2df9062bf6.png?view=o365-worldwide#lightbox)

To export the report data into an Excel .csv file, select **Export**. This action exports the usage data of all users and enables you to do simple sorting, filtering, and searching for further analysis.

| Metric | Definition |
| :--- | :--- |
| Username | The email address of the user. You can display the actual email address or make this field anonymous. This grid shows users who logged into Viva Engage using the Microsoft 365 account or who logged into the network using single sign-on. |
| Display name | The full name of the user. You can display the actual email address or make this field anonymous. |
| User state | One of three values: Activated, Deleted, or Suspended. These reports show data for active, suspended, and deleted users. They don't reflect pending users, because pending users can't post, read, or like a message. |
| State change date \(UTC\) | The date on which the user's state was changed in Viva Engage. |
| Last activity date \(UTC\) | The last date that the user posted, read, or liked a message. |
| Posted | The number of messages the user posted during the time period you specified. |
| Read | The number of conversations that the user read during the time period you specified. |
| Liked | The number of messages that the user liked during the time period you specified. |
| Product assigned | The products that are assigned to this user. |

Note

By default, user-specific information like usernames, display names, groups, and sites is hidden in usage reports. To learn how to display this information in usage reports, see [Show user, group, or site details in usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#show-user-group-or-site-details-in-usage-reports).
