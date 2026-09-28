<!-- Source: https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-integrate-activity-logs-with-azure-monitor-logs -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Integrate Microsoft Entra logs with Azure Monitor logs

Using **diagnostic settings** in Microsoft Entra ID, you can integrate logs with Azure Monitor so your sign-in activity and the audit trail of changes within your tenant can be analyzed along with other Azure data.

This article provides the steps to integrate Microsoft Entra logs with Azure Monitor.

Use the integration of Microsoft Entra activity logs and Azure Monitor to perform the following tasks:

- Compare your Microsoft Entra sign-in logs against security logs published by Microsoft Defender for Cloud.
- Troubleshoot performance bottlenecks on your application's sign-in page by correlating application performance data from Azure Application Insights.
- Analyze the Identity Protection risky users and risk detections logs to detect threats in your environment.
- Identify sign-ins from applications still using the Active Directory Authentication Library \(ADAL\) for authentication. [Learn about the ADAL end-of-support plan.](https://learn.microsoft.com/en-us/entra/identity-platform/msal-migration)

Note

Integrating Microsoft Entra logs with Azure Monitor automatically enables the Microsoft Entra data connector within Microsoft Sentinel.

## Prerequisites

To use this feature, you need:

- An Azure subscription. If you don't have an Azure subscription, you can [sign up for a free trial](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

- At least the [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator) role in the Microsoft Entra tenant.

- A **Log Analytics workspace** in your Azure subscription. Learn how to [create a Log Analytics workspace](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/quick-create-workspace).

- Permission to access data in a Log Analytics workspace. See [Manage access to log data and workspaces in Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/manage-access) for information on the different permission options and how to configure permissions.

## Create a Log Analytics workspace

A Log Analytics workspace allows you to collect data based on a variety or requirements, such as geographic location of the data, subscription boundaries, or access to resources. Learn how to [create a Log Analytics workspace](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/quick-create-workspace).

To learn how to set up a Log Analytics workspace for Azure resources outside of Microsoft Entra ID, see [Collect and view resource logs for Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/diagnostic-settings).

## Send logs to Azure Monitor

Use the following steps to send logs from Microsoft Entra ID to Azure Monitor logs.

Tip

Steps in this article might vary slightly based on the portal you start from.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator).
2. Browse to **Entra ID** > **Monitoring & health** > **Diagnostic settings**. You can also select **Export Settings** from either the **Audit Logs** or **Sign-ins** page.
3. Select **+ Add diagnostic setting** to create a new integration or select **Edit setting** for an existing integration.
4. Enter a **Diagnostic setting name**. If you're editing an existing integration, you can't change the name.
5. Select the log categories that you want to stream. For a description of each log category, see [What are the identity logs you can stream to an endpoint](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-log-monitoring-integration-options-considerations).
6. Under **Destination Details** select the **Send to Log Analytics workspace** check box.
7. Select the appropriate **Subscription** and **Log Analytics workspace** from the menus.
8. Select the **Save** button.

   ![Screenshot of the diagnostics settings with some destination details shown.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/howto-integrate-activity-logs-with-azure-monitor-logs/diagnostic-settings-log-analytics-workspace.png)


   For more information about when logs start appearing in your Log Analytics workspace, see [Diagnostic settings in Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/platform/diagnostic-settings#time-before-telemetry-gets-to-destination).

## Related content

- [Analyze Microsoft Entra activity logs with Azure Monitor logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-analyze-activity-logs-log-analytics)
- [Learn about the data sources you can analyze with Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/data-sources)
- [Automate creating diagnostic settings with Azure Policy](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/diagnostic-settings-policy)
