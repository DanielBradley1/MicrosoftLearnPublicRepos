<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/onedrive-for-business-usage-ww?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# OneDrive Usage report

The OneDrive Usage report provides a high-level view of the value you get from OneDrive. The report includes details about the total number of accounts, files, and storage used across your organization. You can drill into it to understand the trends of active OneDrive accounts, how many files users are interacting with, and the amount of storage used. It also gives you details for each user's OneDrive.

Important

The report only includes users who have a valid OneDrive license.

For general information about usage reports in the Microsoft 365 admin center, and to see a list of all available reports, see [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide).

## View the OneDrive Usage report in the Microsoft 365 admin center

For information about the roles needed to view usage reports, see "Before you begin" in [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#before-you-begin)

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the navigation menu, select **Reports**. If you don't see **Reports**, select **Show all**, and then select **Reports**.
3. Select [Usage](https://go.microsoft.com/fwlink/p/?linkid=2074756).
4. On the **Usage** page, under **Reports**, select **OneDrive**.
5. On the report page, select the **Usage** tab.

## Interpret the OneDrive Usage report

The report displays trends over the last 7, 30, 90, or 180 days. However, if you select a particular day in the report, the table shows data for up to 28 days from the current date, not the date the report generated.

[![Screenshot of the Microsoft OneDrive usage report.](https://learn.microsoft.com/en-us/microsoft-365/media/3cdaf2fb-1817-479b-a0e1-2afa228690cf.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/3cdaf2fb-1817-479b-a0e1-2afa228690cf.png?view=o365-worldwide#lightbox)

To add or remove columns from the report, select **Choose columns**.

[![Screenshot of the columns available for the OneDrive usage report.](https://learn.microsoft.com/en-us/microsoft-365/media/9ee80f25-cfe3-411d-8e31-08f1507d18c1.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/9ee80f25-cfe3-411d-8e31-08f1507d18c1.png?view=o365-worldwide#lightbox)

To export the report data into an Excel .csv file, select **Export**. This action exports the usage data of all users and enables you to do simple sorting, filtering, and searching for further analysis.

| Metric | Definition |
| :--- | :--- |
| URL | The web address for the user's OneDrive. Note: URL is temporarily empty. |
| Deleted | The deletion status of the OneDrive. It takes at least seven days for accounts to be marked as deleted. |
| Owner | The username of the primary administrator of the OneDrive. |
| Owner principal name | The email address of the owner of the OneDrive. |
| Last activity date \(UTC\) | The latest date a file activity was performed in the OneDrive. If the OneDrive has no file activity, the value is blank. |
| Files | The number of files in the OneDrive. |
| Active files | The number of active files within the time period.  <br>  <br>**NOTE:** If you remove files during the specified time period for the report, the number of active files shown in the report might be larger than the current number of files in OneDrive. Deleted users continue to appear in reports for 180 days. |
| Storage used \(MB\) | The amount of storage the OneDrive uses in MB. |
| Site ID | The site ID of the site. |

Note

By default, user-specific information like usernames, display names, groups, and sites is hidden in usage reports. To learn how to display this information in usage reports, see [Show user, group, or site details in usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#show-user-group-or-site-details-in-usage-reports).

Note

The OneDrive site URL might not display in related usage reports. You can use PowerShell to display the site URL. For more information, see [Use PowerShell to resolve site URLs](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/resolve-site-urls?view=o365-worldwide).
