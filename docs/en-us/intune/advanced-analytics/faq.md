<!-- Source: https://learn.microsoft.com/en-us/intune/advanced-analytics/faq -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Advanced Analytics FAQs

This article addresses frequently asked questions about Advanced Analytics in Microsoft Intune.

**Feature comparison and licensing**

- [What's the difference between endpoint analytics and Advanced Analytics?](#what-s-the-difference-between-endpoint-analytics-and-advanced-analytics)
- [Do I need additional licensing for Advanced Analytics?](#do-i-need-additional-licensing-for-advanced-analytics)

**Integration and compatibility**

- [Can Advanced Analytics integrate with other monitoring tools?](#can-advanced-analytics-integrate-with-other-monitoring-tools)
- [Are there limitations with device types or OS versions?](#are-there-limitations-with-device-types-or-os-versions)

**Data collection and refresh**

- [How often is analytics data refreshed?](#how-often-is-analytics-data-refreshed)
- [Why is the analytics data not getting updated?](#why-is-the-analytics-data-not-getting-updated)
- [Why are the device reports incomplete?](#why-are-the-device-reports-incomplete)
- [What should I do if a device is not reporting data?](#what-should-i-do-if-a-device-is-not-reporting-data)

**Dashboards and baselines**

- [Can I customize analytics dashboards?](#can-i-customize-analytics-dashboards)
- [How should the baselines be used?](#how-should-the-baselines-be-used)

**Anomaly detection**

- [Why do some crashes or anomalies sometimes not appear in the anomalies report, even when the devices are correctly licensed and enrolled?](#why-do-some-crashes-or-anomalies-sometimes-not-appear-in-the-anomalies-report--even-when-the-devices-are-correctly-licensed-and-enrolled)

## Feature comparison and licensing

### What's the difference between endpoint analytics and Advanced Analytics?

Advanced Analytics builds on endpoint analytics by offering deeper insights, advanced reporting, and enhanced anomaly detection capabilities.

### Do I need additional licensing for Advanced Analytics?

Yes, Advanced Analytics requires specific licensing. Review the prerequisites for details.

## Integration and compatibility

### Can Advanced Analytics integrate with other monitoring tools?

Advanced Analytics doesn't provide a connector for data to be leveraged in other monitoring tools. Some features, such as Device Query for multiple devices, do support an export via .csv function, which could then be used in other tooling.

### Are there limitations with device types or OS versions?

Some features might be limited to specific Windows builds, OS versions, or device types. Review the prerequisites before deployment.

## Data collection and refresh

### How often is analytics data refreshed?

Data is typically updated every 24 hours. Real-time troubleshooting might require direct device queries.

### Why is the analytics data not getting updated?

Ensure devices are online and have connectivity to required Microsoft endpoints. Verify data collection settings and licensing status. Devices must restart at least once after the policy is applied for data to properly display.

### Why are the device reports incomplete?

Verify that targeted devices meet the [prerequisites](https://learn.microsoft.com/en-us/intune/advanced-analytics/#prerequisites). In some cases, end-to-end latency can exceed 24 hours if event details aren't uploaded from the client immediately. This delay often occurs with events such as restarts or stop errors when the device doesn't reboot right after the shutdown or error. When this happens, the event details are uploaded at the next available opportunity. The event then appears on the timeline with a timestamp that reflects when the event originally occurred.

### What should I do if a device is not reporting data?

Check device connectivity, enrollment status, and compliance with system requirements.

## Dashboards and baselines

### How should the baselines be used?

Baseline scores are shown on charts as triangle markers. There's a built-in baseline for All organizations \(median\), which allows you to compare your scores to a typical enterprise. You can create new baselines based on your current metrics so you can track progress or view regressions over time.

### Can I customize analytics dashboards?

Yes, dashboards can be tailored to highlight key metrics and device scopes relevant to your organization.

## Anomaly detection

### Why do some crashes or anomalies sometimes not appear in the anomalies report, even when the devices are correctly licensed and enrolled?

This is typically due to the volume and usage patterns of devices and apps. The device must be actively used, enrolled in endpoint analytics, and data collection is enabled. In addition, a high volume of events \(such as critical errors or app crashes\) is usually required before the event is flagged as anomalous.
