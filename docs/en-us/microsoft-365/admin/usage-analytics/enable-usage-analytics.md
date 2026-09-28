<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/enable-usage-analytics?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-26 -->

# Enable Microsoft 365 usage analytics

To enable Microsoft 365 usage analytics in a Microsoft 365 US Government Community Cloud \(GCC\) tenant, see [Connect to Microsoft 365 Government Community Cloud \(GCC\) data with Usage Analytics](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/connect-to-gcc-data-with-usage-analytics?view=o365-worldwide).

## Before you begin

To get started with Microsoft 365 usage analytics, you must first make the data available in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), then select **Reports** > **Usage** and initiate the template app in Power BI.

## Get Power BI

If you don't already have Power BI, you can [sign up for Power BI Pro](https://go.microsoft.com/fwlink/p/?linkid=845347). Select **Try free** to sign up for a trial, or **Buy now** to get Power BI Pro.

You can also expand **Products** to buy a version of Power BI.

Note

You must have a Power BI Pro license to install, customize, and distribute a template app. For more information, please see [Prerequisites](https://learn.microsoft.com/en-us/power-bi/service-template-apps-install-distribute?source=docs#prerequisites).

To share your data, both you and the people who you share the data with need a Power BI Pro license. Or the content needs to be in a workspace in a [Power BI premium service](https://learn.microsoft.com/en-us/power-bi/service-premium-what-is).

## Enable the template app

To enable the template app, you have to be a **Global administrator**.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

For more information, see [about admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

1. Sign in to the [Microsoft 365 admin center](https://admin.cloud.microsoft/).
2. From the left navigation bar, select **... Show all**, and then select **Settings** to expand it.
3. Under **Settings**, select [**Org Settings**](https://admin.cloud.microsoft/?#/Settings/SecurityPrivacy).
4. In the **Org Settings** page, select the **Services** tab, and then select **Reports**.
5. Under **Microsoft 365 usage analytics** in the **Reports** panel, select the option **Make report data available to Microsoft 365 usage analytics for Power BI**.
6. Select **Save**.

The data collection process completes in two to 48 hours depending on the size of your tenant. The **Go to Power BI** button is enabled \(no longer gray\) when data collection is complete. Once complete, the app provides historical usage data at your organization level.

Note

The data for the **"User Activity"** tab is only refreshed after the 15th day of the current month and the first day of the next month, so it will remain empty initially until the first refresh is completed.

## Start the template app

To start the template app, you have to have one of the following roles:

- [**Report Reader**](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#reports-reader).
- [**Exchange Administrator**](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#exchange-administrator).
- [**Skype for Business Administrator**](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#skype-for-business-administrator).
- [**SharePoint Administrator**](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator).

1. Copy the tenant ID and select **Go to Power BI**.
2. When you get to Power BI, sign in. Then **Select Apps**->**Get apps** from the navigation menu.
3. In the **Apps** tab, type Microsoft 365 in the search box and then select **Microsoft 365 usage analytics** > **Get it now**.

   [![Select Get it now.](https://learn.microsoft.com/en-us/microsoft-365/media/78102250-9874-4a32-8365-436f13560b52.png?view=o365-worldwide)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)
4. Once the app is installed, open it by selecting the tile.
5. Select **Explore app** to view the app with sample data. Choose **Connect** to connect the app to your organization's data.
6. Choose **Connect**, on the **Connect to Microsoft 365 usage analytics** screen, then type in the tenant ID \(without dashes\) you copied in step \(1\), and select **Next**.
7. On the next screen, select **OAuth2** as the **Authentication method** > **Sign in**. If you choose any other authentication method, the connection to the template app fails.

   ![Choose Microsoft account as authentication method.](https://learn.microsoft.com/en-us/microsoft-365/media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png?view=o365-worldwide)
8. After the template app is instantiated, the Microsoft 365 usage analytics dashboard is available in Power BI on the web. The initial loading of the dashboard takes between 2 to 30 minutes.

Tenant level aggregates will be available in all reports after opting in. **User-level details will only become available around the 5th of the next calendar month after opting in**. This impacts all reports under User Activity \(See [Navigate and utilize the reports in Microsoft 365 usage analytics](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/navigate-and-utilize-reports?view=o365-worldwide) for tips on how to view and use these reports\).

Note

By default, user-specific information like usernames, display names, groups, and sites is hidden in usage reports. To learn how to display this information in usage reports, see [Show user, group, or site details in usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#show-user-group-or-site-details-in-usage-reports).

## Related content

- [About usage analytics](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/usage-analytics?view=o365-worldwide) \(article\)
- [Get the latest version of usage analytics](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/get-the-latest-version-of-usage-analytics?view=o365-worldwide) \(article\)
- [Navigate and utilize the reports in Microsoft 365 usage analytics](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/navigate-and-utilize-reports?view=o365-worldwide) \(article\)
