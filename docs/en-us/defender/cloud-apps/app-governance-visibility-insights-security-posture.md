<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-security-posture -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# Determine your OAuth app security posture

The cards on the **App governance > Overview** page show security posture data.

The **Overview** page shows the following details:

| Apps / incidents | Details shown | Use this data to... |
| --- | --- | --- |
| **Microsoft Entra ID connected OAuth apps** | - How many apps are in your tenant  <br>- How many apps are unused in the last 90 days  <br>- How many apps might be overprivileged  <br>- How many apps are highly privileged  <br>- How many apps have a high risk score | Determine the level of risk to your organization from unused, overprivileged, highly privileged, and high-risk apps. |
| **For incidents** | - How many active incidents your tenant has  <br>- How many are based on app governance detections \(**Threat incidents**\)  <br>- How many are based on app policies you have in place \(**Policy incidents**\)  <br>- The 10 latest incidents | Determine how quickly incidents are being generated and the relative number of detected and policy-based incidents. |

For example:

![Screenshot showing relative number of detected and policy-based incidents.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/incidents-summary1.png)

![Screenshot showing top alerts.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-compliance-posture/top-alerts.png)

## Data usage cards

Data usage cards show the following types of information:

- **Total data accessed by apps** in the tenant through Microsoft Graph and EWS APIs over the current month and previous three calendar months. \(Currently includes emails, files, and chat and channel messages read and written by apps that access Microsoft 365 using Microsoft Graph and EWS APIs\)
- **Data usage over the current month and previous three calendar months**, broken down by resource type. \(Currently includes emails, files, and chat and channel messages read and written by apps that access Microsoft 365 using Microsoft Graph and EWS APIs\)

For example:

![Screenshot showing total data accessed by apps.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-compliance-posture/data-usage-chart.png)

## Apps that access data on Microsoft 365

For apps that access data on Microsoft 365, cards show the number of apps that have accessed data on SharePoint, OneDrive, Exchange Online, or Teams using Microsoft Graph and EWS APIs in the last 30 days.

For example:

![Screenshot showing apps that have accessed data on SharePoint, OneDrive, Exchange Online, or Teams in the last 30 days.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-compliance-posture/apps-accessed-m365-services-chart.png)

## Sensitivity labels accessed

For sensitivity labeling data, cards show the number apps that have accessed content with sensitivity labels on SharePoint, OneDrive, Exchange Online or Teams using Microsoft Graph and EWS APIs in the last 30 days.

For example:

The number of apps that have accessed content with sensitivity labels.

![Screenshot showing the number of apps that have accessed content with sensitivity labels.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/sensitive-data-accessed-chart1.png)

## Next steps

[Get insights on and regulate access to sensitive content](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-sensitive-content)
