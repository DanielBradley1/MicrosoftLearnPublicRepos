<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/sharepoint-site-usage-ww?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-30 -->

# SharePoint Site usage report

The SharePoint Site usage report provides a high-level view of the value you get from SharePoint. The report includes details about the total number of files that users store in SharePoint sites, how many files are actively used, and the storage consumed across all these sites. You can drill into the SharePoint site usage report to understand the trends and per-site level details for all sites.

For general information about usage reports in the Microsoft 365 admin center, and to see a list of all available reports, see [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide).

## View the SharePoint Site usage report in the Microsoft 365 admin center

For information about the roles needed to view usage reports, see "Before you begin" in [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#before-you-begin).

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the navigation menu, select **Reports**. If you don't see **Reports**, select **Show all**, and then select **Reports**.
3. Select [Usage](https://go.microsoft.com/fwlink/p/?linkid=2074756).
4. On the **Usage** page, under **Reports**, select **SharePoint**.
5. On the report page, select the **Site usage** tab.

## Interpret the SharePoint Site usage report

The report displays trends over the last 7, 30, 90, or 180 days. However, if you select a particular day in the report, the table shows data for up to 28 days from the current date, not the date the report generated.

[![Microsoft 365 reports - Microsoft SharePoint site usage report.](https://learn.microsoft.com/en-us/microsoft-365/media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png?view=o365-worldwide#lightbox)

To add or remove columns from the report, select **Choose columns**.

[![Screenshot of the columns available for the SharePoint site usage report.](https://learn.microsoft.com/en-us/microsoft-365/media/71ac3195-c494-40c1-9346-a858125ef6df.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/71ac3195-c494-40c1-9346-a858125ef6df.png?view=o365-worldwide#lightbox)

To export the report data into an Excel .csv file, select **Export**. This action exports the usage data of all users and enables you to do simple sorting, filtering, and searching for further analysis.

| Metric | Description |
| :--- | :--- |
| Site URL | The full URL of the site. |
| Deleted | The deletion status of the site. The site is marked as deleted after at least seven days. |
| Site owner | The username of the primary owner of the site. |
| Site owner principal name | The email address of the owner of the site. |
| Last activity date \(UTC\) | ActiveFiles, AnonymousLinkShared, CompanyLinkShared, FilesSynced, PagesViewed. LAD updates when any event within these five groups is logged as a user action. See the detailed event tables for the specific operations within each group. |
| Site sensitivity label ID | The sensitivity label on the site. |
| External sharing | The value of the external sharing setting for the site. This value doesn't reflect changes to the effective setting made by site sensitivity labels. If you use sensitivity labels, use the [data access governance reports](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-reports) to get the correct values. |
| Unmanaged device policy | The site access policy for unmanaged devices. |
| Geo location | The Geo location of the site. |
| Files | The number of files on the site. |
| Active files | The number of active files on the site. A file is active if it was saved, synced, modified, or shared within the specified time period.  <br>  <br>**NOTE:** If files were removed during the specified time period for the report, the number of active files shown in the report might be larger than the current number of files on the site. |
| Storage used \(MB\) | The amount of storage currently used on the site. |
| Storage allocated \(MB\) | The maximum amount of storage allocated for the site. |
| Page views | The number of times pages were viewed on the site. |
| Pages visited | The number of unique pages that were visited on the site. |
| Anonymous link count | The number of times documents or folders are shared using "Anyone with the link" on the site. |
| Company link count | The number of times documents or folders are shared using "People in org with the link" on the site. |
| Secure link for guest count | The number of times documents or folders are shared using "specific people" on the site. |
| Secure link for member count | The number of times documents or folders are shared using "specific people" on the site. |
| Root Web Template | The template used for creating the site.  <br>  <br>**NOTE:** To filter the data by different site types, export the data and use the Root Web Template column. |
| Site ID | The site ID of the site. |

### Audit log events counted for Last Activity Date

The following table describes the audit log event categories that update the **Last activity date**, helping you understand which user activities are counted when determining whether a site is active.

| EventGroup | Event | Description |
| :--- | :--- | :--- |
| **Active Files** \("ActiveFiles"\) |  |  |
|  | FileAccessed | User or system account accesses a file. After a user accesses a file, the system doesn't log FileAccessed again for the same user and file for five minutes. |
|  | FileCheckedIn | User checks in a document they checked out from a document library. |
|  | FileCheckedOut | User checks out a document in a document library. |
|  | FileCheckOutDiscarded | User discards \(undoes\) a checked-out file; changes made during checkout are not saved. |
|  | FileCopied | User copies a document from a site. |
|  | FileDeleted | User deletes a document from a site. |
|  | FileDownloaded | User downloads a file. |
|  | FileModified | User or system account modifies the content or properties of a document. The system waits five minutes before logging another FileModified for the same user and document. |
|  | FileMoved | User moves a document to a new location. |
|  | FileRenamed | User renames a document. |
|  | FileRestored | User restores a document from a site's recycle bin. |
|  | FileUploaded | User uploads a document to a folder on a site. |
| **Files Shared with Anonymous Link** \("AnonymousLinkShared"\) |  |  |
|  | AnonymousLinkCreated | User created an anonymous link to a resource; anyone with the link can access it without authenticating. |
|  | AnonymousLinkUpdated | User updated an anonymous link to a resource. |
| **Files Shared with Company Link** \("CompanyLinkShared"\) |  |  |
|  | CompanyLinkCreated | User created a company-wide link; usable only by members of the org, not guests. |
| **Files Synced** \("FilesSynced"\) |  |  |
|  | FileSyncDownloadedFull | User downloaded a file from a SharePoint library or OneDrive using the OneDrive sync app \(OneDrive.exe\). |
|  | FileSyncDownloadedPartial | Deprecated along with the old OneDrive sync app \(Groove.exe\). |
|  | FileSyncUploadedFull | User uploaded a new file or changes using the OneDrive sync app \(OneDrive.exe\). |
|  | FileSyncUploadedPartial | Deprecated along with the old OneDrive sync app \(Groove.exe\). |
| **Pages Viewed** \("PagesViewed"\) |  |  |
|  | PageViewed | User views a page on a site \(excludes viewing files in a document library via browser\). Not logged again for the same user and page for five minutes. |
|  | ClientViewSignaled | User's client \(website or mobile app\) signals the page was viewed; often follows a PagePrefetched event. |

Note

By default, user-specific information like usernames, display names, groups, and sites is hidden in usage reports. To learn how to display this information in usage reports, see [Show user, group, or site details in usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#show-user-group-or-site-details-in-usage-reports).

Note

The SharePoint site URL doesn't display if [Bring Your Own Key \(BYOK\)](https://learn.microsoft.com/en-us/azure/information-protection/byok-price-restrictions) or [Customer Lockbox](https://learn.microsoft.com/en-us/azure/security/fundamentals/customer-lockbox-overview) is enabled. If you meet the requirement, Administrators can submit a request via [this link](https://aka.ms/ODSPUsageURLRequest). If the link isn’t working, please file a ticket using subject title: SharePoint and OneDrive Usage Site URL Request. If the requirement isn't met, you can use PowerShell. To follow the steps, see [Use PowerShell to resolve site URLs](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/resolve-site-urls?view=o365-worldwide).

You might see differences between the sites listed in the Site usage report and the sites listed on the **Sites** > [Active sites](https://go.microsoft.com/fwlink/?linkid=2185220) page in the [SharePoint admin center](https://go.microsoft.com/fwlink/?linkid=2185219) because certain site templates and URLs aren't included as Active sites. For more information, see [Manage sites in the SharePoint admin center](https://learn.microsoft.com/en-us/sharepoint/manage-sites-in-new-admin-center).
