<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/viva-engage-device-usage-report-ww?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Viva Engage Device usage report

The Viva Engage Device usage report helps you understand which devices your users prefer for accessing Viva Engage. Use this data to identify adoption patterns across web, mobile, and other platforms—so you can optimize your deployment strategy and support for each device type.

For general information about usage reports in the Microsoft 365 admin center, and to see a list of all available reports, see [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide).

## View the Viva Engage Device usage report in the Microsoft 365 admin center

For information about the roles needed to view usage reports, see "Before you begin" in [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#before-you-begin)

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the navigation menu, select **Reports**. If you don't see **Reports**, select **Show all**, and then select **Reports**.
3. Select [Usage](https://go.microsoft.com/fwlink/p/?linkid=2074756).
4. On the **Usage** page, under **Reports**, select **Viva Engage**.
5. On the report page, select the **Device usage** tab.

## Interpret the Viva Engage Device usage report

The report displays trends over the last 7, 30, 90, or 180 days. However, if you select a particular day in the report, the table shows data for up to 28 days from the current date, not the date the report generated.

[![Screenshot of the Microsoft Viva Engage device usage report.](https://learn.microsoft.com/en-us/microsoft-365/media/e21af4c0-0ad2-4485-8ab1-2f82d7dfa90e.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/e21af4c0-0ad2-4485-8ab1-2f82d7dfa90e.png?view=o365-worldwide#lightbox)

To add or remove columns from the report, select **Choose columns**.

[![Screenshot of the Microsoft Viva Engage device usage report column options.](https://learn.microsoft.com/en-us/microsoft-365/media/fc1fc8db-e197-4878-85c7-7ba0d67b9379.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/fc1fc8db-e197-4878-85c7-7ba0d67b9379.png?view=o365-worldwide#lightbox)

To export the report data into an Excel .csv file, select **Export**. This action exports the usage data of all users and enables you to do simple sorting, filtering, and searching for further analysis.

| Metric | Definition |
| :--- | :--- |
| Username | The email address of the user. You can display the actual email address or make this field anonymous. This grid shows users who logged in to Viva Engage using the Microsoft 365 account or who logged in to the network using single sign-on. |
| Display name | The full name of the user. You can display the actual email address or make this field anonymous. |
| User state | One of three values: Active, Deleted, or Suspended. These reports show data for active, suspended, and deleted users. They don't reflect pending users, because pending users can't post, read, or like a message. |
| State change date \(UTC\) | The date on which the user's state was changed in Viva Engage. |
| Last activity date \(UTC\) | The last date \(UTC\) that the user participated in a Viva Engage activity. |
| Web | Indicates if the user used Viva Engage on the web. |
| Windows phone | Indicates if the user used Viva Engage on a Windows phone. |
| Android phone | Indicates if the user used Viva Engage on an Android phone. |
| iPhone | Indicates if the user used Viva Engage on an iPhone. |
| iPad | Indicates if the user used Viva Engage on an iPad. |
| other | Indicates if the user used Viva Engage on another client, which wasn't listed previously. This metric includes Viva Engage Embed, SharePoint Web Part, Viva Engage, and select Outlook emails. |

Note

By default, user-specific information like usernames, display names, groups, and sites is hidden in usage reports. To learn how to display this information in usage reports, see [Show user, group, or site details in usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#show-user-group-or-site-details-in-usage-reports).
