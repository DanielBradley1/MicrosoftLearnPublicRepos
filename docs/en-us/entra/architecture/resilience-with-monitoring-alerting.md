<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/resilience-with-monitoring-alerting -->
<!-- Sitemap-Last-Modified: 2026-02-26 -->

# Resilience through monitoring and analytics

Important

Effective May 1, 2025, Azure Active Directory B2C \(Azure AD B2C\) is no longer available for new customers to purchase. To learn more, see [Is Azure AD B2C still available to purchase?](https://learn.microsoft.com/en-us/azure/active-directory-b2c/faq?tabs=app-reg-ga#azure-ad-b2c-end-of-sale) in our FAQ.

Monitoring maximizes the availability and performance of your applications and services. It delivers a comprehensive solution for collecting, analyzing, and acting on telemetry from your infrastructure and applications. Alerts notify you when issues are found with your service or applications. You can identify and address issues before the end users of your service notice them. [Microsoft Entra ID Log Analytics](https://azure.microsoft.com/services/monitor/?OCID=AID2100131_SEM_6d16332c03501fc9c1f46c94726d2264:G:s&ef_id=6d16332c03501fc9c1f46c94726d2264:G:s&msclkid=6d16332c03501fc9c1f46c94726d2264#features) helps you analyze, search the audit logs and sign-in logs, and build custom views.

## Monitor and get notified through alerts

Monitoring your system and infrastructure helps ensure the overall health of your services. It starts with the definition of business metrics, such as, new user arrival, end user authentication rates, and conversion. Configure such indicators to monitor. If you're planning for an upcoming surge because of a promotion or holiday traffic, revise your estimates for the event and corresponding benchmark for the business metrics. After the event, fall back to the previous benchmark.

Similarly, to detect failures or performance disruptions, set up a good baseline and then define alerting. Respond to emerging issues promptly.

### Implement monitoring and alerting

- **Monitoring**: Use [Azure Monitor](https://learn.microsoft.com/en-us/azure/active-directory-b2c/azure-monitor) to continuously monitor health against key Service Level Objectives \(SLO\). Get notification when a critical change happens. Identify Azure AD B2C policy or an application as a critical component of your business whose health needs to be monitored to maintain SLO. Identify key indicators that align with your SLOs. For example, track the following metrics, since a sudden drop in either leads to a loss in business.

  - **Total requests**: The total "n" number of requests sent to Azure AD B2C policy.
  - **Success rate \(%\)**: Successful requests/Total number of requests.


  Access the [key indicators](https://learn.microsoft.com/en-us/azure/active-directory-b2c/view-audit-logs) in [application insights](https://learn.microsoft.com/en-us/azure/active-directory-b2c/analytics-with-application-insights) where Azure AD B2C policy-based logs, [audit logs](https://learn.microsoft.com/en-us/azure/active-directory-b2c/analytics-with-application-insights), and sign-in logs are stored.


  - **Visualizations**: Use Log Analytics to build dashboards to visually monitor the key indicators.
  - **Current period**: Create temporal charts to show changes in the total requests and success rate \(%\) in the current period, for example, current week.
  - **Previous period**: Create temporal charts to show changes in the total requests and success rate \(%\) over some previous period.

- **Alerting**: Using Log Analytics, define [alerts](https://learn.microsoft.com/en-us/azure/azure-monitor/alerts/alerts-create-new-alert-rule) triggered when there are sudden changes in the key indicators. These changes might negatively affect the SLOs. Alerts use various forms of notification methods including email, SMS, and webhooks. Define a criterion as a threshold for the alert trigger. For example:

  - Alert for abrupt drop in total requests: Trigger an alert when total requests drop abruptly. For example, when there's a 25% drop in requests compared to previous period, raise an alert.
  - Alert for significant drop in success rate \(%\): Trigger an alert when success rate of the selected policy drops.
  - Upon receiving an alert, troubleshoot the issue using [Log Analytics](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/workbooks-view-designer-conversion-overview), [Application Insights](https://learn.microsoft.com/en-us/azure/active-directory-b2c/troubleshoot-with-application-insights), and [VS Code extension](https://marketplace.visualstudio.com/items?itemName=AzureADB2CTools.aadb2c) for Azure AD B2C. After you resolve the issue and deploy an updated application or policy, it monitors key indicators until they return to normal range.

- **Service alerts**: Use the [Azure AD B2C service level alerts](https://learn.microsoft.com/en-us/azure/service-health/service-health-overview) to get notified of service issues, planned maintenance, health advisories, and security advisories.
- **Reporting**: [By using Log Analytics](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-integrate-activity-logs-with-azure-monitor-logs), build reports about user insights, technical challenges, and growth opportunities.

  - **Azure Dashboard**: Create [custom dashboards using Azure Dashboard](https://learn.microsoft.com/en-us/azure/azure-monitor/app/overview-dashboard#create-custom-kpi-dashboards-using-application-insights) feature, which supports adding charts using Log Analytics queries. For example, identify pattern of successful and failed sign-ins, failure reasons and telemetry about devices used to make the requests.
  - **Abandon Azure AD B2C journeys**: Use the [workbook](https://github.com/azure-ad-b2c/siem#list-of-abandon-journeys) to track abandoned Azure AD B2C journeys wherein users started sign-in or sign-up but never finished it. Find details about policy ID and steps taken by the user before abandoning the journey.
  - **Azure AD B2C monitoring workbooks**: Use the [monitoring workbooks](https://github.com/azure-ad-b2c/siem) that include Azure AD B2C dashboard, multifactor authentication \(MFA\) operations, Conditional Access reports, and search logs by correlationId. This practice provides better insights into the health of your Azure AD B2C environment.

## Next steps

- [Resilience resources for Azure AD B2C developers](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2c)

  - [Resilient end-user experience](https://learn.microsoft.com/en-us/entra/architecture/resilient-end-user-experience)
  - [Resilient interfaces with external processes](https://learn.microsoft.com/en-us/entra/architecture/resilient-external-processes)
  - [Resilience through developer best practices](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2c-developer-best-practices)

- [Build resilience in your authentication infrastructure](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-infrastructure)
- [Increase resilience of authentication and authorization in your applications](https://learn.microsoft.com/en-us/entra/architecture/resilience-app-development-overview)
