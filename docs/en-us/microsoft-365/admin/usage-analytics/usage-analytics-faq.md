<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/usage-analytics-faq?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Microsoft 365 usage analytics overview FAQ

This article provides answers to frequently asked questions that administrators might have about Microsoft 365 usage analytics. For more information about Microsoft 365 usage analytics, see [Microsoft 365 usage analytics overview](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/usage-analytics?view=o365-worldwide).

## Is the template app available through for purchase or is it free?

The template app isn't free. A Power BI Pro license is required. For details, see [prerequisites](https://learn.microsoft.com/en-us/power-bi/service-template-apps-install-distribute#prerequisites) for installing, customizing, and distributing a template app.

To share the dashboards with others, see [Share dashboards and reports](https://learn.microsoft.com/en-us/power-bi/service-how-to-collaborate-distribute-dashboards-reports#share-dashboards-and-reports).

## Who can connect to Microsoft 365 usage analytics?

You must have one of the following roles to connect to the template app:

- **Exchange admin**.
- **Teams admin**.
- **SharePoint admin**.
- **Global reader**.
- **Report reader**.
- **Usage Summary Reports Reader**.

For more information, see [About admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

Note

**Global Reader** and **Usage Summary Reports Reader** can only access tenant level aggregates in Microsoft 365 usage analytics. They don't have permission to view the user activity reports.

## Who can customize the usage analytics reports?

Only the user who makes the initial connection to the template app can customize the reports or create new reports in the Power BI web interface. For instructions, see [Customizing the reports in Microsoft 365 usage analytics](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/customize-reports?view=o365-worldwide).

## Can I only customize the reports from the Power BI web interface?

In addition to customizing the reports from the Power BI web interface, users can also use Power BI Desktop to connect directly to the Microsoft 365 reporting service to build their own reports.

## How can I get the pbit file that this dashboard is associated with?

You can access the pbit file from the [Microsoft Download Center](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit).

## Who can view the dashboards and reports?

If you connect to the template app, you can share it with anyone by using the [sharing functionality](https://learn.microsoft.com/en-us/power-bi/collaborate-share/service-share-dashboards). Power BI licensing requires that both the user sharing and the user with whom a dashboard is shared have Power BI Pro or Power BI Premium.

## Can anyone share the dashboard, or does it have to be the person who connected to the dashboard?

When sharing the dashboard, you can either:

- Allow users to reshare the dashboard with others.
- Not allow users to reshare the dashboard with others.

You can set this option at the time of sharing.

## Is it possible to work on and customize the same template app with a group of people?

Yes. To enable a group of admins to work together on the same template app, use the app workspace functionality of Power BI. For more information, see [How should I collaborate and share dashboards and reports?](https://learn.microsoft.com/en-us/power-bi/collaborate-share/service-how-to-collaborate-distribute-dashboards-reports)

## Which timeframe is data available?

Most of the reports display data for the previous 12 months. However, some of the charts might show less history since data collection for different products and reports started at different times. Therefore, data for the full 12 months might not be available. All the reports eventually build up to 12 months of history. Reports that show user level details show data for the previous complete month.

## What data does the template app include?

The data in the template app currently covers the same set of activity metrics available in the [Activity Reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide). As Microsoft adds reports to the activity reports, they'll add them to the template app in a future release.

## How does the data in the template app differ from the data in the usage reports?

The underlying data you see in the template app matches the data you see in the activity reports in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339). The key differences are:

- In the Microsoft 365 admin center, you can view data for the last 7, 30, 90, or 180 days.
- The template app presents data on a monthly basis for up to 12 months.

In addition, the template app only shows user-level details for the last complete month for users who were assigned a product license and performed an activity.

## When should I use the template app and when should I use the usage reports?

The [Activity Reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide) are a good starting point to understand usage and adoption of Microsoft 365. The template app combines the Microsoft 365 usage data and your organization's Active Directory information. When admins use the visual analytics capabilities of Power BI, they can analyze the data set. This capability enables admins to not just visualize and analyze Microsoft 365 usage data, but also slice it by Active Directory properties such as departments, location, and more. They can also create custom reports and share the insights within their organization.

## How often is the data refreshed?

When you connect to the template app for the first time, it automatically populates with your data for the previous 12 months. After that, the template app data refreshes weekly. You can choose to modify the refresh schedule if your use of this data demands a different update rhythm.

The back-end Microsoft 365 service refreshes data on a daily basis and provides data that is between 5 and 8 days latent from the current date.

The **Content date** column in each dataset represents the freshness date of the data in the template app.

## How is an active user defined?

The definition of active user is the same as the definition of an [active user in the activity reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/active-users?view=o365-worldwide).

## What SharePoint site collections does the SharePoint reports include?

The current version of the template app includes file activity from SharePoint team sites and SharePoint group sites.

## Which groups does the Microsoft 365 Groups usage report include?

The current version of the template app includes usage from:

- Outlook groups.
- Viva Engage groups.
- SharePoint groups.

It doesn't include groups related to Microsoft Teams or Planner.

## When do updated versions of the template app become available?

Major changes to the template app are released twice a year, which might include new reports or new data. Minor changes to the reports might be released more frequently.

## Can I integrate the data from the template app into existing solutions?

You can retrieve the data in the template app through the Microsoft 365 APIs \(in preview\). When they ship to production, they merge within the [Microsoft Graph reporting APIs](https://developer.microsoft.com/graph).

## Are there plans to expand the template app to show usage data from other Microsoft products?

The feature is under consideration for future improvements. For updates, see [Microsoft AI at Work Roadmap](https://www.microsoft.com/microsoft-365/roadmap), formerly known as the Microsoft 365 Roadmap.

## How can I pivot by company information in Active Directory?

Company information is included in one of the Active Directory fields in the template app. You can see it as a prebuilt filter in the **Product User activity** reports. It's available as a column in the **UserState** table.

## Can I bring in more fields from Active Directory?

You can customize this data by connecting to the [Microsoft Graph reporting APIs](https://developer.microsoft.com/graph) to pull additional fields from Microsoft Entra ID and join to the dataset.

## Can I aggregate the information in the template app across multiple subscriptions?

Currently, the template app supports a single subscription because the template app is associated with the credentials you use to initially connect to it.

## Can I see usage by plan, such as E1 or E3?

The template app shows usage at the product level. It provides data for the different subscriptions assigned to users, but you can't correlate user activity to the specific subscription assigned to a user.

## Can I integrate other data sets into the template app?

By using Power BI Desktop, you can connect to the Microsoft 365 APIs \(in preview\) to bring in more data sources to combine with the template app data.

For more information, see the [Customize the reports in Microsoft 365 usage analytics](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/customize-reports?view=o365-worldwide).

## Can I see the Top Users reports for a specific timeframe?

All user-level reports present aggregated data for the previous month.

## Does the template app support localization?

Localization isn't currently on the roadmap.

## I have a specific question about the data I'm seeing for my organization. Who can I reach out to?

You can use the feedback button in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) activity overview page, or you can open a [support case](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-support?view=o365-worldwide) to get help with the template app.

## How can partners access the data?

If a partner delegates admin rights, they can connect to the template app on behalf of their customer.

## Can I hide identifiable information such as user, group, and site names in reports?

By default, the reports hide user-specific data. To change the setting, see [Show user, group, or site details in usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#show-user-group-or-site-details-in-usage-reports).
