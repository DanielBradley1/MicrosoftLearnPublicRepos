<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/visibility-monitoring?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-10 -->

# Monitor the health of apps in Copilot Managed Runtime

To measure and improve operational health metrics for apps in Copilot Managed Runtime for your organization, go to the **Monitor** page under **Apps** in the [Microsoft 365 admin center](https://admin.microsoft.com/AdminPortal/Home#/homepage).

Both Manage and read-only roles can access the **Monitor** experience and use it to understand the aggregate operational health of apps in Copilot Managed Runtime that are created in their tenant. Manage roles can see metrics and create and manage alerts. Read-only roles can see metrics and view alert rules and triggered alert details, but they can't create or manage alert rules. Metrics are calculated by aggregating daily or hourly event logs from runtime activity. They're not real-time. For more information about which roles can manage apps and which roles are read-only, see [Roles and responsibilities](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/roles-responsibilities?view=o365-worldwide).

This article helps you understand the apps inventory and monitor application health.

## Architecture

To produce health metrics and generate recommendations, the **Monitor** experience requires runtime activity. Unused apps don't have metrics.

[![Diagram of the backend architecture of Monitor in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/media/mac-monitor-architecture.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/media/mac-monitor-architecture.png?view=o365-worldwide#lightbox)

## Monitor use cases

The purpose of the **Monitor** area of the Microsoft 365 admin center is to bring attention to apps in Copilot Managed Runtime that have degraded operational health and highlight apps that have opportunities for improvement.

## View an app's health metrics

1. Go to the **All apps** list page under **Apps** in the Microsoft 365 admin center.
2. Select a specific app to open the details pane.
3. Within the pane, select the **Monitor** tab to view operational health metrics and a time-series chart for each available metric.

## Available metrics for apps in Copilot Managed Runtime

The **Monitor** experience provides the following operational health metrics for apps in Copilot Managed Runtime.

| Metric | Definition | Support |
| --- | --- | --- |
| App open success rate | A percentage that describes how often end users can successfully open the app. | Preview |
| Time to interactive \(TTI\) | The time \(in seconds\) it takes for a screen to become interactive after it starts loading. | Preview |
| App session count | The number of distinct user sessions in an app in one day. A session begins when a user opens the app and ends after a period of inactivity or when the app is closed. | Preview |
| Data request success rate | A percentage that describes how often data requests coming from an app are successful. | Preview |
| Data request latency | The average time \(in seconds\) it takes for all data requests made by the app to complete during a session. | Preview |

## Create alerts for your apps

Admins can use *alerts* to track the operational health of their apps. Admins set up custom thresholds and get notifications when metrics for their apps pass specific thresholds. Create alerts on any metrics in the **Monitor** area of the Microsoft 365 admin center. See [Create alerts for your apps](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/alerts?view=o365-worldwide) for more details

## FAQs

### How does Monitor in the Microsoft 365 admin center coexist with Application Insights?

**Monitor** in the Microsoft 365 admin center doesn't require Azure subscriptions.

Application Insights contains a superset of runtime event logs.

- It contains event logs that are beyond the scope of Monitor's app metrics.
- It allows for customer-defined data retention.
- It allows for custom traces, which support custom events, metrics, and dimensions.
- Event logs can be correlated and joined across apps that emit data to the same Application Insights instance.

### How frequently are metrics updated and what determines their aggregation rate?

Metrics aggregate at a point in time, according to their aggregation rate. The default aggregation rate is every 24 hours. For example, the **App open success rate** metric calculates daily and has only one value per day. If there's an alert that has a data review period of an hour, metrics calculate hourly. See the alert section for more details.

### How far back can I view metric data?

You can view metric data for up to 28 days for 24 hour aggregates.

### How are time-based metrics calculated? For example, what percentile is used?

Time-based metrics report out the 75th percentile.

## Related content

- [Overview of integration with Application Insights](https://learn.microsoft.com/en-us/power-platform/admin/overview-integration-application-insights)
- [Create alerts for your apps \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/alerts?view=o365-worldwide)
- [Export Monitor metrics with the Power Platform API \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/monitor-export-metrics?view=o365-worldwide)
