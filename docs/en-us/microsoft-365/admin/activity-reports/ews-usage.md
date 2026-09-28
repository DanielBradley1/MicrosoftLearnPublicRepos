<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/ews-usage?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Exchange Web Services \(EWS\) usage report

The Exchange Web Services \(EWS\) usage report displays the SOAP actions used by each application calling EWS in your organization. It also shows the successful-call volume for each SOAP action. This information enables you to coordinate with the application owners to ensure they're preparing for the [EWS deprecation in October 2026](https://techcommunity.microsoft.com/blog/exchange/retirement-of-exchange-web-services-in-exchange-online/3924440).

For general information about usage reports in the Microsoft 365 admin center, and to see a list of all available reports, see [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide).

## View the EWS usage report in the Microsoft 365 admin center

For information about the roles needed to view usage reports, see "Before you begin" in [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#before-you-begin)

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the navigation menu, select **Reports**. If you don't see **Reports**, select **Show all**, and then select **Reports**.
3. Select [Usage](https://go.microsoft.com/fwlink/p/?linkid=2074756).
4. On the **Usage** page, under **Reports**, select **Exchange**.
5. On the report page, select the **EWS usage** tab.

## Interpret the EWS usage report

You can filter the EWS usage report by the last 7, 30, or 90 days.

Note

Usage data is collected and aggregated weekly, not daily. It can take up to 10 days for usage to show in the report.

To review the applications that use EWS within your organization, examine the **Usage trend** and **Usage details** sections. Additionally, summarized information at the top provides an overview of the overall usage.

[![Screenshot of the Exchange Web Services \(EWS\) usage report.](https://learn.microsoft.com/en-us/microsoft-365/media/exchange-web-usage-report.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/exchange-web-usage-report.png?view=o365-worldwide#lightbox)

### Summary data

Two summary headers appear at the top of the page:

- **Active apps** shows the number of unique apps that sent at least one request to EWS during the selected period.
- **Daily average call volume** shows the average number of daily requests from active apps during the selected period.

### Usage trend chart

The usage trend chart displays the projected EWS usage trend in your tenant, using weekly data points that summarize all active apps in your tenant that use EWS during that week. The Y-axis represents the number of apps, and the X-axis indicates the first date of the week within the selected period.

### Usage details table

The following table provides a breakdown of the EWS usage per SOAP action by each active application in your tenant during the selected period. You can't customize the columns.

| Metric | Definition |
| --- | --- |
| Application ID | The Microsoft Entra identifier for the registered application |
| SOAP Action | The specific Exchange Web Service SOAP action executed |
| Call Volume | The number of SOAP action calls in the given period |
| Last Activity date \(UTC\) | The last date of activity recorded for that app and SOAP action |

To export the report data into an Excel .csv file, select **Export**. This action exports the usage data of all users and enables you to do simple sorting, filtering, and searching for further analysis.

For a list of Microsoft first-party client application IDs, see [Commonly used Microsoft first-party services and portal apps](https://learn.microsoft.com/en-us/power-platform/admin/apps-to-allow). For Microsoft applications, Microsoft periodically updates those apps to remove EWS dependencies. Keep your client applications up-to-date. If you still can't find the Application ID, check your Enterprise Applications in Microsoft Entra ID. For more information, see [Quickstart: View enterprise applications](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/view-applications-portal).
