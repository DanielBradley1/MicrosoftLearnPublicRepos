<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/sharepoint-storage-reports?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# SharePoint Storage report

The SharePoint Storage report provides an overview of your tenant's storage usage. It also offers suggestions for storage optimization and future proofing your organization's file growth capacity.

Use the SharePoint Storage report to quickly answer three admin questions:

- How much SharePoint storage is used, available, and allocated?
- How fast is storage growing over time?
- What actions should you take now to delay or plan additional storage purchase?

Note

This report is available to non-Education tenants. Education tenants should refer to their pooled storage report. For more information about viewing the pooled storage report, see [Pooled storage management](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/pooled-storage-management).

For general information about usage reports in the Microsoft 365 admin center, and to see a list of all available reports, see [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide).

## View the SharePoint Storage report in the Microsoft 365 admin center

For information about the roles needed to view usage reports, see "Before you begin" in [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#before-you-begin)

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the navigation menu, select **Reports**. If you don't see **Reports**, select **Show all**, and then select **Reports**.
3. Select [Usage](https://go.microsoft.com/fwlink/p/?linkid=2074756).
4. On the **Usage** page, under **Reports**, select **SharePoint**.
5. On the report page, select the **Storage** tab.

## Interpret the SharePoint Storage report

This report refreshes every 48-72 hours. Banner notifications appear when SharePoint usage exceeds 80% of quota.

[![Screenshot of the SharePoint storage report page.](https://learn.microsoft.com/en-us/microsoft-365/media/usage-page.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/usage-page.png?view=o365-worldwide#lightbox)

### Optimize your organization's SharePoint storage

Explore ways to manage your storage through setting file history limits, archiving inactive sites<sup>1</sup>, and creating site lifecycle management policies<sup>1</sup>. To increase SharePoint storage capacity, buy more storage in one-gigabyte increments. For more information about planning for SharePoint storage, see [SharePoint storage planning](https://learn.microsoft.com/en-us/sharepoint/sharepoint-storage-planning).

<sup>1</sup> Additional licensing charges might apply.

### Total usage

The **Total usage** chart shows the total storage used by your tenant, total storage quota, and available storage quota. For more information about SharePoint limits, see [SharePoint limits - Service Descriptions](https://learn.microsoft.com/en-us/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits).

### Usage trend

The **Usage trend** report helps you understand your tenant's storage growth trend. Use the estimated future storage usage based on past usage to make informed decisions about when to buy more storage or whether to clean up usage.

Note

The historical trend represents usage across all sites and might slightly differ from the storage bar, which indicates tenant-level quota consumption.

### Featured resources

The **Featured resources** section provides information about options for managing storage, like [site storage limits](https://learn.microsoft.com/en-us/sharepoint/manage-site-collection-storage-limits) and [version history limits](https://learn.microsoft.com/en-us/sharepoint/document-library-version-history-limits). Consider using [Microsoft Graph Data connect](https://techcommunity.microsoft.com/blog/microsoft_graph_data_connect_for_sharepo/links-about-microsoft-graph-data-connect-for-sharepoint/4069045) for more in-depth SharePoint storage insights.

## Next actions

- [Plan storage growth](https://learn.microsoft.com/en-us/sharepoint/sharepoint-storage-planning)
- [Set site storage limits](https://learn.microsoft.com/en-us/sharepoint/manage-site-collection-storage-limits)
- [Set version history limits](https://learn.microsoft.com/en-us/sharepoint/document-library-version-history-limits)
