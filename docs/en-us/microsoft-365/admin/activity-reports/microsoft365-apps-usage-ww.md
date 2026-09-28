<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft365-apps-usage-ww?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Microsoft 365 apps Usage report

Use the Microsoft 365 apps Usage report to understand how licensed users engage with core Microsoft 365 apps across Windows, Mac, web, and mobile. This article explains how to open the report, interpret user and platform trends, review Outlook for Windows migration progress, and use per-user activity data to support adoption and planning decisions.

Note

Shared computer activations aren't included in this report.

For general information about usage reports in the Microsoft 365 admin center, and to see a list of all available reports, see [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide).

## View the Microsoft 365 apps Usage report in the Microsoft 365 admin center

For information about the roles needed to view usage reports, see "Before you begin" in [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#before-you-begin)

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the navigation menu, select **Reports**. If you don't see **Reports**, select **Show all**, and then select **Reports**.
3. Select [Usage](https://go.microsoft.com/fwlink/p/?linkid=2074756).
4. On the **Usage** page, under **Reports**, select **Microsoft 365 apps**.
5. On the reports page, select the **Usage** tab.

## Interpret the Microsoft 365 apps Usage report

The report displays trends over the last 7, 30, 90, or 180 days. However, if you select a particular day in the report, the table shows data for up to 28 days from the current date, not the date the report generated.

The data in each report usually covers up to the last two days. Every six days, the system refreshes the report with minor updates to ensure data quality.

You can view your users' Microsoft 365 apps activity by looking at the **Users** and **Platform** charts.

[![Screenshot of the Microsoft 365 Apps usage report in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/microsoft365-apps-usage-ww/microsoft-365-apps-usage-report.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/microsoft365-apps-usage-ww/microsoft-365-apps-usage-report.png?view=o365-worldwide#lightbox)

You can filter the series you see on the chart by selecting an item in the legend. For example, on the **Users** chart, select Outlook, Word, Excel, PowerPoint, OneDrive, or Teams to see only the info related to each one. Changing this selection doesn't change the info in the grid table below it.

### Users

The **Users** chart shows the trend in the number of active users for each app, including Outlook, Word, Excel, PowerPoint, OneNote, and Teams. "Active users" are any users who perform any intentional actions within these apps.

On the **Users** chart, the Y-axis is the number of unique active users for the respective app. The X-axis is the date on which an app was used on a given platform.

### Platforms

The **Platforms** chart shows the trend of active users across all apps for each platform - Windows, Mac, Web, and Mobile.

On the **Platforms** chart, the Y-axis is the number of unique users for the respective platform. The X-axis is the date on which an app was used on a given platform.

### Outlook for Windows migration progress

The **Outlook for Windows migration process** chart provides your organization with valuable insights into the adoption of the new Outlook for Windows, and trends in migration from the classic version to the new version.

All eligible licenses for Word, Excel, PowerPoint, and OneNote in this report include the following products:

- Office 365 Business
- Office Shared Computer Activation
- Office 365 Proplus for Device
- Office 365 Proplus
- Office 365 Proplus Pilot
- Office 365 Small Business Subscription Preview
- Office 365 Proplus Pilot
- Office 365 Small Business Subscription
- Office 365 Proplus G
- Microsoft 365 Apps for Enterprise \(Unattended\) for GCC
- Microsoft 365 Apps for Enterprise \(Unattended\)
- Microsoft 365 Apps Extended Offline Access
- Microsoft 365 Apps Extended Offline Access G

All eligible licenses for Outlook in this report extend to those that enable Outlook service beyond the ones listed for Word, Excel, PowerPoint, and OneNote.

### Per-user level data table

The following table shows a breakdown of data at the per-user level. You can add or remove columns from the table.

| Metric | Definition |
| --- | --- |
| Username | The email address of the user who performed the activity on Microsoft Apps. |
| Last activation date \(UTC\) | The latest date on which the user activated their Microsoft 365 Apps subscription on a machine or logs on shared computer and starts the app with their account. |
| Last activity date \(UTC\) | The latest date an intentional activity was performed by the user. To see activity that occurred on a specific date, select the date directly in the chart. |
| Activity in classic Outlook | Indicates if the user was active in classic Outlook for Windows during the specified time period. |
| Activity in new Outlook | Indicates if the user was active in new Outlook for Windows during the specified time period. |
| Activity on Windows devices | Indicates if the user was active in Windows during the specified time period. |
| Activity on Mac devices | Indicates if the user was active in Mac during the specified time period. |
| Activity on mobile | Indicates if the user was active in mobile during the specified time period. |
| Activity on web | Indicates if the user was active in web during the specified time period. |
| Activity on Outlook app | Indicates if the user was active on the Outlook app, including both new Outlook and classic Outlook, during the specified time period. |
| Activity on Word app | Indicates if the user was active on the Word app during the specified time period. |
| Activity on Excel app | Indicates if the user was active on the Excel app during the specified time period. |
| Activity on PowerPoint app | Indicates if the user was active on the PowerPoint app during the specified time period. |
| Activity on OneNote app | Indicates if the user was active on the OneNote app during the specified time period. |
| Activity on Teams app | Indicates if the user was active on the Teams app during the specified time period. |
| Activity on Outlook for Windows | Indicates if the user was active on Outlook for Windows, including both new Outlook for Windows and classic Outlook for Windows during the specified time period. |
| Activity on Word for Windows | Indicates if the user was active on Word for Windows during the specified time period. |
| Activity on Excel for Windows | Indicates if the user was active on Excel for Windows during the specified time period. |
| Activity on PowerPoint for Windows | Indicates if the user was active on PowerPoint for Windows during the specified time period. |
| Activity on OneNote for Windows | Indicates if the user was active on OneNote for Windows during the specified time period. |
| Activity on Teams for Windows | Indicates if the user was active on Teams for Windows during the specified time period. |
| Activity on Outlook for Mac | Indicates if the user was active on Outlook for Mac during the specified time period. |
| Activity on Word for Mac | Indicates if the user was active on Word for Mac during the specified time period. |
| Activity on Excel for Mac | Indicates if the user was active on Excel for Mac during the specified time period. |
| Activity on PowerPoint for Mac | Indicates if the user was active on PowerPoint for Mac during the specified time period. |
| Activity on OneNote for Mac | Indicates if the user was active on OneNote for Mac during the specified time period. |
| Activity on Teams for Mac | Indicates if the user was active on Teams for Mac during the specified time period. |
| Activity on Outlook \(mobile\) | Indicates if the user was active on Outlook for mobile during the specified time period. |
| Activity on Word \(mobile\) | Indicates if the user was active on Word for mobile during the specified time period. |
| Activity on Excel \(mobile\) | Indicates if the user was active on Excel for mobile during the specified time period. |
| Activity on PowerPoint \(mobile\) | Indicates if the user was active on PowerPoint for mobile during the specified time period. |
| Activity on OneNote \(mobile\) | Indicates if the user was active on OneNote for mobile during the specified time period. |
| Activity on Teams \(mobile\) | Indicates if the user was active on Teams for mobile during the specified time period. |
| Activity on Outlook \(web\) | Indicates if the user was active on Outlook for web during the specified time period. |
| Activity on Word \(web\) | Indicates if the user was active on Word for web during the specified time period. |
| Activity on Excel \(web\) | Indicates if the user was active on Excel for web during the specified time period. |
| Activity on PowerPoint \(web\) | Indicates if the user was active on PowerPoint for web during the specified time period. |
| Activity on OneNote \(web\) | Indicates if the user was active on OneNote for web during the specified time period. |
| Activity on Teams \(web\) | Indicates if the user was active on Teams for web during the specified time period. |

Note

By default, user-specific information like usernames, display names, groups, and sites is hidden in usage reports. To learn how to display this information in usage reports, see [Show user, group, or site details in usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#show-user-group-or-site-details-in-usage-reports).

Note

- The **Outlook for Windows migration process** chart, and the columns **Activity in classic Outlook** and **Activity in new Outlook** in the per-user level data table are only available in the **Public** environment.
- New Outlook for Windows usage is monitored through the Microsoft 365 admin center and not through Graph API.

The other columns identify if the user was active on that platform for that app within Microsoft 365 apps during the period selected.

To add or remove columns from the report, select **Choose columns**.

To export the report data into an Excel .csv file, select **Export**. This action exports the usage data of all users and enables you to do simple sorting, filtering, and searching for further analysis.
