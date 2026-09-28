<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/connect-to-gcc-data-with-usage-analytics?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# Connect to Microsoft 365 Government Community Cloud \(GCC\) data with Usage Analytics

Use the following procedures to connect to your Microsoft 365 Government Community Cloud \(GCC\) tenant data by using the Microsoft 365 Usage Analytics report in Power BI Desktop.

Note

These instructions are specifically for Microsoft 365 GCC tenants and aren't applicable to GCC High and DOD.

## Before you begin

To initially configure Microsoft 365 Usage Analytics:

- You must be a Microsoft 365 Global Administrator to enable data collection.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

- You must have the [Power BI Desktop](https://powerbi.microsoft.com/desktop/) application to use the template file.
- You must have a [Power BI Pro license](https://go.microsoft.com/fwlink/p/?linkid=845347) or Premium capacity to publish and view the report.

## Step 1: Make your organization's data available for the Microsoft 365 Usage Analytics report

1. Sign in to the [Microsoft 365 admin center](https://admin.cloud.microsoft/).
2. From the left navigation bar, select **… Show all**, and then select **Reports** to expand it.
3. Under **Reports**, select [**Usage**](https://admin.cloud.microsoft/?#/reportsUsage).
4. In the **Microsoft 365 usage analytics** section of the **Usage** page, select **Get Started**.
5. Under **Enable Power BI for usage analytics** in the **Reports** pane, select **Make organizational usage data available to Microsoft 365 usage analytics for Power BI**, and then select **Save**.

   [![Screenshot of the option to make organizational usage data available to Microsoft 365 Usage Analytics for Power BI in the admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/usage-analytics/make-data-available.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/usage-analytics/make-data-available.png?view=o365-worldwide#lightbox)

   Selecting this option starts a process to make your organization's data accessible for this report. You might see a message that states **We're getting your data ready for Microsoft 365 usage analytics**. This process can take 24 hours to complete.
6. When your organization's data is ready, refreshing the page shows a message stating that your data is now available, and provides your **tenant ID** number. You must use the tenant ID in a later step when you attempt to connect to your tenant data.

   [![Screenshot of the tenant ID displayed in the Microsoft 365 admin center after organizational usage data is ready for Usage Analytics.](https://learn.microsoft.com/en-us/microsoft-365/media/usage-analytics/tenant-id-gcc.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/usage-analytics/tenant-id-gcc.png?view=o365-worldwide#lightbox)

   Important

   When your data is available, don't select **Go to Power BI**. That option takes you to the Power BI Marketplace. The template app for this report that GCC tenants require isn't available in the Power BI Marketplace.

## Step 2: Download the Power BI template, connect to your data, and publish the report

Microsoft 365 GCC users can download and use the Microsoft 365 Usage Analytics report template file to connect to their data. You need Power BI Desktop to open and use the template file.

Note

A template app for the Microsoft 365 Usage Analytics report isn't available for GCC tenants in the Power BI Marketplace.

1. Download the [Power BI template](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit).
2. Once the Power BI template is downloaded, open it using Power BI Desktop.
3. When prompted for a **TenantID**, enter the tenant ID you received when you prepared your organization's data for this report in [Step 1](#step-1-make-your-organizations-data-available-for-the-microsoft-365-usage-analytics-report), and then select **Load**. It can take several minutes for your data to load.

   [![Screenshot of the TenantID prompt in Power BI Desktop where you enter your tenant ID to connect to Microsoft 365 usage data.](https://learn.microsoft.com/en-us/microsoft-365/media/usage-analytics/add-tenant-id.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/usage-analytics/add-tenant-id.png?view=o365-worldwide#lightbox)
4. When loading completes, your report is displayed, and you see an executive summary of your data.

   [![Screenshot of the executive summary view of the Microsoft 365 Usage Analytics report displayed in Power BI Desktop after data loads.](https://learn.microsoft.com/en-us/microsoft-365/media/usage-analytics/exec-summary.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/usage-analytics/exec-summary.png?view=o365-worldwide#lightbox)
5. Save your changes to the report.
6. Select **Publish** in the Power BI Desktop menu to publish the report to the Power BI service where it can be viewed. This feature requires either a Power BI Pro license or Power BI Premium capacity. As part of the [publish process](https://learn.microsoft.com/en-us/power-bi/create-reports/desktop-upload-desktop-files#to-publish-a-power-bi-desktop-dataset-and-reports), you must select a destination to publish to an available workspace in the Power BI service.

## Related content

- [About usage analytics](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/usage-analytics?view=o365-worldwide).
- [Get the latest version of usage analytics](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/get-the-latest-version-of-usage-analytics?view=o365-worldwide).
- [Navigate and utilize the reports in Microsoft 365 usage analytics](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/navigate-and-utilize-reports?view=o365-worldwide).
